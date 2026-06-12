---
title: "[SOLVED] Help with Shell Script."
date: 2008-01-06
forum: General Help
---

### Post by papafreebird on 2008-01-06
Hello all.  I'm relatively new to linux (but so far really enjoying it).  I am really fairly adept at windows using the command prompt and / or gui but in linux I really don't know much if any about shell scripts.  In windows I can make a bat file that will create a multiline text file by doing this.

for %%a in (*.avi) do echo whatever > whatever.txt & echo line2 >> whatever.txt & echo line3 >> whatever.txt

this would create a text file for every avi file in the directory like this

whatever
line2
line3

How would I accomplish the same thing using shell script?  
Any suggestions woiuld be appreciated.

---

### Post by PinkFloyd102489 on 2008-01-06
So you're wanting to create a txt file with the same name as the avi file?

---

### Post by Old *ix Geek on 2008-01-07
I'm really not clear on exactly what it is you're trying to accomplish; perhaps an actual example would help clear things up.  Let's say you have a directory with files named:

file1.avi
file2.avi
file3.avi
...
file10.avi

What do you want to end up with in that directory?  What do you want in each multi-line text file?  Do you want a text file with the same base name for each avi file, i.e., file1.txt, file2.txt, and so on?

As a general rule, keep in mind that the *nix shell provides a sophisticated, powerful programming environment, whereas the windoze shell (or whatever they call it) is rudimentary at best.  ANYTHING that can be done in windoze can be done in *nix, but the reverse is definitely not true.  So even though I'm unclear on what you're trying to accomplish, I can say without hesitation that it's not only doable in a Linux shell, but it can be done better, cleaner and faster than in windoze.

---

### Post by ntowakbh on 2008-01-07
> **papafreebird said:**
> Hello all.  I'm relatively new to linux (but so far really enjoying it).  I am really fairly adept at windows using the command prompt and / or gui but in linux I really don't know much if any about shell scripts.  In windows I can make a bat file that will create a multiline text file by doing this.

for %%a in (*.avi) do echo whatever > whatever.txt & echo line2 >> whatever.txt & echo line3 >> whatever.txt

this would create a text file for every avi file in the directory like this

whatever
line2
line3

How would I accomplish the same thing using shell script?  
Any suggestions woiuld be appreciated.

If you want to make a text file, the lists every .avi file in a directory:
```

ls *.avi > file.txt

```

---

### Post by amo-ej1 on 2008-01-07
Bash has the same behaviour

This code will create a new file containing a(followed with a newline), or if the file bla.txt exists already, the previous contents will be overwritten.
```
echo a > bla.txt     
```   

This will append new data to the file bla.txt 
```
echo  b >> bla.txt
```

As stated about ls *.avi > file.txt is what you really want, but the following is an example of your script version:

```

rm -f bla.txt 
for i in *avi ; do echo $i >> bla.txt ; done 

```

The first line removes the file, the second line stores all *.avi in a variable $i (mind the missing $ sign at declaration) en appends it to a textfile.

---

### Post by papafreebird on 2008-01-07
Hello again,

My appologies for not being clear on what I want.  I was worried that I didn't give enough.  Whats funny is that is one of my pet peeves when I answer questions on another forum....

Here is an exact copy of one of my windows bat files.

for %%a in ("*.avi") do echo Avisource("%%a") > "%%a.avs" & echo converttoyv12() >> "%%a.avs" & echo LanczosResize(352,480) >> "%%a.avs"

This bat would produce an avisynth script for each avi file in the directory and the avisynth script would have three lines.

So If the directory had three files...file1.avi, file2.avi, and file3.avi
running that bat would produce three avs files like so.


file1.avi.avs containing the following text
Avisource("file1.avi")
converttoyv12()
LanczosResize(352,480)




file2.avi.avs containing the following text
Avisource("file2.avi")
converttoyv12()
LanczosResize(352,480)




file3.avi.avs containing the following text
Avisource("file3.avi")
converttoyv12()
LanczosResize(352,480)


Once again you have my appologies for the unclear first post and my thanks for trying to help me regardless of that!
:)

---

### Post by juaka on 2008-01-07
> **amo-ej1 said:**
> Bash has the same behaviour

This code will create a new file containing a(followed with a newline), or if the file bla.txt exists already, the previous contents will be overwritten.
```
echo a > bla.txt     
```This will append new data to the file bla.txt 
```
echo  b >> bla.txt
```As stated about ls *.avi > file.txt is what you really want, but the following is an example of your script version:

```

rm -f bla.txt 
for i in *avi ; do echo $i >> bla.txt ; done 

```The first line removes the file, the second line stores all *.avi in a variable $i (mind the missing $ sign at declaration) en appends it to a textfile.


based on that explanation, try

```
for i in *.avi; do
echo "Avisource(\""$i"\")" > $i.avs;
echo "converttoyv12()" >> $i.avs;
echo "LanczosResize(352,480)" >> $i.avs;
done
```

You can copy&paste that code directly into the terminal, no need to create the file.

---

### Post by dagnabit dang doohickey on 2008-01-07
One-liner:
```
for i in *.avi ; do echo -e "Avisource(\"$i\")\nconverttoyv12()\nLanczosResize(352,480)" > "$i.avs" ; done
```

Shell script:
```

#!/usr/bin/env bash

for i in *.avi ; do
    echo -e "Avisource(\"$i\")\nconverttoyv12()\nLanczosResize(352,480)" > "$i.avs"
done

exit 0

```

Another shell script:
```

#!/usr/bin/env bash

for i in *.avi ; do

cat > "$i.avs" <<ENDFILE
Avisource("$i")
converttoyv12()
LanczosResize(352,480)
ENDFILE

done

exit 0

```


Edit: Quoted the outputs to accommodate filenames with spaces per papafreebird's subsequent post.

---

### Post by papafreebird on 2008-01-07
> **dagnabit dang doohickey said:**
> One-liner:
```
for i in *.avi ; do echo -e "Avisource(\"$i\")\nconverttoyv12()\nLanczosResize(352,480)" > $i.avs ; done
```


Beautiful!!!!!!!!!!!!!!
That worked perfectly.  I just changed it to accomodate spaces in the filenames like so
```
for i in *.avi ; do echo -e "Avisource(\"$i\")\nconverttoyv12()\nLanczosResize(352,480)" > "$i.avs" ; done
```
and it worked great.  It created seperate avs files for each avi file in the directory.  Exactly what i wanted.  Thank you so much to all who helped.  

:)):P

---

