---
title: "need to mount hfs+ on pc for data recovery"
date: 2006-12-01
forum: General Help
---

### Post by MyKal on 2006-12-01
ok first off i am using ubuntu ver-6.10 
So heres the deal i am a computer tech who has been charged with rescuing a clients music files from his e-mac. The problem is twofold Problem one his computer will not start up and problem two even if it did he dosnt remember his password to access the hard drive, now as we dont have any other macs here i was wondering if it would be possible to extract his hard drive and plug it into my ubuntu computer mount the filesystem from his drive and somehow use my computer to access his drive possibly as root we have had this machine in our possesion for far too long now and we really just want to fix this thing and get done with it

---

### Post by apjone on 2006-12-01
Remind him about back-ups
Then try the live mac cd on his machine. try synaptic and look for the file system tools.

---

### Post by tomchuk on 2006-12-01
Putting the drive in your Linux PC will work perfectly. The kernel has the hfsplus file system module and with the hfsplus package installed from the repositories, it'll mount just like any other filesystem.

In fact, I've got my HFS+ formatted iPod mounted right now.

---

### Post by MyKal on 2006-12-12
Hey me again 

ok i got ubuntu to mount the hfs+ harddrive but the problem now is that it only sees empty files rather than browsable directories 

there is a text file there that says i can only view an osx partition on a computer running osx 

if this is true then its a disaster for my business 

please somebody give me some good news

---

### Post by MyKal on 2006-12-14
damn i just cant make this work now im in and i can see the files and i can even copy jpegs and text files from the hfs drive to the backup folder on my desktop but i still cant get read/write access to the hfs system and even stranger whenever i try to copy music files from the hfs drive to my desktop nothing happens 

how can it be that i can have access to everything but music files 

i mean either you can read it or you cant am i wrong?? 

somebody please save me my boss is getting very short with me about getting this drive backed up so the customer can get his computer back

---

### Post by tomchuk on 2006-12-15
Have you tried to use hpcopy from the hfsplus package? From the hpcopy man page:
```
Since Macintosh files contain two forks, which are not representably in Unix file systems...
```
It seems like that may solve your issue.

If that fails, it might be time to source an Mac to do the backup. Throw the drive in a USB/Firewire enclosure and get youself to a Mac. Heck, show up at an Apple store with the HDD and some blank DVDs.

---

