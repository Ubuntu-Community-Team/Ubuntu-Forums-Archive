---
title: "User's password failed : I have to change it"
date: 2015-09-18
forum: General Help
---

### Post by Dionisio_Dussart on 2015-09-18
As I was trying commands that included changes in environment variables, I needed to turn off my laptop and open it again (after modifying a .bash_profile file). 
So I turned it off. And then wanted to open again Linux ubuntu. But this time, being asked to give my password, which is the user "user" 's password, and introducing it the same as I did other times, I got a refusal. It's probably due to using a french keyboard and being between one of the french keyboard versions.
I live in Canada and use the 100% french keyboard but I suppose I made a change that made me switch to something franco-canadian, necessarily mysterious, impossible to find out.
I suspect there might have been a corrupted file, maybe a virus that changed my password.
The thing is ... **I need now to change my password**.
Usually it's easy. It would be just to go to gnome-terminal and use the command passwd ... using then the old password. I tried it, in vane.
It's really like my password has changed.
So i took some advice. My purpose here is to check is IF what I was advised to do would 1°) work; 2°) avoid destroying my files.
# Shift while PC is starting up => the Grub page will open
# On that page, choose second line and open it. Starting up mode.
# Choose ROOT as way of acting (sorry ... I am translating : was written in French)
# Mount the system partition with reading and writing rights : mount -o rw,remount /
# Modifying then, being "root", the password : passwd user
# ... which is then easy : just introducing twice the new password, without giving the old one
# Reboot it : reboot
What I suspect is that "mount", then "remount /" (by the way : just a command between them ? does it make sense ?) would be similar as a "format C" in MS-Dos.
I did not get any answer about it which meant for me a Yes. But I need to save my old files.

---

### Post by nknwn on 2015-09-18
Change password before boot:
[http://ubuntuforums.org/showthread.php?t=133102](http://ubuntuforums.org/showthread.php?t=133102)

If you want to back your files just boot with a live Linux disk and copy your important files to some other device, pen rive of external hard drive.

---

### Post by deadflowr on 2015-09-18
I'd guess since these problems occurred after you mucked about with some file, then the problems are related to the changes you tried to make to said file.
Do you remember the exact files you were making changes to?
(Bonus if you remember what changes you made to them.)

---

### Post by Dionisio_Dussart on 2015-09-18
Thank you. Looks interesting. Hopefully helpful. (Otherwise I'll be back ...)

---

### Post by Dionisio_Dussart on 2015-09-18
> **deadflowr said:**
> Do you remember the exact files you were making changes to?
(Bonus if you remember what changes you made to them.)

~/.bashrc
~/.bash_profile.
After noticing my modifications on bash_profile were without effect, I decided to transfer them to bashrc.
They included a modification of environmental variables ... LANG ... something like that was declared fr_FR UTF-8 which apparently messed it all up. 
I saw Indeed appear the ridiculous mention "Français obsolète". Typically a franco-canadian trick. I am probably supposed to write their way. I should try, actually. But I suspect this time my laptop would explode (it's a really french one) so I want by any means make something else.

---

### Post by Sweet_Baby_Jamie on 2015-09-18
> **nknwn said:**
> Change password before boot:
[http://ubuntuforums.org/showthread.php?t=133102](http://ubuntuforums.org/showthread.php?t=133102)

If you want to back your files just boot with a live Linux disk and copy your important files to some other device, pen rive of external hard drive.

Psychocats has a nice description of the process complete with screenshots!


[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Dionisio_Dussart on 2015-09-19
> **Sweet_Baby_Jamie said:**
> Psychocats has a nice description of the process complete with screenshots!


[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Thanks for adding this link, this being said thanks also to nknwn.
I did this, according to these instructions :
- Turn off the laptop then turn it on.
- Press shift (which was not what said nknwn's recommended link) for some seconds.
Then opened a GNU GRUB Version 2.02 window.
- I chose the second option : "Options avancées pour Ubuntu"
- I chose again the second option : "Ubuntu with Linux 3.13.0.49-generic (recovery mode)".
Then i saw flowing lots of impossible to understand lines.
Then this finally arrived to "Menu de récupération" (whose options are in english).
- I chose the almost last one : "root".
Then ... !!! I was asked "give root password for maintenance" !!!! (or type Ctrl-D to continue)
- I typed Ctrl-D which was just a way of going back to "Menu de récupération".
- Without any solution, unable to be really declared "root" and make the password command
I chose the first option of this menu : "resume".
And here I am, still "guest" on my very own laptop, unable to access to the files that I
put inside my former (I hope it still exists) /home/user directory.

---

### Post by Dionisio_Dussart on 2015-09-19
> **nknwn said:**
> Change password before boot:
[http://ubuntuforums.org/showthread.php?t=133102](http://ubuntuforums.org/showthread.php?t=133102)


This was in 2005. It was much simpler than now.
Probably for security reasons, there have been changes. You can see below another link (psychocats) more recent.
And i tried it. And it still is simpler than what should be done, that i don't know yet.

> **nknwn said:**
> 
If you want to back your files just boot with a live Linux disk and copy your important files to some other device, pen rive of external hard drive.

Thank you for the advice. Looks like it's what I have to do, and forget the files (fortunately, not relying on it I didn't put lots of files at that place) at my ... former ? ):P ... "user" space.

---

