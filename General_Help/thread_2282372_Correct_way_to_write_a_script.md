---
title: "Correct way to write a script"
date: 2015-06-13
forum: General Help
---

### Post by gr8 on 2015-06-13
I put together a script that barely works. Is there a tutorial for the right way to write these things? I want to take an ffmpeg command I use on a file and apply it to a whole directory.

*ffmpeg -i file.mp4 {commands} newfile.mp4* 

Can I just do something like below and apply it to a whole directory.

*ffmpeg -i *.mp4 {commands} "\newfiles\*.mp4"*

---

### Post by Holger_Gehrke on 2015-06-13
> **gr8 said:**
> I put together a script that barely works. Is there a tutorial for the right way to write these things? 

There's a sticky thread [over in the New to Ubuntu Forum]("http://ubuntuforums.org/showthread.php?t=2015424"). A lot of the resources mentioned there also apply to scripting, for example "Advanced Bash Scripting" or the free ebook "The Linux Command Line".

> **gr8 said:**
> 
I want to take an ffmpeg command I use on a file and apply it to a whole directory.

*ffmpeg -i file.mp4 {commands} newfile.mp4* 

Can I just do something like below and apply it to a whole directory.

*ffmpeg -i *.mp4 {commands} "\newfiles\*.mp4"*

There's always a way to do something you want -- or need -- to do. 

```

for i in *mp4 ; do ffmpeg -i "$i" ...commands... "/newfiles/$i.mp4"; done

```
(directly on the command line or as a script) would be one way; another would be
```

#!/bin/bash
while [ -n $1 ] ; do 
  ffmpeg -i "$1" ...commands... "/newfiles/$1.mp4"
  shift
done

```
(as a script) would be another; the latter one accepts parameters which can use wildcards (wildcards are expanded into lists of files by the shell before the script is executed); by **shift**ing the parameters (the first parameter gets lost, the second becomes the first, the third becomes second and so on) and using a loop, which stops when the first parameter is empty, all files passed as parameters or matched by wildcards will get converted.

---

