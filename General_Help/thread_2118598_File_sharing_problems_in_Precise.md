---
title: "File sharing problems in Precise"
date: 2013-02-21
forum: General Help
---

### Post by tsaker on 2013-02-21
I posted this over in Networking & Wireless before noticing that that forum is for basic hardware connectivity issues which I don't have.  I may have misposted there, so at the risk of drawing fire, I reposted here in hope of getting an answer.

Ever since I installed U 12.04 LTS x64, I have had a nagging problem with file sharing.
I installed Samba in an effort to get my computers to talk to each other. 
The best I can do is get them to see the shares on each other, but they  break off connection when trying to copy and paste files between them.
The most common error message I get can be found in these posts:
[http://ubuntuforums.org/showthread.php?t=1670314](http://ubuntuforums.org/showthread.php?t=1670314)
[http://askubuntu.com/questions/74789...share-with-nau]("http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau")
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/851055]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851055")
I tried the solutions there but no joy.
Frequently, a window will pop up on my laptop saying, "System program  problem detected Do you want to report the problem now?"  I go through  the steps, reboot, and it continues to haunt me.
Now, it does a new thing.  The OS will suddenly log me off, shutting  down my programs, and dump me into the logon screen seemingly at random.
Anybody else run into this?

---

### Post by JiuJitsu500 on 2013-02-21
Well, I'm probably not the expert you're looking for, but I've had enough issues with samba and file-sharing in the past that I simply gave up on it a few releases ago in favor of the cloud.

I have CentOS, Ubuntu, ArchBang, Windows 7 and 8, Mac 10.6 and 10.8, and DragonflyBSD to transfer between... the only thing I've been able to successfully do this with is a cloud. Ubuntu One specifically, but I'm switching to MEGA (50GB for free?!?!?!) as soon as clients for mac and linux are released (haven't checked in about a month though).

I'd like samba to work correctly for me too, but I haven't tried in a while since the mac was giving me too much trouble for whatever reason. BSD would never work right, but linux and windows were never really an issue.

Cloud man! Cloud! :)

---

### Post by tsaker on 2013-02-21
JJ, I've been trying to avoid the cloud for a number of reasons with stubbornness being at the top of the list. It vexes me that file sharing became a problem when I updated Meerkat, Narwal & Ocelot to Pangolin.

---

### Post by bab1 on 2013-02-21
> **tsaker said:**
> I posted this over in Networking & Wireless before noticing that that forum is for basic hardware connectivity issues which I don't have.  
What makes you sure of that?  What have you done for hosts/DNS on your LAN?  How have you setup IP addressing?> 

I may have misposted there, so at the risk of drawing fire, I reposted here in hope of getting an answer.
Duplicate postings are frowned upon.  Use the "report abuse" to get the mods to move your post to the appropriate place.> 

Ever since I installed U 12.04 LTS x64, I have had a nagging problem with file sharing.
I installed Samba in an effort to get my computers to talk to each other. 
The best I can do is get them to see the shares on each other, but they  break off connection when trying to copy and paste files between them.
The most common error message I get can be found in these posts:
[http://ubuntuforums.org/showthread.php?t=1670314](http://ubuntuforums.org/showthread.php?t=1670314)
[http://askubuntu.com/questions/74789...share-with-nau]("http://askubuntu.com/questions/74789/failed-to-retrieve-share-list-from-server-error-when-browsing-a-share-with-nau")
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/851055]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851055")
I tried the solutions there but no joy.
Describe your problem and what diagnoses you have done.  Most likely your problem is not exactly the same as others if their cures don't work for you. > 
Frequently, a window will pop up on my laptop saying, "System program  problem detected Do you want to report the problem now?"  I go through  the steps, reboot, and it continues to haunt me.
This does not sound like a Samba issue at all.> 
Now, it does a new thing.  The OS will suddenly log me off, shutting  down my programs, and dump me into the logon screen seemingly at random.
Anybody else run into this?
Definitely  not directly related to Samba.  It sounds more like a hardware or a video card problem.  Have you looked through the logs?  Maybe /var/log/kern.log or /var/log/messages.  You can view them from the bottom up like this```
tail -n25 <log>
```...where <log> is the log you want to look at.

---

### Post by JiuJitsu500 on 2013-02-21
I feel you man, it does seem like it's become harder and harder to do. Maybe Apple and Microsoft make it hard as hell for their own reasons, and the linux, BSD, and even Solaris guys get kind of stuck in the middle... without support from the biggest dogs in the park.

mofos!

Stubborn you say? I feel that too, but I had to give it up. Lucid was fine, everything after that has been a pain more and more so Cloud I went. I'm not sure if the samba server(s) and the related projects can keep up with the crap the Micro and Fruit companies are pulling - like mac's STILL not natively supporting r/w to ntfs. that still irks me, and micro's "secure boot" in a futile attempt to refuse installs of other OS's...

linux it is, for real, from now on. Just Could for me, MEGA hopefully soon.

---

### Post by tsaker on 2013-02-21
> **bab1 said:**
> What makes you sure of that?  What have you done for hosts/DNS on your LAN?  How have you setup IP addressing?

I have IPs assigned automatically.  

Describe your problem and what diagnoses you have done.  Most likely your problem is not exactly the same as others if their cures don't work for you. This does not sound like a Samba issue at all.

1) Open Nautilus, click Network--if the network share appears, click on icon/link. Error message comes up.

2) Open Nautilus, click Network--if the network share appears, click on icon/link. Files in folder appear.  Attempt to copy/paste file to network shared folder.  Error message appears. 

Diagnoses:  add line to samba.conf file network bcast host = <my network name>
Save file, exit, restart samba

Repeat 1 and 2 with similar results.

Definitely  not directly related to Samba.  It sounds more like a hardware or a video card problem.  Have you looked through the logs?  Maybe /var/log/kern.log or /var/log/messages.  You can view them from the bottom up like this```
tail -n25 <log>
```...where <log> is the log you want to look at.

I know enough to be dangerous, but wouldn't have any idea what log files to look at.

---

### Post by tsaker on 2013-02-21
JJ, I guess that's where the multiverses collide with catastrophic results.

---

### Post by JiuJitsu500 on 2013-02-21
Here here!

And by the way, I'm going to try to re-open all my samba jazz later too now. You got me curious.

---

### Post by bab1 on 2013-02-21
> **tsaker said:**
> ...I know enough to be dangerous, but wouldn't have any idea what log files to look at.
Having IP addresses assigned automatically is only part of a correctly configured network.

I assume you mean *name resolve order = bcast hosts*.  The results are what they are.  You need to diagnose what is wrong.  Post what you get with this```
smbtree -d3
```

It would help if you described the shares you have created.  Post he output of this```
testparm -s
```

I mentioned 2 logs you could look at,  Why not start with the kern.log?
```
tail -n25 /var/log/kern.log
```...you know the drill; post the info back here.

---

