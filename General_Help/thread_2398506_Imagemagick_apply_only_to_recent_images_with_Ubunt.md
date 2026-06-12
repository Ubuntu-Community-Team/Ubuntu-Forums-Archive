---
title: "Imagemagick apply only to recent images with Ubuntu"
date: 2018-08-13
forum: General Help
---

### Post by ultragamer2 on 2018-08-13
I am using Imagemagick to mogrify some images from png to jpg.

So you go to the folder with the
cd "folder" command

I am using the command                          [FONT=Verdana][SIZE=2]
mogrify -format jpg *.png

[SIZE=2]But I only want it to affect the images with a modified date of today but there is apparently no such command in imagemagick is there a way to write a command that puts a Ubuntu command before the mogrify to only affect images modified or created today automatically?

*Using the latest Ubuntu 18.04.*[/SIZE]
[/SIZE][/FONT]

---

### Post by TheFu on 2018-08-13
I would make a list of files using **find**, then using the -exec option, have find call **mogrify**.  This assumes only the files I want are found. 

 Find doesn't have much resolution with date-bases searches, so it is usually easier to use find to get files with an mtime less than 1day, then manually trim that list to files for today only.  An **ls -l |sort** on the correct field should show which files are good and which files should be out.

You can find examples of **find** with google. Seeing some examples is really helpful.

---

### Post by Holger_Gehrke on 2018-08-13
There are two  ways around the low resolution of find with the '-atime', '-ctime' and '-mtime' (which  have a resolution of 1 day). Either use the minute-based '-amin N', '-cmin N' and '-mmin N' (N= number of minutes, put a - before the number for files newer than that or a + for files older than that, example '-mmin -60' files newer than 1 hour) options or create a temporary file, set its modification time with 'touch -d "date and time to set as a string" name-of-file' and then use  find with the option '-newer name-of-file'. If you want to work on just the files modified in the current session, you could use the file '~/.xsession-errors.old' as a reference, since it always has the end of the last session as it's mtime.

Holger

---

### Post by ultragamer2 on 2018-08-14
Actually I got it to work using just the 1 day, I don't need really specific times but thanks for the info it's good to know.

---

### Post by TheFu on 2018-08-14
> **ultragamer2 said:**
> Actually I got it to work using just the 1 day, I don't need really specific times but thanks for the info it's good to know.

Agreed!   Options for commands change slowly, but some like being able to minutes in a **find** command are completely new to me. I don't remember those being available on Solaris, HP-UX, AIX, or any other Unix. 

In the last 10 yrs, lots of extra convenience options have been added to multiple commands. When the -h option was added to sort, free, df, du, and a few others, I got really happy. "Human readable" is a great thing in my book. Sorting that understands human readable file sizes like 3G or 40M  or 8K is a wonderful thing.

If this is solved, please use the thread tools near the top to mark so. That helps the community greatly.

---

### Post by mjonutz on 2018-08-24
Not all the time i use Imagemagick, for simple image processing like resizing and cropping i use an online image resizer tool. This one is fairly easy to use [http://resizemyimg.com](http://resizemyimg.com)

---

