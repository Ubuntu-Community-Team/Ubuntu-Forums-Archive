---
title: "another broken package"
date: 2007-01-08
forum: General Help
---

### Post by iitywygms on 2007-01-08
Hi All
My package manager is broken and I cant get it fixed.  Seems like some kind of permission issue.   Take a look and let me know what I should try next.
Thanks

kevin@kevins-laptop:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kevin@kevins-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libc6-i686 libberylsettings0 libxcomposite1 beryl-plugins-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libc6-i686
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2576kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113227 files and directories currently installed.)
Removing libc6-i686 ...
dpkg: error processing libc6-i686 (--remove):
 cannot remove `/lib/tls/i686/cmov/libc-2.4.so': Permission denied
Errors were encountered while processing:
 libc6-i686
E: Sub-process /usr/bin/dpkg returned an error code (1)
kevin@kevins-laptop:~$ sudo dpkg -r libc6-i686
(Reading database ... 113227 files and directories currently installed.)
Removing libc6-i686 ...
dpkg: error processing libc6-i686 (--remove):
 cannot remove `/lib/tls/i686/cmov/libc-2.4.so': Permission denied
Errors were encountered while processing:
 libc6-i686
kevin@kevins-laptop:~$

---

### Post by scrooge_74 on 2007-01-08
Did you try fixing the broken package first? I am no expert doing that have only done that from inside synaptic

---

### Post by obsidion on 2007-01-08
>Hi All
>My package manager is broken and I cant get it fixed.  Seems like some kind of permission issue.   Take a l>ook and let me know what I should try next.
>Thanks


Try  from a terminal, sudo apt-get install -f

---

### Post by scrooge_74 on 2007-01-08
He seems to have tried that already with not much luck

---

### Post by iitywygms on 2007-01-08
Tried all that with no luck.  I could really use some help because I cant install or delete any packages now.

---

### Post by iitywygms on 2007-01-08
oopps

---

### Post by iitywygms on 2007-01-08
tried manually  removing libc2.4.so by using natulis, (as root) no luck.  Also the properties windows said the permission could not be determined??????
so i tried this
kevin@kevins-laptop:/lib/tls/i686/cmov$ sudo chmod a+rw libc-2.4.so
chmod: cannot access `libc-2.4.so': Permission denied
hmmm. I need a expert here.

---

### Post by obsidion on 2007-01-08
> **iitywygms said:**
> Tried all that with no luck.  I could really use some help because I cant install or delete any packages now.


  Have you tried sudo dpkg -r libc6-i686

It could possible be a corrupted dpkg data base, I saw a post the other day about how to fix it but didn't bookmark it, silly me.

---

### Post by iitywygms on 2007-01-09
kevin@kevins-laptop:~$ sudo dpkg -r libc6-i686
(Reading database ... 113227 files and directories currently installed.)
Removing libc6-i686 ...
dpkg: error processing libc6-i686 (--remove):
 cannot remove `/lib/tls/i686/cmov/libc-2.4.so': Permission denied
Errors were encountered while processing:
 libc6-i686

---

### Post by obsidion on 2007-01-09
> **iitywygms said:**
> kevin@kevins-laptop:~$ sudo dpkg -r libc6-i686
(Reading database ... 113227 files and directories currently installed.)
Removing libc6-i686 ...
dpkg: error processing libc6-i686 (--remove):
 cannot remove `/lib/tls/i686/cmov/libc-2.4.so': Permission denied
Errors were encountered while processing:
 libc6-i686

 OK it sounds like something could be using this program, even though it wants to remove it.
Have you tried logging right out of the gui and going to a tty instead ?

 The only thing I found that might be of some help is this debian page

[http://qref.sourceforge.net/Debian/quick-reference/ch-package.en.html](http://qref.sourceforge.net/Debian/quick-reference/ch-package.en.html)

---

### Post by scrooge_74 on 2007-01-09
I don't think he can't take it out because something is using that package, I once manage to uninstall the entire gnome desktop from right under me.  It was funny I manage to get everything out, I just kept on working next time I rebooted there was no GUI!

I was mad at the time, now I laugh about it. I had the impression I had to do like in windows not been using stuff in order to uninstall it.

---

### Post by iitywygms on 2007-01-09
So should I or should I not uninstall this package?

---

### Post by obsidion on 2007-01-09
> **iitywygms said:**
> So should I or should I not uninstall this package?


  Have a look in /var/cache/apt/arcives

You might be able to suss out what  the corrupt file is.
 
sudo dpkg -l |grep libc

Might give you some pointers as well, maybe you have 2 versions of libc installed.

---

### Post by iitywygms on 2007-01-09
> **obsidion said:**
> Have a look in /var/cache/apt/arcives

You might be able to suss out what  the corrupt file is.
 
sudo dpkg -l |grep libc

Might give you some pointers as well, maybe you have 2 versions of libc installed.

Thank you, I will try that when I get home. 
What does suss mean?

---

### Post by Modernity on 2007-01-09
When did this occur, during install of a package?

---

### Post by obsidion on 2007-01-09
> **iitywygms said:**
> Thank you, I will try that when I get home. 
What does suss mean?

Sorry kiwi slang, --- figure out, work out the answer

---

### Post by iitywygms on 2007-01-09
> **Modernity said:**
> When did this occur, during install of a package?
Yes, I noticed it right after I installed suggested updates.

> **obsidion said:**
> Sorry kiwi slang, --- figure out, work out the answer

Thnx, I grew up in a cave. LOL

---

### Post by iitywygms on 2007-01-10
Okay
I rebooted in recovery mode. Tried doing the apt-get install-f. No luck. :mad: 
I tried to remove the file. Permission denied. :evil:  
I am running out of ideas here.:confused: 

I am by no means a linux expert so I need some help here.  Should I get my live cd and try to remove the file (libc6-686) by using the cd?  Am I going to blow up my install?
Argh!](*,) ](*,) ](*,)

---

### Post by obsidion on 2007-01-10
> **iitywygms said:**
> Okay
I rebooted in recovery mode. Tried doing the apt-get install-f. No luck. :mad: 
I tried to remove the file. Permission denied. :evil:  
I am running out of ideas here.:confused: 

I am by no means a linux expert so I need some help here.  Should I get my live cd and try to remove the file (libc6-686) by using the cd?  Am I going to blow up my install?
Argh!](*,) ](*,) ](*,)


  Recovery mode is probably not the tool to use here. You could try something I have tried before and it worked at the tme. It is time consuming and there is no guarantee that it will work. You open a tty, ie you ctrl-alt-F2 log in as yourself and cd /var/cache/apt/archives


  Now ls this is the linux equivalent of dir in dos


you can ls l* etc

The package that is being the pain and not installing should be in here...


So once you find the name sudo dpkg -i thefullpackagename enter

Remembering that tab is your friend :)

It might tell you things like needs another package just use the up arrow to get back the last command and add the needed packages and try again. Like I said it can be time consuming.
 The other thing that just may fix it is sudo dpkg-reconfigure -a

 This again will take some time and you have to be careful and read the instructions for each reconfiguration.
I realise you are probably getting a little anti at this satge and strongly considering a reinstall :)
  In some ways this would be the way to go, but I am a stubborn cuss and don't like to have something defeat me. The problem with never finding the cause is that it can happen again and the next time you might have more to lose by reinstalling.  Personally, I back up the things I need to keep to cd, my genealogy data and my music being the main ones, so reinstalling is not a biggie, the other thing I do is copy the files from /var/cache/apt/archives after a major update or every couple of weeks to a cd, that way if I do for some unknown reason have to reinstall I don't have to download everything again. I have about 7 disks of these and have only had to use them once, a xorg update on dapper managed to make a real mess, I couldn't even see the terminal to log in and fix things.

---

### Post by iitywygms on 2007-01-11
Obsidion
Thanks for your help.  I am not ready to throw in the towel just yet.  I, like you, want to fix the problem so that I can learn. :mrgreen: 

you say

"the package that is being the pain and not installing should be in here..."

How do I figure out which package is the bad one?
I looked for anything to do with libc6-i686, and I found a couple that had some similarities but nothing exactly.
I also noticed some packages were listed after the word lock. Some were listed after the word partial.  Should I be concerned about those packages?

Another question.  What if I just removed the "problem file" and then reinstalled it from a live cd?

Thanks for your help

---

### Post by iitywygms on 2007-01-11
Output from  sudo dpkg -l |grep libc

ii  klibc-utils                                1.4.10-0ubuntu3                      small statically-linked utilities built with
ii  libc6                                      2.4-1ubuntu12.1                      GNU C Library: Shared libraries
ii  libc6-dev                                  2.4-1ubuntu12.1                      GNU C Library: Development Libraries and Hea
iH  libc6-i686                                 2.4-1ubuntu12                        GNU C Library: Shared libraries [i686 optimi
ii  libcairo-perl                              0.03-1ubuntu1                        Perl interface to the Cairo graphics library
ii  libcairo2                                  1.2.4-1ubuntu2                       The Cairo 2D vector graphics library
ii  libcairo2-dev                              1.2.4-1ubuntu2                       Development files for the Cairo 2D graphics 
ii  libcairomm-1.0-1                           1.2.0-0ubuntu1                       C++ wrappers for Cairo (shared libraries)
ii  libcamel1.2-8                              1.8.1-0ubuntu3                       The Evolution MIME message handling library
ii  libcap1                                    1.10-14                              support for getting/setting POSIX.1e capabil
ii  libcdio6                                   0.76-1ubuntu1                        library to read and control CD-ROM
ii  libcdk5                                    5.0.20050424-2                       C-based curses widget library
ii  libcdparanoia0                             3a9.8-13                             Shared libraries for cdparanoia
ii  libcomerr2                                 1.39-1                               common error description library
ii  libcompress-zlib-perl                      1.41-1                               Perl module for creation and manipulation of
ii  libconsole                                 0.2.3dbs-62ubuntu10                  Shared libraries for Linux console and font 
ii  libcroco3                                  0.6.1-1build1                        a generic Cascading Style Sheet (CSS) parsin
ii  libcrypto++5.2c2a                          5.2.1c2a-3                           General purpose cryptographic shared library
ii  libcupsimage2                              1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - image libs
ii  libcupsys2                                 1.2.4-2ubuntu3                       Common UNIX Printing System(tm) - libs
ii  libcurl3                                   7.15.4-1ubuntu2                      Multi-protocol file transfer library
ii  libcurl3-gnutls                            7.15.4-1ubuntu2                      Multi-protocol file transfer library
ii  libklibc                                   1.4.10-0ubuntu3                      minimal libc subset for use with initramfs
ii  liblocale-gettext-perl                     1.05-1                               Using libc functions for internationalizatio
ii  linux-libc-dev                             2.6.17.1-10.34                       Linux Kernel Headers for development

---

### Post by obsidion on 2007-01-11
Ok have got some advice from a geek friend of mine he says this

 I think that there may be a corruption on the filesystem because it says 
 
"chmod: cannot access `libc-2.4.so': Permission denied" 
 
That's odd behaviour, because if it were a permissions problem, it'd just say 
 
chmod: changing permissions of `Desktop': Operation not permitted 
 
So, the following link will either repair or rule out file system damage: 
 
[http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/](http://www.cyberciti.biz/faq/howto-boot-ubuntu-linux-rescue-mode/)


 Not sure if it will work as I have not had the problem you have, so good luck

---

### Post by iitywygms on 2007-01-11
I cannot boot into recovery mode.  My install disk does not have that option.  So I tried using a live cd but it says that hda2 is mounted as read only.  So I used a different cd "slax" but I get the same thing.  So, I need a way to check my file system. How can I do this.
I have not mentioned that I am using reiserfs.  Dont ask my why I chose that but I did. 
Thanks

---

### Post by scrooge_74 on 2007-01-11
How come you dont have recovery mode? When the machine boots you have a couple of seconds to go into the GRUB menu and choose it.

Did you remove it from GRUB?

---

### Post by iitywygms on 2007-01-11
> **scrooge_74 said:**
> How come you dont have recovery mode? When the machine boots you have a couple of seconds to go into the GRUB menu and choose it.

Did you remove it from GRUB?
Sorry about that. I do have a recovery mode. I meant to say that I do not have the option "recover a broken system" from my Ubuntu install disk.  If you look at the link I was pointed to in a previous post, it said that the ubuntu install cd would have this option.  My edgy install disk does not.

---

### Post by iitywygms on 2007-01-11
I am going for a new install.   Gonna use dapper and ext3.  More stable and solid.
I was able to use my old dapper disk to go into recover a system mode but got errors there to.  I think I can call this install hosed.
Dangit!!!!!!!!!!!!

---

### Post by iitywygms on 2007-01-11
The error was a kernel panic.

---

### Post by iitywygms on 2007-01-12
Okay this is just a bitch session but I am now frustrated.
I decided that I need to reinstall.  So I went with dapper and ext3 file system.
Cool, my computer boots and works.  However, I want to get wireless working.  The network I access is wpa.  So I need to install network manager.  I download this to a cd and try to install it.  Needs libc6. So i burn that to cd and try to instlall it.  That needs tzdata, so i try to install that.  Broken pipe.  Cant install that. 
why is tzdata such a pain!!!!!
I have to use windblows now to access the internet.

---

