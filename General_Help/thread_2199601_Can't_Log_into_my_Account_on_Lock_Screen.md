---
title: "Can't Log into my Account on Lock Screen"
date: 2014-01-14
forum: General Help
---

### Post by ishaan2 on 2014-01-14
I have recently went on Terminal and logged into root then changed the permissions of /. Then I closed Terminal then reopened it it said some red text. When I tried to type it wouldn't how up on the screen. So I restarted my computer. When I tried to log back in it would go to a black screen with some text on it. Then it would switch back to the lock screen. I tried restarting my computer many times and it would do the same thing over and over. The black screen switches to fast to read the tet.

---

### Post by ian-weisser on 2014-01-14
Reboot into your recovery console and change the permissions of / back to their proper values.
Don't do that again.

---

### Post by ishaan2 on 2014-01-15
How do you get to the recovery console

---

### Post by ian-weisser on 2014-01-15
It's one of the options on your GRUB bootloader screen.

---

### Post by ishaan2 on 2014-01-15
what commands do I punch into it

---

### Post by ian-weisser on 2014-01-15
What commands did you use to cause the problem?

---

### Post by ishaan2 on 2014-01-16
Sudo -I then sudo nautilus then went to / and changed the group to my user.
When I did any sudo prompts it said usr/lib/sudo/sudoers.so must be writable

---

### Post by ian-weisser on 2014-01-16
Did you change *only* /, or did you change all subordinate directories too?
If you only changed /, then change it back.
If you changed all directories, then you must reinstall.

---

### Post by silvervulpus on 2014-01-16
ok so i know from experience the fastest way to mess up your system beyond repair is to screw around with chmod and root "/" (having previously made my root chmod 666 and bricked my whole system) atleast you can access your files though, and there is a minor chance of recovery. the idea i am working on here is to create a live boot disk of the same exact distro you are using, on a flash drive or CD. do this on a different computer or boot your second OS if your dual booting. also you are going to need a decent sized external drive. if your using a dual boot you can simply load on your second OS and copy your files out of your ubuntu partition and into your windows side or other distro's side. if you are not dual booting or for some reason cannot recover all your data and files this way, back to the first method. boot from your live CD and attach the external HDD, from the live CD copy all of your sensitive or necessary data to the external drive. after you have fully copied your data to the external, go about attempting to reset your permissions on your root from the live cd, most likely using the CHMOD command lines. (if you dont know CHMOD or how to use it, check out "The Linux Command Line" it is the authority on using any linux os properly in terminal) if you cannot change your permissions from the live boot disk via chmod, use the live boot disk to reinstall your OS over your old one, and simply reinstall any programming you had before, then copy your files from the external back to the new clean install... good luck, i hope i was helpful, and i know im not the best tech in the world, so i hope the tech who reads this after me and tries to help you, can build upon what i have written and give your more information than i was able to.  oh and ian is right, if you changed the sub directories permissions with the root, you are screwed and HAVE to do a new install. it would take days of research alone just to figure out the permission type necessary for each individual directory/file, let alone the weeks it would take to actually manually reset all of them back to what they need to be >.<

---

### Post by ishaan2 on 2014-01-16
only / I think

---

### Post by silvervulpus on 2014-01-16
if its only / then you should be capable of changing the permissions back to what they need to be very easily from the live disc via CHMOD. i recommend yet again reading "The Linux Command Line" its a book by william e shotts. it should have full instructions in there on how to use chmod.... be careful not to destroy your system like i did. if i was you i would wait for an admin to respond though. an admin should be able to give you the exact command line you will need to run from the live disc to change your / folder back to where it needs to be. i think its 660 but it might not be, and i dont want to brick your system as badly as i did with my own (also when i bricked my system i used sudo chmod 666 / and i did it not only to just my root folder but to all my subdirectories too.... it was bad)

---

### Post by ian-weisser on 2014-01-16
> **ishaan2 said:**
> only / I think

Well, let's make sure.
Use the **ls -l  **command on a subdirectory.

Example:
```
$ ls -l /usr      # Subdirectory
total 268
drwxr-xr-x   2 root root 106496 Jan 16 16:23 bin
drwxr-xr-x   2 root root   4096 Jan 13 20:09 games
drwxr-xr-x  63 root root  20480 Nov 12 22:54 include
drwxr-xr-x 215 root root  86016 Jan 16 16:22 lib
drwxr-xr-x  10 root root   4096 Apr 20  2009 local
drwxr-xr-x   2 root root  20480 Jan 16 06:24 sbin
drwxr-xr-x 408 root root  20480 Jan 16 16:09 share
drwxrwsr-x   7 root src    4096 Dec 30 15:33 src
```
Does your owner and group look like mine?

---

### Post by ishaan2 on 2014-01-17
Yes everything looks the same except for the bottom part instead of root src it says root root

---

### Post by ian-weisser on 2014-01-17
Then the problem you described (chown /, but not any subdirectories) is fixed.

---

### Post by ishaan2 on 2014-01-18
Okay, but I accidentally went in to failsafeX graphics mode and now I can't get out. It says can't detect graphics card and running low on graphics

---

