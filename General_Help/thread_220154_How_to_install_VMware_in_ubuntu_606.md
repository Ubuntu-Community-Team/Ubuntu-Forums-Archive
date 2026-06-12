---
title: "How to install VMware in ubuntu 606?"
date: 2006-07-21
forum: General Help
---

### Post by wifiabc on 2006-07-21
I would like to install VMware in my ubuntu Desktop. Are there any good instructions for doing this? Do I need to erase ubuntu desktop and install the ubuntu server first before installing VMware?

---

### Post by ifokkema on 2006-07-21
> **wifiabc said:**
> I would like to install VMware in my ubuntu Desktop. Are there any good instructions for doing this? Do I need to erase ubuntu desktop and install the ubuntu server first before installing VMware?
Which VMWare tool are you referring to? VMPlayer? VMWare Server?
WMPlayer can be installed through the repositories:
```
sudo apt-get install vmware-player vmware-player-kernel-modules-2.6.15-26
```
(choose different module package when running a different kernel)

---

### Post by djsroknrol on 2006-07-21
Right now the VMware server is a free download on their web site..Look for the How-to in the tips & tricks sub forum....

---

### Post by wifiabc on 2006-07-21
Thanks. I'm interested in installing the vmware server. I went to vmware website to download but got confused. If you look at the attached screenshot, there are a number of files under the linux download. 

If I just want to create VM on my ubuntu host so that I can install guest O/S in them, which are the files I should download?

---

### Post by PriceChild on 2006-07-21
You don't need to remove ubuntu desktop no.

Vmware is an application that sits in its own little window inside of an ubuntu workspace, with a guest os inside.

You can install from the repositories (although i've not had any success)

I strongly advise you to install the free vmware server tar.gz file.

Simply unzip it to a folder, then run the install file "vmware-install.pl" from a terminal:

```
cd <<directory downloaded
sudo ./vmware-install.pl
``` 
The instillation's pretty straight forward, enjoy!

---

### Post by wifiabc on 2006-07-22
Hi,
There are four files for linux. Minimum, which of the following files must be downloaded in order to be able to create and run VM images?  

VMware-server-1.0.0-28343.tar.gz
VMware-mui-1.0.0-28343.tar.gz
VMware-server-linux-client-1.0.0-28343.zip
VMware-server-win32-client-1.0.0-28343.zip

Can VMware server also run the many virtual appliances or do I need to get VMware-player for that?

Thanks.

---

### Post by ifokkema on 2006-07-22
> **wifiabc said:**
> Hi,
There are four files for linux. Minimum, which of the following files must be downloaded in order to be able to create and run VM images?  

VMware-server-1.0.0-28343.tar.gz
VMware-mui-1.0.0-28343.tar.gz
VMware-server-linux-client-1.0.0-28343.zip
VMware-server-win32-client-1.0.0-28343.zip
The first is enough. The second one is for connecting to the server from a webbrowser, and the last two are the clients for Linux and Windows (connect to a VMWare server only), but that's included in the server TAR file.

> **wifiabc said:**
> Can VMware server also run the many virtual appliances or do I need to get VMware-player for that?
Yes, it runs virtual machines created elsewhere. VMWare server extends VMWare Player with many other functionalities, such as creating virtual machines. That is something VMWare Player cannot do.

---

### Post by wifiabc on 2006-07-22
OK. Thanks.

---

### Post by bobosity on 2006-07-23
I've been trying to install vmplayer and it is not working. From Synaptic I choose vmplayer and away we go until I start getting stuff about 'can't find vmnet module' or some such silly thing. 

Back to Synaptic and a search for vmnet serves up two unlikely candidates. Hmmm...

Finally it exits with an error message.


Any thoughts?

---

### Post by wifiabc on 2006-07-24
Perhaps you may want to install vmware server instead. I just installed it. I used it to create a VM to install a minimal centos 4.3. Works great.

But you have to install the following first.
-build-essential
-xinetd
-linux-headers for your kernel version

---

### Post by ifokkema on 2006-07-24
> **bobosity said:**
> I've been trying to install vmplayer and it is not working. From Synaptic I choose vmplayer and away we go until I start getting stuff about 'can't find vmnet module' or some such silly thing. 

Back to Synaptic and a search for vmnet serves up two unlikely candidates. Hmmm...
You need to install the kernel module for your kernel. Such as the vmware-player-kernel-modules-2.6.15-26 package.

---

### Post by bobosity on 2006-07-24
I did finally get it installed by doing much what you suggested. This was the first time I've had this kind of trouble with synaptic. Maybe this package needs some reworking to get all the requirements on the first pass.

I've run Ubuntu for a month now and it is awesome. Recently I had to reinstall due to a drive failure. On my first installation I was able to go straight to vmware and install the player in my home directory. No root privileges involved. This time it didn't work and I had to use sudo.  hmmmm......

---

### Post by Tehas on 2006-07-26
I just installed Ubuntu this weekend and when I tried to install VMware Player I also ran into the problems with the vmmon and vmnet not being installed correctly.  When I tried to run the player, it complained about the vmmon file not being installed.

I used the Synaptic utility to un-install VMWare Player and the associated libraries.  It seemed to leave behind the /etc/vmware folder which needs to be removed before trying to run VMWare's install script below.

I used the VMWare Workstation instructions from the community site as a guide but adjusted Player in for Workstation.  [https://help.ubuntu.com/community/VmWare]("https://help.ubuntu.com/community/VmWare")

1)  Follow instruction #1 as-is to install the compiler and headers that you'll need to do a compile.

2)  I downloaded VMWare Player from the VMWare download site:  [http://www.vmware.com/download/player/]("http://www.vmware.com/download/player/")

The tar command shown for step 2 should be tweaked to be name of the player file instead of the workstation file.

[INDENT]tar xzf [COLOR="Red"]VMware-player-1.0.1-19317.tar.gz[/COLOR][/INDENT]

3)  Similarly, the actual build step should be done on the Player install directory instead of the workstation one.
[INDENT]( export CC=/usr/bin/gcc-3.4 && cd [COLOR="Red"]vmware-player-distrib[/COLOR] && sudo ./vmware-install.pl )[/INDENT]


Once I did these steps, I was able to start up the player and run an image that I had built on another system.

---

### Post by matjaz_pirnovar on 2006-08-16
> **PriceChild said:**
> You don't need to remove ubuntu desktop no.

Vmware is an application that sits in its own little window inside of an ubuntu workspace, with a guest os inside.

You can install from the repositories (although i've not had any success)

I strongly advise you to install the free vmware server tar.gz file.

Simply unzip it to a folder, then run the install file "vmware-install.pl" from a terminal:

```
cd <<directory downloaded
sudo sh vmware-install.pl
```

The instillation's pretty straight forward, enjoy!

Hi,

I followed your instructions and what I'm getting is:

> matjaz@PCPlus:~/Matjazprog/vmware-player-distrib$ sudo sh vmware-install.pl
vmware-install.pl: line 8: use: command not found
vmware-install.pl: line 14: use: command not found
vmware-install.pl: line 17: my: command not found
vmware-install.pl: line 18: my: command not found
vmware-install.pl: line 19: my: command not found
vmware-install.pl: line 20: my: command not found
vmware-install.pl: line 21: my: command not found
vmware-install.pl: line 22: my: command not found
vmware-install.pl: line 23: my: command not found
vmware-install.pl: line 24: my: command not found
vmware-install.pl: line 25: my: command not found
vmware-install.pl: line 26: my: command not found
vmware-install.pl: line 27: my: command not found
vmware-install.pl: line 28: my: command not found
vmware-install.pl: line 31: my: command not found
vmware-install.pl: line 34: my: command not found
vmware-install.pl: line 38: my: command not found
vmware-install.pl: line 39: my: command not found
vmware-install.pl: line 40: my: command not found
vmware-install.pl: line 41: my: command not found
vmware-install.pl: line 42: my: command not found
vmware-install.pl: line 43: my: command not found
vmware-install.pl: line 44: my: command not found
vmware-install.pl: line 46: my: command not found
vmware-install.pl: line 47: my: command not found
vmware-install.pl: line 48: my: command not found
vmware-install.pl: line 49: my: command not found
vmware-install.pl: line 50: my: command not found
vmware-install.pl: line 53: sub: command not found
vmware-install.pl: line 54: undef: command not found
vmware-install.pl: line 55: undef: command not found
vmware-install.pl: line 56: undef: command not found
vmware-install.pl: line 57: undef: command not found
vmware-install.pl: line 58: undef: command not found
vmware-install.pl: line 60: syntax error near unexpected token `INSTALLDB,'
vmware-install.pl: line 60: `  open(INSTALLDB, '<' . $gInstallerMainDB)'
matjaz@PCPlus:~/Matjazprog/vmware-player-distrib$


Am I missing something? Did I forgot to install something beforehand?

Regards,
M

---

### Post by David Corrales on 2006-08-16
> **matjaz_pirnovar said:**
> Hi,

I followed your instructions and what I'm getting is:



Am I missing something? Did I forgot to install something beforehand?

Regards,
M
Did you apt-get the build-essential package?

---

### Post by matjaz_pirnovar on 2006-08-17
> **David Corrales said:**
> Did you apt-get the build-essential package?

Hi,

No, I didn't pre-install anything.
I have read in this thread that they are needed, but only for wmserver?
For wm server these should be installed right? (from one of the postings on the 1st page):

build-essential
xinetd
linux-headers for your kernel version

PS: Can you perhaps give me a hint of the whole commands?

Thanks,
M

---

### Post by ifokkema on 2006-08-17
> **matjaz_pirnovar said:**
> Hi,

I followed your instructions and what I'm getting is:
```
sudo sh vmware-install.pl
```

Instructions were faulty, I'm afraid. This is just telling bash to interpret a perl file, which goes hopelessly wrong.

You need to cd to it's directory and run:
```
sudo ./vmware-install.pl
```
Have fun!

---

### Post by matjaz_pirnovar on 2006-08-17
You need to cd to it's directory and run:
```
sudo ./vmware-install.pl
```
Have fun![/QUOTE]

Cool! Thanks. Gonna try it today.

M :)

---

### Post by PriceChild on 2006-08-17
Whoops i'm extremely sorry about those instructions...

make sure you've allowed the file to be executed with a

```
sudo chmod 775 vmware-install.pl
``` 
Before you try and run it.

---

### Post by ifokkema on 2006-08-17
> **PriceChild said:**
> Whoops i'm extremely sorry about those instructions...

make sure you've allowed the file to be executed with a

```
sudo chmod 775 vmware-install.pl
``` 
Before you try and run it.

It should be executable by default. I've installed the VMWare Player and the VMWare Server from the download from the website, and the vmware-install.pl was always executable.

Anyway, I have my share of issues with VMWare Player from the repositories. The player and the server always start whining after a while that you have to reinstall. I was quite annoyed with that, so I figured going with the repositories fix that issue. Took me quite some trouble to fix it; I currently have the problem that every time I start up my PC and try to run VMWare Player, it claims it needs to reconfigure, incl. recompiling the module. Then that goes wrong, and I have to apt-get install --reinstall the whole package to get away from that issue... Possibly related to having installed from the sources first, but either way - just another vote that you may want to install from the VMWare download.

---

### Post by matjaz_pirnovar on 2006-08-17
Hey,

Everything runs and installs fine until I try to run it (have followed this thread [http://www.ubuntuforums.org/showthread.php?p=1390992#post1390992)](http://www.ubuntuforums.org/showthread.php?p=1390992#post1390992)).
Then home window and vmware window pop out as if just about to start and in terminal I get:

> matjaz@PCPlus:~$ /usr/bin/vmplayer
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

When I close the home window everything stops as if nothing has happened.
What does it mean: No version information available? Is that why it doesn't open?

What am I doing wrong?

Thanks.

---

### Post by Aikon- on 2006-08-17
> **PriceChild said:**
> 
```
cd <<directory downloaded
sudo sh vmware-install.pl
```

I had to use:

```
sudo perl vmware-install.pl
```

I went through the setup process choosing install directories and then I got the following error message:

```
Unable to get the access rights of source file "./vmware-vix/bin".

Execution aborted.
```

Any suggestions?

---

### Post by PriceChild on 2006-08-17
Yeah i'm sorry i got that wrong earlier... its been pointed out :)

*EDITS post*

---

### Post by ifokkema on 2006-08-17
> **matjaz_pirnovar said:**
> 
/usr/lib/vmware/bin/vmplayer: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
I got the exact same error but... it's running fine anyway.
What do you mean with 'Home window'? When you run VMPlayer you get two windows?!!??

---

### Post by matjaz_pirnovar on 2006-08-18
> **ifokkema said:**
> I got the exact same error but... it's running fine anyway.
What do you mean with 'Home window'? When you run VMPlayer you get two windows?!!??

Hi,

Yes, sort of. Well I get WM Player window with its icon and logo etc. and then another window where it says Open virtual machine where I can select files and has an 'Open' button.

I never used vmplayer before. Could it be that in this case I need to just open (start) another OS I intend to use (Windows) and start uploading/installing it?

Have a feeling that this could be the issue...


Also have a feeling that it works and I'm overlooking something. Feels there is something very simple...

This is the image I get:

[IMG]http://static.flickr.com/66/218283132_49a3a64da1.jpg?v=0[/IMG]

---

### Post by matjaz_pirnovar on 2006-08-18
x

---

### Post by ifokkema on 2006-08-18
Ah, now I get it. You don't have any virtual machines!
VMWare Player runs (plays) Virtual Machines. These are a set of files that hold an whole Operating System. However, you can't create these Virtual Machines with VMWare Player, you need VMWare Server!

If you don't have any Virtual Machine, you need to install VMWare Server. Then you can select to create a Virtual Machine, and install Windows in it. After that, you can use the VMWare Player (or just the Server) to run the Virtual Machine... :)

Hope this clearifies the issue.

---

### Post by ajaustin on 2006-08-18
I'm trying to get VMWare working again after upgrading to 6.06; it used to work on 5.10 but now I have a different kernel 2.6.15-26-386.

I am running the install script ./vmware-install.pl as I did on previous occasions and it says that I need to compile the vmware kernel module as there is not a stock one for this kernel.

I have installed linux-headers-2.6.15-26, linux-headers-2.6.15-26.386 and linux-source-2.6.15 but the VMWare install script complains that 

> The directory of kernel headers (version 2.6.15.7-ubuntu1) does not match your running kernel (version 2.6.15-26-386).  Even if the module were to compile successfully, it would not load into the running kernel.

---

### Post by ifokkema on 2006-08-18
> **ajaustin said:**
> I'm trying to get VMWare working again after upgrading to 6.06; it used to work on 5.10 but now I have a different kernel 2.6.15-26-386.
You can just install the new kernel module package matching your kernel version; you don't **need** to compile it yourself.

```
sudo apt-get install vmware-player-kernel-modules-2.6.15-26
```

HTH

---

### Post by ajaustin on 2006-08-18
Thanks but I am not sure that this quite does it for me.

Forgot to mention - it's VMWare Workstation that I have.  It needs a kernel module called vmmon.

When I try to run vmware it says that it is installed but not configured and that I need to run /usr/bin/vmware-config.pl, this script then wants me to compile the vmmon kernel module as before even after installing vware-player-kernel-modules-2.6.15-23.  I have reverted to kernel 2.6.15-23 so that the versions match.

---

### Post by mojavelinux on 2006-08-18
> **ifokkema said:**
> You can just install the new kernel module package matching your kernel version; you don't **need** to compile it yourself.

If it helps anyone, I found that the reason I could not get vmware-player installed properly is because I didn't have the "security" source setup for my multiverse repository.  Hence, my vmware-player-kernel-modules did not match my kernel version.  Depending on the path you took to get to your current Ubuntu installation, your sources might not be correct.

Ensure that you have:

```
deb http://security.ubuntu.com/ubuntu dapper-security multiverse
```

---

### Post by matjaz_pirnovar on 2006-08-18
> **ifokkema said:**
> Ah, now I get it. You don't have any virtual machines!
VMWare Player runs (plays) Virtual Machines. These are a set of files that hold an whole Operating System. However, you can't create these Virtual Machines with VMWare Player, you need VMWare Server!

If you don't have any Virtual Machine, you need to install VMWare Server. Then you can select to create a Virtual Machine, and install Windows in it. After that, you can use the VMWare Player (or just the Server) to run the Virtual Machine... :)

Hope this clearifies the issue.

Thanks a lot. Will try it.

Can you give me a hint if I need to uninstall present 'leftover' of vmplayer before installing wmserver? I've noticed some guys had troubles clashing with previous wmware... :)

---

### Post by ifokkema on 2006-08-19
> **ajaustin said:**
> Thanks but I am not sure that this quite does it for me.

Forgot to mention - it's VMWare Workstation that I have.  It needs a kernel module called vmmon.

When I try to run vmware it says that it is installed but not configured and that I need to run /usr/bin/vmware-config.pl, this script then wants me to compile the vmmon kernel module as before even after installing vware-player-kernel-modules-2.6.15-23.  I have reverted to kernel 2.6.15-23 so that the versions match.

Ah, sorry, just assumed you were talking about the player as well. If you want to still run it in the newer kernel, you need to provide the vmware-config.pl the currect (new) location of the kernel headers, so it can recompile the module. You don't need the kernel source, though.

It would be:
/usr/src/linux-headers-2.6.15-26-386/include/linux/

---

### Post by ifokkema on 2006-08-19
> **matjaz_pirnovar said:**
> Thanks a lot. Will try it.

Can you give me a hint if I need to uninstall present 'leftover' of vmplayer before installing wmserver? I've noticed some guys had troubles clashing with previous wmware... :)

Hmm... you might be right to remove the Player. My Dapper install at work had the VMWare Server and then I tried swithing to the VMWare Player from the repositories. Quite a pain and it still doesn't fully work.

I guess it's best to remove the Player, and then install the Server. :)

---

### Post by matjaz_pirnovar on 2006-08-20
> **ifokkema said:**
> Hmm... you might be right to remove the Player. My Dapper install at work had the VMWare Server and then I tried swithing to the VMWare Player from the repositories. Quite a pain and it still doesn't fully work.

I guess it's best to remove the Player, and then install the Server. :)

Yep, I deleted /etc/vmware and its sub-files. Installation of wmserver worked like a charm.
Now I will need to get Win package to install it on - don't like Win but it will only be for two programmes and virtual! ;)

Thanks, M

---

### Post by ifokkema on 2006-08-21
> **matjaz_pirnovar said:**
> (...) - don't like Win but it will only be for two programmes and virtual! ;)
Same for me, am just using it for converting .doc documents people send me to .pdf (using Open Office makes the documents just look a bit different) and in the past, printing in color. But now I bought I *Linux compatible* colour laser printer and I don't need VMWare for that anymore... :)

---

