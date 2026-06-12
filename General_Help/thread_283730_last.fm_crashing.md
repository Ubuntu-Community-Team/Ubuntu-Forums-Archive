---
title: "last.fm crashing"
date: 2006-10-24
forum: General Help
---

### Post by tronica on 2006-10-24
when i try to run last.fm on edgy it opens fine but when i click play it justs closes. so i ran it from the terminal and got this


> lyle@ubuntu:~$ cd /home/lyle/Last.fm/
[email]lyle@ubuntu:~/Last.fm[/email]$ ./lastfm 
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    147 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    147 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
Running on: "en_US" 
Initialising Search Extension 
Initialising Search GUI 
Initialising Sidebar Extension 
Initialising Sidebar GUI 
Initialising UserInfo Extension 
Segmentation fault (core dumped)
[email]lyle@ubuntu:~/Last.fm[/email]

whats the segmentation fault?

---

### Post by matthewstory on 2006-10-24
A Segmentation Fault is a bad pointer in the program.  I would talk to the lastFM developers and also check to see if there are any known bugs in the lastFM code.  If not, make sure you're copy of lastFM is good by checking the checksums, and do a check on your memory.  But most likely this is a C error in the lastFM code.  By the looks of it, it seems that lastFM has a problem using the X gui.

---

### Post by cybercoin on 2006-10-26
I have the same problem, I have heard that it might be that the last.fm player doesn't support ALSA but just the OSS mixer... how can I make it use OSS?

---

### Post by PriceChild on 2006-10-26
I've installed it from the repos and all is perfect.

---

### Post by handband2 on 2006-10-26
See if either of these posts can help:

[http://www.ubuntuforums.org/showpost.php?p=1239424&postcount=1]("http://www.ubuntuforums.org/showpost.php?p=1239424&postcount=1")

[http://ubuntuforums.org/showpost.php?p=1590605&postcount=4]("http://ubuntuforums.org/showpost.php?p=1590605&postcount=4")

---

### Post by tronica on 2006-10-26
tells you what I know, I wasn't aware they were in the repos.](*,)

---

