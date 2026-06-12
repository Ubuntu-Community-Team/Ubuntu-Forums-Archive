---
title: "I really need an on-demand AV, F-prot or Clam or AntiVir"
date: 2008-01-31
forum: General Help
---

### Post by jesrani on 2008-01-31
I have finally setup my Ubuntu 7.10 desktop as I wanted, in a Windows network. Samba is working, am able to auto mount/unmount shares and backup the folders on Windows PC onto a seperate HDD using rsync scheduled in Cron. Now I do need an Anti-virus with on-access scanner, especially for the Backed-up folders, as my Windows PC's do not have any anti-virus. I did lot of searching and I have following questions:
1) I downloaded F-Prot tarball and installed in /opt/f-prot. It has a good scan but no GUI which I dont like. I want to know how to uninstall this. I also couldnt figure out the Dazuko installation.
2) It seemed ClamFS was easy, I downloaded and installed as given on the site. I thought I configured the .xml file but it doesnt seem to do the on-access scans. I am just not sure. It also doesn't have a GUI.
3) Now I feel AntiVir is good as it has a GUI and there are good instructions on installation of AntiVir and Dazuko.

Anyone has any other ideas. This is not as easy as XP but I think I have to have an anti-virus so than an infected file from Windows should not affect other files. I know this question has been asked many times but I could not find the right answer. Some posts are also quite old.

---

### Post by AnonCat on 2008-01-31
I'm not sure if it's good for your particular application, but AVG anti-virus for Linux might be worth looking into.  I use it to check email and files intended for use on Windows computers and it does have a nice GUI.  You can find it here:

[http://www.grisoft.com/doc/31/us/crp/0?prd=avl](http://www.grisoft.com/doc/31/us/crp/0?prd=avl)

---

### Post by jesrani on 2008-02-02
First of all sorry for the title. It is just a way to get more people to read this thread as I was not getting the replies to my post. I love Ubuntu but would like to get a reliable av for the files I have backed up from Windows PC's. Please see the post below.

I have finally setup my Ubuntu 7.10 desktop as I wanted, in a Windows network. Samba is working, am able to auto mount/unmount shares and backup the folders on Windows PC onto a seperate HDD using rsync scheduled in Cron. Now I do need an Anti-virus with on-access scanner, especially for the Backed-up folders, as my Windows PC's do not have any anti-virus. I did lot of searching and I have following questions:
1) I downloaded F-Prot tarball and installed in /opt/f-prot. It has a good scan but no GUI which I dont like. I want to know how to uninstall this. I also couldnt figure out the Dazuko installation.
2) It seemed ClamFS was easy, I downloaded and installed as given on the site. I thought I configured the .xml file but it doesnt seem to do the on-access scans. I am just not sure. It also doesn't have a GUI.
3) Now I feel AntiVir is good as it has a GUI and there are good instructions on installation of AntiVir and Dazuko.

Anyone has any other ideas. This is not as easy as XP but I think I have to have an anti-virus so than an infected file from Windows should not affect other files. I know this question has been asked many times but I could not find the right answer. Some posts are also quite old.

---

### Post by steveneddy on 2008-02-02
I don't like Ubuntu either. Let's install Kubuntu.

---

### Post by Mahiwaga on 2008-02-02
Hey any one knows how to install a mouse cursor for Ubuntu server 7.10? With out using any GUI settings I just want the mouse to move on the normal tty screen. Thanks..

---

### Post by jesrani on 2008-02-02
Hey no thats not the reply I want. I like Ubuntu of course. Just a bit frustrated at not getting replies sometimes.

---

### Post by jaytek13 on 2008-02-02
As far as uninstalling something you compiled from source, you'd just go into the directory and type 

```

sudo make uninstall

```

As far as antivirus, if you're adamant about having something installed on your Linux box you might try AVG. They do make a Linux version.

---

### Post by Mahiwaga on 2008-02-02
Hey any one knows how to install a mouse cursor for Ubuntu server 7.10? With out using any GUI settings I just want the mouse to move on the normal tty screen. Thanks..

---

### Post by steveneddy on 2008-02-02
> **jesrani said:**
> Hey no thats not the reply I want. I like Ubuntu of course. Just a bit frustrated at not getting replies sometimes.

Trust me - you take what you can get on these forums.

---

### Post by jesrani on 2008-02-02
I know I have to take what I get, so I am repeating the problem. I have managed to do almost everything I had thought and could not have done anything without this forum. I am sure someone knows the answer to my problem. I NEED an on-access av because I am backing up files from unprotected Windows PC's.

---

### Post by TeaSwigger on 2008-02-02
> **steveneddy said:**
> I don't like Ubuntu either. Let's install Kubuntu.

lol exactly my thought. Bless ya.

> **jesrani said:**
> First of all sorry for the title. It is just a way to get more people to read this thread as I was not getting the replies to my post. I love Ubuntu but would like to get a reliable av for the files I have backed up from Windows PC's. Please see the post below.

I have finally setup my Ubuntu 7.10 desktop as I wanted, in a Windows network. Samba is working, am able to auto mount/unmount shares and backup the folders on Windows PC onto a seperate HDD using rsync scheduled in Cron. Now I do need an Anti-virus with on-access scanner, especially for the Backed-up folders, as my Windows PC's do not have any anti-virus. I did lot of searching and I have following questions:
1) I downloaded F-Prot tarball and installed in /opt/f-prot. It has a good scan but no GUI which I dont like. I want to know how to uninstall this. I also couldnt figure out the Dazuko installation.
2) It seemed ClamFS was easy, I downloaded and installed as given on the site. I thought I configured the .xml file but it doesnt seem to do the on-access scans. I am just not sure. It also doesn't have a GUI.
3) Now I feel AntiVir is good as it has a GUI and there are good instructions on installation of AntiVir and Dazuko.

Anyone has any other ideas. This is not as easy as XP but I think I have to have an anti-virus so than an infected file from Windows should not affect other files. I know this question has been asked many times but I could not find the right answer. Some posts are also quite old.

It can take persistence to get replies sometimes. You really don't need the slighting title, especialy since nobody is gaining a darn thing whether or not you ever use or like ubuntu. We're all just users like yourself and, if I may stress so, should be grateful for the software kindly shared with us. Please do search, research and search some more especially when starting, since there is a lot to learn, and a lot is just picking up as you go.

Understand please that Linux is not Windows. They don't work the same. That doesn't mean that there is nothing which can harm a Linux system, just that the viruses, designed for Windows, aren't a concern. Not even if you're accessing a share on a Windows unit. If you observe good permissions practices and have a decent firewall protection, all of which are nicely set by ubuntu upon install, you really don't need the anti-virus on ubuntu. That's a wonderful thing. It would be adviseable to protect the Windows units with an antivirus, and yes I absolutely agree AntiVir is a fine choice. Again, AntiVir should be installed and running on the Windows units only, there is no need for the antivirus on the Linux unit. If there are security concerns, see to the security of the Windows units in terms of firewall etc, as they remain vulnerable and that would be the most likely vulerable point.

If you are backing up files which were on Windows units to a space that you'll only be accessing in Linux from now on, preferably formatted in a linux file system like the ext3 ubuntu prefers, I don't see any need for any antivirus at all. I hope this helps, and please remember that persistence, not hype, gets the results.

---

### Post by jesrani on 2008-02-03
> **TeaSwigger said:**
> lol exactly my thought. Bless ya.

It can take persistence to get replies sometimes. You really don't need the slighting title, especialy since nobody is gaining a darn thing whether or not you ever use or like ubuntu. We're all just users like yourself and, if I may stress so, should be grateful for the software kindly shared with us. Please do search, research and search some more especially when starting, since there is a lot to learn, and a lot is just picking up as you go.
Understand please that Linux is not Windows. They don't work the same. That doesn't mean that there is nothing which can harm a Linux system, just that the viruses, designed for Windows, aren't a concern. Not even if you're accessing a share on a Windows unit. If you observe good permissions practices and have a decent firewall protection, all of which are nicely set by ubuntu upon install, you really don't need the anti-virus on ubuntu. That's a wonderful thing. It would be adviseable to protect the Windows units with an antivirus, and yes I absolutely agree AntiVir is a fine choice. Again, AntiVir should be installed and running on the Windows units only, there is no need for the antivirus on the Linux unit. If there are security concerns, see to the security of the Windows units in terms of firewall etc, as they remain vulnerable and that would be the most likely vulerable point.
If you are backing up files which were on Windows units to a space that you'll only be accessing in Linux from now on, preferably formatted in a linux file system like the ext3 ubuntu prefers, I don't see any need for any antivirus at all. I hope this helps, and please remember that persistence, not hype, gets the results.

I understand, I am very grateful for this wonderful software. I had never done or seen a Linux Install a few months back and only because of the forums could I set up a Ubuntu desktop and do most of the things I wanted. Only I couldn't find a proper answer to on-access av even after searching a lot (maybe it may not be a lot for someone else). Maybe Linux does not require it, but I would prefer to have it. I can't put AV on the windows PC's as they don't have an internet connection. Maybe I have to find a free client/server type AV but I couldn't find one. Yes, the backed up files are on ext3 HDD.
I appreciate the help available on these forums, without which I would ever have setup a Linux PC.
But I think the title pulled you to this thread, didn't it... My actual post on av software received only one reply. Thanks anyway.

---

### Post by jaytek13 on 2008-02-03
You might try the beginner forum.

---

