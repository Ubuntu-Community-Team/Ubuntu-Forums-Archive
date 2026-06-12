---
title: "Creating a new Sources.list in /etc/apt"
date: 2014-09-04
forum: General Help
---

### Post by Cocolate on 2014-09-04
Hello, Ive come a cross problems on a fresh new install adding UbuntuStudio-desktop flavor on my UEFI system running Ubuntu 13.10

I just spent the day yesterday reinstalling my system, then the UbuntuStudio has caused a faulty system errors.

I was suggest to find my "sources.list" and post results. 

The "sources.list" only opens the picture attached below

I created a new "sources.list" file with the generator > [http://askubuntu.com/questions/161239/where-can-i-find-my-original-sources-list-file](http://askubuntu.com/questions/161239/where-can-i-find-my-original-sources-list-file)


Here is the attachment. I do not get much responses on this forum. Any advice or help is greatly appreciated.

Thank you

---

### Post by Bashing-om on 2014-09-04
Cocolate; Hello ;

Be aware, release 13.10 is End_Of_Life and the software repository has been turned away and no longer exist as you may have known it.
It is most highly suggested that you either upgrade the present install to 14.04 OR
a clean fresh install of a current release ( 12.04, 14.04)
See:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
old info, but remains apt.

[INDENT][INDENT]time past to move on up
[/INDENT][/INDENT]

---

### Post by Cocolate on 2014-09-04
Hello Bashin-om thank you for your response.

I cannot use 12.04 or 14.04 because my UEFI system does not have  Secure Boot option so I cannot boot anything without Microsoft key,  which 12.04 used to have but no longer will it install. I did try  yesterday when reinstalling 13.10.

I was having ZERO problems until the exact moment I tried installing  UbuntuStudio-desktop. Which I believe was UbuntuStudio-desktop 14.04..  Maybe its the 14.04 flavor that is the problem, but the system runs fine  until I did that and I would just like to get back before the error  occured without having to completely reinstall and do everything over. I  mean it took me literally 5 hrs to get done and I really do not want to  go through that all over again....! Isnt there a way to just erase the  UbuntuStudio-desktop flavor comletely as the system was before it was  there?

> **Bashing-om said:**
> Cocolate; Hello ;

Be aware, release 13.10 is End_Of_Life and the software repository has been turned away and no longer exist as you may have known it.
It is most highly suggested that you either upgrade the present install to 14.04 OR
a clean fresh install of a current release ( 12.04, 14.04)
See:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
old info, but remains apt.
[INDENT][INDENT]time past to move on up
[/INDENT]
[/INDENT]


---

### Post by grahammechanical on 2014-09-04
> 
[LIST]
[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Ubuntu 2010 was the first Linux distribution to be able to install on machines with secure boot enabled. Since October 2010 every release of Ubuntu and its flavours, such as Ubuntu Studio comes with Linux kernels that have been signed by a Microsoft key. We should not need to disable secure boot.

We cannot install Ubuntu Studio 14.04 desktop on Ubuntu 13.10. So, what version of Ubuntu do you have installed? Is it 13.10 or 14.04? You may find that re-installing is the best option for you. 

Why did you think that you needed to re-generate the sources list? What errors were you getting? If we are running an out of support version of Ubuntu then we will have problems getting updates and installing software because the repositories have been closed and moved. And that means that the addresses to the servers in our sources list are now inaccurate.

Regards.

---

### Post by Bashing-om on 2014-09-04
Cocolate;

Short answer, NO .
Running an End_Of_Life version is not ever a recommendation. In that event there are no updates to the system, and that includes security updates/fixes.

I have no experience with Windows 8 or UEFI, sorry, others will have to advise on how to cope with the "MicroSoft key". 

It is an imperative  to get you up on a current release, but with UbuntuStudio-desktop, I again have no experience and can not advise.
I will say, IF there is no access to the software repository - to fix the present install - the prospect is bleak.

But as a poke to see what might be done:
```

sudo apt-get remove --purge  UbuntuStudio-desktop

```
Which I expect will rip the guts out of the operating system, and may require some to be reinstalled:
IF there is no software repository that is accessible, then the better thing at this point is a fresh install, however you must do it ( Win8, UEFI, keys !)

Else one can try and release upgrade, with no desktop installed -> CLI system;
see what now results: 
```

sudo apt-get -f install
sudo dpkg -C

```
Now if the package manager is in a happy state, try and do the release_upgrade: MAYBE !! 
1) Make sure all proprietary drivers are reverted to open source - No access to the repository, ummm, is this even possible ?
2) Make sure all 3rd party software sources are disabled
3) Make sure no screensaver is active

Then: -> terminal command:
```

sudo do-release-upgrade

```

All I can do is offer my suggestions, and some insight on what might happen, It is up to you to decide what is in your best interest, and how you want to proceed. With that focus to our attention, we can then best offer assistance.

[INDENT]no easy solution
[/INDENT]

---

### Post by Cocolate on 2014-09-04
I dont know if I explained it correctly:

I CANNOT USE 12.04 OR 14.04

I tried to install them yesterday.... they DO NOT install. 13.10 distro is the only I have been able to install as of now. 12.04 USED to be compatible but it not longer actively runs on my system. The error refuses to allow the bootloader to install. I understand why youre saying that, and what youre saying, but it DOES NOT WORK anymore. I know ALOT about UEFI because I didnt want Ubuntu at the time, but I am stuck with it unless I change the partition from MBR to GPT which is too advanced for me because I have to do it manually and so I just stick with Ubuntu.

So if that is more clear, 13.10 runs perfectly fine. I have ZERO issues running 13.10 right now, the problem I have is I installed UbuntuStudio-desktop with this link: [http://www.javacodegeeks.com/2014/02/5-most-awesome-desktop-environments-for-ubuntu.html](http://www.javacodegeeks.com/2014/02/5-most-awesome-desktop-environments-for-ubuntu.html)

And I have also ran every command I could find to purge UbuntuStudio which is not working, because upon installing UbuntuStudio there was an error and did not fully install.

To remove: [http://askubuntu.com/questions/186425/how-do-i-uninstall-the-ubuntu-studio-desktop-package](http://askubuntu.com/questions/186425/how-do-i-uninstall-the-ubuntu-studio-desktop-package)

The error on my PC I have is:
```

An error occured, please run Package Manager from the right-click menu or apt-get in the terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies
```

This happened only AFTER UbuntuStudio-desktop installation.

I just do not want to do a complete reinstall because I just got everything set up perfectly I thought it would be possible to just extract the installation and reboot somehow but I guess that is rhetorical.

---

### Post by Bashing-om on 2014-09-04
Cocolate;
In that case, regretfully, I have no other solution to offer.

[INDENT]it is all in knowing how
[INDENT][INDENT][INDENT]here, I don't
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Cocolate on 2014-09-04
Well, I appreciate your feedback. I dont usually get replies on this forum. Reinstallation is my final option

---

