---
title: "[Kubuntu]Adept updater error : &quot;Could not commit changes&quot;"
date: 2007-01-04
forum: General Help
---

### Post by cgizmo on 2007-01-04
Hi,
I rencently got an error from adept updater saying : "There was an error committing changes. Possibly there was a problem downloading some packages or the commit would break packages". This error appears every time I try to install packages (at the beginning, in the "Preparing..." stage) and it first appeared when i put my computer on stand by while adept was running an install ](*,) .
Do you have any idea how to fix this?
If so, please post an answer!

---

### Post by NeoLithium on 2007-01-04
try ```
sudo dpkg --reconfigure -a
```

---

### Post by cgizmo on 2007-01-04
The option --reconfigure doesn't exist, so I tried configure, and it still doesn't work.

---

### Post by wersdaluv on 2007-02-03
Same case with mine. I also tried the code and got the same result. 

I attached a screenshot of what happened

---

### Post by calwolf on 2007-02-13
Same problem here... I'm new to linux, and have no clue what I did wrong.  Suggestions for getting rid of the error?  Thanks.

---

### Post by raskolnik0w on 2007-02-24
it's 
[FONT="Courier New"]sudo dpkg-reconfigure -a[/FONT] 
without a space, but i'm not shure if this is really what you want because then you are asked for every option of every package you have installed. 
maybe it's easier to use [FONT="Courier New"]sudo apt-get install 3dchess[/FONT] ,
than the system tries to install this package and tries to configure the packages that aren't configured, yet and you can see it's ouput. maybe this helps you to find out where the problem is.

---

### Post by f22buntu on 2007-03-09
I have the same problem and here are the details. :mad: 


(Reading database ... 172443 files and directories currently installed.)
Unpacking 3dchess (from .../3dchess_0.8.1-12_i386.deb) ...
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Setting up 3dchess (0.8.1-12) ...

Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by anachreon_ on 2007-03-11
Same problem here.  Also, anybody know how to get adept_notifier to run at startup again?  My brother stopped it loading into the system tray.

---

### Post by wolfger on 2007-11-20
So what the heck causes this to occur in the first place?

---

### Post by femitre on 2007-12-06
Please. Help. I have the same problem in 7.10! Sick. Thnx for helping!

---

### Post by RoShamBoU4It on 2007-12-07
Found a post on linuxforums.org that had a solution. Here is the text:

"Try this: Close out of Adept and open Konsole. Enter the following commands in order: "sudo apt-get install -f", "sudo dpkg --configure -a", "sudo apt-get autoremove", "sudo apt-get clean && sudo apt-get autoclean", and finally, "sudo apt-get update && sudo apt-get upgrade"."

I only needed the first two commands and a simple test confirmed that the configuration issue was corrected: "sudo apt-get install -f", "sudo dpkg --configure -a"

Good Luck.

---

### Post by Tzolkin on 2007-12-13
I had the same issue.. RoShamBoU4It's finding fixed it though. I hope it does not happen again...

---

### Post by jfank on 2007-12-13
> **RoShamBoU4It said:**
> Found a post on linuxforums.org that had a solution. Here is the text:

"Try this: Close out of Adept and open Konsole. Enter the following commands in order: "sudo apt-get install -f", "sudo dpkg --configure -a", "sudo apt-get autoremove", "sudo apt-get clean && sudo apt-get autoclean", and finally, "sudo apt-get update && sudo apt-get upgrade"."

I only needed the first two commands and a simple test confirmed that the configuration issue was corrected: "sudo apt-get install -f", "sudo dpkg --configure -a"

Good Luck.

You know I was having the problem with the update error, and I came across this topic.  I ran the codes that you gave above, and now my update works perfectly.  This might not help with everyone, but it should work.  I did this to all 4 of my computers, and they all update without a problem.  Thank you for posting those codes on here.

---

### Post by SneakPeak on 2008-01-11
I tried this which I found on another forum and it worked for me:

type the command in ur terminal "sudo apt-get -f install"

First time I typed it it asked me to run something else which I did. During the process I had to make a choice about Y, N and some other options. The default was N but I chose Y. I then ran the command above again and hey presto!!!

---

### Post by scottk on 2008-01-16
I just found this using a google search and I'm glad I did I was running Kubuntu in a virtual machine using Windoze I know I know I'm trying though! 

I was all set to kill it and write off the whole Ubuntu open source OS business but I ran the commands and now Adept manager works again. :guitar:
I found that it was the Java installer which had gone pear shaped must have been when Windoze crashed. Reinstalled and now it works :) One happy converter now to triple boot!:popcorn:

---

### Post by Eland on 2008-01-17
Well, this seems to be really helpfull, but unfortunatelly I had already tried this:

sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo dpkg --configure -a
-> read the output, you will have to answer a few questions
sudo dpkg --configure --pending

and now, when I try 

apt-get install -f

i get the errors:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Do you know any way to fix it?
p.s. Note that I'm completely newbie to Linux, I have Kubuntu 7.10 :roll:

---

### Post by sabresong on 2008-01-18
I've been getting this error a lot lately.  I thought I fixed it yesterday using the suggestions posted here, but it happened again today when I tried to apply updates.  When I used apt-get install -f, most of the updates did get applied, but one of the updates is now giving me a 403 error (permission denied).

It seems that every time I run the adept updater, I get this "could not commit changes" error.  Is this a bug in Gutsy?

---

### Post by AlanR8 on 2008-01-18
When this has happened to me in the past I've found the solution to be to run 

> sudo apt-get update

in terminal. The output will usually tell you what to run to fix the problem.

---

### Post by Val_0 on 2008-01-18
I get the same error when trying to update X.org through Adept Installer (cannot commit changes...). When running apt-get upgrade I get the 403 Forbidden error. Any ideas?

---

### Post by Val_0 on 2008-01-18
> **sabresong said:**
> I've been getting this error a lot lately.  I thought I fixed it yesterday using the suggestions posted here, but it happened again today when I tried to apply updates.  When I used apt-get install -f, most of the updates did get applied, but one of the updates is now giving me a 403 error (permission denied).

It seems that every time I run the adept updater, I get this "could not commit changes" error.  Is this a bug in Gutsy?

I found this on #kubuntu. "The latest security updates unfortunately broke Java and wxWidgets applications. See [https://launchpad.net/bugs/183969](https://launchpad.net/bugs/183969) for more information. The X.org package causing  the problem has been pulled from the repositories, which is why you currently get a "403 Forbidden" error." Hopefully this explains it a little bit more. You can update all the packages except that one. For now at least.


Quick update: (12:50 PST) Just tried running Adept Installer again. They added an extra packed to X.Org and everything updates fine.

---

### Post by Eland on 2008-01-19
Everything seems to be ok now!
After an update of Adept, and putting RoShamBoU4It's comments, my Adept Manager works  without errors! 
It was so simple.....

---

