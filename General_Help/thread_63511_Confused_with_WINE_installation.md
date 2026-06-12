---
title: "Confused with WINE installation"
date: 2005-09-08
forum: General Help
---

### Post by darkside on 2005-09-08
Hello,

I have just installed Ubuntu 5.04 yesterday and I'd really like to see Wine running
my Windows programs. Going on to the different threads discussing about Wine
installation, I just can't seem to understand which way to go.  :???: 
First, Wine HQ says all I have to do is use Synaptic Package Manager. From the image of that program itself, the difference begins because it seems that Ubuntu 
5.04's Synaptic Package Manager is of different version than that of the one 
displayed in Wine HQ for Ubuntu installation. This is of course no big deal but the instruction there which says I should make a repository that points to [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) stalls because that URI doesn't seem to exists. And so I tried using apt-get update but it's the same. There's a problem with the URI [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) I guess. Now, I read that I should be checking backports, whatever this means. And then, somebody also says all I need is Winetools which should take care of everything. Reading about Winetools, it seems to me I have to install Wine separately, I'm not sure about this but why use Winetools when all I want is Wine? Could somebody please enlighten me please? I've used Redhat as a server and I can do RPM installations or compiling from source code. But with Ubuntu it seems that synaptic is the recommended method. I would appreciate very much if somebody could provide a step by step instruction for installing Wine in an Ubuntu 5.04 fresh install. Or maybe there's a site already doing that, please tell me.

---

### Post by frodon on 2005-09-08
Basicly all I do is install with synaptic wine package and also winesetuptk package then I run winesetuptk in a terminal to configure wine and all worked in 2min. However i don't remember if i installed winetools.

---

### Post by X5-655 on 2005-09-08
[QUOTE=frodon]Basicly all I do is install with synaptic wine package and also winesetuptk package then I run winesetuptk in a terminal to configure wine and all worked in 2min. However i don't remember if i installed winetools.[/QUOTE]
how do I run winesetuptk in the terminal?  I tried typing it in but get command not found..

---

### Post by darkside on 2005-09-08
[QUOTE=frodon]Basicly all I do is install with synaptic wine package and also winesetuptk package then I run winesetuptk in a terminal to configure wine and all worked in 2min. However i don't remember if i installed winetools.[/QUOTE]


Have you done a synaptic installation or upgrade lately? I'm just following the
instructions from here [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
But it really doesn't work.  :mad: Could anybody guide me to what's the right URI?

---

### Post by frodon on 2005-09-09
EDIT : oups  :roll: , see the post below

---

### Post by frodon on 2005-09-09
[QUOTE=darkside]Have you done a synaptic installation or upgrade lately? I'm just following the
instructions from here [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
But it really doesn't work.  :mad: Could anybody guide me to what's the right URI?[/QUOTE]I didn't add the wine repository to install wine with synaptic, I just installed the wine ubuntu package.[QUOTE=X5-655]how do I run winesetuptk in the terminal?  I tried typing it in but get command not found..[/QUOTE]Have you installed the winesetup package (I'm not sure of the exact name).  when it's done, open a terminal and type wine, use the "tab" key to see the possible commands which start with the caracters "wine" and you will see a command like "winesetup" or "winesetuptk" (winesetuptk is a graphical setup program for wine).

---

### Post by darkside on 2005-09-09
[QUOTE=frodon]I didn't add the wine repository to install wine with synaptic, I just installed the wine ubuntu package.[/QUOTE]

Where can I get this? And how do I install it?

---

### Post by frodon on 2005-09-09
When i said i installed wine ubuntu package I mean i used synaptic to install it and for that I have enabled ubuntu repositories (main, restricted, universe, multiverse), look [here](http://ubuntuguide.org/#extrarepositories) (put in comment the backports lines at the end of the file).
Then open synaptic and search for wine and install the wine package and also a package called winesetuptk or something like that (i'm not in front of my computer).
Let me know if you still have problems

---

### Post by giodarkstar on 2005-09-09
Try using "WineTools"! WineTools configure automatically wine processes! [download WineTools](http://sourceforge.net/projects/winetools/)

---

### Post by frodon on 2005-09-09
[QUOTE=giodarkstar]Try using "WineTools"! WineTools configure automatically wine processes! [download WineTools](http://sourceforge.net/projects/winetools/)[/QUOTE]It's also in synaptic, why make things more complicated ?

---

### Post by darkside on 2005-09-09
I have these lines now in my sources.list. (I removed the commented lines)

```
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

```

So this should be adding repositories. But upon starting Synaptic Package Manager, It issues these warnings:

```
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

```

which I suppose means these locations cannot be located or I don't have access?
Should I be using mirror locations?

I wonder if adding repositories is affected by firewalls as discussed in this thread
[http://ubuntuforums.org/showthread.php?t=43770&highlight=adding+repositories](http://ubuntuforums.org/showthread.php?t=43770&highlight=adding+repositories)

Yeah, my company is also using a firewall.

---

### Post by frodon on 2005-09-09
Your source.list seems to be good, do you find the wanted packages in synaptic ? maybe you should install winetools as giodarkstar suggested it, i can't remember but maybe that's the winetools packages which offer the winesetuptk command.
However when i will come back home, i will give you the exact names of the packages to install, wine shouldn't be so hard to install, it takes me 2min !

---

### Post by darkside on 2005-09-09
I edited my previous post. Just wondered if a firewall have something to do with this.

I don't see any new things displayed in the package list. Also I tried sudo apt-get update and got the same warnings.

---

### Post by ultima2k on 2005-09-09
Just a question...is it better to use fake-windows instead of mounting the real windows-partition? Of course the program on a real one can not write to the ntfs-partition...

When saying that you can install windows-application on the fake, does it mean you run the install through wine?

---

### Post by darkside on 2005-09-09
[QUOTE=giodarkstar]Try using "WineTools"! WineTools configure automatically wine processes! [download WineTools](http://sourceforge.net/projects/winetools/)[/QUOTE]

Does WineTools installation also include Wine installation? Or it's just a utility to support Wine configuration after Wine has been installed. My main problem is installing Wine itself.

---

### Post by frodon on 2005-09-09
darkside, maybe your problem is more a repository problem if you really can't find wine in synaptic after a  apt-get update. So i think it should be helpful for you to post a new thread for this issue.

---

### Post by darkside on 2005-09-09
Hey you have just done it!

That's all I need. It is indeed a repository problem. Being a new Ubuntu and Synaptic user (w/c is no excuse) I just learned that Synaptic needs a Network configuration. I'm using a proxy server for internet connection and it's there in Preferences->Network tab being left blank. Next I did was just to click Reload and I don't know the many things it downloaded. I got lots of new packages now. The next worry I have is do I really need all those things coz I don't know what they do. I can see wine and winesetuptk alright, just I  don't know what version wine is.

Wow! I just had a neat lesson with Synaptic today. frodon and the rest of you guys thanks a lot for the support. I appreciate it very much.

Have a nice weekend everyone!

cheers,

from the darkside

---

### Post by darkside on 2005-09-09
This is really funny.

Of all the packages downloaded, only wine doesn't have a version and so doesn't get
marked for installation. Any quick fix?

---

