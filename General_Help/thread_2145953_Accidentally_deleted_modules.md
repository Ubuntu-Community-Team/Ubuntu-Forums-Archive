---
title: "Accidentally deleted modules"
date: 2013-05-17
forum: General Help
---

### Post by lemonoid on 2013-05-17
OKAY. So I know better than to play around and make changes in any other section other than my home folder unless I know exactly what I'm doing and have a good reason to venture into /. So my disk space was getting really low so I used disk analyzer to see where all the space was being taken up and what I could remove. I have recently made a /lib folder in my home for some reasons regarding some Android development. When the disk analyzer was done it showed a TON of space being taken up in /lib. I didn't even think to look that it wasn't listed under /home/username/lib instead of just /lib and I went in and deleted all old kernel modules, and the most recent I believe 2.0-40-generic-pae. BUT due to my curiosity in how all this works together, I was going through scripts and everything and decided hey, I'm gonna copy this to my external. so I have a copy of it on my external but I can't connect to the internet and I can't connect my external HDD because obviously, I deleted the kernel modules. Does ANYONE know how I can possibly fix this? Like I said I have a copy of the most recent module folder on my external but cannot figure out a way to get ALL the files back into the computer except by going in and manually typing the modules through a text editor and saving them into the /lib/modules but I know that modules are .ko files and I'm sure I can find a program on this Windows computer to open and read the .ko files so I can type them into my Ubuntu. I don't even know if typing in the modules one by one and saving them would even work. But I have an idea, if I can find a way to get my usb module somehow back into its proper area, then I can copy the most recent kernel modules back to the device and put them back in the right section and insmod the necessities (such as internet connection) and run an update and maybe this will load the rest of the modules back. I feel like I'm correct in my thinking, but I don't know HOW to do this. Am I right? could I posssibly just hand-copy the usb modules needed to load my external and copy the entire package back where it belongs and this fix it? load them into lib and then restart the computer and the kernel should load the modules back. I REALLY don't want to have to re-install because I have a lot of data on here I don't want to lose, and without my internet connection and usb modules I have no way to save my data. I guess I could do a backup but there's not enough space for me to save my data on the internal, and obviously I can't make a backup to a disc or a usb, or the cloud. So I'm stymied until I figure out how I can reload these modules. If I AM right and I can type up the kernel modules needed for usb and save them as a .ko in /lib/modules, which USB modules will I need to do (or internet if its easier/faster) and does anyone know a program for windows in which I can open these module files (.ko) so I can view them and copy the code over by hand. I know this was really stupid, but once I was in the lib folder I wasn't even thinking about what I was removing, I was thinking it was something I loaded for building a kernel for Android. Oh and btw they aren't in the trash for me to restore, because I used rm -r. THANK YOU so much for any help. Btw I'm on 12.04 and can't upgrade to 12.10, I've tried running it live, and I guess my computer is just too old for it because the graphics wouldn't load properly.

---

### Post by dino99 on 2013-05-17
if you wish someone reading your stuff, then print it more sexiest  :mad:

if a kernel is broken, then purge it and reinstall it; thats it, no headaches  :guitar:

---

### Post by Impavidus on 2013-05-17
+1 to formatting your posts.

Get a live disk and boot from it. That should give you access to internet and usb drives. Then make backups. Maybe you can reinstall all deleted modules using the live disk, but reinstalling the entire system may be easier. I can't really follow what you deleted exactly.

---

### Post by lemonoid on 2013-05-17
> **dino99 said:**
> if you wish someone reading your stuff, then print it more sexiest  :mad:

if a kernel is broken, then purge it and reinstall it; thats it, no headaches  :guitar:
ok thx. I will look for a guide on that.

---

### Post by lemonoid on 2013-05-17
> **Impavidus said:**
> +1 to formatting your posts.

Get a live disk and boot from it. That should give you access to internet and usb drives. Then make backups. Maybe you can reinstall all deleted modules using the live disk, but reinstalling the entire system may be easier. I can't really follow what you deleted exactly.

if purging & reinstalling doesn't work with my kernel then I'll do this. Ya know, I thought about this but I was sitting there thinking well I can't load a disc, but I didn't even think about the modules don't matter if I'm booting into a live disc, because my bootloader takes care of that, not my current OS's modules. I guess I could boot live and download, and save it to the current file-system on my computer, then boot into Ubuntu and hope they sticked in there. Thanks for this. I'm gonna try to purge & reinstall, which I've never done. I've heard of purging a kernel many times but never done it, I'm guessing that somehow from in my command line I get the kernel to reinstall itself without any internet connection. That's what I'm taking from that, I've got a couple guides pulled up now I'm about to start reading through. Will mark solved once i've got it all goin.

---

### Post by Zill on 2013-05-18
lemonoid:  If you want any help here I respectfully request that you make your posts more readable.  Large blocks of text are simply *very* difficult to read!

Clue:  Hit your "Enter" key occasionally to create an empty line.  This will allow your block of text to be broken up into concise and easily-readable [paragraphs]("http://www.thefreedictionary.com/paragraph").

From what I can glean from your problem I suggest you might find the best solution is to reinstall Ubuntu.  If you don't currently have backups of your data then it must not be important to you.

---

