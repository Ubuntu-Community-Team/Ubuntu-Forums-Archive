---
title: "How to install REALVNC gui in ubuntu 12.04?"
date: 2013-03-21
forum: General Help
---

### Post by uzumakifahim on 2013-03-21
I need RealVNC (open edition) GUI in my ubuntu 12.04. I know ubuntu 12.04 has remote desktop software preinstalled, but I need RealVNC for some specific users, because they are very familiar with RealVNC in windows. I want to give them same experience in ubuntu. 

Please help me experts. Thanks in advance.

---

### Post by TheFu on 2013-03-21
> **uzumakifahim said:**
> I need RealVNC (open edition) GUI in my ubuntu 12.04. I know ubuntu 12.04 has remote desktop software preinstalled, but I need RealVNC for some specific users, because they are very familiar with RealVNC in windows. I want to give them same experience in ubuntu. 

Please help me experts. Thanks in advance.

I applaud your attempt to make a transition easier.  Having mostly the same programs available in a new OS is comforting to most people.  When I migrated Mom from Windows to Linux, she was pleased to see the same programs used that I'd taught her on Windows during the prior 5 years.

However, sometimes the Windows tool is not the best answer on another platform. I fear this is the case with RealVNC.  According to this [https://help.ubuntu.com/community/VNC/Clients](https://help.ubuntu.com/community/VNC/Clients) page, there is a native VNC for Windows and a Java App for Linux.  By now, we've all learned a few things about Java:
1) Java is a security risk when run inside a browser
2) Java applications tend to load slow, used lots of RAM and have a dated look and feel.

The folks building Ubuntu probably selected the best alternative for VNC clients, IMHO. Your people can learn to use it as well, I'm certain.  If needed, a side-by-side how-to guide to show them where X in RealVNC goes into field A under the build-in VNC client can't be too hard to create.  After all, there are only about 10 settings for VNC clients.

If you really want to blow them away, you might consider using NX instead of VNC. The performance is 2-3x more efficient, IMHO. It is snappy compared to any VNC that I've used.  [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) has a setup guide.  Of course, you might not control the servers or there might be so many that setting up NX on each isn't practical. Only you can decide.

Google found this: [http://www.plugintolinux.ca/smf/index.php?topic=815.0](http://www.plugintolinux.ca/smf/index.php?topic=815.0) which claims that **xvnc4viewer** is realvnc. I dunno. To install:
```
$ sudo apt-get install xvnc4viewer
```
Good luck.

Seems to be true:
```
$ xvnc4viewer

VNC Viewer Free Edition 4.1.1 for X - built Feb  5 2012 20:02:23
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
```

---

### Post by uzumakifahim on 2013-03-21
@[**[COLOR=#000000]TheFu[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037685"), Thanks to you that, you understand my situation. I've already installed xvnc4viewer, but it's terminal based, which is still very scary for my new Linux users. For this reason, I'm looking for GUI of RealVNC. **To get that I've downloaded RealVNC, common Linux edition (.tar.gz) file from their website, but I don't understand how to install that.** Could you help me on that regard please.

By the way, I also need know that, [B]
 1. Is it possible to connect to windows PC using RealVNC from Ubuntu 12.04 PC using vino and Remmina? 
 2. How is the performance? 
 3. Is it possible transfer file within these two? [/B]

If all the answers of above question is positive then I can give a try with vino and remmina.

---

### Post by TheFu on 2013-03-22
I've never used any of those tools or tried to transfer files using them.  For remote file access I'd use ssh/scp/sftp or setup samba/cifs sharing. Doing it through a remote desktop seems ass-backwards to me - oh - right - that's the way the "other OS" does it.

You will need to try it yourself and decide if those tools fit your needs.
Here is what I know about remote desktops: [http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications)
I use NX (freenx and nxclient from nomachine) for remote desktops to Linux. 

If you want a point-n-click for your users, why not make a tiny script that gets placed in their "Desktop" folder to launch the rdp-viewer of your choice for them?  Coming from Windows - think of this as a "shortcut".  All the end user needs to know is to double-click on that icon.

---

### Post by uzumakifahim on 2013-03-22
@TheFu, thanks for the link. it gives me much clear concept about this topic.

**Now, how can I install that .tar.gz file on ubuntu 12.04? **

---

### Post by TheFu on 2013-03-23
> **uzumakifahim said:**
> @TheFu, thanks for the link. it gives me much clear concept about this topic.

**Now, how can I install that .tar.gz file on ubuntu 12.04? **

Google found this: [http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file) that tries to answer it.
A .tar.gz or .tgz file can hold almost anything (sorta like a ZIP file), so how to install it is usually described inside a README file stored inside the tgz file.

The name tar.gz tells me that gzip was used on a tar file.  Tar is short for "tape archive" and has all the great things AND all the bad things about that format.
A gz.tar file would mean that someone gzipped files, then put them into a tar archive.  I have to admit, I've never seen that, but you get the idea, so if you ever see a tar.zip or tar.bz2 or tar.Z file, you'll understand - the last part is some sort of compression and the .tar. part means the tar program was used to create it.

There are probably 50 different tools that can pull files from a tgz or tar.gz file.  I would do it "the hard way", so I won't bore you with my CLI/shell methods. To me, using the shell is easier.

I hope you understand that by installing a program that is not in a repository, you are breaking the best part of Linux systems - the repository.  When you break that, it means you will have to maintain the patching manually going forward for whatever programs you install. This is why I stopped running MS-Wnidows. Linux has better tools for system and application management. We just need to use them.

Anyway, I hope that link gets you to a point where you can install the program.

---

### Post by uzumakifahim on 2013-03-24
> **TheFu said:**
> Google found this: [http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file) that tries to answer it.
A .tar.gz or .tgz file can hold almost anything (sorta like a ZIP file), so how to install it is usually described inside a README file stored inside the tgz file.

The name tar.gz tells me that gzip was used on a tar file.  Tar is short for "tape archive" and has all the great things AND all the bad things about that format.
A gz.tar file would mean that someone gzipped files, then put them into a tar archive.  I have to admit, I've never seen that, but you get the idea, so if you ever see a tar.zip or tar.bz2 or tar.Z file, you'll understand - the last part is some sort of compression and the .tar. part means the tar program was used to create it.

There are probably 50 different tools that can pull files from a tgz or tar.gz file.  I would do it "the hard way", so I won't bore you with my CLI/shell methods. To me, using the shell is easier.

I hope you understand that by installing a program that is not in a repository, you are breaking the best part of Linux systems - the repository.  When you break that, it means you will have to maintain the patching manually going forward for whatever programs you install. This is why I stopped running MS-Wnidows. Linux has better tools for system and application management. We just need to use them.

Anyway, I hope that link gets you to a point where you can install the program.

Yes, I also believe that system and application management tools is one of the strongest side of Linux. 

I think, it's better to get my job done with Remmina or other tools which are available in the repository. 

After all, thanks for your continuous help.

---

