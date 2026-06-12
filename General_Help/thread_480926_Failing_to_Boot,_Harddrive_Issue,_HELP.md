---
title: "Failing to Boot, Harddrive Issue, HELP"
date: 2007-06-21
forum: General Help
---

### Post by BlazinNightSkye on 2007-06-21
I have two HD's a 30G and a 20G, The 30G being my main HD but not the one thats supposedly having the issue. It starts to boot, gets past loading GRUB and first Ubuntu splash screen, stops in the middle of loading and starts fsck check on /dev/hdb1 saying it contains a corrupt filesystem. Lists about 50+ lines of "Buffer I/O error on device hdb1 and lists different logical blocks. When it finishes that it says there was a unexpected inconsistency and that fsck died with exit status 4, and that i should run fsck manually. After it lists that apt-get was not installed and that i could install it, But all the commands i type are ignored saying they do not exsist. It also mentioned that i could skip this if i type CONTROL-D to resume system boot. 

----->I have minimal experience with Linux, but am trying to learn because i prefer it to Windows. Before this happened i was downloading different things to customize my desktop (i.e new splash screen, BG's and icons) I went to restart my system, it loaded but it was only half done (theme was half present, not responding ect..) I had to unplug my computer to get it to restart. Thats when this new problem occured.

Please help!!

--Ashley

---

### Post by BlazinNightSkye on 2007-06-21
I forgot to mention that i can boot my LiveCD and that i can see my HD's and access their files, but i dont know whats wrong.:(

---

### Post by empthollow on 2007-06-21
this hasn't happened to me in a while, what i would try is to boot from live cd and run
```
fsck hdb1
```
if it gives you and complaints use
```
fsck -f hdb1
```
the -f option is to fix all errors without asking, this is listed as a "dangerous" option because if it fixes it wrong you can lose all of your data.  However, i tried this and most of the time it worked for me. there was one time i lost my partition but at that point i couldn't read it anyway and there was no saving it.  good luck.

---

### Post by BlazinNightSkye on 2007-06-21
thanks, ill give it a try

---

### Post by BlazinNightSkye on 2007-06-21
Well all it gave me was fsck 1.48-WIP (14-Nov-2006)..whatever that means

---

### Post by empthollow on 2007-06-22
found a couple of threads regarding this, maybe they will help but i have one question. what was the last thing you did before you got this error. for example transfering files.
[http://ubuntuforums.org/archive/index.php/t-438361.html](http://ubuntuforums.org/archive/index.php/t-438361.html)
[http://ubuntuforums.org/showthread.php?p=2693892](http://ubuntuforums.org/showthread.php?p=2693892)

---

### Post by BlazinNightSkye on 2007-06-23
I was getting random icons and such to customize my desktop

---

### Post by empthollow on 2007-06-23
my best guess is to try :
Opened in Recovery Mode (from the GRUB menu), got through and logged in, then changed root password by opening the terminal and typing 'sudo passwd root'.
as suggested by the first thread. i have no idea why changing the root password has anything to do with that, i would probably try booting into recovery mode, reboot, if you still get the error then do recovery mode again w/ chng root password.  i imagine you could change it back to whatever you had it orignally after you get you system working again.  it seems like it would be the password changing process that helped this person out.  if both of those fail, try recovery mode and do an fsck as i suggested above. good luck!

---

