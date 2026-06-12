---
title: "Skype on Ubuntu 13.04?"
date: 2013-05-15
forum: General Help
---

### Post by markw10 on 2013-05-15
I have heard that Skype is available for Linux.  Yet I don't see it on Ubuntu 13.04 and don't see it in the Software Center.  Is there any way to get Skype for Ubuntu Linux 13.04?  Thanks!

---

### Post by zombifier25 on 2013-05-15
If you're running 64bit Ubuntu, then run this command first:
```
sudo dpkg --add-architecture i386
```

You need to go into Software Sources to enable the Partner Repositories. In Software Center, go to Edit > Software Sources > Other Software and enable the two "Canonical Partners" checkboxes. Once done, exit, and update your repository info:
```
sudo apt-get update
```
Skype should show up.

---

### Post by AmandaLovatt on 2013-05-15
> **zombifier25 said:**
> If you're running 64bit Ubuntu, then run this command first:
```
sudo dpkg --add-architecture i386
```
Is this some equivalent to "apt-get install ia32-libs"? Which is better?

---

### Post by zombifier25 on 2013-05-15
Well Skype is multiarch, which means the same package is used for both 32 and 64bit systems.

More info here: [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by timgood on 2013-05-15
Just enabling the partner repository should pull down all the necessary 32bit libs to work on 64bit. It did for me.

---

### Post by Jovanontherun on 2013-05-15
Helo Dip, I'm a bit geek with linux and ubuntu, I have read these instructions but it is not working pls see what it wrote back to me:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

I don know and how to run skype at the end, I have HP probook i3, with Intel's HD4000? Thank in advance

---

### Post by rrich1974 on 2013-05-15
just download the .deb from their website and install it.

---

### Post by grahammechanical on 2013-05-15
You will notice that the Skype developers only support Ubuntu LTS releases - 10.04 and 12.04 and not interim releases. That is the issue here.

[http://www.skype.com/en/download-skype/skype-for-linux/](http://www.skype.com/en/download-skype/skype-for-linux/)

Here will see the difference between free to download with limited freedom to use proprietary software and open source software. If you start skype from the terminal you may see some error messages that indicate missing libraries that can then be installed through Synaptic Package Manager. It is a bit of an experiment.

Regards.

---

### Post by timgood on 2013-05-15
> **Jovanontherun said:**
> Helo Dip, I'm a bit geek with linux and ubuntu, I have read these instructions but it is not working pls see what it wrote back to me:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.

I don know and how to run skype at the end, I have HP probook i3, with Intel's HD4000? Thank in advance

Try: ```
sudo apt-get remove skype
```

Add partner repository (if not already done).

Then: ```
sudo apt-get install skype
```

This should pull down all the necessary dependencies. Installing skype from the Skype website will not do that.

Hope this helps.

---

### Post by Jovanontherun on 2013-05-15
Hi Tim,

It does not work see the msg:

Reading package lists... Done
jovan@jovan-HP-ProBook-4540s:~$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
jovan@jovan-HP-ProBook-4540s:~$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'skype:i386' has no installation candidate
jovan@jovan-HP-ProBook-4540s:~$

---

### Post by Nolix on 2013-05-15
The simplest way to install skype on ubuntu is to go to [www.skype.com]("http://www.skype.com") > downloads > choose your distro then select ubuntu 12.04 (multiarch) and it should open in the ubuntu software center, click install enter your password and run skype.

Also if you're on a 64-bit system, and need the 32-bit libraries for the gtk theme, just download them from the terminal ```
sudo apt-get install ia32-libs
```

---

### Post by Jovanontherun on 2013-05-15
I'm not sure it'll work

---

### Post by Jovanontherun on 2013-05-15
As I said:

jovan@jovan-HP-ProBook-4540s:~$ sudo apt-get install ia32-libs
[sudo] password for jovan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

---

### Post by Nolix on 2013-05-15
> **Jovanontherun said:**
> As I said:

jovan@jovan-HP-ProBook-4540s:~$ sudo apt-get install ia32-libs
[sudo] password for jovan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

As far as that issue goes, theres a ton of suggestions on this page to look at. [http://askubuntu.com/questions/136394/cannot-install-ia32-libs](http://askubuntu.com/questions/136394/cannot-install-ia32-libs)
but since you have broken packages it may be as simple as running```
sudo apt-get install -f
```

---

### Post by Jovanontherun on 2013-05-15
Check it now:

jovan@jovan-HP-ProBook-4540s:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-eggtrayicon
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by philinux on 2013-05-15
> **Nolix said:**
> The simplest way to install skype on ubuntu is to go to [www.skype.com]("http://www.skype.com") > downloads > choose your distro then select ubuntu 12.04 (multiarch) and it should open in the ubuntu software center, click install enter your password and run skype.

Also if you're on a 64-bit system, and need the 32-bit libraries for the gtk theme, just download them from the terminal ```
sudo apt-get install ia32-libs
```

Title says 13.04. Enable partner repo and just install skype from software center. Now that is simple

---

### Post by Jovanontherun on 2013-05-15
Thanks, but look:

jovan@jovan-HP-ProBook-4540s:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.

---

### Post by Nolix on 2013-05-15
> **philinux said:**
> Title says 13.04. Enable partner repo and just install skype from software center. Now that is simple

I'm guessing the only difference is it pulls the 32-bit libs along with it.

---

### Post by Jovanontherun on 2013-05-15
what's the solution?

---

### Post by Jovanontherun on 2013-05-15
Have a word for my problem?

---

### Post by timgood on 2013-05-16
Did you do sudo apt-get update before you ran the install?

---

### Post by philinux on 2013-05-16
I've just done a check on my system which is 64 bit 13.04

```
apt-rdepends skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
skype
  Depends: skype-bin
skype-bin

```

and

```
apt-cache policy ia32-libs
ia32-libs:
 **[COLOR="#FF0000"] Installed: (none)[/COLOR]**
  Candidate: 20090808ubuntu36
  Version table:
     20090808ubuntu36 0
        500 http://archive.ubuntu.com/ubuntu/ raring/universe amd64 Packages


```

And attached pic of skype running. All I did was install skype from synaptic. Which pulls in skype-bin:i386 
[ATTACH=CONFIG]242640[/ATTACH]

---

### Post by zombifier25 on 2013-05-16
Try doing an "sudo apt-get update" first. If that doesn't work, then try changing the mirror in Software Sources to another location, then "sudo apt-get update" again. I was having the same problem and it solved it for me.

---

### Post by Jovanontherun on 2013-05-16
Yes I did

---

### Post by Jovanontherun on 2013-05-16
What does it means change the mirror?

---

### Post by Jovanontherun on 2013-05-16
I've got this:

jovan@jovan-HP-ProBook-4540s:~$ apt-rdepends skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Unable to locate package skype
skype
jovan@jovan-HP-ProBook-4540s:~$

---

### Post by Jovanontherun on 2013-05-26
@zombifier25
@philinux

Thanks for the info, I've changed the  mirror, try to download missing libs, reinstall and install different  tools to build unmet dependencies, etc. and ended with complete system  re-installation, since I fuc... somehow during the process of getting  skype, :) :), so I had to do it. Now I'm awaiting fro someone to solve this  issue, or simply stop using skype with this computer...

---

### Post by ShadowVegan on 2013-05-30
> **Jovanontherun said:**
> @zombifier25
@philinux

Thanks for the info, I've changed the  mirror, try to download missing libs, reinstall and install different  tools to build unmet dependencies, etc. and ended with complete system  re-installation, since I fuc... somehow during the process of getting  skype, :) :), so I had to do it. Now I'm awaiting fro someone to solve this  issue, or simply stop using skype with this computer...

Try downloading and installing Skype from the [official website]("http://www.skype.com/en/download-skype/skype-for-computer/"). Then you don't need to deal with repositories or even the terminal at all. Choose 12.04 (I have 13.04 and the 12.04 works on mine; there is no 13.04 version) and when it gives you the option to save or open, open with GDebi Package Installer (or a equivalent).

If you already have Skype installed but not working, make sure to remove the existing installation first with ```
sudo apt-get remove --purge skype
```

---

