### apsw
---
https://github.com/rogerbinns/apsw

https://rogerbinns.github.io/apsw/

```py
// tools/coverageanalyser.py
import glob
import os
import sys

out=sys.stdout.write

def output(filename, percent, total):
  op=["%-40s" % (filename,),
    "% 3.2f%%" %(percent,),
    " of % 6d" % (total,)]
  if percent==100:
    op[1]="100.00%"
  out("".join(op)+"\n")

linesexecuted=0
linestotal=0

names=glob.glob("src/*.c.gcov")
names.sort()

for f in names:
  if f.startswith("sqlite3"):
    continue
  fileexec=0
  filetotal=0
  for line in open(f, "rtU"):
    if ":" not in line: continue
    line=line.split(":", 1)[0].strip()
    if line=="-":
      continue
     if line!="#####":
       linesexecuted+=1
       fileexec+=1
     linesotal+=1
     filetotal+=1
   n=os.path.splitext(f)[0]
   output(n, fileexec*100.0/filetotal, filetotal)

out("\n")
output("Total", linesexecuted*100.0/(linestotal if linestotal else 1), linestotal)
```

```
```

```
```
