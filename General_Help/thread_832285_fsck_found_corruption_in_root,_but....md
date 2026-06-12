---
title: "fsck found corruption in root, but..."
date: 2008-06-17
forum: General Help
---

### Post by LeoSolaris on 2008-06-17
[I started up Ubuntu today and as expected it ran fsck on root. However this time, it found corruption. I need my root password in recovery to run the recovery tool. My issue is that the password I set root to is not working at all. I tried every possible combination of what my usual passwords are, but it isn't accepting anything.

I have the LiveCD, and I can access the hard drive. So all I need to do is find the file where the password is kept so I can either change it or read it so I can put it in at boot up. 

Leo

Solved

---

### Post by HalPomeranz on 2008-06-18
No need for recovery mode if you have a LiveCD.  Just boot your LiveCD and then fsck the root file system on your hard drive to fix the corruption.  You should probably fsck the other file systems on the drive, just to be on the safe side.  At that point you should be able to reboot normally and everything should be OK.

FYI, passwords are stored in the second field of the /etc/shadow file, but are in a hashed (encrypted) format.  You can create properly hashed passwords on the command-line using "mkpasswd -H md5" and then cut'n'paste them into the /etc/shadow file.

---

### Post by LeoSolaris on 2008-06-18
Thanks! Info I didn't know for the password location and making a new one.

I ended up figuring out how to bypass the fsck check (dumb but accidental, power cord was out on my laptop and I forgot it) and I found out that I forgot to actually set a root password after reinstalling. Not normally something I forget.

I couldn't for the life of me remember how to run fsck from the LiveCD till I hunted it down a little while ago.

Leo

---

