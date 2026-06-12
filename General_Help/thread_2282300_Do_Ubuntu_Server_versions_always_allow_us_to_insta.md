---
title: "Do Ubuntu Server versions always allow us to install Ubuntu minimal/mini"
date: 2015-06-13
forum: General Help
---

### Post by tech291083 on 2015-06-13
Hi Friends,

I like the Ubuntu Minimal iso quite a bit and in the past I did use it on a few of my old pcs at work, but each time during installation I had to have an active internet connection in order to install the basic packages, which were not included in the downloaded iso (the iso was burned to a CD to facilitate installation via CD). But I do happen to be in situations where there is no active internet connection and thus I am desperate to look for a method that would allow me to install Ubuntu minimal iso onto an old pc with no working internet, and I did come across the following page today morning, which basically, as I understand, says that one can install minimal version just by pressing F4 during the installation of Ubuntu Server 12.10 off a DVD/CD. Now, my query is, are all the new (after 12.10) Ubuntu Server releases designed to allow the option of installing Ubuntu minimal just by pressing F4? Will the installation done by this method ensure that all the basic packages that were previously downloaded via a must have internet connection will automatically be installed offline this time around? 

And one more thing, as per the page given below, even Ubuntu Alternate installers also allows us to install Ubuntu minimal system offline just by pressing F4? Is this true as well?

Thanks a lot.

Below is the page, I came across this morning,

[http://askubuntu.com/questions/203122/how-do-i-do-a-minimal-install-without-an-internet-connection](http://askubuntu.com/questions/203122/how-do-i-do-a-minimal-install-without-an-internet-connection)

Normally, I visit the following page in order to download the Lubuntu mini (minimal) iso.

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Downloading](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Downloading)

---

### Post by sudodus on 2015-06-13
I'm not sure that I understand why you want this. Please explain more, and you will get a more relevant answer :-)

I have used the Ubuntu mini.iso, as well as the iso files for Ubuntu Server and Lubuntu, that you are mentioning. Is the target system for you Lubuntu Core plus some program packages? I suppose that you want a very light-weight Ubuntu based system with a desktop environment or maybe only a window manager, but at least some tools to run graphical application programs.

Somewhere, sometime, you must download every package that you need. The Ubuntu mini.iso and the Ubuntu Server iso file contain no graphical application programs, that you would want. So you need an internet connection to get them.

It is possible to create the system you want (an installed system) as an OEM install, add the tweaks, and then distribute those programs either as cloned copies, compressed image files or tarballs (compressed tar files). There are several other alternatives, but I think these are fairly easy to use. See the following links

OEM - [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

Cloned copies, compressed image files - [http://clonezilla.org/](http://clonezilla.org/)

Tarballs - [https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

---

### Post by v3.xx on 2015-06-13
> Ubuntu Server releases designed to allow the option of installing Ubuntu minimal just by pressing F4?
Don't overlook the next step. Tick on 'Manual Package Selection' or you end up with server stuff :)

> Will the installation done by this method ensure that all the basic packages that were previously downloaded via a must have internet connection will automatically be installed offline this time around?
I do believe so, the basics should all be on the install cd.  Although I have not ever unplugged the internet to prove this.

As sudodus (morning sudodus :) ) has pointed out, that will be all you can get from the server install.  To add the GUI, you will need internet.

---

### Post by tgalati4 on 2015-06-13
If you know exactly what packages you want in a system, then you can spin your own ISO with those packages included.  Otherwise, look through [http://distrowatch.org](http://distrowatch.org) and find a Debian/Ubuntu-based distro that is close to what you want and just burn that.  There are several hundred to choose from, and you only need one.  Chances are there is a distro that is 99% of what you want already.

---

### Post by v3.xx on 2015-06-13
> And one more thing, as per the page given below, even Ubuntu Alternate installers also allows us to install Ubuntu minimal system offline just by pressing F4? Is this true as well?
As far as I know, there is only one 'Alt install CD' and it is Lubuntu.  Which will also give you a terminal only (no GUI) install.  When using this, the Lubuntu CD does not know its Lubuntu and will allow you to install any desktop or any flavor.  Again, you need internet to add your GUI.

---

### Post by grahammechanical on 2015-06-13
Your question:

> Now, my query is, are all the new (after 12.10) Ubuntu Server releases  designed to allow the option of installing Ubuntu minimal just by  pressing F4?

Answer: Yes. I have just tested a 15.04 server ISO image and pressing F4 brings up the following options;

Normal install
OEM install
Install a minimal system
Install a minimal virtual machine.

My  understanding of a "minimal" installation is that we get Linux and  nothing more. If we do not use the installer options to select packages  to install then once we have installed Linux we need to use the command  line to install anything else and that would require an internet  connection. Or, an offline repository.

Regards.

---

### Post by v3.xx on 2015-06-13
> My  understanding of a "minimal" installation is that we get Linux and  nothing more.
Thats my understanding too.

And I use 'Install a minimal system'

'Install a minimal virtual machine' really knocks the package count down, but you end up putting those packages back in when adding a desktop environment.

---

### Post by tech291083 on 2015-06-23
Friends,

Thanks for the replies. Appreciated. But query is simple. I have in the past installed Ubuntu Desktop, Ubuntu Server (it has no GUI I know that and I installed the GUI later on with an internet connection), Lubuntu Desktop, which has LXDE and Ubuntu Mini as well. What I mean by Ubuntu Mini is here on the below page. 

[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Downloading](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#Downloading)

I have downloaded this 14.04 Trusty Tahr[ 32 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/installer-i386/current/images/netboot/mini.iso")   (32 MB) and burned to a CD and installed it on my pc with an active internet connection. I knew before installing that it has no regular GUI (Desktop Enviorment), after installing the pacakges during installation process via internet connection, I rebooted the pc and installed the regular desktop environment with the following command, it was LXDE. And I was happy with it. 

> sudo apt-get --no-install-recommends install lubuntu-desktop

But I am a little curious to know whether there is any way I can install even the basic minimum packages without having an internet connection?

 and whether pressing F4 while installing the regular Ubuntu Server version, which brings up the - Install a minimal system - as one of the options will also help me install even the basic minimum packages without having an internet connection?

I know that I will later on need an active internet connection to install GUI and other applications I want. But I only want to know whether it is possible to install Ubuntu Mini just like the way we install any regular Ubuntu Desktop version, during which one doesn't require an active connection. For updaing Ubuntu Mini I know that internet is a must, but for the time being I only want to install it as it does, without GUI enviornment like Unity etc. Thanks

---

### Post by sudodus on 2015-06-23
Now I think I understand what you want.

Yes, it is possible to use the Ubuntu Server iso file instead of the mini.iso file and install a minimal system without a graphical desktop and without any server software. Just don't select any server packages, not even basic server. I don't remember exactly how to do it, but I have done it, maybe one year ago, and the advantages (compared to using the mini.iso) are

- faster (I know, because it uses files that the mini.iso must download)
- needs no internet (I think, but I don't remember if I actually tried without an internet connection)

but it does not create exactly the same minimal installed system as from mini.iso. At least I remember that there were slight differences.

Anyway try it, and find out if it is useful for you :-)

---

### Post by v3.xx on 2015-06-23
A bit dated, but a good reference.

[http://ubuntuforums.org/showthread.php?t=2092654](http://ubuntuforums.org/showthread.php?t=2092654)

---

### Post by tech291083 on 2015-06-25
> **sudodus said:**
> Now I think I understand what you want.

Yes, it is possible to use the Ubuntu Server iso file instead of the mini.iso file and install a minimal system without a graphical desktop and without any server software. Just don't select any server packages, not even basic server. 

but it does not create exactly the same minimal installed system as from mini.iso. At least I remember that there were slight differences.


Yes, you are spot on.

Yes, I was able to install the minimum system from the Ubuntu Server iso itself just by pressing F4 and selecting minimal system. No internet was required. Smooth install. Text based only. As per your advice, I did not select any server packages, not even basic server. 

And yes, you are right that installing from the Server iso, it does not create the same system. The biggest difference was no of packages installed, while regular install from the Ubuntu Mini iso installed 390 pacakges as I had to keep the internet connection on and it does download latest packges during install, as we all know.

Install from the Server iso without internet connection got me 380 packages.

I used the following command after install in both to know the exact no of packages installed.

```
dpkg -l | wc -l
```

The best thing to come out of all this effort, is nothing else but a clear understanding of the fact that minimum (GUI less, kernel only) Ubuntu install is very much possible via the Server iso, that too without a working internet connection.

Thanks a lot for the wonderful guidance. Appreciated and thank you all who have tried to help.

---

### Post by sudodus on 2015-06-26
Congratulations :KS and thanks for sharing your results with so many details :-)

Finally,please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

