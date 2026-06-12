---
title: "Malformed line 58 in source list /etc/apt/sources.list"
date: 2013-10-08
forum: General Help
---

### Post by Daniel_Krueger on 2013-10-08
I am fairly new to ubuntu and have run into a problem. I was trying to get netflix to work on my browser and a couple of sources said to use this command in terminal. this is my output: 
```
root@daniel-NV55C:/home/daniel# apt-add-repository ppa:echoover/compholio
Cannot access PPA ([https://launchpad.net/api/1.0/~echoover/+archive/compholio](https://launchpad.net/api/1.0/~echoover/+archive/compholio)) to get PPA information, please check your internet connection.
```

I then went to the software center and tried to add it manually. I went to this website [https://launchpad.net/~ehoover/+archive/compholio/](https://launchpad.net/~ehoover/+archive/compholio/) and pasted 'deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu 13.04]("http://ppa.launchpad.net/ehoover/compholio/ubuntu")' into the source window. After I that I went to the terminal and got this:

```
root@daniel-NV55C:/home/daniel# apt-get install netflix-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netflix-desktop
Now when I run apt-get update I get this output:
root@daniel-NV55C:/home/daniel# apt-get update
E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read
When I try to use gedit and gksu I get these outputs respectively:
root@daniel-NV55C:/home/daniel# gedit /etc/apt/sources.list
(gedit:7456): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported
** (gedit:7456): WARNING **: Could not connect to session bus

root@daniel-NV55C:/home/daniel# gksu gedit /etc/apt/sources.list
(gksu:7460): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running
(gksu:7460): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running
(gksu:7460): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running
(gksu:7460): GConf-WARNING **: Client failed to connect to the D-BUS daemon:
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
GConf Error: No D-BUS daemon running
(gksu:7460): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(gedit:7463): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported
** (gedit:7463): WARNING **: Could not connect to session bus

```
I have tried using the GUI to go in and manually look at the sources.list folder and was able to look at it but when I try to remove the source lines and save I am told I do not have permission. I'm assuming I did something wrong and messed up a part of the system but am unable to change anything. I would greatly appreciate any and all help as I don't know what to do and don't know much in general. The contents of the sources.list file is:

```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Release amd64 (20130424)]/ raring main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb-src [http://repository.spotify.com](http://repository.spotify.com) stable non-free
deb [http://ppa.launchpad.net/echoover/compholio/ubuntu](http://ppa.launchpad.net/echoover/compholio/ubuntu) 13.04 [COLOR=#00ff00]<Line 58>[/COLOR]
deb-src [http://ppa.launchpad.net/echoover/compholio/ubuntu](http://ppa.launchpad.net/echoover/compholio/ubuntu) 13.04
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main
```

If I could either remove or edit the lines to the correct format I hope/assume that would solve the problem but am unable to do either with the current methods I have tried. I am able to download specific programs, I did not have gksu at first but saw other people fixing their problems with it so I downloaded it and recieved the output shown earlier. Again I realize I this is a self caused problem but would really like any help wether it be solutions or pointing me in the right direction.

---

### Post by howefield on 2013-10-08
Thread moved to the "*General Help*" forum.

---

### Post by sanderj on 2013-10-08
Based on which instruction where do you issue "apt-add-repository ppa:echoover/compholio"?

I think it should be ehoover/compholio ... do you see the difference?

So ... remove that line from /etc/apt/sources.list with "sudo gedit /etc/apt/sources.list"

---

### Post by Daniel_Krueger on 2013-10-08
*smashes face on keyboard* thank you very much, gosh darn padcak.

---

### Post by Daniel_Krueger on 2013-10-08
Ah sorry another question, do I just change the name in the thread to include [SOLVED]? and does it matter if it's is before or after the problem?

---

### Post by sanderj on 2013-10-08
> **Daniel_Krueger said:**
> Ah sorry another question, do I just change the name in the thread to include [SOLVED]? and does it matter if it's is before or after the problem?

"Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button."

and/or

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by oldos2er on 2013-10-09
You can mark the the thread as 'Solved' under the Thread Tools menu, the work-around of editing your first post is no longer necessary.

---

