---
title: "Help w/Gutsy pendrive - missing permissions"
date: 2008-02-20
forum: General Help
---

### Post by Akovia on 2008-02-20
Hi,
I tried searching the forums for my issue, but nothing seemed to match up. After a rocky start, [http://ubuntuforums.org/showthread.php?t=698158](http://ubuntuforums.org/showthread.php?t=698158) I did manage to get my pendrive/persistent install going. Before I posted to that thread I had installed Opera browser and did some minor configuration changes like import bookmarks and change the skin. I also changed the wallpaper and theme of the desktop. 

After making those changes I decided to reboot to see if everything would stay persistent. I hit restart and it showed the message to remove the media and press enter to reboot. Thinking it was just the same message from the Live-CD to prevent booting from media instead of the harddisk I left the USB in and rebooted. I use the bootloader that came with my mainboard that let's me select which media to boot from by pressing F8 as the machine is booting. This time when the boot menu came up, my pendrive was not listed. I noticed that the light was lit on my pendrive but couldn't understand why the bootloader didn't see it, as it doesn't care if it can boot or not, it just gives you the option to try.

I booted my harddisk and reset the USB and rebooted again. IT was there this time and booted fine. Problem is that "some" of my setting held, and some did not.

Network setup did not persist
Desktop changes did
Opera did and didn't

Investigating further in my Opera setting folder I noticed that there are some files with no permissions set at all.

ubuntu@ubuntu:~$ cd .opera/
[email]ubuntu@ubuntu:~/.oper[/email]a$ ls -la
ls: opera6.ini: Input/output error
total 172
drwx------ 10 ubuntu ubuntu  4096 2008-02-20 15:24 .
drwxr-xr-x 28 ubuntu ubuntu  4096 2008-02-20 16:04 ..
-rw-r--r--  1 ubuntu ubuntu 79589 2008-02-20 00:01 browser.js
drwxr-xr-x  2 ubuntu ubuntu  8192 2008-02-20 16:04 cache4
----------  1 ubuntu ubuntu   347 2008-02-20 15:24 cookies4.dat
-rw-r--r--  1 ubuntu ubuntu  1869 2008-02-20 15:30 global.dat
drwxr-xr-x  2 ubuntu ubuntu  4096 2008-02-20 00:19 images
-rw-r--r--  1 ubuntu ubuntu     0 2008-02-20 16:04 lock
drwxr-xr-x  4 ubuntu ubuntu  4096 2008-02-20 16:04 mail
-rw-r--r--  1 ubuntu ubuntu  1468 2008-02-20 00:47 notes.adr
drwxr-xr-x  2 ubuntu ubuntu  4096 2008-02-20 15:24 opcache
-rw-r--r--  1 ubuntu ubuntu    27 2008-02-20 00:18 opcert6.dat
----------  0 ubuntu ubuntu 15108 2008-02-20 16:04 opera6.ini
-rw-r--r--  1 ubuntu ubuntu    83 2008-02-20 00:19 opssl6.dat
-rw-r--r--  1 ubuntu ubuntu  3227 2008-02-20 00:01 override_downloaded.ini
-rw-r--r--  1 ubuntu ubuntu   497 2008-02-20 00:28 override.ini
-rw-r--r--  1 ubuntu ubuntu   181 2008-02-20 00:01 pluginpath.ini
drwxr-xr-x  2 ubuntu ubuntu  4096 2008-02-20 00:49 sessions
drwxr-xr-x  2 ubuntu ubuntu  4096 2008-02-20 00:03 skin
-rw-r--r--  1 ubuntu ubuntu   155 2008-02-20 00:47 spellcheck.ini
drwxr-xr-x  3 ubuntu ubuntu  4096 2008-02-20 00:01 styles
drwxr-xr-x  2 ubuntu ubuntu  4096 2008-02-20 16:06 toolbar
----------  1 ubuntu ubuntu   114 2008-02-20 15:24 vlink4.dat
-rw-r--r--  1 ubuntu ubuntu   838 2008-02-20 00:19 wand.dat
[email]ubuntu@ubuntu:~/.oper[/email]a$ chmod 633 opera6.ini 
chmod: changing permissions of `opera6.ini': Input/output error
[email]ubuntu@ubuntu:~/.oper[/email]a$ 

So is everything just Fubar'd and should start over and did this happen because I didn't remove my pendrive when I rebooted?

Any insight at all is appreciated. 

Regards,
Akovia

---

### Post by OwnName on 2008-06-25
Today I installed Opera 9.50.
Then I opened opera:config to change some annoying settings.
The result is I couldn't change any preference at all.
Then I checked the opera6.ini (which contains all the opera:config informations, and can be found under ./opera/) and there I found:

-rw-r--r-- 1 root    root     14028 2008-05-08 23:24 opera6.ini

so seems like by default the installation set it up the permission to root. I truly don't see the reason for that behaviour, if then I can customize opera through opera:config.

Last but not least, that can be fixed with

sudo chown <name>:<name> opera6.ini

---

