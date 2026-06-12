---
title: "Veracrypt - how to mount volume using Terminal?"
date: 2017-10-22
forum: General Help
---

### Post by sprinterdriver on 2017-10-22
Hi.

Basically - title is the question.

I simply want to make it easier to mount one or more volume without using the gui to browse for container file and then browse for mounting folder - because that is just so tedious, especially since I always mount one or two volumes into the excact same folder each time.

The online documentation for Veracrypt does tell how to use command line, but that is for Windows only.

Is there anyone that have ever successfully mounted a Veracrypt file container into a folder using Linux?

---

### Post by sprinterdriver on 2017-11-01
update.

I also posted a similar question on Veracrypt home page:
[https://sourceforge.net/p/veracrypt/discussion/general/thread/6db864e1/](https://sourceforge.net/p/veracrypt/discussion/general/thread/6db864e1/)

So I'm almost there - but haven't figured out how to specify "iocharset=utf8" option on command line. I hope you guys at this forum is experienced users of Terminal and can provide help.

---

### Post by sprinterdriver on 2017-11-12
I'm still no closer to solve this issue.

Reading the man page for mount and for Veracrypt, one should think that --fs-iocharset=utf8 should be the argument to use, but no - instead I just get this stupid error message "Unknown long option". . .

I have tried the following commands but without success (same error message for all)
[[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")[[COLOR=#000000]veracrypt -t --fs-iocharset=utf8 /media/filecontainer.db /home/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")[[COLOR=#000000]sprinterdriver[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")[[COLOR=#000000]/fat-volume/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")
veracrypt -t --iocharset=utf8 /media/filecontainer.db /home/[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]sprinterdriver/fat-volume/
veracrypt -t --fs--iocharset=utf8 /media/filecontainer.db /home/[[COLOR=#000000]sprinterdriver[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]/fat-volume/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")
[[COLOR=#000000]veracrypt -t -v --fs-iocharset=utf8 /media/filecontainer.db /home/[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]sprinterdriver[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]/fat-volume/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")
veracrypt -t -v --fs-iocharset=utf8,codepage=866 /media/filecontainer.db /home/[[COLOR=#000000]sprinterdriver[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]/fat-volume/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")
veracrypt -t --fs-iocharset utf8 /media/filecontainer.db /home/[[COLOR=#000000]sprinterdriver[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]/fat-volume/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")
veracrypt -t --fs -iocharset=utf8 /media/filecontainer.db /home/[[COLOR=#000000]sprinterdriver[URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000]/fat-volume/[/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")
[[COLOR=#000000][URL="https://ubuntuforums.org/member.php?u=2068796"][COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=2068796")[/COLOR][/URL][/COLOR][/URL][/COLOR][/URL][/COLOR][/URL][/COLOR][/URL][/COLOR][/URL][/COLOR][/URL]
[/COLOR][/URL]

---

### Post by Holger_Gehrke on 2017-11-12
I'm just guessing, since I don't use veracrypt, but have you tried '--fs-options="iocharset=utf8" '? mencoder uses a similar syntax for options to pass to ffmpeg ...

Or -- if the graphical version acts just as a frontend and calls the command line version to do the actual work - you could mount your container using the frontend and then do a 'ps ax|grep vera' (ps cuts off the command at end of line if it detects it's doing output to a terminal; if its writing to a pipe or a file it doesn't ...) and will then see the correct syntax ...

Holger

---

### Post by sprinterdriver on 2017-11-23
Tank you very much for your help, Holger.

Haven't tested yet with filenames full of Ø and Æ characters yet, but the mounting of the volume seems to works just fine.

---

