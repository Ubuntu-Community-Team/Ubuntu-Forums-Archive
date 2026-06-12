---
title: "Software Updater is blank"
date: 2018-06-14
forum: General Help
---

### Post by &amp;KyT$0P# on 2018-06-14
Getting this when checking for updates in Xubuntu 18.04 -
[ATTACH=CONFIG]280101[/ATTACH]
???

I notice it says there are 295 kB to be downloaded, despite not listing anything.  Synaptic shows some available updates, but I don't know how many of those are phased updates that I 'shouldn't' get yet (is there a way to check this?).

What is happening to Software Updater?  Is this normal and expected behavior?  If not, how to set it right?

Thanks

---

### Post by oldos2er on 2018-06-14
Can you run sudo apt update in a terminal and post the output here?

---

### Post by bodhin2 on 2018-06-14
you could also run sudo apt-get dist-upgrade after you fo the sudo apt-get update.  i run them both.   sorry to but in oldos2er.  :-)

---

### Post by &amp;KyT$0P# on 2018-06-14
> **oldos2er said:**
> Can you run sudo apt update in a terminal and post the output here?
```
$ sudo apt update
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
Hit:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Hit:5 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Hit:6 http://ppa.launchpad.net/git-core/ppa/ubuntu bionic InRelease            
Fetched 74.6 kB in 1s (83.3 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

> **bodhin2 said:**
> you could also run sudo apt-get dist-upgrade after you fo the sudo apt-get update. 
```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libpcre2-8-0 linux-headers-4.15.0-20 linux-headers-4.15.0-20-generic
  linux-image-4.15.0-20-generic linux-modules-4.15.0-20-generic
  linux-modules-extra-4.15.0-20-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  command-not-found command-not-found-data desktop-file-utils file
  libmagic-mgc libmagic1 python3-commandnotfound wireless-regdb
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,360 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by deadflowr on 2018-06-14
If you were to cancel/close the updater and then try opening it again, does it show as blank still?

---

### Post by &amp;KyT$0P# on 2018-06-14
> **deadflowr said:**
> If you were to cancel/close the updater and then try opening it again, does it show as blank still?
Already tried that and yes it does.

---

### Post by &amp;KyT$0P# on 2018-06-15
Just tried Software Updater again now, and it's back working.  I didn't change anything in my system.  No idea what the issue was. :???:

---

### Post by bodhin2 on 2018-06-15
glad it's all working!

---

### Post by &amp;KyT$0P# on 2018-07-12
Well, this happened again today.  This time it says there are 1.9 MB of stuff to download.

Is there something in common about the day I first saw this issue and today in terms of the phased updates that are available?
Could it be related to my deliberately keeping some old kernels that got marked for auto-removal?

* Maybe answering one of my own questions here.  I decided to be daring and run [FONT=Courier New]sudo apt-get --purge autoremove[/FONT] and try Software Updater again.  It now seems back working and it lists 1.8 MB of available updates. :-k

---

### Post by deadflowr on 2018-07-12
Someone else seems to have had the same thing today:
[https://ubuntuforums.org/showthread.php?t=2396226]("https://ubuntuforums.org/showthread.php?t=2396226")
weird, huh.

---

### Post by &amp;KyT$0P# on 2018-07-21
And this problem is back yet again.  Says there are 4.0 MB to be downloaded.

As with the previous two times, I have old kernel that could be auto-removed, but I deliberately choose not to do that.

Is there a way to tell Software Updater to just ignore old auto-removable kernels?
If not, is there a way to do phased updates from the command line, so that I don't have to use Software Updater at all?

Should I report this behavior as a bug?

---

### Post by &amp;KyT$0P# on 2018-07-21
I decided to modify [FONT=Courier New]/etc/kernel/postinst.d/apt-auto-removal[/FONT] to keep the latest 4 kernels instead of just the latest 2.  Now Software Updater says my software is up to date.

If the problem returns again, hopefully this change can make [FONT=Courier New]sudo apt-get --purge autoremove[/FONT] a reasonable workaround for me.

---

### Post by RobGoss on 2018-07-21
Same here just started to get this when I run the updater and I'm using Ubuntu mate 18.04 is there a fix for this problem

---

### Post by &amp;KyT$0P# on 2018-07-21
@RobGoss I haven't found an actual fix yet.  In the mean time, does [FONT=Courier New]sudo apt-get --purge autoremove[/FONT] get your Software Updater working for now too?

---

### Post by RobGoss on 2018-07-22
Thanks Halogens for the response, The funny thing is I have mate on a few other machines and as far as I can see I'm having this issue on at least one machine. I'll try what you suggested

---

### Post by kazakore on 2018-07-22
I can't find the article but I only found out recently that Software Updater does not provide all updates to all users at the same time, but purposely stages them (I believe to try and help any bugs surface and get reported before they have been pushed to every single user.) If you update by the command line then you bypass this. Can anybody find the source to this info??

---

### Post by PaulW2U on 2018-07-22
> **kazakore said:**
> Can anybody find the source to this info??
Phased Updates - [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

### Post by kazakore on 2018-07-22
> **PaulW2U said:**
> Phased Updates - [https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

Thanks, I was searching Staged instead of Phased.

Could this be related at all?? I never use the GUI so not sure if the blankness is just no updates or a deeper issue...

---

### Post by PaulW2U on 2018-07-22
> **RobGoss said:**
> The funny thing is I have mate on a few other machines and as far as I can see I'm having this issue on at least one machine.
Strange. I have three installations of Xubuntu 18.04 and one of the Ubuntu development release (18.10)  and I don't see this issue on any of them.
> **halogen2 said:**
> Should I report this behavior as a bug?
May be you should. 

The list of currently open bugs against the Software Updater (update-manager) is [here]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bugs?orderby=-id&start=0"). I can't find anything that exactly reflects what has been discussed here over the past month. If you do report a bug you should provide as much information as possible to make the report stand out otherwise it will just be seen as *another* bug report and perhaps not get the attention from the developers that it deserves.

---

### Post by &amp;KyT$0P# on 2018-07-22
> **PaulW2U said:**
> If you do report a bug you should provide as much information as possible to make the report stand out otherwise it will just be seen as *another* bug report and perhaps not get the attention from the developers that it deserves.
Thanks PaulW2U.  Right now the only information I have is, "*Sometimes when there are ONLY phased updates and auto-removable kernel(s), Software Updater is blank*".  I don't know anything about the specific state of available phased updates relative to my machine that triggers this.  Between that, and the fact I don't control which updates are phased and when, I have no idea how to get a consistent set of steps-to-reproduce for a dev to follow.

Is the info I do have enough to file an actionable bug report?

---

### Post by PaulW2U on 2018-07-22
> **halogen2 said:**
> I have no idea how to get a consistent set of steps-to-reproduce for a dev to follow.

Is the info I do have enough to file an actionable bug report?
I've had another look at the reports already filed against the update-manager.

Does [software updater presents an empty panel for updating]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1766217") look like what you're seeing? Reported three months ago but no developer action.

It's not really clear what was actually installed. Did the reporter even know? I think any developer needs to know a few more details such as dates and the names of any packages that are installed but not displayed otherwise the report might just sit there along with the other 1500+.

---

### Post by &amp;KyT$0P# on 2018-07-22
> **PaulW2U said:**
> Does [software updater presents an empty panel for updating]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1766217") look like what you're seeing?
I think that's something else.  That bug was reported against 16.04.  I never saw such an issue in 16.04, and I'm not triggering this with back-to-back running Software Updater like in that bug's steps-to-reproduce.

>  I think any developer needs to know a few more details such as dates and the names of any packages that are installed but not displayed
Well in this latest case the packages available for update were (and still are) -
```
$ apt list --upgradable
Listing... Done
libnss-systemd/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]
libpam-systemd/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]
libsystemd0/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]
libudev1/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]
systemd/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]
systemd-sysv/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]
udev/bionic-updates 237-3ubuntu10.2 amd64 [upgradable from: 237-3ubuntu10]

```
Dates are whenever I posted in this thread about the issue.  Is it possible to get the forum to display more specific date information than "1 week ago"?

---

### Post by PaulW2U on 2018-07-22
> **halogen2 said:**
> Dates are whenever I posted in this thread about the issue.  Is it possible to get the forum to display more specific date information than "1 week ago"?
I wouldn't worry too much about the _exact_ date(s). Quoting the version numbers of the packages concerned will enable a developer to find in Launchpad the date that each package was actually released. It's really about giving someone who is able to actually fix a bug as much information as you can possibly give them.

---

### Post by &amp;KyT$0P# on 2018-07-22
Filed [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023")

Thanks PaulW2U for your help! :KS

---

### Post by jakobg on 2018-09-03
On Ubuntu Mate 16.04, the [FONT=Courier New]sudo apt-get --purge autoremove [/FONT]solution works for me.

The problem started for me on August 29, upgrading these files:
"Upgraded the following packages:
fwupd (0.8.3-0ubuntu3) to 0.8.3-0ubuntu4
gnome-software (3.20.5-0ubuntu0.16.04.10) to 3.20.5-0ubuntu0.16.04.11
gnome-software-common (3.20.5-0ubuntu0.16.04.10) to 3.20.5-0ubuntu0.16.04.11
intel-microcode (3.20180425.1~ubuntu0.16.04.2) to 3.20180807a.0ubuntu0.16.04.1
libappstream-glib8 (0.5.13-1ubuntu5) to 0.5.13-1ubuntu6
libdfu1 (0.8.3-0ubuntu3) to 0.8.3-0ubuntu4
libfwupd1 (0.8.3-0ubuntu3) to 0.8.3-0ubuntu4
libgd3 (2.1.1-4ubuntu0.16.04.8) to 2.1.1-4ubuntu0.16.04.10
libgd3:i386 (2.1.1-4ubuntu0.16.04.8) to 2.1.1-4ubuntu0.16.04.10
libpam-systemd (229-4ubuntu21.2) to 229-4ubuntu21.4
libsystemd0 (229-4ubuntu21.2) to 229-4ubuntu21.4
libsystemd0:i386 (229-4ubuntu21.2) to 229-4ubuntu21.4
libudev1 (229-4ubuntu21.2) to 229-4ubuntu21.4
libudev1:i386 (229-4ubuntu21.2) to 229-4ubuntu21.4
systemd (229-4ubuntu21.2) to 229-4ubuntu21.4
systemd-sysv (229-4ubuntu21.2) to 229-4ubuntu21.4
udev (229-4ubuntu21.2) to 229-4ubuntu21.4"

---

### Post by Redalien0304 on 2018-10-06
Ubuntu 18.04 Has a "Blank Software updater shows empty Panel"
Shows up Blank on 2 Laptops & Shows up on 1 Laptop
There is Bug Report on it though
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1795814](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1795814)

---

### Post by PaulW2U on 2018-10-07
> **halogen2 said:**
> Filed [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1783023")
Now marked as a duplicate of bug [#1072136]("https://bugs.launchpad.net/bugs/1072136") which was reported back in 2012. The fix has been applied to the development version (Cosmic) and will hopefully be backported to Bionic and Xenial in due course.
> **Redalien0304 said:**
> There is Bug Report on it though
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1795814](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1795814)
Should probably be marked as also being a duplicate of bug [#1072136]("https://bugs.launchpad.net/bugs/1072136").

---

### Post by alchap on 2018-10-16
I currently have this on 3 computers running 18.04, and have seen it on at least 2 occasions in the past.  As I wouldn't accept "anonymous" updates I closed Software Updater and waited for the next daily check.  In the past the issue appeared to resolve in a week or so, when Software Updater would begin displaying details again.  However today I ran "sudo apt autoremove" and when I ran "update-manager" after this, Software Updater was no longer blank.

---

### Post by &amp;KyT$0P# on 2018-11-25
The bug has been fixed since a while and I haven't seen this issue since installing the associated Software Updater update.

---

### Post by Quarkrad on 2019-01-03
I'm having this problem running mate 18.04 - the output of **sudo apt-get --purge autoremove** is: 

```
dad@dadubuntu:~$ sudo apt-get --purge autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  qtdeclarative5-qtquick2-plugin* qtdeclarative5-window-plugin*
0 to upgrade, 0 to newly install, 2 to remove and 1 not to upgrade.
21 not fully installed or removed.
After this operation, 145 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 225864 files and directories currently installed.)
Removing qtdeclarative5-qtquick2-plugin:amd64 (5.9.5-0ubuntu1.1) ...
Removing qtdeclarative5-window-plugin:amd64 (5.9.5-0ubuntu1.1) ...
Setting up python3 (3.6.7-1~18.04) ...
running python rtupdate hooks for python3.6...
E: py3compile:183: cannot create directory /usr/share/hplip/ui5/__pycache__: FileNotFoundError(2, 'No such file or directory')
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aboutdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/aligndialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/cleandialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/colorcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devicesetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/deviceuricombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr5_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/devmgr_ext.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabgrouptable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabnametable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/fabwindow_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/faxsetupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/filetable.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/firmwaredialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/infodialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/linefeedcaldialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/loadpapergroupbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/makecopiesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/mimetypesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/mimetypesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/nodevicesdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/nodevicesdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindiagnose.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindiagnose_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/plugindialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pluginlicensedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pluginlicensedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pqdiagdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/pqdiagdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printernamecombobox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettings_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingsdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingsdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printsettingstoolbox.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printtestpagedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/printtestpagedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/queuesconf.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/readonlyradiobutton.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/sendfaxdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/sendfaxdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/settingsdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/settingsdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/setupdialog_base5.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systemtray.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systrayframe.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/systrayframe_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/ui_utils.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/upgradedialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/upgradedialog_base.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog.py'
[Errno 2] No such file or directory: '/usr/share/hplip/ui5/wifisetupdialog_base.py'
error running python rtupdate hook hplip-data
dpkg-query: package 'virtualbox' is not installed
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
Traceback (most recent call last):
  File "/usr/bin/py3clean", line 210, in <module>
    main()
  File "/usr/bin/py3clean", line 196, in main
    pfiles = set(dpf.from_package(options.package))
  File "/usr/share/python3/debpython/files.py", line 53, in from_package
    raise Exception("cannot get content of %s" % package_name)
Exception: cannot get content of virtualbox
error running python rtupdate hook virtualbox
dpkg: error processing package python3 (--configure):
 installed python3 package post-installation script subprocess returned error exit status 4
dpkg: dependency problems prevent configuration of update-notifier-common:
 update-notifier-common depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package update-notifier-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3:any (>= 3.2~); however:
  Package pythoNo apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                                           No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                  No apport report written because MaxReports has already been reached
                                                                                                      No apport report written because MaxReports has already been reached
                                                                                                                                                                          No apport report written because MaxReports has already been reached
                                         No apport report written because MaxReports has already been reached
                                                                                                             No apport report written because MaxReports has already been reached
                                                                                                                                                                                 No apport report written because MaxReports has already been reached
                                                No apport report written because MaxReports has already been reached
                                                                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                                                                        n3 is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-problem-report:
 python3-problem-report depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-problem-report (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-drivers-common:
 ubuntu-drivers-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ubuntu-drivers-common (--configure):
 dependency problems - leNo apport report written because MaxReports has already been reached
                                                                                             No apport report written because MaxReports has already been reached
                                                                                                                                                                 No apport report written because MaxReports has already been reached
                                aving unconfigured
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-uno depends on python3 (<< 3.7); however:
  Package python3 is not configured yet.
 python3-uno depends on python3 (>= 3.6~); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of software-properties-gtk:
 software-properties-gtk depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-gtk depends on python3; however:
  Package python3 is not configured yet.
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.75); however:
  Package ubuntu-drivers-common is not configured yet.

dpkg: error processing package software-properties-gtk (--configure):
 dependency problems - leaving unconfiguNo apport report written because MaxReports has already been reached
                                                                                                            red
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on update-notifier-common (= 3.192.1.4); however:
  Package update-notifier-common is not configured yet.

dpkg: error processing package update-notifier (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of unattended-upgrades:
 unattended-upgrades depends on python3; however:
  Package python3 is not configured yet.

dpkg: error processing package unattended-upgrades (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3; however:
  Package python3 is not configured yet.
 apport depends on python3-apport (>= 2.20.9-0ubuntu7.5); however:
  Package python3-apport is not configured yet.

dpkg: error processing package apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 update-manager depends on update-notifier; however:
  Package update-notifier is not configured yet.

dpkg: error processing package update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-gdbm:amd64:
 python3-gdbm:amd64 depends on python3 (>= 3.6.6-1~); however:
  Package python3 is not configured yet.
 python3-gdbm:amd64 depends on python3 (<< 3.8); however:
  Package python3 is not configured yet.

dpkg: error processing package python3-gdbm:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-software-properties:
 python3-software-properties depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-software-properties depends on python3; however:
  Package python3 is not configured yet.

dpkg: errorNo apport report written because MaxReports has already been reached
                                                                                processing package python3-software-properties (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 python3-distupgrade depends on python3-update-manager (>= 1:0.196.2~); however:
  Package python3-update-manager is not configured yet.

dpkg: error processing package python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of software-properties-common:
 software-properties-common depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.
 software-properties-common depends on python3; however:
  Package python3 is not configured yet.
 software-properties-common depends on python3-software-properties (= 0.96.24.32.6); however:
  Package python3-software-properties is not configured yet.

dpkg: error processing package software-properties-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent processing triggers for ufw:
 ufw depends on python3:any (>= 3.3.2-2~); however:
  Package python3 is not configured yet.

dpkg: error processing package ufw (--configure):
 dependency problems - leaving triggers unprocessed
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:18.04.29); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:18.04.29); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing package ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3:any (>= 3.2~); however:
  Package python3 is not configured yet.
 update-manager-core depends on python3-update-manager (= 1:18.04.11.8); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core (>= 1:18.04.9); however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing package update-manager-core (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of nvidia-prime:
 nvidia-prime depends on python3:any; however:
  Package python3 is not configured yet.

dpkg: error processing package nvidia-prime (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 python3
 update-notifier-common
 python3-update-manager
 apport-gtk
 ubuntu-release-upgrader-core
 python3-apport
 python3-problem-report
 ubuntu-drivers-common
 python3-uno
 software-properties-gtk
 update-notifier
 unattended-upgrades
 apport
 update-manager
 python3-gdbm:amd64
 python3-software-properties
 python3-distupgrade
 software-properties-common
 ufw
 ubuntu-release-upgrader-gtk
 update-manager-core
 nvidia-prime
E: Sub-process /usr/bin/dpkg returned an error code (1)
dad@dadubuntu:~$ 
```

---

### Post by &amp;KyT$0P# on 2019-01-03
@Quarkrad Your issue appears to be a problem installing python3.  Looks more related to [https://ubuntuforums.org/showthread.php?t=2409500](https://ubuntuforums.org/showthread.php?t=2409500) than this thread.  I don't know how to help with that issue, sorry.

---

### Post by deadflowr on 2019-01-03
> **halogen2 said:**
> @Quarkrad Your issue appears to be a problem installing python3.  Looks more related to [https://ubuntuforums.org/showthread.php?t=2409500](https://ubuntuforums.org/showthread.php?t=2409500) than this thread.  I don't know how to help with that issue, sorry.

It's an hplip problem going back a hop skip and a jump.
See 1fallen's post from a month ago:
[https://ubuntuforums.org/showthread.php?t=2406825&p=13819079#post13819079]("https://ubuntuforums.org/showthread.php?t=2406825&p=13819079#post13819079")

---

