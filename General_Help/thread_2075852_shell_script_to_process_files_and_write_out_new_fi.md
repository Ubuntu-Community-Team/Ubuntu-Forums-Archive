---
title: "shell script to process files and write out new file with different extension"
date: 2012-10-24
forum: General Help
---

### Post by PaulHuffman on 2012-10-24
I have some ascii lidar files that need to have the first column in each line removed to get them ready for the XYZI format of the ASCII 3D To Feature Class tool. I wanted to make a list of all the files in a folder with the suffix .gnd and output the modified data to files with the same name but a txt suffix so the original ascii files were not modified.

What I used to do was I had an XP machine with Unix services for Windows installed that somehow let me use the Linux cut command inside a dos bat file:
```
for %%f in (*.gnd) do call :sub %%f %%~nf 
GOTO:EOF

:sub
cut -d" " -f2-4 %1 > %2.txt
```

The DOS %~ can give you a lot of useful file name manipulations. I installed Unix Services for Windows on a new Win 7 64 machine, and I don't understand why, but cut is not available to bat files on the new machine, although I can start a Unix C or K shell where cut is available but the %~n trick is not. 

Seems like I could do this all with Linux shell scripting but I'm stuck at how to change the extension of the output file name. 

I got started with python, but got stuck: 
```
env.workspace = "G:/elevation/lidar2010/points/asc_grounds"
fileSuffix = ".gnd"
txtList = arcpy.ListFiles("*" + fileSuffix)
    for file in txtList:
        for line in open("my file"):
        parts = line.split(" ")
        print " ".join(parts[1:4])
```

Then I was stuck. I guess I need a new line inside the first loop to write the file to a new file name with a .txt suffix, and I haven't even figured out how to get the file name stripped of the suffix.

---

### Post by Vaphell on 2012-10-24
> Seems like I could do this all with Linux shell scripting but I'm stuck at how to change the extension of the output file name. 

that's easy, bash has toys for simple text manipulation
[http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion](http://www.gnu.org/software/bash/manual/bash.html#Shell-Parameter-Expansion)

```
for f in *.gnd; do cut -d' ' -f2-4 "$f" > "${f%.*}.txt"; done
```

**${[COLOR="Blue"]f[/COLOR][COLOR="DarkGreen"]%[/COLOR][COLOR="Sienna"].*[/COLOR]}.txt** removes [COLOR="DarkGreen"]shortest possible[/COLOR] [COLOR="Sienna"].(anything)[/COLOR] [COLOR="DarkGreen"]from the right side[/COLOR] of the [COLOR="Blue"]filename[/COLOR] and glues the result with .txt

---

### Post by drmrgd on 2012-10-24
I'm not sure what the Unix services entails, but if is has awk built in, you might be able to strip out the first column with something like:

```
awk '{OFS="\t"; $1=""; print}' <file>
```

which you might be able to string into your for loop:

```
for f in *.gnd; do awk '{$1=""; print}' "$f" > "${f%.*}.txt"; done
```

Haven't tested that, but it should be close.

EDIT: Mistyped the output file.  Oh wait, I may have misunderstood...thought you said cut was not availble, but after reading Vaphell's post, I see that it might be and I didn't understand you correctly.  If you have cut, it's probably better! :P

---

### Post by Vaphell on 2012-10-24
it is me who probably misunderstood. I used bash features but i don't see OP mention having it (only csh/ksh and i never used them)

edit: it appears that at least ksh supports the same expansion options so my previous post stands
[http://www2.research.att.com/sw/download/man/man1/ksh.html](http://www2.research.att.com/sw/download/man/man1/ksh.html)

> ${parameter %pattern }

${parameter %%pattern }

    If the shell pattern  matches the end of the value of parameter, then the value of this expansion is the value of the parameter  with the matched part deleted; otherwise substitute the value of parameter. In the first form the smallest matching pattern is deleted and in the second form the largest matching pattern is deleted. When parameter  is @, *, or an array variable with subscript @ or *, the substring operation is applied to each element in turn. 



---

### Post by drmrgd on 2012-10-24
The other problem with my method is that I over simplified it and found that it leaves behind some white space, which wasn't immediately noticeable until I tried it on a different column:

```
$ awk 'NR>1 {$1=""; print}' MPACT_hotspots_v2.0_rev3.bed | more
 11169360 11169361 COSM26975 0 + REF=C;OBS=G;ANCHOR=C AMPL535569155
 11169725 11169726 COSM13324 0 + REF=G;OBS=A;AqNCHOR=C AMPL535311535
 11174457 11174458 COSM51966 0 + REF=A;OBS=G;qANCHOR=G AMPL535573086
 11184558 11184559 COSM51889 0 + REF=G;OBS=A;ANCHOR=G AMPL535502114
```

There's a slight indent in the first column, which becomes even more obvious when I tab delimit the output:

```
$ awk 'NR>1 {OFS="\t"; $1=""; print}' MPACT_hotspots_v2.0_rev3.bed | more
        11169360        11169361        COSM26975       0       +       REF=C;OBS=G;ANCHOR=C    AMPL535569155
        11169725        11169726        COSM13324       0       +       REF=G;OBS=A;ANCHOR=C    AMPL535311535
        11174457        11174458        COSM51966       0       +       REF=A;OBS=G;ANCHOR=G    AMPL535573086
        11184558        11184559        COSM51889       0       +       REF=G;OBS=A;ANCHOR=G    AMPL535502114
        11184572        11184573        COSM20417       0       +       REF=G;OBS=T;ANCHOR=G    AMPL535502114
        11184613        11184614        COSM95905       0       +       REF=G;OBS=C;ANCHOR=A    AMPL535502114

```

So, yeah, if you have cut, go with that, or modify the awk script to take care of the extra space :)

---

### Post by PaulHuffman on 2012-10-24
Vaphell's solution worked really well. The output file had UNIX line endings but that didn't bother the Windows program I used on the next step.  

I haven't used this "Subsystem for UNIX based applications" much, but the C shell window is awkward to use. No cut and pasting to the C shell, no command line editing that I could figure out. When I tried typing Vaphell's line in the C shell window, I got a complaint "Missing }". I don't know if I mistyped something or should have dropped to b shell to run this, but when I copied and pasted the line into Windows Notepad, saved it as a .sh file, the .sh file appeared in the C shell window as executable and ran through all the files in the directory just fine. 

The more elegant way of running this would be to run this cut shell script from my Ubuntu machine on files on the Windows machine via samba mounts like I used to do, but I don't have those running yet with this new Windows PC.

I'm still working on how to do this in python because the ESRI ArcGIS system I'm using on Windows has really aborted python. I could use on python script to reformat the input, then sent it into the ArcGIS tool in the same script if not in the same loop.

---

### Post by Vaphell on 2012-10-24
```
#!/usr/bin/env python

import glob
import os.path

workdir = "/home/me/test/python/"
fileSuffix = ".gnd"
outSuffix = ".txt"
fileList = glob.glob( workdir+"*"+fileSuffix )

for f in fileList:
  name, ext = os.path.splitext( f )
  infile = open( f, "r" ) 
  outfile = open( name+outSuffix, "w" )
  for line in infile:
    print >> outfile, " ".join( line.strip().split(" ")[1:4] )
  outfile.close()
  infile.close()

```

---

### Post by PaulHuffman on 2012-10-25
I like the use of glob. I need to read up on that.  But glob doesn't seem to be available on my Windows machine and python 2.7.2

---

### Post by Vaphell on 2012-10-25
so maybe something like this
```
#!/usr/bin/env python

import os

workdir = "/home/me/test/python/"
fileSuffix = ".gnd"
outSuffix = ".txt"
#fileList = glob.glob( workdir+"*"+fileSuffix )
fileList = [ os.path.join( workdir, f ) for f in os.listdir( workdir ) if f.endswith( fileSuffix ) ]

for f in fileList:
  name, ext = os.path.splitext( f )
  print name, ext
  infile = open( f, "r" ) 
  outfile = open( name+outSuffix, "w" )
  for line in infile:
    print >> outfile, " ".join( line.strip().split(" ")[1:4] )
  outfile.close()
  infile.close()
```

---

### Post by PaulHuffman on 2012-10-25
The ArcGIS software I'm working on has a python library that has some stuff that works, and is available to IDLE on Windows and the embedded python windows in ArcGIS. This works with that arcpy library:

```
import arcpy
import os

arcpy.env.workspace = r"G:\elevation\lidar2010\points\asc_grounds\"
fileSuffix = ".gnd"
fileList = arcpy.ListFiles("*" + fileSuffix)

for f in fileList:
    print "Processing file", f, "..."
    # Text File to Write Out
    txtFile = os.path.splitext(f)[0] + ".txt"
    fobj = open(txtFile, 'w')
    
    for line in open(f):
        parts = line.split(" ")
        fobj.write(" ".join(parts[1:4]))

    fobj.close()
```

I was wrong about glob not being available on Windows. The reason my file list was empty was that I had the slashes the wrong way in the directory string. It should be "G:/elevation/lidar2010/points/asc_grounds/" or I could have used the r literal quote construction.

---

