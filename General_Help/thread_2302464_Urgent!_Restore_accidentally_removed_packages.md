---
title: "Urgent! Restore accidentally removed packages"
date: 2015-11-10
forum: General Help
---

### Post by zeron00 on 2015-11-10
Urgent help needed!
I accidentally removed over 500 packages with apt-get -- I was trying to downgrade 2 packages and didn't notice that all those other packages are about to be removed). Among those removed are dependencies of cryptsetup and kdm. Now I'm unable to restore them. The output I get when trying to restore them is as following:
```

zeron@ZeronKb:~$ sudo apt-get install cryptsetup
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 cryptsetup : Depends: dmsetup
              Depends: initramfs-tools (>= 0.91) but it is not going to be installed or
                       linux-initramfs-tool
              Depends: plymouth but it is not going to be installed
              Depends: cryptsetup-bin but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
zeron@ZeronKb:~$ sudo apt-get install kdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 kdm : Depends: kde-runtime but it is not going to be installed
       Depends: libkio5 (>= 4:4.11) but it is not going to be installed
       Depends: libknewstuff3-4 (>= 4:4.11) but it is not going to be installed
       Depends: libkworkspace4abi2 (= 4:4.11.14-0ubuntu1~ubuntu14.04~ppa9) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I'm on 64-bit Kubuntu trusty

---

### Post by ajgreeny on 2015-11-10
Do you have some packages installed from a ppa which you have later removed or disabled as the libkworkspace4abi2 version needed is a ppa version, ie, 4:4.11.14-0ubuntu1~ubuntu14.04~ppa9

---

### Post by QDR06VV9 on 2015-11-10
Have you yet tried
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
And maybe post back the out put of the last command.
Sorry ajgreeny ninjaed you were faster

---

### Post by zeron00 on 2015-11-10
Yes. At one time I upgraded to utopic. And I still have some packages that belonged to utopic release, but many of utopic repositories are gone now. I had to revert many of the repositories to trusty release. That was the reason I needed to downgrade those two packages that caused this: I needed to install some development packages for gtk and these required specific versions of the regular packages. But since the repositories for utopic release are gone the versions that are available do not correspond to the versions that I already had on my system. Hence the downgrade.
The repository for libkworkspace4abi2 is enabled. As are others -- backports, update, security, etc.

---

### Post by zeron00 on 2015-11-10
> **ajgreeny said:**
> Do you have some packages installed from a ppa which you have later removed or disabled as the libkworkspace4abi2 version needed is a ppa version, ie, 4:4.11.14-0ubuntu1~ubuntu14.04~ppa9

Yes. At one time I upgraded to utopic. And I still have some packages  that belonged to utopic release, but many of utopic repositories are  gone now. I had to revert many of the repositories to trusty release.  That was the reason I needed to downgrade those two packages that caused  this: I needed to install some development packages for gtk and these  required specific versions of the regular packages. But since the  repositories for utopic release are gone the versions that are available  do not correspond to the versions that I already had on my system.  Hence the downgrade.
The repository for libkworkspace4abi2 is enabled. As are others -- backports, update, security, etc.

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> Have you yet tried
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
And maybe post back the out put of the last command.
Sorry ajgreeny ninjaed you were faster

Thanks, but dist-upgrade is not what I want -- especially on a broken system.

I did an upgrade to vivid in the spring. But I didn't like it so I restored from backup.

---

### Post by QIII on 2015-11-10
Just to clarify:  dist-upgrade does not upgrade to a new release, if that is what concerns you.  dist-upgrade is like upgrade, but it goes a little further (kernels, for instance) and attempts to intelligently handle dependencies within your current release.

You may be confusing the command with do-release-upgrade, which will upgrade to a new release.

---

### Post by QDR06VV9 on 2015-11-10
Just to be clear "[COLOR=#000000][FONT=Ubuntu Mono]dist-upgrade"  dose not upgrade your OS to a newer version IE: From 15.04 to 15.10
but merely updates original OS you are now on with needed packages and dependencies.
But OK and Good Luck.
Kind Regards[/FONT][/COLOR]

---

### Post by zeron00 on 2015-11-10
@[**[COLOR=#C61919][B]QIII**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=628170")
@[**[COLOR=#000000]runrickus[/COLOR]**]("http://ubuntuforums.org/member.php?u=27449")
Thanks for the clarification. I'll try that.

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> Have you yet tried
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
And maybe post back the out put of the last command.

Didn't work.
The output of the last command:
```
zeron@ZeronKb:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  dbconfig-common libc-client2007e libonig2 libqdbm14 libsmokeqtuitools4-3 mlock php5-gd php5-imap php5-mcrypt php5-pgsql php5-sqlite
Use 'apt-get autoremove' to remove them.
Done
The following packages will be upgraded:
  flashplugin-installer
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
Need to get 6,844 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
flashplugin-installer is not an essential package and so it can wait. But cryptsetup and kdm are essential to my system -- without cryptsetup I will be unable to boot even into commandline. Kdm can possibly be replaced by some other display manager, but I don't know of any replacement for cryptsetup.

---

### Post by matt_symes on 2015-11-10
Hi

> I was trying to downgrade 2 packages

Have you removed those two packages and any dependencies they may have installed ?

Have you edited your source files to remove any sources you were using to pull those two packages from ?

**EDIT:**

Back up any important files to an unencrypted drive now if you can.

Kind regards

---

### Post by QDR06VV9 on 2015-11-10
> **zeron00 said:**
> Didn't work.
The output of the last command:
```
zeron@ZeronKb:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  dbconfig-common libc-client2007e libonig2 libqdbm14 libsmokeqtuitools4-3 mlock php5-gd php5-imap php5-mcrypt php5-pgsql php5-sqlite
Use 'apt-get autoremove' to remove them.
Done
The following packages will be upgraded:
  flashplugin-installer
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
4 not fully installed or removed.
Need to get 6,844 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
flashplugin-installer is not an essential package and so it can wait. But cryptsetup and kdm are essential to my system -- without cryptsetup I will be unable to boot even into commandline. Kdm can possibly be replaced by some other display manager, but I don't know of any replacement for cryptsetup.

It was not meant to be a fix but to see possible solutions
So lets see if we can get this sorted out
```
sudo apt-get install dbconfig-common libc-client2007e libonig2 libqdbm14 libsmokeqtuitools4-3 mlock php5-gd php5-imap php5-mcrypt php5-pgsql php5-sqlite
```
Fingers crossed and paste back any errors, some of these packages don't look like stock apps.

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> It was not meant to be a fix but to see possible solutions
So lets see if we can get this sorted out
```
sudo apt-get install dbconfig-common libc-client2007e libonig2 libqdbm14 libsmokeqtuitools4-3 mlock php5-gd php5-imap php5-mcrypt php5-pgsql php5-sqlite
```
Fingers crossed and paste back any errors, some of these packages don't look like stock apps.

Seems that all the packages in this list are up to date. Here's the output:
```

zeron@ZeronKb:~$ sudo apt-get install dbconfig-common libc-client2007e libonig2 libqdbm14 libsmokeqtuitools4-3 mlock php5-gd php5-imap php5-mcrypt php5-pgsql php5-sqlite
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dbconfig-common is already the newest version.
libc-client2007e is already the newest version.
mlock is already the newest version.
libsmokeqtuitools4-3 is already the newest version.
php5-gd is already the newest version.
php5-imap is already the newest version.
php5-pgsql is already the newest version.
php5-sqlite is already the newest version.
php5-mcrypt is already the newest version.
libqdbm14 is already the newest version.
libonig2 is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```
I aborted to shorten the output -- on top of everything else I have 5 unconfigured packages. I installed them trying to correct this problem. Here's the output from dpkg --configure:
```

zeron@ZeronKb:~$ sudo dpkg --configure -a          
Setting up x11-common (1:7.7+1ubuntu8.1) ...
debconf: Unable to initialise frontend: Kde
debconf: (Unable to load QtCore -- is libqtcore4-perl installed?)
debconf: falling back to frontend: Dialog
Can't exec "insserv": No such file or directory at /usr/sbin/update-rc.d line 406.
update-rc.d: error: insserv rejected the script header
dpkg: error processing package x11-common (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up initscripts (2.88dsf-41ubuntu6.2) ...
Can't exec "insserv": No such file or directory at /usr/sbin/update-rc.d line 406.
update-rc.d: error: insserv rejected the script header
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libice6:amd64:
 libice6:amd64 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libice6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libice6:i386:
 libice6:i386 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libice6:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libice-dev:amd64:
 libice-dev:amd64 depends on libice6 (= 2:1.0.8-2); however:
  Package libice6:amd64 is not configured yet.

dpkg: error processing package libice-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 x11-common
 initscripts
 libice6:amd64
 libice6:i386
 libice-dev:amd64

```

---

### Post by zeron00 on 2015-11-10
> **matt_symes said:**
> Hi

Have you removed those two packages and any dependencies they may have installed ?

I have downgraded them. I don't remember exactly what they were -- I think one of them was libgdm1 and the other was some similar -- and that's when apt removed over 500 packages that had dependencies on these two.

> **matt_symes said:**
> 
Have you edited your source files to remove any sources you were using to pull those two packages from ?
I edited the sources some time ago -- when I discovered that many of the repositories for utopic have been removed. I reverted most of my repositories back to trusty then.
> **matt_symes said:**
> 
**EDIT:**

Back up any important files to an unencrypted drive now if you can.

Kind regards
I can't access any other drives right now. when I try to open folders on any other drives dolphin tells me that:
```
Could not start process Unable to create io-slave:
klauncher said: error loading 'kio-file'.
```

---

### Post by matt_symes on 2015-11-10
Hi

> **zeron00 said:**
> I have downgraded them. I don't remember exactly what they were -- I think one of them was libgdm1 and the other was some similar -- and that's when apt removed over 500 packages that had dependencies on these two.

Those two packages and any dependencies they brought in may stop you fixing this problem.

You really want to try to remove them. Look in the directory
```

/var/log/apt/
```

and in the file

```
/var/log/dpkg.log
```

to see what was added and removed.

> I edited the sources some time ago -- when I discovered that many of the repositories for utopic have been removed. I reverted most of my repositories back to trusty then.

Good.

> I can't access any other drives right now. when I try to open folders on any other drives dolphin tells me that:
```
Could not start process Unable to create io-slave:
klauncher said: error loading 'kio-file'.
```

Can you backup from the terminal ? ...by manually mounting an external drive and copying the files across ?

You have encryption so this would be my _first_ step, while you can, if you can, as trying to fix things may make them worse.

Kind regards

---

### Post by QDR06VV9 on 2015-11-10
> [COLOR=#000000]and that's when apt removed over 500 packages that had dependencies on these two.[/COLOR]
Yikes this might just be over my pay grade.
Need to think a bit on this one?!?
In the mean time post back the out put of 
```
sudo [COLOR=#000000]apt-get -f install -s[/COLOR]
```
But follow matt_symes advice first

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> Yikes this might just be over my pay grade.
Need to think a bit on this one?!?
In the mean time post back the out put of 
```
sudo [COLOR=#000000]apt-get -f install -s[/COLOR]
```
But follow matt_symes advice first

Output of this comand:
```

zeron@ZeronKb:~$ sudo apt-get -f install -s
[sudo] password for zeron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
5 not fully installed or removed.
Conf initscripts (2.88dsf-41ubuntu6.2 Ubuntu:14.04/trusty-updates [amd64])
Conf x11-common (1:7.7+1ubuntu8.1 Ubuntu:14.04/trusty-updates [all])
Conf libice6 (2:1.0.8-2 Ubuntu:14.04/trusty [amd64])
Conf libice6:i386 (2:1.0.8-2 Ubuntu:14.04/trusty [i386])
Conf libice-dev (2:1.0.8-2 Ubuntu:14.04/trusty [amd64])


```
Seems I need to complete installation of these packages first -- before apt can do anything else.

---

### Post by QDR06VV9 on 2015-11-10
Well Maybe?
So run it for real this time, That was just a simulation.(A dry Run)
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]apt-get -f install[/FONT][/COLOR][/COLOR]
```

---

### Post by zeron00 on 2015-11-10
> **matt_symes said:**
> Hi
Those two packages and any dependencies they brought in may stop you fixing this problem.

You really want to try to remove them.

As far as I could figure those two files are part of X11, so if they're removed the graphics system will stop working. 
> **matt_symes said:**
> 
 Look in the directory
```

/var/log/apt/
```

and in the file

```
/var/log/dpkg.log
```

to see what was added and removed.
I can only access those files through the terminal. They're quite large.

> **matt_symes said:**
> 
Can you backup from the terminal ? ...by manually mounting an external drive and copying the files across ?

You have encryption so this would be my _first_ step, while you can, if you can, as trying to fix things may make them worse.

Kind regards

Yes, I can try. Although I'm not sure how. Should I use cp command or maybe tar? I'm unsure of the syntax. I would appreciate a suggestion.

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> Well Maybe?
So run it for real this time, That was just a simulation.(A dry Run)
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo [/FONT][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Ubuntu Mono]apt-get -f install[/FONT][/COLOR][/COLOR]
```

Same result, only with more text. Output:
```

zeron@ZeronKb:~$ sudo apt-get -f install
[sudo] password for zeron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 1 not to upgrade.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.

(apt-listchanges:15114): IBUS-WARNING **: The owner of /home/zeron/.config/ibus/bus is not root!
Setting up initscripts (2.88dsf-41ubuntu6.2) ...
Can't exec "insserv": No such file or directory at /usr/sbin/update-rc.d line 406.
update-rc.d: error: insserv rejected the script header
dpkg: error processing package initscripts (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up x11-common (1:7.7+1ubuntu8.1) ...
debconf: Unable to initialise frontend: Kde
debconf: (Unable to load QtCore -- is libqtcore4-perl installed?)
debconf: falling back to frontend: Dialog
Can't exec "insserv": No such file or directory at /usr/sbin/update-rc.d line 406.
update-rc.d: error: insserv rejected the script header
dpkg: error processing package x11-common (--configure):
 subprocess installed post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of libice6:amd64:
 libice6:amd64 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libice6:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libice6:i386:
 libice6:i386 depends on x11-common; however:
  Package x11-common is not configured yet.

dpkg: error processing package libice6:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libice-dev:amd64:
 libice-dev:amd64 depends on libice6 (= 2:1.0.8-2); however:
  Package libice6:amd64 is not configured yet.

dpkg: error processing package libice-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            No apport report written because MaxReports has already been reached
                                                                                                                                                                                No apport report written because MaxReports has already been reached
                                                    Errors were encountered while processing:
 initscripts
 x11-common
 libice6:amd64
 libice6:i386
 libice-dev:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
I can try to uninstall them and then reinstall them again -- although I don't think this operation will be successful. :(
:(:(:(:(:(

---

### Post by QDR06VV9 on 2015-11-10
You should be able to use a live cd session to copy things over to another device, Drive, Thumbdrive.
[Recover Encrypted Home Folder From Live CD]("http://ubuntuforums.org/showthread.php?t=1597246")      Post #1
You will need to know your encrypted phasephrase or password. Or the above line^^
go directly to terminal and enter "sudo dolphin"

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> You should be able to use a live cd session to copy things over to another device, Drive, Thumbdrive.
[Recover Encrypted Home Folder From Live CD]("http://ubuntuforums.org/showthread.php?t=1597246")      Post #1
You will need to know your encrypted phasephrase or password. Or the above line^^
go directly to terminal and enter "sudo dolphin"

Thanks for the link, runrickus, but this guide is for ecryptfs encrypted home. I'm using dm-crypt/luks.

So, your suggestion is to stop screwing around in the dependency hell and just reinstall from scratch?

---

### Post by zeron00 on 2015-11-10
Well, at least this latest hurdle has been overcome -- the dpkg error were it said it can't configure 5 installed packages. It turns out that file insserv was in the wrong place. So I did:
```

sudo ln -s /usr/lib/insserv/insserv /sbin/insserv

```
After this dpkg could complete installation of those packages.

Now, to solve the rest of the problem...

---

### Post by QDR06VV9 on 2015-11-10
Ok Great Good Job. Disregard this then unless needed.
I see (just me) no way to fix this?
But do get more opinions here.
 I have a short tolerance to spending many hours trying to fix situations like this.
As a result I have disciplined my self to doing daily and sometimes twice daily backups and Re-installs were at a minimum usually under an hour with updates and upgrades.
Although in 10 years I have only had to Re-install only twice.(Knock on Wood)
As far as the link this might be a little more helpful  [https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/](https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/) 
Sorry I am dealing with multiple problems at one time. Sorry (No Excuse) the focus should be on you!

---

### Post by matt_symes on 2015-11-10
Hi

> **zeron00 said:**
> As far as I could figure those two files are part of X11, so if they're removed the graphics system will stop working.

I don;t know what you installed so i can't comment on that.

> I can only access those files through the terminal. They're quite large.

If you want to get a list of packages that were installed/removed then try this command.

It should list all the packages installed or removed today.

```
egrep "$(date +%F) [0-9:]{8} (install|remove) " /var/log/dpkg.log
```

If you made the changes yesterday or earlier then look you'll want the --date option for the date command. 

Here's an example for yesterday.

```
egrep "$(date --date='-1 day' +%F) [0-9:]{8} (install|remove) " /var/log/dpkg.log
```

]That may help you take stock on what was installed and removed. 

You may or may not find that useful depending on the state of your system.

Rolling back to a previous version (of a previous release) of a package can hold other packages from upgrading or being installed and that may be why you could not install the crypto package in post #1.

> Yes, I can try. Although I'm not sure how. Should I use cp command or maybe tar? I'm unsure of the syntax. I would appreciate a suggestion.

Well only you know what files you want to keep but i would use the mount and cp commands to copy all the files under your home directory for a start.

It's hard to advise as i have no idea about the state of your system so my posts are suggestions only.

Kind regards

---

### Post by zeron00 on 2015-11-10
> **runrickus said:**
> 
But do get more opinions here.

Thank you for your effort and your patience! I appreciate it!
> **runrickus said:**
> Although in 10 years I have only had to Re-install only twice.(Knock on Wood)
I had to reinstall once since 2012 - after an upgrade to quantal some things became messed up. So I make a complete backup just before a distro-upgrade. And this spring I restored a backup after an upgrade to vivid -- I just hated the look of the new plasma desktop. :)

 > **runrickus said:**
> 
As a result I have disciplined my self to doing daily and sometimes twice daily backups and Re-installs were at a minimum usually under an hour with updates and upgrades.

Can you recommend a good soft for regular backups? The backup I do before a distro-upgrade is not really a backup -- I use clonezilla to make an image of the whole system. It's not something you can do everyday.
> **runrickus said:**
> 
As far as the link this might be a little more helpful  [https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/](https://alvinabad.wordpress.com/2012/09/22/how-to-recover-a-luks-encrypted-disk/) 

Thank you! This is a useful guide.

---

### Post by zeron00 on 2015-11-10
Hi



I don;t know what you installed so i can't comment on that.


> **matt_symes said:**
> 
If you want to get a list of packages that were installed/removed then try this command.

It should list all the packages installed or removed today.

```
egrep "$(date +%F) [0-9:]{8} (install|remove) " /var/log/dpkg.log
```

If you made the changes yesterday or earlier then look you'll want the --date option for the date command. 

Here's an example for yesterday.

```
egrep "$(date --date='-1 day' +%F) [0-9:]{8} (install|remove) " /var/log/dpkg.log
```

]That may help you take stock on what was installed and removed. 

Thank you. These commands do make it easier. But there are still over 500 lines. It seems that the two packages I tried to downgrade were udev packages.

> **matt_symes said:**
> 
Rolling back to a previous version (of a previous release) of a package can hold other packages from upgrading or being installed and that may be why you could not install the crypto package in post #1.

You are completely right! It might have been much easier to edit the sources to point to vivid release instead. Maybe I can do it now. What do you think? Edit sources by hand to point at vivid repositories and do an apt-get update etc.? Vivid shoud have newer libraries than either trusty or utopic and so no packages will need a downgrade.

---

### Post by matt_symes on 2015-11-11
Hi

Sorry for the late reply. Timezones, sleep and work got in the way.

Do you still need help as i'll be available in a couple of hours ?

Kind Regards

---

### Post by zeron00 on 2015-11-16
Thank you Matt! I made a complete reinstall of the whole system, rather than trying to save one that is completely broken. Took the opportunity to try out some arch-based distros, but then went back to Kubuntu. Made a server install of trusty and then apt-get kubuntu-desktop on top of it. Thank you anyway!
I like the idea of a rolling release, but synaptic is still superior to all other package management that I've seen!

---

