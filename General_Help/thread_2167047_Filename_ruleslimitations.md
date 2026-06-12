---
title: "Filename rules/limitations"
date: 2013-08-12
forum: General Help
---

### Post by tapasray on 2013-08-12
I am in the process of moving out of Windows and into Ubuntu as completely as possible. One of the problems I am having to deal with has to do with filenames. I had given names starting with a period sign ('.') to a large number of files in Windows over the years ... they will easily run into the hundreds ... mainly to keep them at the top in their respective directories. Now that I am in Ubuntu 12.04 LTS, I can't see them at all. If I go back to Windows and delete the period signs, they show up nicely in Ubuntu. But it's next to impossible ... well, extremely time-consuming ... to change the names of all those hundreds of files. Wondering if there's a way around this. Would really appreciate some help. Thanks!

---

### Post by 3rdalbum on 2013-08-12
There are several bulk renamer utilities in the Ubuntu Software Center that you could try.

Or maybe somebody here could quickly knock up a three-line Bash script to remove the periods?

---

### Post by davetv on 2013-08-12
In Linux, putting a period at the start of a folder name or file name signifies  it is a hidden folder or file.

---

### Post by tapasray on 2013-08-12
Thanks, 3rdalbum! Will try that.

---

### Post by steeldriver on 2013-08-12
You could use the perl-based 'rename' utility

CAUTION: this will attempt to rename ALL 'dot files' in the current directory including any legitimately hidden system / application configuration files
[B]ONLY RUN IT IN A DIRECTORY IF YOU ARE SURE THE ONLY 'DOT FILES' ARE YOUR OWN WINDOWS DATA FILES
[/B]IN PARTICULAR [B]DON'T RUN IT IN THE TOP LEVEL OF YOUR HOME DIRECTORY
[/B]
```
GLOBIGNORE=.:.. ; rename -nv -- 's/^\.//' .*
```

I've left a '-n' switch in which is a dry-run (no op) - check the list of files it says it has renamed (it hasn't ... yet) and if they are all good then remove the 'n' and run it again

---

### Post by tapasray on 2013-08-12
Got it. Thanks, davetv. Won't make that mistake now.

Great! Thanks, steeldriver!

---

### Post by pholden on 2013-08-12
If you're viewing the directory in the nautilus browser, hit **Ctrl+H** to toggle viewing hidden files. If it's through a terminal, add the **-a** switch, i.e. *ls -la .* :)

---

### Post by 3rdalbum on 2013-08-12
I thought somebody would quickly knock up a small Bash script to automate the job, in the end I wrote an eight-line Python script. It will look at a directory that you specify and rename all the files that have a period at the beginning of the filename, so it no longer has a period at the beginning of the filename.

Instructions for use are inside the file.

I haven't done major testing of the script and it will not work around errors (what do you expect in eight lines!) but it should work well enough for most scenarios. The warnings Steeldriver gave you also apply to this script.

---

### Post by tapasray on 2013-08-12
Thanks, 3rdalbum and all others. I got myself pyRenamer, KRename and PrefixSuffix. The first two confused me. As for the third, after a couple of trial-and-error runs, I think I have the hang of it finally. 

Tomorrow's projects for myself - to try out your codes, and also to find out how to keep those priority files at the top of their respective directories, obviously without the period sign. I have tried with a '~' prefix but it doesn't work. Works in Windows, but that's beside the point.

---

