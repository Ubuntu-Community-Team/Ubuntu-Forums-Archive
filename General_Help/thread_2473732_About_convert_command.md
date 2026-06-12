---
title: "About convert command"
date: 2022-04-12
forum: General Help
---

### Post by satimis on 2022-04-12
I have >30 .webp files.  I can convert them to jpg files running```

convert xxx.webp xxx.jpg
convert yyy.webp yyy.jpg
convert zzz.webp zzz.jpg
etc

```

Can I run one command line to convert all .webp files to .jpg files?

Thanks

Regards

---

### Post by &amp;KyT$0P# on 2022-04-12
Assuming your shell is bash or ksh,
```
for i in *.webp;do convert "$i" "${i%%.*}.jpg";done
```

---

### Post by satimis on 2022-04-12
> **halogen2 said:**
> Assuming your shell is bash or ksh,
```
for i in *.webp;do convert "$i" "${i%%.*}.jpg";done
```
Thanks for your advice

$ apt policy ksh```

ksh:
  Installed: (none)
  Candidate: 2020.0.0-5
  Version table:
     2020.0.0-5 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
```
        
Shall I install ksh?
        
All .webp files are in Botanic_webp folder.  If I expect all output .jpg files be directed to Biotanic_jpg folder, how to change your command line?

Thanks.

Regards

---

### Post by &amp;KyT$0P# on 2022-04-12
> **satimis said:**
> Shall I install ksh?

It's not necessary for this if you can use bash.

> All .webp files are in Botanic_webp folder. If I expect all output .jpg files be directed to Biotanic_jpg folder, how to change your command line?

[s]Open Terminal in the directory containing the "Botanic_webp" and "Botanic_jpg" folders, and try -
```
for i in Botanic_webp/*.webp;do convert "$i" "Botanic_jpg/${i%%.*}.jpg";done
```[/s]
* #-o Oops, the now-struck-through suggestion won't work as the [FONT=Courier New]$i[/FONT] is not just the filename, but "Botanic_webp/<filename.webp>" and the above code forgot to account for that.  Sorry :(

---

### Post by dragonfly41 on 2022-04-12
Have you tried pandoc?

[https://github.com/jgm/pandoc/issues/5267](https://github.com/jgm/pandoc/issues/5267)

---

### Post by TheFu on 2022-04-13
There are lots of common patterns in shell scripting. One is to do something with files provided as input:
```
#!/bin/bash

for IN in Some-globbing-pattern*  ; do
   OUT="${IN/%.png/.jpg}"
   convert "$IN"  "$OUT"
 done
```

This can be more generalized by using the $@ which gets the files from the shell pattern match instead:
```
#!/bin/bash

for IN in $@  ; do
   OUT="${IN/%.png/.jpg}"
   convert "$IN"  "$OUT"
 done
```
But the creation of "$OUT" will fail if the input pattern above doesn't have png at the end.

We can also use **xargs** for stuff like this:
```
find . -iname \*png | xargs printf "\nFound: %s" 
```
It doesn't work well if we need to specify both the input AND the output filename, but if we just need to specify the input, xargs is an excellent tool.  For long running stuff, xargs can parallelize X number of processes. We can choose how many to be used.  1, 20, 500, whatever our system supports.  We can also tell xargs how many inputs to chunk for each command, if the command to be run will handle some number of inputs, but we have many, many, more than allowed.  Say we have 20,000 files. It would be smart to chunk the processing into batches of 50 or so.

---

### Post by satimis on 2022-04-13
> **halogen2 said:**
>  .....
.....
(I assume that "Biotanic_jpg" was not a typo.)

Sorry I don't follow.

Structure of folders:

Image Storage folder;
Botanic_webp (sub-folder)
Botanic_jpg (sub-folder)

Botanic_webp (sub-folder) containing all .webp files
Botanic_jpg (sub-folder) is an empty folder, created for containing all output .jpg files

Regards

---

### Post by satimis on 2022-04-13
> **dragonfly41 said:**
> Have you tried pandoc?

[https://github.com/jgm/pandoc/issues/5267](https://github.com/jgm/pandoc/issues/5267)
No

pando is on repo

$ apt policy pandoc```

pandoc:
  Installed: (none)
  Candidate: 2.5-3build2
  Version table:
     2.5-3build2 500
        500 http://hk.archive.ubuntu.com/ubuntu focal/universe amd64 Packages

```

'Convert' works great, able to convert image files to different format.

Regards

---

### Post by &amp;KyT$0P# on 2022-04-13
> **satimis said:**
> Sorry I don't follow.

Structure of folders:

Image Storage folder;
Botanic_webp (sub-folder)
Botanic_jpg (sub-folder)

Botanic_webp (sub-folder) containing all .webp files
Botanic_jpg (sub-folder) is an empty folder, created for containing all output .jpg files

Regards

Thanks for clarifying.  I edited my post based on this information.

---

### Post by satimis on 2022-04-13
> **halogen2 said:**
> Thanks for clarifying.  I edited my post based on this information.
Performed following steps;

$ cd Videos/Image_Storage/
$ ls```

Botanic_jpg  Botanic_webp

```

$ for i in Botanic_webp/*.webp;do convert "$i" "Botanic_jpg/${i%%.*}.jpg";done > convert.txt```

.....
.....
.....
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Petals_and_Water.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Phalaenopsis_Orphan_Annie.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Rocky_Mountain_Columbines.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Roses_Say_I_Love_You.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Spouting_Horn_Kauai_Hawaii.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Towards_the_Sky.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Tropical_Harmony.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Tropical_Setting_Hawaii.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Vines_and_Flowers_Brixen_Italy.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.
convert-im6.q16: unable to open image `Botanic_jpg/Botanic_webp/Wild_Cotton.jpg': No such file or directory @ error/blob.c/OpenBlob/2874.

```

Fail.

convert.txt is an empty file

Regards

---

### Post by &amp;KyT$0P# on 2022-04-13
#-o Sorry, I make that mistake too often :( Try this instead
```
cd Videos/Image_Storage/Botanic_webp
for i in *.webp;do convert "$i" ../Botanic_jpg/"${i%%.*}.jpg";done
```

---

### Post by satimis on 2022-04-14
> **halogen2 said:**
> #-o Sorry, I make that mistake too often :( Try this instead
```
cd Videos/Image_Storage/Botanic_webp
for i in *.webp;do convert "$i" ../Botanic_jpg/"${i%%.*}.jpg";done
```
Performed following steps;

$ cd Videos/Image_Storage/Botanic_webp/
$ for i in *.webp;do convert "$i" ../Botanic_jpg/"${i%%.*}.jpg";done
$ cd ..
$ ls Botanic_jpg/```

Clipper.jpg                              Grand_Teton_and_Wildflowers_Wyoming.jpg  Petals_and_Water.jpg
Day_Lily.jpg                             Hawaiian_Plumeria.jpg                    Phalaenopsis_Orphan_Annie.jpg
Deptford_Pink_and_Queen_Anne_s_Lace.jpg  Helani_Gardens_Maui.jpg                  Rocky_Mountain_Columbines.jpg
Drummond_s_Skullcap.jpg                  Illuminating_Cactus_Flower.jpg           Roses_Say_I_Love_You.jpg
Dune_Primrose_and_Sand_Verbena.jpg       Indiana_Wildflowers.jpg                  Spouting_Horn_Kauai_Hawaii.jpg
Fall_Garden_Poulsbo_Washington.jpg       Keukenhof_Holland.jpg                    Towards_the_Sky.jpg
......
......

```

Your command line works here.  Lot of thanks

**[COLOR="#FF0000"]Edit:[/COLOR]**
**Could you please help me to understand the function of your command line?  Thnaks**

Regards

---

### Post by satimis on 2022-04-14
> **TheFu said:**
> There are lots of common patterns in shell scripting. One is to do something with files provided as input:
```
#!/bin/bash

for IN in Some-globbing-pattern*  ; do
   OUT="${IN/%.png/.jpg}"
   convert "$IN"  "$OUT"
 done
```

This can be more generalized by using the $@ which gets the files from the shell pattern match instead:
```
#!/bin/bash

for IN in $@  ; do
   OUT="${IN/%.png/.jpg}"
   convert "$IN"  "$OUT"
 done
```
But the creation of "$OUT" will fail if the input pattern above doesn't have png at the end.

We can also use **xargs** for stuff like this:
```
find . -iname \*png | xargs printf "\nFound: %s" 
```
It doesn't work well if we need to specify both the input AND the output filename, but if we just need to specify the input, xargs is an excellent tool.  For long running stuff, xargs can parallelize X number of processes. We can choose how many to be used.  1, 20, 500, whatever our system supports.  We can also tell xargs how many inputs to chunk for each command, if the command to be run will handle some number of inputs, but we have many, many, more than allowed.  Say we have 20,000 files. It would be smart to chunk the processing into batches of 50 or so.
Hi,

Your advice noted.  Thanks

Regards

---

### Post by &amp;KyT$0P# on 2022-04-14
> **satimis said:**
> Your command line works here.  Lot of thanks

You're welcome! :KS

> **[COLOR="#FF0000"]Edit:[/COLOR]**
**Could you please help me to understand the function of your command line?  Thnaks**

Regards

Sure.

```
for i in *.webp;do
```
This part starts a [shell [FONT=Courier New]for[/FONT] loop]("https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-7.html") looping over the [glob expansion]("https://www.baeldung.com/linux/bash-globbing") of [FONT=Courier New]*.webp[/FONT] in the current working directory.

```
convert "$i" ../Botanic_jpg/"${i%%.*}.jpg"
```
Run [FONT=Courier New]convert[/FONT] with input file being the current item iterated over in the [FONT=Courier New]for[/FONT] loop.  Output filename is constructed by removing the extension from the input filename, then inserting that into the string [FONT=Courier New]../Botanic_jpg/[COLOR="#FF0000"]<inserted here>[/COLOR].jpg[/FONT].

The input and output filenames are double-quoted in case the filename might contain characters that are special to the shell, so that the shell knows it's all part of the filename.

The %% syntax is described in more detail on [this page]("https://tldp.org/LDP/abs/html/string-manipulation.html"), which also describes other types of variable manipulations.

```
done
```
Closes the for loop and starts running it.

---

### Post by satimis on 2022-04-15
Hi halogen2,

Lot of thanks for your detailed explanation on post #14 and your time spent to help me.

I'll take time to learn;
*** Introduction to Bash 
Globbing        
[https://www.baeldung.com/linux/bash-globbing](https://www.baeldung.com/linux/bash-globbing)

and

*** Advanced Bash-Scripting Guide
An in-depth exploration of the art of shell scripting
[https://tldp.org/LDP/abs/html/](https://tldp.org/LDP/abs/html/)

Best Regards

---

