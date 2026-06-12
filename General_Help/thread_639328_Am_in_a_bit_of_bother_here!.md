---
title: "Am in a bit of bother here!"
date: 2007-12-13
forum: General Help
---

### Post by PRC on 2007-12-13
Hands up guys I am a newbe here to Linux - I can make windows work but this is all new to me!

I installed 7:10 a week or two ago here at work - up until now we have been dominated by Windoze.

I have a couple of problems with my 7.10 installation which until today I have lived with, I installed Samba and my Ubuntu box can see the windows network and the machines on it fine - but no other machine can see any of the folder shares created on my machine. This 'issue' has been on my 'todo' list....

Then today it seems that my Ubuntu machine has been elected as the master browser system on the network - BUT as no one can actually see the system on the network I have effectively shut down the whole company's network browsing.

Suggestions are appropriate at this point before some greater god asks me to unload Linux and put Bill back in control :(

Paul C

---

### Post by Lostincyberspace on 2007-12-13
About the samba you need to make sure you are in the same workgroup.

---

### Post by PRC on 2007-12-13
mmm yes - pretty sure that the workgroup setting is correct - the default installation had a diferent workgroup (default) but I changed it.

I have been using webmin to admister the system so that I have a GUI rather than having to mess with those scary text files.

Paul C

---

### Post by PRC on 2007-12-13
Well I fixed the master browser thing by adding the following in smb.conf

preferred master = no

So I guess my major issue is fixed.

Paul C

---

### Post by daengbo on 2007-12-13
Paul,

I had a similar problem on Gutsy and had to muck around in the .conf file to get things working right. I believe you need to look for the "browsable" entry for each shared folder and change it to "true" --  though I don't have my work machine with me right now so I can't check for sure.

---

### Post by strabes on 2007-12-13
For more information see these pages:
[https://help.ubuntu.com/community/ComprehensiveSambaGuide](https://help.ubuntu.com/community/ComprehensiveSambaGuide)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[http://ubuntuforums.org/showthread.php?t=26438](http://ubuntuforums.org/showthread.php?t=26438)

---

