---
title: "Update problems"
date: 2013-08-06
forum: General Help
---

### Post by Mazate on 2013-08-06
Ok, first off I'm using 13.04 , not whatever my signature says I have.  Yes, I need to update it.

I just did a manual install of adobe reader.  It works perfectly.  However, I was notified that there are updates.  I went to install the updates[ATTACH=CONFIG]245141[/ATTACH] and got this error.  I did the terminal command that it advised me to do but it still popped up again when I went to install.  Any help that anyone can provide would be most appreciated.

I also just noticed in the upper right corner where the icons are in unity, there is a red circle with a horizontal white line in the middle.  When I click on it it gives me this message:

An error occurred.  Please run package manager from the right click menu or apt-get in a terminal to see what is wrong.  The error message was:  'Error:brokencount>0.'  This usually means that your installed packages have unmet dependencies.

Hopefully that will help.  Ironically my update notification popped up right while I was installing acroread.

Also just noticed that adobe reader has unmet dependencies which may be the problem.  In retrospect, I did use -f on my install...

---

### Post by Bashing-om on 2013-08-06
Mazate; Hi !

I will start this ball rolling .. I am about done for the night ... but let's see what the packaage manager has to advise.
do in terminal:
```

sudo apt-get update

```
and post back to us the output of terminal command:
```

sudo apt-get upgrade

```

[INDENT]so a tale gets told[/INDENT]

---

### Post by Mazate on 2013-08-06
Can I start out by saying that its a pain to have to login every time I go to the forum to post?

Ok, #1:

```
david@david-desktop:~$ sudo apt-get update
[sudo] password for david: 
Hit http://springseed.s3.amazonaws.com stable Release.gpg
Hit http://us.archive.ubuntu.com raring Release.gpg                            
Hit http://springseed.s3.amazonaws.com stable Release                          
Get:1 http://security.ubuntu.com raring-security Release.gpg [933 B]           
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://us.archive.ubuntu.com raring-updates Release.gpg                    
Hit http://springseed.s3.amazonaws.com stable/main amd64 Packages              
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://deb.playonlinux.com precise Release.gpg                             
Hit http://springseed.s3.amazonaws.com stable/main i386 Packages               
Hit http://us.archive.ubuntu.com raring-backports Release.gpg                  
Get:2 http://security.ubuntu.com raring-security Release [40.8 kB]             
Hit http://archive.canonical.com precise Release                               
Hit http://us.archive.ubuntu.com raring Release                                
Hit http://extras.ubuntu.com raring Release                                    
Hit http://repository.spotify.com stable Release.gpg                           
Hit http://deb.playonlinux.com precise Release                                 
Hit http://us.archive.ubuntu.com raring-updates Release                        
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://download.opensuse.org  Release.gpg                                  
Hit http://deb.playonlinux.com precise/main amd64 Packages                     
Hit http://repository.spotify.com stable Release                               
Hit http://extras.ubuntu.com raring/main Sources                               
Hit http://us.archive.ubuntu.com raring-backports Release                      
Hit http://deb.playonlinux.com precise/main i386 Packages                      
Hit http://archive.canonical.com precise/partner i386 Packages                 
Hit http://repository.spotify.com stable/non-free amd64 Packages               
Hit http://us.archive.ubuntu.com raring/main Sources                           
Hit http://extras.ubuntu.com raring/main amd64 Packages                        
Hit http://us.archive.ubuntu.com raring/restricted Sources                     
Hit http://repository.spotify.com stable/non-free i386 Packages                
Hit http://extras.ubuntu.com raring/main i386 Packages                         
Hit http://us.archive.ubuntu.com raring/universe Sources                       
Hit http://download.opensuse.org  Release                                      
Hit http://us.archive.ubuntu.com raring/multiverse Sources                     
Ign http://springseed.s3.amazonaws.com stable/main Translation-en_US           
Hit http://us.archive.ubuntu.com raring/main amd64 Packages                    
Ign http://springseed.s3.amazonaws.com stable/main Translation-en              
Get:3 http://security.ubuntu.com raring-security/main Sources [36.2 kB]        
Hit http://us.archive.ubuntu.com raring/restricted amd64 Packages              
Hit http://us.archive.ubuntu.com raring/universe amd64 Packages                
Hit http://us.archive.ubuntu.com raring/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com raring/main i386 Packages                     
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages               
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                 
Get:4 http://security.ubuntu.com raring-security/restricted Sources [14 B]     
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages               
Get:5 http://security.ubuntu.com raring-security/universe Sources [8,408 B]    
Hit http://us.archive.ubuntu.com raring/main Translation-en                    
Hit http://download.opensuse.org  Packages                                     
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://deb.playonlinux.com precise/main Translation-en_US                  
Get:6 http://security.ubuntu.com raring-security/multiverse Sources [1,825 B]  
Ign http://repository.spotify.com stable/non-free Translation-en_US            
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en              
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://deb.playonlinux.com precise/main Translation-en                     
Get:7 http://security.ubuntu.com raring-security/main amd64 Packages [94.9 kB] 
Ign http://extras.ubuntu.com raring/main Translation-en_US                     
Ign http://repository.spotify.com stable/non-free Translation-en               
Hit http://us.archive.ubuntu.com raring/restricted Translation-en              
Ign http://extras.ubuntu.com raring/main Translation-en                        
Hit http://us.archive.ubuntu.com raring/universe Translation-en                
Hit http://us.archive.ubuntu.com raring-updates/main Sources                   
Hit http://us.archive.ubuntu.com raring-updates/restricted Sources             
Hit http://us.archive.ubuntu.com raring-updates/universe Sources               
Hit http://us.archive.ubuntu.com raring-updates/multiverse Sources             
Hit http://us.archive.ubuntu.com raring-updates/main amd64 Packages            
Get:8 http://security.ubuntu.com raring-security/restricted amd64 Packages [14 B]
Hit http://us.archive.ubuntu.com raring-updates/restricted amd64 Packages      
Get:9 http://security.ubuntu.com raring-security/universe amd64 Packages [31.7 kB]
Hit http://us.archive.ubuntu.com raring-updates/universe amd64 Packages        
Hit http://us.archive.ubuntu.com raring-updates/multiverse amd64 Packages      
Get:10 http://security.ubuntu.com raring-security/multiverse amd64 Packages [3,426 B]
Hit http://us.archive.ubuntu.com raring-updates/main i386 Packages             
Hit http://us.archive.ubuntu.com raring-updates/restricted i386 Packages       
Get:11 http://security.ubuntu.com raring-security/main i386 Packages [94.3 kB] 
Hit http://us.archive.ubuntu.com raring-updates/universe i386 Packages         
Hit http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en            
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en      
Get:12 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]
Hit http://repo.steampowered.com precise Release.gpg                           
Hit http://repo.steampowered.com precise Release                               
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en        
Get:13 http://security.ubuntu.com raring-security/universe i386 Packages [32.2 kB]
Hit http://repo.steampowered.com precise/steam Sources                         
Hit http://us.archive.ubuntu.com raring-backports/main Sources                 
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Hit http://us.archive.ubuntu.com raring-backports/restricted Sources           
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Hit http://us.archive.ubuntu.com raring-backports/universe Sources             
Hit http://us.archive.ubuntu.com raring-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com raring-backports/main amd64 Packages          
Get:14 http://security.ubuntu.com raring-security/multiverse i386 Packages [3,612 B]
Hit http://us.archive.ubuntu.com raring-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com raring-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com raring-backports/multiverse amd64 Packages    
Hit http://security.ubuntu.com raring-security/main Translation-en    
Hit http://us.archive.ubuntu.com raring-backports/main i386 Packages  
Hit https://private-ppa.launchpad.net oneiric Release.gpg             
Hit http://us.archive.ubuntu.com raring-backports/restricted i386 Packages
Ign http://repo.steampowered.com precise/steam Translation-en_US      
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages
Ign http://repo.steampowered.com precise/steam Translation-en         
Hit https://private-ppa.launchpad.net raring Release.gpg              
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages
Hit https://private-ppa.launchpad.net oneiric Release                          
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en          
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Hit https://private-ppa.launchpad.net raring Release                           
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en    
Hit https://private-ppa.launchpad.net oneiric/main amd64 Packages              
Ign http://download.opensuse.org  Translation-en_US                            
Hit http://security.ubuntu.com raring-security/restricted Translation-en       
Hit https://private-ppa.launchpad.net oneiric/main i386 Packages               
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en    
Ign http://download.opensuse.org  Translation-en                      
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en      
Hit http://security.ubuntu.com raring-security/universe Translation-en         
Hit https://private-ppa.launchpad.net raring/main amd64 Packages               
Hit https://private-ppa.launchpad.net raring/main i386 Packages                
Ign http://security.ubuntu.com raring-security/main Translation-en_US          
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US    
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US    
Ign http://security.ubuntu.com raring-security/universe Translation-en_US      
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                 
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US             
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US
Ign https://private-ppa.launchpad.net oneiric/main Translation-en_US
Ign https://private-ppa.launchpad.net oneiric/main Translation-en
Ign https://private-ppa.launchpad.net raring/main Translation-en_US
Ign https://private-ppa.launchpad.net raring/main Translation-en
Fetched 348 kB in 23s (14.8 kB/s)
Reading package lists... Done
```

Here's output for #2

```
david@david-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 acroread : Depends: acroread-bin
E: Unmet dependencies. Try using -f.
```

---

### Post by QIII on 2013-08-06
> **Mazate said:**
> Can I start out by saying that its a pain to have to login every time I go to the forum to post?


Yes, you may -- so long as you take care to follow the forum CoC.  ;)

This is a function of the Ubuntu One login now being used.  This has been brought to the attention of Canonical IS.  It is not something for forum Staff has control over at this point.

---

### Post by Mazate on 2013-08-06
I wasn't looking for a solution per se.  I was merely venting.

---

### Post by Bashing-om on 2013-08-07
Mazate; Hey...

Try this: maybe.
```

sudo apt-get install --reinstall acroread

```

[INDENT][INDENT]simple things first
[/INDENT][/INDENT]

---

### Post by Mazate on 2013-08-07
Here's what I got:

```
david@david-desktop:~$ sudo apt-get install --reinstall acroread
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 acroread : Depends: acroread-bin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by Bashing-om on 2013-08-07
Mazate; Hey...

Did not mean to leave ya ... I presently do not know why that dependency still exist.. I have been look'n and think'n...
Like maybe acroread is still a 32 bit application ... on a 64 bit machine ,,, and some library is not available ...
How to see what is not going on ???
[INDENT][INDENT]I will be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-07
Mazate; Hi !

Not making much headway on this... I do not have multi-arch enabled on my system, so not able to do much looking/testing.
What methods have you employed to try and install "acroread" ... maybe we ought to consider removing the ap and trying to (re)install ??
If the only method to install is via the repository; 
Then:

Do you have the required libraries installed ?
```

dpkg -l ia32-libs-multiarch

```
If "ia32-libs-multiarch" is installed (ii shows so) ... then what results from a simulation of installing "acroread-bin"
```

sudo apt-get install -s acroread-bin

```

look'n for a cause

---

### Post by Mazate on 2013-08-07
I'll try this when I get home.  I'm at work at the moment.

If this helps, I at first tried to follow some instructions that I found on the internet to install acroread.  It wasn't working correctly and I saw other instructions that had me try the -f addon.  I think that's what screwed me up.  Anyway, that didn't do it either.  After that, I found out how to turn on the correct Ubuntu repo and then installed it without issue.  It works fine but obviously is giving me issues with updates.  I'll try these when I get home.  Hopefully we can get this resolved because the thought of having to reinstall Ubuntu along with everything else just makes my eyes bleed.

---

### Post by Bashing-om on 2013-08-07
Mazate; Hey ...
Know where you are coming from in respect to an aversion to (re-)install . I have heavily customized this install. I am real fond of what I have accomplished thus far. But there are a few things now I know to do different than what I did on that initial install ... All my faults are small and niggly, none affect performance... however, I still consider (re-)installing and see if that corrects the difficulties. (... but then again, I am learning lots about differing processes in the OS in troubleshooting these little things)

In respect to acroread, yeah .. that would cause some problems... let's by all means ->... purge all we can find and start all over from scratch ... see what results...
All I have seen lately in regards to acroread in the repository .. all issues supposedly resolved .. should install slick as a whistle.

[INDENT][INDENT]ubuntu, workie great supposed to last long time[/INDENT][/INDENT]

---

### Post by Mazate on 2013-08-07
Ok, here's the first one:

```
david@david-desktop:~$ dpkg -l ia32-libs-multiarch
dpkg-query: no packages found matching ia32-libs-multiarch
```

And here's the 2nd one:

```
david@david-desktop:~$ sudo apt-get install -s acroread-bin
[sudo] password for david: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libldap2:i386 libgnome-speech7:i386
The following NEW packages will be installed:
  acroread-bin:i386
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
4 not fully installed or removed.
Inst acroread-bin:i386 (9.5.5-1precise1 Partner archive:12.04/precise [i386])
Conf libidn11:i386 (1.25-2 Ubuntu:13.04/raring [i386])
Conf nspluginviewer:i386 (1.4.4-0ubuntu5 Ubuntu:13.04/raring [i386])
Conf acroread-bin:i386 (9.5.5-1precise1 Partner archive:12.04/precise [i386])
Conf nspluginwrapper (1.4.4-0ubuntu5 Ubuntu:13.04/raring [amd64])
Conf acroread (9.5.5-1precise1 Partner archive:12.04/precise [amd64])
```

Unfortunately, that didn't do anything one way or the other so far as I can tell.

---

### Post by Bashing-om on 2013-08-07
Mazate; Hey.

Here is what it looks like to me:
1.) acroread is a 32 bit application, are you attempting to install on a 64 bit machine without the 32 bit libraries ?
lets look at what you are running:
```

uname -a

```
2.) There is a mixed install attempt of acroread between versions precise and raring ... as advised /// let's see if we can remove/purge what is installed ... 
what does terminal codes:
```

ls -la /etc/apt/sources.list.d/
ls -la /opt/
##do you have this file ?
ls -la /opt/Adobe/bin/UNINSTALL

```

Tell us In the quest to find out what it is going to take to remove all existence of acroread prior to proceeding.

[INDENT][INDENT]that's the way, dancing with your computer[/INDENT][/INDENT]

---

### Post by Mazate on 2013-08-07
#1

```
david@david-desktop:~$ uname -a
Linux david-desktop 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

#2


```
david@david-desktop:~$ ls -la /etc/apt/sources.list.d/
total 56
drwxr-xr-x 2 root root 4096 Aug  6 19:03 .
drwxr-xr-x 6 root root 4096 Aug  6 19:03 ..
-rw-r--r-- 1 root root   82 Aug  6 19:03 owncloud-client.list
-rw-r--r-- 1 root root   82 Aug  6 19:03 owncloud-client.list.save
-rw-r--r-- 1 root root   45 Aug  6 19:03 playonlinux.list
-rw-r--r-- 1 root root   45 Aug  6 19:03 playonlinux.list.save
-rw-r--r-- 1 root root  167 Aug  6 19:03 private-ppa.launchpad.net_commercial-ppa-uploaders_fluendo-plugins_ubuntu.list
-rw-r--r-- 1 root root  167 Aug  6 19:03 private-ppa.launchpad.net_commercial-ppa-uploaders_fluendo-plugins_ubuntu.list.save
-rw-r--r-- 1 root root  156 Aug  6 19:03 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list
-rw-r--r-- 1 root root  156 Aug  6 19:03 private-ppa.launchpad.net_commercial-ppa-uploaders_steam_ubuntu.list.save
-rw-r--r-- 1 root root  116 Aug  6 19:03 springseed.list
-rw-r--r-- 1 root root  116 Aug  6 19:03 springseed.list.save
-rw-r--r-- 1 root root  112 Aug  6 19:03 steam.list
-rw-r--r-- 1 root root  112 Aug  6 19:03 steam.list.save
david@david-desktop:~$ ls -la /opt/
total 20
drwxr-xr-x  5 root  root   4096 Aug  6 19:00 .
drwxr-xr-x 25 root  root   4096 Aug  3 11:02 ..
drwxr-xr-x  3 10490 floppy 4096 Aug  6 19:00 Adobe
drwxr-xr-x  3 root  root   4096 Aug  4 20:26 spotify
drwxr-xr-x  2 root  root   4096 Aug  4 13:31 springseed
david@david-desktop:~$ ls -la /opt/Adobe/bin/UNINSTALL
ls: cannot access /opt/Adobe/bin/UNINSTALL: No such file or directory
```

---

### Post by Bashing-om on 2013-08-07
Mazate; welp ...

I am considering .. and considering ...
I am under the understanding that acroread is a 32 bit application still;

I was thinking that multiarch was installed by default on later versions of ubuntu desktop systems... you are 64 bit and those libraries are not installed??)
Maybe I am falling behind with the times ? Has multiarch finally been migrated ??? ..The last time I messed with multiarch was version 10.04 ...
confirm:
```

dpkg --print-foreign-architectures
sudo apt-cache policy ia32-libs

```
 we can fix that by installing them if required.. no great big deal.

I was hoping there was an UNINSTALL script to remove the initial acroread install .. no such luck ... then looked for a PPA that might have been employed ... nope ... // so ...put on your thinking cap and see if you recall where/how you did that first install attempt; for guidance on how to remove that attempted install //otherwise slashing at files can be hazardous to the computers health.
To that end also ... let's see what is contained in the Adobe directory.
```

ls -la /opt/Adobe/

```
How about some files from an earlier install that might shed a bit of light on "uninstall"
```

sudo find / -name "adobereader-enu*"

```

Gonna go look and see what version 12.04 (standard install) looks like !

[INDENT]clean up, set up, install !
[/INDENT]

---

### Post by Mazate on 2013-08-07
Does this shed any light on the matter?

```
root@david-desktop:/home/david# dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 acroread             Adobe Reader
```

One is from the distro and the other is the one I tried (and failed) to manually install.  That of course is a huge assumption on my part.

---

### Post by Mazate on 2013-08-07
dpkg -P acroread  <---- This fixed it.  It works great now.  Thank you for helping me troubleshoot.  I very much appreciate it.

---

### Post by Bashing-om on 2013-08-07
Mazate; Hey !

I am relieved as well as glad ya got it working ...
That indeed leaves me in a state of finding out the current disposition of multiarch (32 bit libraries on 64 bit architectures) ..
also still suggest we find a way to purge that bad install... no need to leave orphan packages around to foul up the works later.

This sure had me thinking .. and that puts a smile on my face.

---

### Post by juanchorobles on 2013-10-09
I have the same problem but I never try to install adobe, I dont have any idea how to solve this problem, and the software center dont let me install new software, when i try said "new software cant be installed because theres a problem with currently installed, do you want to repair this sofrware now?" when i try it the software center gime me the same advise, please help

---

### Post by Bashing-om on 2013-10-09
juanchorobles; Hi ! Welcome to the forum.

The terminal will yield more prolific messages; aiding us in isolating the fault.
Please post the outputs of terminal commands:
```

software-center
##Then close the Software Center out, and do:
sudo apt-get update
sudo apt-get upgrade 

```
Place the outputs between code tags, per this tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We will see what is to be done.

[INDENT][INDENT]so a tale is told
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
**```
**
juancho@juancho-Satellite-C845:~$ software-center

** (software-center:23645): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-WMMbFIzFdp: Connection refused
2013-10-09 12:52:45,712 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-10-09 12:52:46,527 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-10-09 12:52:46,529 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-10-09 12:52:46,536 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-10-09 12:52:46,535 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-10-09 12:52:46,688 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-10-09 12:52:52,166 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/utils.py', 271, 'get_title_from_html')'
2013-10-09 12:52:52,166 - root - WARNING - failed to parse: '<div style="background-color: #161513; width:1680px; height:200px;">
 <div style="background: url('/site_media/exhibits/2013/09/AAMFP_Leaderboard_700x200_1.jpg') top left no-repeat; width:700px; height:200px;"></div>
</div>' ('ascii' codec can't encode character u'\xa0' in position 70: ordinal not in range(128))
2013-10-09 12:53:09,803 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-10-09 12:53:14,960 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-10-09 12:53:22,762 - softwarecenter.backend - ERROR - error in _on_trans_finished 'Error: Package operation failed
The installation or removal of a software package failed.

(Reading database ... 470947 files and directories currently installed.)
Unpacking linux-image-3.8.0-32-generic (from .../linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-32-generic' to '/boot/vmlinuz-3.8.0-32-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Unpacking linux-image-3.8.0-31-generic (from .../linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-31-generic' to '/boot/vmlinuz-3.8.0-31-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb
 /var/cache/apt/archives/linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-31-generic:
 linux-image-extra-3.8.0-31-generic depends on linux-image-3.8.0-31-generic; however:
  Package linux-image-3.8.0-31-generic is not installed.

dpkg: error processing linux-image-extra-3.8.0-31-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.8.0-32-generic:
 linux-image-extra-3.8.0-32-generic depends on linux-image-3.8.0-32-generic; however:
  Package linux-image-3.8.0-32-generic is not installed.

dpkg: error processing linux-image-extra-3.8.0-32-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-3.8.0-30-generic (3.8.0-30.44) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-30-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-30-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.8.0-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.8.0-32-generic; however:
  Package linux-image-3.8.0-32-generic is not installed.
 linux-image-generic depends on linux-image-extra-3.8.0-32-generic; however:
  Package linux-image-extra-3.8.0-32-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.8.0.32.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
'
2013-10-09 12:53:45,355 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

```

```

juancho@juancho-Satellite-C845:~$ sudo apt-get update
[sudo] password for juancho: 
Hit http://archive.ubuntu.com raring Release.gpg
Get:1 http://archive.ubuntu.com raring-updates Release.gpg [933 B]             
Hit http://www.geogebra.net stable Release.gpg                                 
Hit http://archive.canonical.com raring Release.gpg
Hit http://archive.ubuntu.com raring-backports Release.gpg
Get:2 http://archive.ubuntu.com raring-security Release.gpg [933 B]
Hit http://www.geogebra.net stable Release                                     
Hit http://archive.canonical.com raring Release 
Get:3 http://archive.ubuntu.com raring-proposed Release.gpg [933 B]    
Hit http://archive.ubuntu.com raring Release                                   
Hit http://www.geogebra.net stable/main i386 Packages                          
Hit http://archive.canonical.com raring/partner Sources              
Get:4 http://archive.ubuntu.com raring-updates Release [40,8 kB]
Hit http://archive.canonical.com raring/partner i386 Packages                
Hit http://archive.ubuntu.com raring-backports Release                         
Get:5 http://archive.ubuntu.com raring-security Release [40,8 kB]              
Get:6 http://archive.ubuntu.com raring-proposed Release [40,8 kB]              
Hit http://archive.ubuntu.com raring/main Sources                              
Hit http://archive.ubuntu.com raring/restricted Sources               
Hit http://archive.ubuntu.com raring/universe Sources
Ign http://www.geogebra.net stable/main Translation-en_US
Hit http://archive.ubuntu.com raring/multiverse Sources
Hit http://archive.ubuntu.com raring/main i386 Packages
Ign http://www.geogebra.net stable/main Translation-en                
Ign http://archive.canonical.com raring/partner Translation-en_US     
Hit http://archive.ubuntu.com raring/restricted i386 Packages
Hit http://archive.ubuntu.com raring/universe i386 Packages
Ign http://archive.canonical.com raring/partner Translation-en
Hit http://archive.ubuntu.com raring/multiverse i386 Packages
Hit http://archive.ubuntu.com raring/main Translation-en
Hit http://archive.ubuntu.com raring/multiverse Translation-en
Hit http://archive.ubuntu.com raring/restricted Translation-en
Hit http://archive.ubuntu.com raring/universe Translation-en                   
Get:7 http://archive.ubuntu.com raring-updates/main Sources [74,4 kB]          
Get:8 http://archive.ubuntu.com raring-updates/restricted Sources [14 B]       
Get:9 http://archive.ubuntu.com raring-updates/universe Sources [72,8 kB]      
Get:10 http://archive.ubuntu.com raring-updates/multiverse Sources [2 266 B]   
Get:11 http://archive.ubuntu.com raring-updates/main i386 Packages [188 kB]    
Get:12 http://archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]
Get:13 http://archive.ubuntu.com raring-updates/universe i386 Packages [150 kB]
Get:14 http://archive.ubuntu.com raring-updates/multiverse i386 Packages [3 864 B]
Hit http://archive.ubuntu.com raring-updates/main Translation-en               
Hit http://archive.ubuntu.com raring-updates/multiverse Translation-en         
Hit http://archive.ubuntu.com raring-updates/restricted Translation-en         
Hit http://archive.ubuntu.com raring-updates/universe Translation-en           
Hit http://archive.ubuntu.com raring-backports/main Sources                    
Hit http://archive.ubuntu.com raring-backports/restricted Sources              
Hit http://archive.ubuntu.com raring-backports/universe Sources                
Hit http://archive.ubuntu.com raring-backports/multiverse Sources              
Hit http://archive.ubuntu.com raring-backports/main i386 Packages              
Hit http://archive.ubuntu.com raring-backports/restricted i386 Packages        
Hit http://archive.ubuntu.com raring-backports/universe i386 Packages          
Hit http://archive.ubuntu.com raring-backports/multiverse i386 Packages        
Hit http://archive.ubuntu.com raring-backports/main Translation-en             
Hit http://archive.ubuntu.com raring-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com raring-backports/restricted Translation-en       
Hit http://archive.ubuntu.com raring-backports/universe Translation-en         
Get:15 http://archive.ubuntu.com raring-security/main Sources [46,6 kB]        
Get:16 http://archive.ubuntu.com raring-security/restricted Sources [14 B]     
Get:17 http://archive.ubuntu.com raring-security/universe Sources [9 271 B]    
Get:18 http://archive.ubuntu.com raring-security/multiverse Sources [2 266 B]  
Get:19 http://archive.ubuntu.com raring-security/main i386 Packages [120 kB]   
Get:20 http://archive.ubuntu.com raring-security/restricted i386 Packages [14 B]
Get:21 http://archive.ubuntu.com raring-security/universe i386 Packages [39,0 kB]
Get:22 http://archive.ubuntu.com raring-security/multiverse i386 Packages [3 864 B]
Hit http://archive.ubuntu.com raring-security/main Translation-en              
Hit http://archive.ubuntu.com raring-security/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-security/restricted Translation-en        
Hit http://archive.ubuntu.com raring-security/universe Translation-en          
Get:23 http://archive.ubuntu.com raring-proposed/main i386 Packages [56,6 kB]  
Get:24 http://archive.ubuntu.com raring-proposed/restricted i386 Packages [14 B]
Get:25 http://archive.ubuntu.com raring-proposed/multiverse i386 Packages [14 B]
Get:26 http://archive.ubuntu.com raring-proposed/universe i386 Packages [39,3 kB]
Hit http://archive.ubuntu.com raring-proposed/main Translation-en              
Hit http://archive.ubuntu.com raring-proposed/multiverse Translation-en        
Hit http://archive.ubuntu.com raring-proposed/restricted Translation-en        
Hit http://archive.ubuntu.com raring-proposed/universe Translation-en          
Ign http://archive.ubuntu.com raring/main Translation-en_US                    
Ign http://archive.ubuntu.com raring/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring/restricted Translation-en_US
Ign http://archive.ubuntu.com raring/universe Translation-en_US
Ign http://archive.ubuntu.com raring-updates/main Translation-en_US
Ign http://archive.ubuntu.com raring-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-updates/universe Translation-en_US
Ign http://archive.ubuntu.com raring-backports/main Translation-en_US
Ign http://archive.ubuntu.com raring-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-backports/universe Translation-en_US
Ign http://archive.ubuntu.com raring-security/main Translation-en_US
Ign http://archive.ubuntu.com raring-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-security/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-security/universe Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/main Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com raring-proposed/universe Translation-en_US
Fetched 934 kB in 43s (21,3 kB/s)
Reading package lists... Done

```

```

juancho@juancho-Satellite-C845:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not installed
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles; Hey ;

Try;
```

sudo apt-get dist-upgrade

``` seeing if this approach to updating will install the needed kernels.

[INDENT][INDENT]only a maybe/perhaps
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ sudo apt-get dist-upgrade
[sudo] password for juancho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not installed
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb linux-headers-3.8.0-19 linux-headers-3.8.0-19-generic
  linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.8.0-31-generic linux-image-3.8.0-32-generic
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.8.0-31-generic linux-image-3.8.0-32-generic
0 upgraded, 2 newly installed, 0 to remove and 103 not upgraded.
5 not fully installed or removed.
Need to get 0 B/24,8 MB of archives.
After this operation, 54,9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 470947 files and directories currently installed.)
Unpacking linux-image-3.8.0-32-generic (from .../linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-32-generic' to '/boot/vmlinuz-3.8.0-32-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Unpacking linux-image-3.8.0-31-generic (from .../linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-31-generic' to '/boot/vmlinuz-3.8.0-31-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb
 /var/cache/apt/archives/linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
juancho@juancho-Satellite-C845:~$ 

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles; Well, well ..
This do tell the tale!
> 
cannot copy extracted data for './boot/vmlinuz-3.8.0-31-generic' to '/boot/vmlinuz-3.8.0-31-generic.dpkg-new': failed to write (No space left on device)

Let's see what is taking up all the disk space - as if we did not know .. just checking.
```

df -h
df -i
du -h --max-depth=1 | sort -hr
##and because I suspect strongly it is the /boot partition that is going to be full:
uname -r
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-
ls -la /boot

```
Then we go to work and see about removing those old unwanted kernels. I prefer to do so from terminal, though from synaptic is equally effective.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  457G   95G  339G  22% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         940M  4,0K  940M   1% /dev
tmpfs                        190M  860K  189M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         949M  548K  948M   1% /run/shm
none                         100M   16K  100M   1% /run/user
/dev/sda1                    228M  225M     0 100% /boot
juancho@juancho-Satellite-C845:~$ df -i
Filesystem                    Inodes  IUsed    IFree IUse% Mounted on
/dev/mapper/ubuntu--vg-root 30384128 538700 29845428    2% /
none                          214448      1   214447    1% /sys/fs/cgroup
udev                          210174    517   209657    1% /dev
tmpfs                         214448    493   213955    1% /run
none                          214448      4   214444    1% /run/lock
none                          214448     11   214437    1% /run/shm
none                          214448     16   214432    1% /run/user
/dev/sda1                     124496    302   124194    1% /boot
juancho@juancho-Satellite-C845:~$ du -h --max-depth=1 | sort -hr
87G    .
43G    ./Desktop
24G    ./Videos
13G    ./Music
5,9G    ./Downloads
1,6G    ./Pictures
623M    ./Documents
422M    ./.cache
314M    ./.thunderbird
212M    ./.local
106M    ./tor-browser_en-US
89M    ./.mozilla
88M    ./otros programas
38M    ./.config
4,5M    ./.kde
3,7M    ./.adobe
2,2M    ./.tor
2,0M    ./.Skype
884K    ./.gstreamer-0.10
748K    ./.compiz
424K    ./.stellarium
104K    ./.gconf
84K    ./.java
56K    ./.icons
52K    ./.macromedia
28K    ./.filezilla
24K    ./.gtkboard
24K    ./etc
16K    ./.dbus
12K    ./.gnome2
8,0K    ./.vidalia
8,0K    ./.dreamchess
4,0K    ./Ubuntu One
4,0K    ./Templates
4,0K    ./Public
4,0K    ./.kajonggserver

```

```

juancho@juancho-Satellite-C845:~$ uname -r
3.8.0-30-generic
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-image-
ii  linux-image-3.8.0-19-generic              3.8.0-19.30                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-21-generic              3.8.0-21.32                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-22-generic              3.8.0-22.33                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-23-generic              3.8.0-23.34                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-25-generic              3.8.0-25.37                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-26-generic              3.8.0-26.38                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-27-generic              3.8.0-27.40                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-29-generic              3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-19-generic        3.8.0-19.30                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-21-generic        3.8.0-21.32                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-22-generic        3.8.0-22.33                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-23-generic        3.8.0-23.34                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-25-generic        3.8.0-25.37                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-26-generic        3.8.0-26.38                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-27-generic        3.8.0-27.40                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-29-generic        3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iF  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-32-generic        3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.32.50                            i386         Generic Linux kernel image
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-19                    3.8.0-19.30                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-19-generic            3.8.0-19.30                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-21                    3.8.0-21.32                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-21-generic            3.8.0-21.32                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-22                    3.8.0-22.33                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-22-generic            3.8.0-22.33                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-23                    3.8.0-23.34                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-23-generic            3.8.0-23.34                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-25                    3.8.0-25.37                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-25-generic            3.8.0-25.37                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-26                    3.8.0-26.38                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-26-generic            3.8.0-26.38                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-27                    3.8.0-27.40                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-27-generic            3.8.0-27.40                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-29                    3.8.0-29.42                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29-generic            3.8.0-29.42                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                    3.8.0-32.47                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic            3.8.0-32.47                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.32.50                            i386         Generic Linux kernel headers
juancho@juancho-Satellite-C845:~$ ls -la /boot
total 225948
drwxr-xr-x  4 root root     2048 oct  9 15:17 .
drwxr-xr-x 23 root root     4096 oct  9 12:53 ..
-rw-r--r--  1 root root   925685 may  1 11:12 abi-3.8.0-19-generic
-rw-r--r--  1 root root   925685 may 14 16:53 abi-3.8.0-21-generic
-rw-r--r--  1 root root   925807 may 16 09:54 abi-3.8.0-22-generic
-rw-r--r--  1 root root   925807 may 29 14:56 abi-3.8.0-23-generic
-rw-r--r--  1 root root   925769 jun  6 15:19 abi-3.8.0-25-generic
-rw-r--r--  1 root root   925769 jun 17 16:19 abi-3.8.0-26-generic
-rw-r--r--  1 root root   926261 jul  8 18:51 abi-3.8.0-27-generic
-rw-r--r--  1 root root   926372 ago 13 17:44 abi-3.8.0-29-generic
-rw-r--r--  1 root root   926429 ago 22 15:26 abi-3.8.0-30-generic
-rw-r--r--  1 root root   160890 may  1 11:12 config-3.8.0-19-generic
-rw-r--r--  1 root root   160890 may 14 16:53 config-3.8.0-21-generic
-rw-r--r--  1 root root   160891 may 16 09:54 config-3.8.0-22-generic
-rw-r--r--  1 root root   160891 may 29 14:56 config-3.8.0-23-generic
-rw-r--r--  1 root root   160891 jun  6 15:19 config-3.8.0-25-generic
-rw-r--r--  1 root root   160893 jun 17 16:19 config-3.8.0-26-generic
-rw-r--r--  1 root root   160908 jul  8 18:51 config-3.8.0-27-generic
-rw-r--r--  1 root root   160908 ago 13 17:44 config-3.8.0-29-generic
-rw-r--r--  1 root root   160908 ago 22 15:26 config-3.8.0-30-generic
drwxr-xr-x  5 root root     1024 sep 15 21:42 grub
-rw-r--r--  1 root root 16632524 may 10 18:23 initrd.img-3.8.0-19-generic
-rw-r--r--  1 root root 16632499 may 20 17:50 initrd.img-3.8.0-21-generic
-rw-r--r--  1 root root 16632311 may 26 12:16 initrd.img-3.8.0-22-generic
-rw-r--r--  1 root root 16632219 jun  5 06:57 initrd.img-3.8.0-23-generic
-rw-r--r--  1 root root 16634445 jun 18 17:31 initrd.img-3.8.0-25-generic
-rw-r--r--  1 root root 16634814 jul  7 16:35 initrd.img-3.8.0-26-generic
-rw-r--r--  1 root root 16699888 ago 15 21:17 initrd.img-3.8.0-27-generic
-rw-r--r--  1 root root 16699862 ago 27 08:41 initrd.img-3.8.0-29-generic
-rw-r--r--  1 root root 16695836 sep 15 21:42 initrd.img-3.8.0-30-generic
drwxr-xr-x  2 root root    12288 may 10 17:07 lost+found
-rw-r--r--  1 root root   176764 dic  5  2012 memtest86+.bin
-rw-r--r--  1 root root   178944 dic  5  2012 memtest86+_multiboot.bin
-rw-------  1 root root  2443743 may  1 11:12 System.map-3.8.0-19-generic
-rw-------  1 root root  2443743 may 14 16:53 System.map-3.8.0-21-generic
-rw-------  1 root root  2444032 may 16 09:54 System.map-3.8.0-22-generic
-rw-------  1 root root  2444032 may 29 14:56 System.map-3.8.0-23-generic
-rw-------  1 root root  2444283 jun  6 15:19 System.map-3.8.0-25-generic
-rw-------  1 root root  2444419 jun 17 16:19 System.map-3.8.0-26-generic
-rw-------  1 root root  2444894 jul  8 18:51 System.map-3.8.0-27-generic
-rw-------  1 root root  2445641 ago 13 17:44 System.map-3.8.0-29-generic
-rw-------  1 root root  2445814 ago 22 15:26 System.map-3.8.0-30-generic
-rw-------  1 root root  5368560 may  1 11:12 vmlinuz-3.8.0-19-generic
-rw-------  1 root root  5368560 may 14 16:53 vmlinuz-3.8.0-21-generic
-rw-------  1 root root  5368656 may 16 09:54 vmlinuz-3.8.0-22-generic
-rw-------  1 root root  5368656 may 29 14:56 vmlinuz-3.8.0-23-generic
-rw-------  1 root root  5370096 jun  6 15:19 vmlinuz-3.8.0-25-generic
-rw-------  1 root root  5369008 jun 17 16:19 vmlinuz-3.8.0-26-generic
-rw-------  1 root root  5372784 jul  8 18:51 vmlinuz-3.8.0-27-generic
-rw-------  1 root root  5373360 ago 13 17:44 vmlinuz-3.8.0-29-generic
-rw-------  1 root root  5373488 ago 22 15:26 vmlinuz-3.8.0-30-generic

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles[ Yuk, I was concerned that this would be the result.
Do you see the problem ? The /boot partition is 100% ! Means there is no overhead to operate in. Let's TRY this, hoping we do not have to resort to manually removing the kernels and all those config files,
```

sudo dpkg -P linux-image-3.8.0-{19,21,22,23,25,26,27,29}-generic
sudo dpkg -P linux-headers-3.8.0-{19,21,22,23,25,26,27,29}-generic

```
From the output of "uname -r" we know you are booting with "3.8.0-30-generic" kernel. Make sure you DO NOT remove it or it's headers file.

If those two commands run successfully, Halt ! Do nothing else until I see an updated dpkg ! Else there can be a real mess for sure on our hands.
If they run show me:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
And we can continue the cleanup process.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
i think the first one didnt work
```

uancho@juancho-Satellite-C845:~$ sudo dpkg -P linux-image-3.8.0-{19,21,22,23,25,26,27,29}-generic
[sudo] password for juancho: 
dpkg: dependency problems prevent removal of linux-image-3.8.0-19-generic:
 linux-image-extra-3.8.0-19-generic depends on linux-image-3.8.0-19-generic.

dpkg: error processing linux-image-3.8.0-19-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-21-generic:
 linux-image-extra-3.8.0-21-generic depends on linux-image-3.8.0-21-generic.

dpkg: error processing linux-image-3.8.0-21-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-22-generic:
 linux-image-extra-3.8.0-22-generic depends on linux-image-3.8.0-22-generic.

dpkg: error processing linux-image-3.8.0-22-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-23-generic:
 linux-image-extra-3.8.0-23-generic depends on linux-image-3.8.0-23-generic.

dpkg: error processing linux-image-3.8.0-23-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-25-generic:
 linux-image-extra-3.8.0-25-generic depends on linux-image-3.8.0-25-generic.

dpkg: error processing linux-image-3.8.0-25-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-26-generic:
 linux-image-extra-3.8.0-26-generic depends on linux-image-3.8.0-26-generic.

dpkg: error processing linux-image-3.8.0-26-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-27-generic:
 linux-image-extra-3.8.0-27-generic depends on linux-image-3.8.0-27-generic.

dpkg: error processing linux-image-3.8.0-27-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.8.0-29-generic:
 linux-image-extra-3.8.0-29-generic depends on linux-image-3.8.0-29-generic.

dpkg: error processing linux-image-3.8.0-29-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.8.0-19-generic
 linux-image-3.8.0-21-generic
 linux-image-3.8.0-22-generic
 linux-image-3.8.0-23-generic
 linux-image-3.8.0-25-generic
 linux-image-3.8.0-26-generic
 linux-image-3.8.0-27-generic
 linux-image-3.8.0-29-generic
juancho@juancho-Satellite-C845:~$ sudo dpkg -P linux-headers-3.8.0-{19,21,22,23,25,26,27,29}-generic
(Reading database ... 470946 files and directories currently installed.)
Removing linux-headers-3.8.0-19-generic ...
Removing linux-headers-3.8.0-21-generic ...
Removing linux-headers-3.8.0-22-generic ...
Removing linux-headers-3.8.0-23-generic ...
Removing linux-headers-3.8.0-25-generic ...
Removing linux-headers-3.8.0-26-generic ...
Removing linux-headers-3.8.0-27-generic ...
Removing linux-headers-3.8.0-29-generic ...

```

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-image-
pi  linux-image-3.8.0-19-generic              3.8.0-19.30                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-21-generic              3.8.0-21.32                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-22-generic              3.8.0-22.33                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-23-generic              3.8.0-23.34                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-25-generic              3.8.0-25.37                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-26-generic              3.8.0-26.38                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-27-generic              3.8.0-27.40                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-29-generic              3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-19-generic        3.8.0-19.30                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-21-generic        3.8.0-21.32                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-22-generic        3.8.0-22.33                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-23-generic        3.8.0-23.34                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-25-generic        3.8.0-25.37                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-26-generic        3.8.0-26.38                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-27-generic        3.8.0-27.40                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-29-generic        3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iF  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-32-generic        3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.32.50                            i386         Generic Linux kernel image
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-19                    3.8.0-19.30                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-21                    3.8.0-21.32                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-22                    3.8.0-22.33                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-23                    3.8.0-23.34                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-25                    3.8.0-25.37                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-26                    3.8.0-26.38                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-27                    3.8.0-27.40                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29                    3.8.0-29.42                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                    3.8.0-32.47                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic            3.8.0-32.47                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.32.50                            i386         Generic Linux kernel headers

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles; Most not good !

Ok, one more try: do:
```

sudo dpkg -P linux-image-extra-3.8.0-{19,21,22,23,25,26,27,29}-generic

```
See if we can finish "purging" those image files.

and in preparation if we have to do this manually; show me:
```

ls -la /usr/src/

```

[INDENT][INDENT]this could get hairy [/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ sudo dpkg -P linux-image-extra-3.8.0-{19,21,22,23,25,26,27,29}-generic
[sudo] password for juancho: 
(Reading database ... 397996 files and directories currently installed.)
Removing linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found initrd image: /boot/initrd.img-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Removing linux-image-extra-3.8.0-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found initrd image: /boot/initrd.img-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
Removing linux-image-extra-3.8.0-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found initrd image: /boot/initrd.img-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
Removing linux-image-extra-3.8.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found initrd image: /boot/initrd.img-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
Removing linux-image-extra-3.8.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found initrd image: /boot/initrd.img-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
Removing linux-image-extra-3.8.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found initrd image: /boot/initrd.img-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
Removing linux-image-extra-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Removing linux-image-extra-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic

```

```

juancho@juancho-Satellite-C845:~$ ls -la /usr/src/
total 64
drwxr-xr-x 16 root root 4096 oct  9 19:33 .
drwxr-xr-x 10 root root 4096 abr 24 11:02 ..
drwxr-xr-x 24 root root 4096 may 10 18:21 linux-headers-3.8.0-19
drwxr-xr-x 24 root root 4096 may 20 17:48 linux-headers-3.8.0-21
drwxr-xr-x 24 root root 4096 may 26 12:15 linux-headers-3.8.0-22
drwxr-xr-x 24 root root 4096 jun  5 06:55 linux-headers-3.8.0-23
drwxr-xr-x 24 root root 4096 jun 18 17:30 linux-headers-3.8.0-25
drwxr-xr-x 24 root root 4096 jul  7 16:33 linux-headers-3.8.0-26
drwxr-xr-x 24 root root 4096 ago  2 10:36 linux-headers-3.8.0-27
drwxr-xr-x 24 root root 4096 ago 27 08:40 linux-headers-3.8.0-29
drwxr-xr-x 24 root root 4096 sep 15 21:36 linux-headers-3.8.0-30
drwxr-xr-x  7 root root 4096 sep 15 21:36 linux-headers-3.8.0-30-generic
drwxr-xr-x 24 root root 4096 sep 30 11:46 linux-headers-3.8.0-31
drwxr-xr-x  7 root root 4096 sep 30 11:46 linux-headers-3.8.0-31-generic
drwxr-xr-x 24 root root 4096 oct  2 08:22 linux-headers-3.8.0-32
drwxr-xr-x  7 root root 4096 oct  2 08:22 linux-headers-3.8.0-32-generic

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles; That is a load off ! looking better.
Now terminal code:
```

sudo dpkg -P linux-headers-3.8.0-{19,21,22,23,25,26,27,29}

```
and a new status to look at, show me:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```

[INDENT][INDENT]we be steppn' ?
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-image-
pi  linux-image-3.8.0-19-generic              3.8.0-19.30                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-21-generic              3.8.0-21.32                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-22-generic              3.8.0-22.33                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-23-generic              3.8.0-23.34                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-25-generic              3.8.0-25.37                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-26-generic              3.8.0-26.38                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-27-generic              3.8.0-27.40                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
pi  linux-image-3.8.0-29-generic              3.8.0-29.42                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iF  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-32-generic        3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.32.50                            i386         Generic Linux kernel image
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                    3.8.0-32.47                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic            3.8.0-32.47                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.32.50                            i386         Generic Linux kernel headers

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles; Well;
"dpkg" still with "pi" meaning (P)urged but some files still (I)nstalled.
see what happens now with: 
```

sudo dpkg -P linux-image-3.8.0-{19,21,22,23,25,26,27,29}-generic

```
And perhaps now we have room to work with.. might see next if "apt-get" can help us.
show:
```

df -h

```

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ sudo dpkg -P linux-image-3.8.0-{19,21,22,23,25,26,27,29}-generic
[sudo] password for juancho: 
(Reading database ... 248268 files and directories currently installed.)
Removing linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found linux image: /boot/vmlinuz-3.8.0-21-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
Removing linux-image-3.8.0-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found linux image: /boot/vmlinuz-3.8.0-22-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-21-generic /boot/vmlinuz-3.8.0-21-generic
Removing linux-image-3.8.0-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found linux image: /boot/vmlinuz-3.8.0-23-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
Removing linux-image-3.8.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found linux image: /boot/vmlinuz-3.8.0-25-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
Removing linux-image-3.8.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found linux image: /boot/vmlinuz-3.8.0-26-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-25-generic /boot/vmlinuz-3.8.0-25-generic
Removing linux-image-3.8.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found linux image: /boot/vmlinuz-3.8.0-27-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-26-generic /boot/vmlinuz-3.8.0-26-generic
Removing linux-image-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-27-generic /boot/vmlinuz-3.8.0-27-generic
Removing linux-image-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic

```

```

juancho@juancho-Satellite-C845:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  457G   93G  341G  22% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         940M   12K  940M   1% /dev
tmpfs                        190M  860K  189M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         949M  324K  948M   1% /run/shm
none                         100M   20K  100M   1% /run/user
/dev/sda1                    228M   29M  187M  14% /boot

```

---

### Post by Bashing-om on 2013-10-09
juanchorobles; Looking much better.

let's do some housecleaning and see what we look like .. and try and install the latest kernels if all looks likely.
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install linux-generic linux-headers-generic linux-image-generic linux-image-extra

##And again a new dpkg status:
dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
And I will begin to think we are out of the hairy woods

[INDENT][INDENT][INDENT]making progress
[/INDENT][/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-09
```

juancho@juancho-Satellite-C845:~$ sudo apt-get autoclean
[sudo] password for juancho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
juancho@juancho-Satellite-C845:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not installed
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not installed
E: Unmet dependencies. Try using -f.
juancho@juancho-Satellite-C845:~$ sudo apt-get clean
juancho@juancho-Satellite-C845:~$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic linux-image-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-extra

```

```

juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-image-
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iF  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-32-generic        3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.32.50                            i386         Generic Linux kernel image
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                    3.8.0-32.47                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic            3.8.0-32.47                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.32.50                            i386         Generic Linux kernel headers

```

---

### Post by Bashing-om on 2013-10-10
juanchorobles; You did well !

Let's try apt-get now:
```

sudo apt-get --purge remove linux-image-extra-3.8.0-31-generic
sudo apt-get --purge remove linux-image-extra-3.8.0-32-generic

```
and see where are now:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```
[INDENT][INDENT]backing up but still with progress
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-10
```

juancho@juancho-Satellite-C845:~$ sudo apt-get --purge remove linux-image-extra-3.8.0-31-generic
[sudo] password for juancho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
juancho@juancho-Satellite-C845:~$ sudo apt-get --purge remove linux-image-extra-3.8.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
                       Depends: linux-image-extra-3.8.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```

juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-image-
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iF  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-extra-3.8.0-32-generic        3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic                       3.8.0.32.50                            i386         Generic Linux kernel image
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                    3.8.0-32.47                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic            3.8.0-32.47                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.32.50                            i386         Generic Linux kernel headers

```

---

### Post by Bashing-om on 2013-10-10
juanchorobles; Shucks,

Let's see if we can back door them, install and then purge !
```

sudo apt-get install linux-image-3.8.0-31-generic

```

[INDENT][INDENT]backing up to get better traction
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-10
mmmm i think didnt work :(
```

juancho@juancho-Satellite-C845:~$ sudo apt-get install linux-image-3.8.0-31-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2013-10-10
juanchorobles; I'll add this to "things I do not understand" !
But OK, let's see what results:
```

sudo apt-get install linux-image-3.8.0-32-generic

```

[INDENT][INDENT]we will find a way
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-10
```

juancho@juancho-Satellite-C845:~$ sudo apt-get install linux-image-3.8.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
:(   do you think is better if i reinstall ubuntu? i dont want to but at this moment i think is the only solution

---

### Post by Bashing-om on 2013-10-10
juanchorobles; 

(re-)install is the nuclear solution .. always a sure fix, but all we have here presently is a dependency issue that has a solution.
Get that out of the way .. and all that I expect is left to do is update the index files and upgrade .. looks to me .

Lets try this .. as those images are marked "iu" ->(I)nstalled but (U)npacked .. let try dpkg's advise and do:
```

sudo apt-get -f install linux-image-extra-3.8.0-31-generic
sudo apt-get -f install linux-image-extra-3.8.0-32-generic

```

[INDENT][INDENT]there is a way
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-10
```

juancho@juancho-Satellite-C845:~$ sudo apt-get -f install linux-image-extra-3.8.0-31-generic
[sudo] password for juancho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-extra-3.8.0-31-generic is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not going to be installed
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
juancho@juancho-Satellite-C845:~$ sudo apt-get -f install linux-image-extra-3.8.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-extra-3.8.0-32-generic is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not going to be installed
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2013-10-10
juanchorobles; shucks. again !
As we are presently going round and round .. let me rest on this as is, and get a fresh perspective on it in my afternoon. It has become difficult for me to focus my thoughts.

We are so close !

[INDENT][INDENT]but so far away
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-10
thanks!!

---

### Post by Bashing-om on 2013-10-10
juanchorobles; Hey !

Still trying to wrap my mind around this, it is taxing my understanding of the package management system.
Let's us see if it is possible to reduce to simpler terms:
Show me:
```

ls -la /var/cache/apt/archives/linux-image*
ls -la /var/cache/apt/archives/linux-headers*
apt-cache policy linux-image* | grep Installed
ls -la /usr/src/
ls -la /var/lib/dpkg/info/linux*.list

``` As I really do not want to underhand the package manager system and leave the index files in a inconsistent state. Once I do understand the why, we can do the how.

[INDENT][INDENT]gotta be a way
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-11
```

juancho@juancho-Satellite-C845:~$ ls -la /var/cache/apt/archives/linux-image*
ls: cannot access /var/cache/apt/archives/linux-image*: No such file or directory
juancho@juancho-Satellite-C845:~$ ls -la /var/cache/apt/archives/linux-headers*
ls: cannot access /var/cache/apt/archives/linux-headers*: No such file or directory
juancho@juancho-Satellite-C845:~$ apt-cache policy linux-image* | grep Installed  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.8.0.32.50
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.8.0-31.46
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.8.0-30.44
  Installed: (none)
  Installed: 3.8.0-32.47
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: 3.8.0-30.44
  Installed: (none)
  Installed: (none)
  Installed: (none)
  Installed: (none)
juancho@juancho-Satellite-C845:~$ ls -la /usr/src/
total 32
drwxr-xr-x  8 root root 4096 oct  9 20:28 .
drwxr-xr-x 10 root root 4096 abr 24 11:02 ..
drwxr-xr-x 24 root root 4096 sep 15 21:36 linux-headers-3.8.0-30
drwxr-xr-x  7 root root 4096 sep 15 21:36 linux-headers-3.8.0-30-generic
drwxr-xr-x 24 root root 4096 sep 30 11:46 linux-headers-3.8.0-31
drwxr-xr-x  7 root root 4096 sep 30 11:46 linux-headers-3.8.0-31-generic
drwxr-xr-x 24 root root 4096 oct  2 08:22 linux-headers-3.8.0-32
drwxr-xr-x  7 root root 4096 oct  2 08:22 linux-headers-3.8.0-32-generic
juancho@juancho-Satellite-C845:~$ ls -la /var/lib/dpkg/info/linux*.list
-rw-r--r-- 1 root root  26319 abr 24 11:04 /var/lib/dpkg/info/linux-firmware.list
-rw-r--r-- 1 root root    144 oct  2 08:22 /var/lib/dpkg/info/linux-generic.list
-rw-r--r-- 1 root root 628325 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30-generic.list
-rw-r--r-- 1 root root 936606 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30.list
-rw-r--r-- 1 root root 628325 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31-generic.list
-rw-r--r-- 1 root root 936606 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31.list
-rw-r--r-- 1 root root 628325 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32-generic.list
-rw-r--r-- 1 root root 936606 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32.list
-rw-r--r-- 1 root root    168 oct  2 08:22 /var/lib/dpkg/info/linux-headers-generic.list
-rw-r--r-- 1 root root  47785 sep 15 21:35 /var/lib/dpkg/info/linux-image-3.8.0-30-generic.list
-rw-r--r-- 1 root root 275469 sep 15 21:36 /var/lib/dpkg/info/linux-image-extra-3.8.0-30-generic.list
-rw-r--r-- 1 root root 275469 sep 30 11:46 /var/lib/dpkg/info/linux-image-extra-3.8.0-31-generic.list
-rw-r--r-- 1 root root 275469 oct  2 08:22 /var/lib/dpkg/info/linux-image-extra-3.8.0-32-generic.list
-rw-r--r-- 1 root root    162 oct  2 08:22 /var/lib/dpkg/info/linux-image-generic.list
-rw-r--r-- 1 root root  24375 sep 30 11:46 /var/lib/dpkg/info/linux-libc-dev:i386.list
-rw-r--r-- 1 root root    456 abr 24 11:04 /var/lib/dpkg/info/linux-sound-base.list

```

---

### Post by Bashing-om on 2013-10-11
juanchorobles;hey, The thought had occurred to me you had lost faith.

Let's try this as next expedient:
```

sudo rm -rf /var/lib/apt/lists/*
sudo apt-get --purge remove linux-image-extra-3.8.0-31-generic
sudo apt-get --purge remove linux-image-extra-3.8.0-32-generic

```
Might not be the proper order in removal, this "extra" is a new addition and not familiar with it .. could be that the -image file should be removed 1st. We will see. 
We will re-build "/var/lib/apt/lists/" at a later stage.

Try it and we will see what results from this attempt.

[INDENT][INDENT]try try again.
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-12
```

juancho@juancho-Satellite-C845:~$ sudo rm -rf /var/lib/apt/lists/*
juancho@juancho-Satellite-C845:~$ sudo apt-get --purge remove linux-image-extra-3.8.0-31-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-32-generic : Depends: linux-image-3.8.0-32-generic but it is not installable
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
juancho@juancho-Satellite-C845:~$ sudo apt-get --purge remove linux-image-extra-3.8.0-32-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.8.0-31-generic : Depends: linux-image-3.8.0-31-generic but it is not installable
 linux-image-generic : Depends: linux-image-3.8.0-32-generic but it is not installable
                       Depends: linux-image-extra-3.8.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by Bashing-om on 2013-10-12
juanchorobles; That last, disappointed but not real surprised.
I do not understand how version 32 could depend on version 31 and vice versa !
I am actively looking at a way to remove that dependency, Are you comfortable editing files ?

I will be back.

---

### Post by juanchorobles on 2013-10-12
i dont understand either, but i hope and i think we are going to make it, thanks for all your help! i dont know how to edit files

---

### Post by Bashing-om on 2013-10-12
juanchorobles; OK.
In preparation for editing dpkg's file "status"; Show me:
```

ls -la /var/lib/dpkg/info/linux*.list
ls -la /usr/src

```
Editing files: Welcome to mastering your operating system !
We will make a backup of the file -standard operating procedure, for what ever might happen;
Remove the references for the 31 and 32 versions of images-extras and images; - slowly, carefully, paying attention to detail -
Attempt to remove those old kernels;
Then see if we can install the latest kernel.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-13
```
 juancho@juancho-Satellite-C845:~$ ls -la /var/lib/dpkg/info/linux*.list -rw-r--r-- 1 root root  26319 abr 24 11:04 /var/lib/dpkg/info/linux-firmware.list -rw-r--r-- 1 root root    144 oct  2 08:22 /var/lib/dpkg/info/linux-generic.list -rw-r--r-- 1 root root 628325 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30-generic.list -rw-r--r-- 1 root root 936606 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30.list -rw-r--r-- 1 root root 628325 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31-generic.list -rw-r--r-- 1 root root 936606 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31.list -rw-r--r-- 1 root root 628325 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32-generic.list -rw-r--r-- 1 root root 936606 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32.list -rw-r--r-- 1 root root    168 oct  2 08:22 /var/lib/dpkg/info/linux-headers-generic.list -rw-r--r-- 1 root root  47785 sep 15 21:35 /var/lib/dpkg/info/linux-image-3.8.0-30-generic.list -rw-r--r-- 1 root root 275469 sep 15 21:36 /var/lib/dpkg/info/linux-image-extra-3.8.0-30-generic.list -rw-r--r-- 1 root root 275469 sep 30 11:46 /var/lib/dpkg/info/linux-image-extra-3.8.0-31-generic.list -rw-r--r-- 1 root root 275469 oct  2 08:22 /var/lib/dpkg/info/linux-image-extra-3.8.0-32-generic.list -rw-r--r-- 1 root root    162 oct  2 08:22 /var/lib/dpkg/info/linux-image-generic.list -rw-r--r-- 1 root root  24375 sep 30 11:46 /var/lib/dpkg/info/linux-libc-dev:i386.list -rw-r--r-- 1 root root    456 abr 24 11:04 /var/lib/dpkg/info/linux-sound-base.list juancho@juancho-Satellite-C845:~$ ls -la /usr/src total 32 drwxr-xr-x  8 root root 4096 oct  9 20:28 . drwxr-xr-x 10 root root 4096 abr 24 11:02 .. drwxr-xr-x 24 root root 4096 sep 15 21:36 linux-headers-3.8.0-30 drwxr-xr-x  7 root root 4096 sep 15 21:36 linux-headers-3.8.0-30-generic drwxr-xr-x 24 root root 4096 sep 30 11:46 linux-headers-3.8.0-31 drwxr-xr-x  7 root root 4096 sep 30 11:46 linux-headers-3.8.0-31-generic drwxr-xr-x 24 root root 4096 oct  2 08:22 linux-headers-3.8.0-32 drwxr-xr-x  7 root root 4096 oct  2 08:22 linux-headers-3.8.0-32-generic 
```

---

### Post by juanchorobles on 2013-10-13
```
 juancho@juancho-Satellite-C845:~$ ls -la /var/lib/dpkg/info/linux*.list -rw-r--r-- 1 root root  26319 abr 24 11:04 /var/lib/dpkg/info/linux-firmware.list -rw-r--r-- 1 root root    144 oct  2 08:22 /var/lib/dpkg/info/linux-generic.list -rw-r--r-- 1 root root 628325 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30-generic.list -rw-r--r-- 1 root root 936606 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30.list -rw-r--r-- 1 root root 628325 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31-generic.list -rw-r--r-- 1 root root 936606 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31.list -rw-r--r-- 1 root root 628325 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32-generic.list -rw-r--r-- 1 root root 936606 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32.list -rw-r--r-- 1 root root    168 oct  2 08:22 /var/lib/dpkg/info/linux-headers-generic.list -rw-r--r-- 1 root root  47785 sep 15 21:35 /var/lib/dpkg/info/linux-image-3.8.0-30-generic.list -rw-r--r-- 1 root root 275469 sep 15 21:36 /var/lib/dpkg/info/linux-image-extra-3.8.0-30-generic.list -rw-r--r-- 1 root root 275469 sep 30 11:46 /var/lib/dpkg/info/linux-image-extra-3.8.0-31-generic.list -rw-r--r-- 1 root root 275469 oct  2 08:22 /var/lib/dpkg/info/linux-image-extra-3.8.0-32-generic.list -rw-r--r-- 1 root root    162 oct  2 08:22 /var/lib/dpkg/info/linux-image-generic.list -rw-r--r-- 1 root root  24375 sep 30 11:46 /var/lib/dpkg/info/linux-libc-dev:i386.list -rw-r--r-- 1 root root    456 abr 24 11:04 /var/lib/dpkg/info/linux-sound-base.list juancho@juancho-Satellite-C845:~$ ls -la /usr/src total 32 drwxr-xr-x  8 root root 4096 oct  9 20:28 . drwxr-xr-x 10 root root 4096 abr 24 11:02 .. drwxr-xr-x 24 root root 4096 sep 15 21:36 linux-headers-3.8.0-30 drwxr-xr-x  7 root root 4096 sep 15 21:36 linux-headers-3.8.0-30-generic drwxr-xr-x 24 root root 4096 sep 30 11:46 linux-headers-3.8.0-31 drwxr-xr-x  7 root root 4096 sep 30 11:46 linux-headers-3.8.0-31-generic drwxr-xr-x 24 root root 4096 oct  2 08:22 linux-headers-3.8.0-32 drwxr-xr-x  7 root root 4096 oct  2 08:22 linux-headers-3.8.0-32-generic  
```

---

### Post by Jonathan Precise on 2013-10-13
Try

```
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get -f install
```

As a side-note, [FONT=Courier New]apt-get -f install[/FONT] should be run alone.

---

### Post by Bashing-om on 2013-10-14
juanchorobles; Hey,

See Jonathan's last, his advise is well worth trying.
And, please edit that last output and place returns at the appropriate places to make that output "readable".

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-14
```

juancho@juancho-Satellite-C845:~$ ls -la /var/lib/dpkg/info/linux*.list
-rw-r--r-- 1 root root  26319 abr 24 11:04 /var/lib/dpkg/info/linux-firmware.list
-rw-r--r-- 1 root root    144 oct  2 08:22 /var/lib/dpkg/info/linux-generic.list
-rw-r--r-- 1 root root 628325 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30-generic.list
-rw-r--r-- 1 root root 936606 sep 15 21:36 /var/lib/dpkg/info/linux-headers-3.8.0-30.list
-rw-r--r-- 1 root root 628325 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31-generic.list
-rw-r--r-- 1 root root 936606 sep 30 11:46 /var/lib/dpkg/info/linux-headers-3.8.0-31.list
-rw-r--r-- 1 root root 628325 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32-generic.list
-rw-r--r-- 1 root root 936606 oct  2 08:22 /var/lib/dpkg/info/linux-headers-3.8.0-32.list
-rw-r--r-- 1 root root    168 oct  2 08:22 /var/lib/dpkg/info/linux-headers-generic.list
-rw-r--r-- 1 root root  47785 sep 15 21:35 /var/lib/dpkg/info/linux-image-3.8.0-30-generic.list
-rw-r--r-- 1 root root 275469 sep 15 21:36 /var/lib/dpkg/info/linux-image-extra-3.8.0-30-generic.list
-rw-r--r-- 1 root root 275469 sep 30 11:46 /var/lib/dpkg/info/linux-image-extra-3.8.0-31-generic.list
-rw-r--r-- 1 root root 275469 oct  2 08:22 /var/lib/dpkg/info/linux-image-extra-3.8.0-32-generic.list
-rw-r--r-- 1 root root    162 oct  2 08:22 /var/lib/dpkg/info/linux-image-generic.list
-rw-r--r-- 1 root root  24375 sep 30 11:46 /var/lib/dpkg/info/linux-libc-dev:i386.list
-rw-r--r-- 1 root root    456 abr 24 11:04 /var/lib/dpkg/info/linux-sound-base.list

```

```

juancho@juancho-Satellite-C845:~$ ls -la /usr/src
total 32
drwxr-xr-x  8 root root 4096 oct  9 20:28 .
drwxr-xr-x 10 root root 4096 abr 24 11:02 ..
drwxr-xr-x 24 root root 4096 sep 15 21:36 linux-headers-3.8.0-30
drwxr-xr-x  7 root root 4096 sep 15 21:36 linux-headers-3.8.0-30-generic
drwxr-xr-x 24 root root 4096 sep 30 11:46 linux-headers-3.8.0-31
drwxr-xr-x  7 root root 4096 sep 30 11:46 linux-headers-3.8.0-31-generic
drwxr-xr-x 24 root root 4096 oct  2 08:22 linux-headers-3.8.0-32
drwxr-xr-x  7 root root 4096 oct  2 08:22 linux-headers-3.8.0-32-generic

```

---

### Post by juanchorobles on 2013-10-14
```

juancho@juancho-Satellite-C845:~$ sudo mkdir /var/lib/apt/lists/partial
[sudo] password for juancho: 
mkdir: cannot create directory &#8216;/var/lib/apt/lists/partial&#8217;: File exists
juancho@juancho-Satellite-C845:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  linux-image-3.8.0-31-generic linux-image-3.8.0-32-generic
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.8.0-31-generic linux-image-3.8.0-32-generic
0 upgraded, 2 newly installed, 0 to remove and 116 not upgraded.
5 not fully installed or removed.
Need to get 24,8 MB of archives.
After this operation, 54,9 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ raring-proposed/main linux-image-3.8.0-32-generic i386 3.8.0-32.47 [12,4 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ raring-updates/main linux-image-3.8.0-31-generic i386 3.8.0-31.46 [12,4 MB]
Err http://archive.ubuntu.com/ubuntu/ raring-updates/main linux-image-3.8.0-31-generic i386 3.8.0-31.46
  Connection failed [IP: 91.189.92.176 80]
Get:3 http://archive.ubuntu.com/ubuntu/ raring-security/main linux-image-3.8.0-31-generic i386 3.8.0-31.46 [12,4 MB]
Fetched 12,4 MB in 9min 46s (21,2 kB/s)                                        
(Reading database ... 242005 files and directories currently installed.)
Unpacking linux-image-3.8.0-32-generic (from .../linux-image-3.8.0-32-generic_3.8.0-32.47_i386.deb) ...
Done.
Unpacking linux-image-3.8.0-31-generic (from .../linux-image-3.8.0-31-generic_3.8.0-31.46_i386.deb) ...
Done.
Setting up linux-image-3.8.0-32-generic (3.8.0-32.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-3.8.0-32-generic (3.8.0-32.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (3.8.0.32.50) ...
Setting up linux-generic (3.8.0.32.50) ...
Setting up linux-image-extra-3.8.0-30-generic (3.8.0-30.44) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-30-generic /boot/vmlinuz-3.8.0-30-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-3.8.0-31-generic (3.8.0-31.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-3.8.0-31-generic (3.8.0-31.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found linux image: /boot/vmlinuz-3.8.0-30-generic
Found initrd image: /boot/initrd.img-3.8.0-30-generic
Found memtest86+ image: /memtest86+.bin
done

```

---

### Post by juanchorobles on 2013-10-14
i think this work!! :)  thanks!!!!!  :) :)

---

### Post by Bashing-om on 2013-10-14
juanchorobles; Looking good !

let's do:
```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic linux-image-extra

```
see if that pulls in the latest kernel.

[INDENT][INDENT]that was a big step
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-15
```

juancho@juancho-Satellite-C845:~$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic linux-image-extra
[sudo] password for juancho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-extra

```

---

### Post by Bashing-om on 2013-10-15
juanchorobles; Well, well ..
As I said I am not familiar with "linux-image-extra". Did not know what might result with that shot.
Let's try as :
```

sudo apt-get install linux-generic linux-headers-generic linux-image-generic

```

[INDENT][INDENT]getting close
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-15
```

juancho@juancho-Satellite-C845:~$ sudo apt-get install linux-generic linux-headers-generic linux-image-generic
[sudo] password for juancho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
linux-image-generic is already the newest version.
linux-image-generic set to manually installed.
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 116 not upgraded.

```

---

### Post by Bashing-om on 2013-10-15
juanchorobles; Not too shabby !

Latest kernel is installed.

Maybe we are bitten by an apt bug:
> 
linux-image-generic set to manually installed.

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1175637](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1175637)

As we do not want those kernels on hold let's do:
```

sudo apt-mark markauto linux-image.*

```
And when that runs, let's update your system:
```

sudo apt-get update
sudo apt-get upgrade

```

and then we will look at where we stand.

[INDENT][INDENT]looking better all the time
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-15
it looks good

```

Processing triggers for man-db ...
Setting up apt (0.9.7.7ubuntu6) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: key C0B21F32: "Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>" not changed
gpg: key EFE21092: "Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 4
gpg:              unchanged: 4
(Reading database ... 243286 files and directories currently installed.)
Preparing to replace bsdutils 1:2.20.1-5.1ubuntu8 (using .../bsdutils_1%3a2.20.1-5.1ubuntu8.1_i386.deb) ...
Unpacking replacement bsdutils ...
Processing triggers for man-db ...
Setting up bsdutils (1:2.20.1-5.1ubuntu8.1) ...
(Reading database ... 243286 files and directories currently installed.)
Preparing to replace libuuid1:i386 2.20.1-5.1ubuntu8 (using .../libuuid1_2.20.1-5.1ubuntu8.1_i386.deb) ...
Unpacking replacement libuuid1:i386 ...
Setting up libuuid1:i386 (2.20.1-5.1ubuntu8.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 243286 files and directories currently installed.)
Preparing to replace libblkid1:i386 2.20.1-5.1ubuntu8 (using .../libblkid1_2.20.1-5.1ubuntu8.1_i386.deb) ...
Unpacking replacement libblkid1:i386 ...
Setting up libblkid1:i386 (2.20.1-5.1ubuntu8.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 243286 files and directories currently installed.)
Preparing to replace libmount1:i386 2.20.1-5.1ubuntu8 (using .../libmount1_2.20.1-5.1ubuntu8.1_i386.deb) ...
Unpacking replacement libmount1:i386 ...
Setting up libmount1:i386 (2.20.1-5.1ubuntu8.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 243286 files and directories currently installed.)
Preparing to replace libapt-inst1.5:i386 0.9.7.7ubuntu5 (using .../libapt-inst1.5_0.9.7.7ubuntu6_i386.deb) ...
Unpacking replacement libapt-inst1.5:i386 ...
Preparing to replace libpython3.3:i386 3.3.1-1ubuntu5 (using .../libpython3.3_3.3.1-1ubuntu5.2_i386.deb) ...
Unpacking replacement libpython3.3:i386 ...
Preparing to replace python3.3 3.3.1-1ubuntu5 (using .../python3.3_3.3.1-1ubuntu5.2_i386.deb) ...
Unpacking replacement python3.3 ...
Preparing to replace libpython3.3-stdlib:i386 3.3.1-1ubuntu5 (using .../libpython3.3-stdlib_3.3.1-1ubuntu5.2_i386.deb) ...
Unpacking replacement libpython3.3-stdlib:i386 ...
Preparing to replace libpython3.3-minimal:i386 3.3.1-1ubuntu5 (using .../libpython3.3-minimal_3.3.1-1ubuntu5.2_i386.deb) ...
Unpacking replacement libpython3.3-minimal:i386 ...
Preparing to replace python3.3-minimal 3.3.1-1ubuntu5 (using .../python3.3-minimal_3.3.1-1ubuntu5.2_i386.deb) ...
Unpacking replacement python3.3-minimal ...
Preparing to replace ifupdown 0.7.5ubuntu2 (using .../ifupdown_0.7.5ubuntu2.2_i386.deb) ...
Unpacking replacement ifupdown ...
Preparing to replace libprocps0:i386 1:3.3.3-2ubuntu5 (using .../libprocps0_1%3a3.3.3-2ubuntu5.1_i386.deb) ...
Unpacking replacement libprocps0:i386 ...
Preparing to replace libsasl2-modules:i386 2.1.25.dfsg1-6 (using .../libsasl2-modules_2.1.25.dfsg1-6ubuntu0.1_i386.deb) ...
Unpacking replacement libsasl2-modules:i386 ...
Preparing to replace libsasl2-2:i386 2.1.25.dfsg1-6 (using .../libsasl2-2_2.1.25.dfsg1-6ubuntu0.1_i386.deb) ...
Unpacking replacement libsasl2-2:i386 ...
Preparing to replace python3-gi-cairo 3.8.0-2 (using .../python3-gi-cairo_3.8.0-2ubuntu1_i386.deb) ...
Unpacking replacement python3-gi-cairo ...
Preparing to replace python3-gi 3.8.0-2 (using .../python3-gi_3.8.0-2ubuntu1_i386.deb) ...
Unpacking replacement python3-gi ...
Preparing to replace libcupsppdc1:i386 1.6.2-1ubuntu5 (using .../libcupsppdc1_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement libcupsppdc1:i386 ...
Preparing to replace libcupsimage2:i386 1.6.2-1ubuntu5 (using .../libcupsimage2_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement libcupsimage2:i386 ...
Preparing to replace libcupscgi1:i386 1.6.2-1ubuntu5 (using .../libcupscgi1_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement libcupscgi1:i386 ...
Preparing to replace procps 1:3.3.3-2ubuntu5 (using .../procps_1%3a3.3.3-2ubuntu5.1_i386.deb) ...
Unpacking replacement procps ...
Preparing to replace cups-daemon 1.6.2-1ubuntu5 (using .../cups-daemon_1.6.2-1ubuntu7_i386.deb) ...
cups stop/waiting
Unpacking replacement cups-daemon ...
Preparing to replace cups-common 1.6.2-1ubuntu5 (using .../cups-common_1.6.2-1ubuntu7_all.deb) ...
Unpacking replacement cups-common ...
Preparing to replace cups-bsd 1.6.2-1ubuntu5 (using .../cups-bsd_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement cups-bsd ...
Preparing to replace cups-client 1.6.2-1ubuntu5 (using .../cups-client_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement cups-client ...
Preparing to replace libcupsmime1:i386 1.6.2-1ubuntu5 (using .../libcupsmime1_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement libcupsmime1:i386 ...
Preparing to replace cups 1.6.2-1ubuntu5 (using .../cups_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement cups ...
Preparing to replace libcups2:i386 1.6.2-1ubuntu5 (using .../libcups2_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement libcups2:i386 ...
Preparing to replace cups-ppdc 1.6.2-1ubuntu5 (using .../cups-ppdc_1.6.2-1ubuntu7_i386.deb) ...
Unpacking replacement cups-ppdc ...
Preparing to replace gvfs-fuse 1.16.1-0ubuntu1 (using .../gvfs-fuse_1.16.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gvfs-fuse ...
Preparing to replace gvfs-backends 1.16.1-0ubuntu1 (using .../gvfs-backends_1.16.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gvfs-backends ...
Preparing to replace gvfs-daemons 1.16.1-0ubuntu1 (using .../gvfs-daemons_1.16.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gvfs-daemons ...
Preparing to replace gvfs-libs:i386 1.16.1-0ubuntu1 (using .../gvfs-libs_1.16.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gvfs-libs:i386 ...
Preparing to replace gvfs-bin 1.16.1-0ubuntu1 (using .../gvfs-bin_1.16.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gvfs-bin ...
Preparing to replace gvfs-common 1.16.1-0ubuntu1 (using .../gvfs-common_1.16.1-0ubuntu1.1_all.deb) ...
Unpacking replacement gvfs-common ...
Preparing to replace gvfs:i386 1.16.1-0ubuntu1 (using .../gvfs_1.16.1-0ubuntu1.1_i386.deb) ...
Unpacking replacement gvfs:i386 ...
Preparing to replace libaudio2:i386 1.9.3-5 (using .../libaudio2_1.9.3-5ubuntu0.13.04.1_i386.deb) ...
Unpacking replacement libaudio2:i386 ...
Preparing to replace libdvdread4 4.2.0+20121016-1ubuntu1 (using .../libdvdread4_4.2.0+20121016-1ubuntu1.1_i386.deb) ...
Unpacking replacement libdvdread4 ...
Preparing to replace xserver-common 2:1.13.3-0ubuntu6 (using .../xserver-common_2%3a1.13.3-0ubuntu6.1_all.deb) ...
Unpacking replacement xserver-common ...
Preparing to replace libgl1-mesa-dri:i386 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-dri_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-dri:i386 ...
Preparing to replace xserver-xorg-core 2:1.13.3-0ubuntu6 (using .../xserver-xorg-core_2%3a1.13.3-0ubuntu6.1_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Preparing to replace libgles2-mesa:i386 9.1.4-0ubuntu0.1 (using .../libgles2-mesa_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libgles2-mesa:i386 ...
Preparing to replace libgl1-mesa-glx:i386 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-glx_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-glx:i386 ...
Preparing to replace libegl1-mesa-drivers:i386 9.1.4-0ubuntu0.1 (using .../libegl1-mesa-drivers_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libegl1-mesa-drivers:i386 ...
Preparing to replace libglapi-mesa:i386 9.1.4-0ubuntu0.1 (using .../libglapi-mesa_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libglapi-mesa:i386 ...
Preparing to replace libgbm1:i386 9.1.4-0ubuntu0.1 (using .../libgbm1_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libgbm1:i386 ...
Preparing to replace libopenvg1-mesa:i386 9.1.4-0ubuntu0.1 (using .../libopenvg1-mesa_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libopenvg1-mesa:i386 ...
Preparing to replace libegl1-mesa:i386 9.1.4-0ubuntu0.1 (using .../libegl1-mesa_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libegl1-mesa:i386 ...
Preparing to replace libgrip0 0.3.6daily13.02.26-0ubuntu1 (using .../libgrip0_0.3.6+13.04.20130711-0ubuntu1_i386.deb) ...
Unpacking replacement libgrip0 ...
Preparing to replace libicu48:i386 4.8.1.1-12 (using .../libicu48_4.8.1.1-12ubuntu0.1_i386.deb) ...
Unpacking replacement libicu48:i386 ...
Preparing to replace python2.7 2.7.4-2ubuntu3 (using .../python2.7_2.7.4-2ubuntu3.2_i386.deb) ...
Unpacking replacement python2.7 ...
Preparing to replace python2.7-minimal 2.7.4-2ubuntu3 (using .../python2.7-minimal_2.7.4-2ubuntu3.2_i386.deb) ...
Unpacking replacement python2.7-minimal ...
Preparing to replace libpython2.7:i386 2.7.4-2ubuntu3 (using .../libpython2.7_2.7.4-2ubuntu3.2_i386.deb) ...
Unpacking replacement libpython2.7:i386 ...
Preparing to replace libpython2.7-stdlib:i386 2.7.4-2ubuntu3 (using .../libpython2.7-stdlib_2.7.4-2ubuntu3.2_i386.deb) ...
Unpacking replacement libpython2.7-stdlib:i386 ...
Preparing to replace libpython2.7-minimal:i386 2.7.4-2ubuntu3 (using .../libpython2.7-minimal_2.7.4-2ubuntu3.2_i386.deb) ...
Unpacking replacement libpython2.7-minimal:i386 ...
Preparing to replace libqtwebkit4:i386 2.3.0-0ubuntu2 (using .../libqtwebkit4_2.3.0-0ubuntu2.1_i386.deb) ...
Unpacking replacement libqtwebkit4:i386 ...
Preparing to replace libreoffice-calc 1:4.0.2-0ubuntu1 (using .../libreoffice-calc_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-calc ...
Preparing to replace libreoffice-gnome 1:4.0.2-0ubuntu1 (using .../libreoffice-gnome_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-gnome ...
Preparing to replace libreoffice-gtk 1:4.0.2-0ubuntu1 (using .../libreoffice-gtk_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-gtk ...
Preparing to replace libreoffice-writer 1:4.0.2-0ubuntu1 (using .../libreoffice-writer_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-writer ...
Preparing to replace python3-uno 1:4.0.2-0ubuntu1 (using .../python3-uno_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement python3-uno ...
Preparing to replace libreoffice-common 1:4.0.2-0ubuntu1 (using .../libreoffice-common_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-common ...
Preparing to replace libreoffice-pdfimport 1:4.0.2-0ubuntu1 (using .../libreoffice-pdfimport_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-pdfimport ...
Preparing to replace libreoffice-math 1:4.0.2-0ubuntu1 (using .../libreoffice-math_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-math ...
Preparing to replace libreoffice-base-core 1:4.0.2-0ubuntu1 (using .../libreoffice-base-core_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-base-core ...
Preparing to replace libreoffice-draw 1:4.0.2-0ubuntu1 (using .../libreoffice-draw_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-draw ...
Preparing to replace libreoffice-impress 1:4.0.2-0ubuntu1 (using .../libreoffice-impress_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-impress ...
Preparing to replace libreoffice-core 1:4.0.2-0ubuntu1 (using .../libreoffice-core_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-core ...
Preparing to replace libreoffice-ogltrans 1:4.0.2-0ubuntu1 (using .../libreoffice-ogltrans_1%3a4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-ogltrans ...
Preparing to replace ure 4.0.2-0ubuntu1 (using .../ure_4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement ure ...
Preparing to replace uno-libs3 4.0.2-0ubuntu1 (using .../uno-libs3_4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement uno-libs3 ...
Preparing to replace fonts-opensymbol 2:102.2+LibO4.0.2-0ubuntu1 (using .../fonts-opensymbol_2%3a102.2+LibO4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement fonts-opensymbol ...
Preparing to replace libreoffice-style-human 1:4.0.2-0ubuntu1 (using .../libreoffice-style-human_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-style-human ...
Preparing to replace libxatracker1:i386 9.1.4-0ubuntu0.1 (using .../libxatracker1_9.1.7-1ubuntu2_i386.deb) ...
Unpacking replacement libxatracker1:i386 ...
Preparing to replace lightdm 1.6.0-0ubuntu3.1 (using .../lightdm_1.6.0-0ubuntu4_i386.deb) ...
Unpacking replacement lightdm ...
Preparing to replace python-gi-cairo 3.8.0-2 (using .../python-gi-cairo_3.8.0-2ubuntu1_i386.deb) ...
Unpacking replacement python-gi-cairo ...
Preparing to replace software-center 5.6.0-0ubuntu2 (using .../software-center_5.6.0-0ubuntu3_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace python-gi 3.8.0-2 (using .../python-gi_3.8.0-2ubuntu1_i386.deb) ...
Unpacking replacement python-gi ...
Preparing to replace apt-utils 0.9.7.7ubuntu5 (using .../apt-utils_0.9.7.7ubuntu6_i386.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace initramfs-tools 0.103ubuntu0.7 (using .../initramfs-tools_0.103ubuntu0.8_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace initramfs-tools-bin 0.103ubuntu0.7 (using .../initramfs-tools-bin_0.103ubuntu0.8_i386.deb) ...
Unpacking replacement initramfs-tools-bin ...
Preparing to replace apt-transport-https 0.9.7.7ubuntu5 (using .../apt-transport-https_0.9.7.7ubuntu6_i386.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace uuid-runtime 2.20.1-5.1ubuntu8 (using .../uuid-runtime_2.20.1-5.1ubuntu8.1_i386.deb) ...
Unpacking replacement uuid-runtime ...
Preparing to replace python3-problem-report 2.9.2-0ubuntu8.3 (using .../python3-problem-report_2.9.2-0ubuntu8.4_all.deb) ...
Unpacking replacement python3-problem-report ...
Preparing to replace python3-apport 2.9.2-0ubuntu8.3 (using .../python3-apport_2.9.2-0ubuntu8.4_all.deb) ...
Unpacking replacement python3-apport ...
Preparing to replace apport 2.9.2-0ubuntu8.3 (using .../apport_2.9.2-0ubuntu8.4_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace gnome-terminal-data 3.6.1-0ubuntu4 (using .../gnome-terminal-data_3.6.1-0ubuntu4.1_all.deb) ...
Unpacking replacement gnome-terminal-data ...
Preparing to replace gnome-terminal 3.6.1-0ubuntu4 (using .../gnome-terminal_3.6.1-0ubuntu4.1_i386.deb) ...
Unpacking replacement gnome-terminal ...
Preparing to replace apport-gtk 2.9.2-0ubuntu8.3 (using .../apport-gtk_2.9.2-0ubuntu8.4_all.deb) ...
Unpacking replacement apport-gtk ...
Preparing to replace libgnome-bluetooth11 3.6.1-0ubuntu3 (using .../libgnome-bluetooth11_3.6.1-0ubuntu3.1_i386.deb) ...
Unpacking replacement libgnome-bluetooth11 ...
Preparing to replace gnome-bluetooth 3.6.1-0ubuntu3 (using .../gnome-bluetooth_3.6.1-0ubuntu3.1_i386.deb) ...
Unpacking replacement gnome-bluetooth ...
Preparing to replace gir1.2-gnomebluetooth-1.0 3.6.1-0ubuntu3 (using .../gir1.2-gnomebluetooth-1.0_3.6.1-0ubuntu3.1_i386.deb) ...
Unpacking replacement gir1.2-gnomebluetooth-1.0 ...
Preparing to replace glib-networking:i386 2.36.1-0ubuntu1 (using .../glib-networking_2.36.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement glib-networking:i386 ...
Preparing to replace glib-networking-services 2.36.1-0ubuntu1 (using .../glib-networking-services_2.36.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement glib-networking-services ...
Preparing to replace glib-networking-common 2.36.1-0ubuntu1 (using .../glib-networking-common_2.36.2-0ubuntu0.1_all.deb) ...
Unpacking replacement glib-networking-common ...
Preparing to replace liblightdm-gobject-1-0 1.6.0-0ubuntu3.1 (using .../liblightdm-gobject-1-0_1.6.0-0ubuntu4_i386.deb) ...
Unpacking replacement liblightdm-gobject-1-0 ...
Preparing to replace libreoffice-l10n-en-gb 1:4.0.2-0ubuntu1 (using .../libreoffice-l10n-en-gb_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-l10n-en-gb ...
Preparing to replace libreoffice-help-en-gb 1:4.0.2-0ubuntu1 (using .../libreoffice-help-en-gb_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-help-en-gb ...
Preparing to replace libreoffice-help-en-us 1:4.0.2-0ubuntu1 (using .../libreoffice-help-en-us_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-help-en-us ...
Preparing to replace libreoffice-l10n-es 1:4.0.2-0ubuntu1 (using .../libreoffice-l10n-es_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-l10n-es ...
Preparing to replace libreoffice-help-es 1:4.0.2-0ubuntu1 (using .../libreoffice-help-es_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-help-es ...
Preparing to replace libreoffice-l10n-en-za 1:4.0.2-0ubuntu1 (using .../libreoffice-l10n-en-za_1%3a4.0.4-0ubuntu1_all.deb) ...
Unpacking replacement libreoffice-l10n-en-za ...
Preparing to replace libreoffice-presentation-minimizer 1.0.4+LibO4.0.2-0ubuntu1 (using .../libreoffice-presentation-minimizer_1.0.4+LibO4.0.4-0ubuntu1_i386.deb) ...
Unpacking replacement libreoffice-presentation-minimizer ...
Preparing to replace linux-libc-dev:i386 3.8.0-31.46 (using .../linux-libc-dev_3.8.0-32.47_i386.deb) ...
Unpacking replacement linux-libc-dev:i386 ...
Preparing to replace python-gobject 3.8.0-2 (using .../python-gobject_3.8.0-2ubuntu1_all.deb) ...
Unpacking replacement python-gobject ...
Preparing to replace vino 3.6.2-0ubuntu4 (using .../vino_3.6.2-0ubuntu4.1_i386.deb) ...
Unpacking replacement vino ...
Preparing to replace xserver-xorg-video-intel 2:2.21.6-0ubuntu4.1 (using .../xserver-xorg-video-intel_2%3a2.21.6-0ubuntu4.3_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Preparing to replace xserver-xorg-video-savage 1:2.3.6-0ubuntu1 (using .../xserver-xorg-video-savage_1%3a2.3.6-0ubuntu1.1_i386.deb) ...
Unpacking replacement xserver-xorg-video-savage ...
Preparing to replace unity-webapps-gmail 2.4.7 (using .../unity-webapps-gmail_2.4.7.2_all.deb) ...
Unpacking replacement unity-webapps-gmail ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for ufw ...
Processing triggers for doc-base ...
Processing 2 changed doc-base files...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for gconf2 ...
Processing triggers for mime-support ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for fontconfig ...
Setting up tzdata-java (2013g-0ubuntu0.13.04) ...
Setting up libapt-inst1.5:i386 (0.9.7.7ubuntu6) ...
Setting up libpython3.3-minimal:i386 (3.3.1-1ubuntu5.2) ...
Setting up libpython3.3-stdlib:i386 (3.3.1-1ubuntu5.2) ...
Setting up libpython3.3:i386 (3.3.1-1ubuntu5.2) ...
Setting up python3.3-minimal (3.3.1-1ubuntu5.2) ...
Setting up python3.3 (3.3.1-1ubuntu5.2) ...
Setting up ifupdown (0.7.5ubuntu2.2) ...
Setting up libprocps0:i386 (1:3.3.3-2ubuntu5.1) ...
Setting up libsasl2-2:i386 (2.1.25.dfsg1-6ubuntu0.1) ...
Setting up libsasl2-modules:i386 (2.1.25.dfsg1-6ubuntu0.1) ...
Setting up python3-gi (3.8.0-2ubuntu1) ...
Setting up python3-gi-cairo (3.8.0-2ubuntu1) ...
Setting up libcups2:i386 (1.6.2-1ubuntu7) ...
Setting up libcupsppdc1:i386 (1.6.2-1ubuntu7) ...
Setting up libcupsimage2:i386 (1.6.2-1ubuntu7) ...
Setting up libcupscgi1:i386 (1.6.2-1ubuntu7) ...
Setting up procps (1:3.3.3-2ubuntu5.1) ...
procps stop/waiting
Setting up libcupsmime1:i386 (1.6.2-1ubuntu7) ...
Setting up cups-daemon (1.6.2-1ubuntu7) ...
cups start/running, process 13133
Setting up cups-common (1.6.2-1ubuntu7) ...
Setting up cups-client (1.6.2-1ubuntu7) ...
Setting up cups-bsd (1.6.2-1ubuntu7) ...
Setting up cups-ppdc (1.6.2-1ubuntu7) ...
Setting up cups (1.6.2-1ubuntu7) ...
Updating PPD files for cups ...
Setting up gvfs-common (1.16.1-0ubuntu1.1) ...
Setting up gvfs-libs:i386 (1.16.1-0ubuntu1.1) ...
Setting up gvfs-daemons (1.16.1-0ubuntu1.1) ...
Setting up gvfs:i386 (1.16.1-0ubuntu1.1) ...
Setting up gvfs-fuse (1.16.1-0ubuntu1.1) ...
Setting up gvfs-backends (1.16.1-0ubuntu1.1) ...
Setting up gvfs-bin (1.16.1-0ubuntu1.1) ...
Setting up libaudio2:i386 (1.9.3-5ubuntu0.13.04.1) ...
Setting up libdvdread4 (4.2.0+20121016-1ubuntu1.1) ...
Setting up xserver-common (2:1.13.3-0ubuntu6.1) ...
Setting up libglapi-mesa:i386 (9.1.7-1ubuntu2) ...
Setting up libgl1-mesa-dri:i386 (9.1.7-1ubuntu2) ...
Setting up xserver-xorg-core (2:1.13.3-0ubuntu6.1) ...
Setting up libgles2-mesa:i386 (9.1.7-1ubuntu2) ...
Setting up libgl1-mesa-glx:i386 (9.1.7-1ubuntu2) ...
Setting up libgbm1:i386 (9.1.7-1ubuntu2) ...
Setting up libegl1-mesa:i386 (9.1.7-1ubuntu2) ...
Setting up libopenvg1-mesa:i386 (9.1.7-1ubuntu2) ...
Setting up libegl1-mesa-drivers:i386 (9.1.7-1ubuntu2) ...
Setting up libgrip0 (0.3.6+13.04.20130711-0ubuntu1) ...
Setting up libicu48:i386 (4.8.1.1-12ubuntu0.1) ...
Setting up libpython2.7-minimal:i386 (2.7.4-2ubuntu3.2) ...
Setting up python2.7-minimal (2.7.4-2ubuntu3.2) ...
Setting up libpython2.7-stdlib:i386 (2.7.4-2ubuntu3.2) ...
Setting up python2.7 (2.7.4-2ubuntu3.2) ...
Setting up libpython2.7:i386 (2.7.4-2ubuntu3.2) ...
Setting up libqtwebkit4:i386 (2.3.0-0ubuntu2.1) ...
Setting up fonts-opensymbol (2:102.2+LibO4.0.4-0ubuntu1) ...
Setting up libreoffice-style-human (1:4.0.4-0ubuntu1) ...
Setting up libxatracker1:i386 (9.1.7-1ubuntu2) ...
Setting up lightdm (1.6.0-0ubuntu4) ...
Setting up python-gi (3.8.0-2ubuntu1) ...
Setting up python-gi-cairo (3.8.0-2ubuntu1) ...
Setting up software-center (5.6.0-0ubuntu3) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser-layer.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/sonic-visualiser:x-sonicvisualiser.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
WARNING:softwarecenter.db.update:The file: '/usr/share/app-install/desktop/workrave:workrave.desktop' could not be read correctly. The application associated with this file will not be included in the software catalog. Please consider raising a bug report for this issue with the maintainer of that application
Software catalog update was successful.
Setting up apt-utils (0.9.7.7ubuntu6) ...
Setting up initramfs-tools-bin (0.103ubuntu0.8) ...
Setting up initramfs-tools (0.103ubuntu0.8) ...
update-initramfs: deferring update (trigger activated)
Setting up apt-transport-https (0.9.7.7ubuntu6) ...
Setting up uuid-runtime (2.20.1-5.1ubuntu8.1) ...
Setting up python3-problem-report (2.9.2-0ubuntu8.4) ...
Setting up python3-apport (2.9.2-0ubuntu8.4) ...
Setting up apport (2.9.2-0ubuntu8.4) ...
apport start/running
Setting up gnome-terminal-data (3.6.1-0ubuntu4.1) ...
Setting up gnome-terminal (3.6.1-0ubuntu4.1) ...
Setting up apport-gtk (2.9.2-0ubuntu8.4) ...
Setting up libgnome-bluetooth11 (3.6.1-0ubuntu3.1) ...
Setting up gir1.2-gnomebluetooth-1.0 (3.6.1-0ubuntu3.1) ...
Setting up gnome-bluetooth (3.6.1-0ubuntu3.1) ...
Setting up glib-networking-common (2.36.2-0ubuntu0.1) ...
Setting up glib-networking-services (2.36.2-0ubuntu0.1) ...
Setting up glib-networking:i386 (2.36.2-0ubuntu0.1) ...
Setting up liblightdm-gobject-1-0 (1.6.0-0ubuntu4) ...
Setting up linux-libc-dev:i386 (3.8.0-32.47) ...
Setting up python-gobject (3.8.0-2ubuntu1) ...
Setting up vino (3.6.2-0ubuntu4.1) ...
Setting up xserver-xorg-video-intel (2:2.21.6-0ubuntu4.3) ...
Setting up xserver-xorg-video-savage (1:2.3.6-0ubuntu1.1) ...
Setting up unity-webapps-gmail (2.4.7.2) ...
Setting up ure (4.0.4-0ubuntu1) ...
Setting up uno-libs3 (4.0.4-0ubuntu1) ...
Setting up libreoffice-common (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-core (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-base-core (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-calc (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-gtk (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-gnome (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-writer (1:4.0.4-0ubuntu1) ...
Setting up python3-uno (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-pdfimport (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-math (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-draw (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-impress (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-ogltrans (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-l10n-en-gb (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-help-en-gb (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-help-en-us (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-l10n-es (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-help-es (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-l10n-en-za (1:4.0.4-0ubuntu1) ...
Setting up libreoffice-presentation-minimizer (1.0.4+LibO4.0.4-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-32-generic
Processing triggers for libreoffice-common ...

```

---

### Post by Bashing-om on 2013-10-15
juanchorobles; YES !

Let's now get a fresh update and see where we are !
Reboot and:

```

uname -r
df -h
dpkg -l | grep linux-image- 
dpkg -l | grep linux-headers-
ls -la /boot

```

Get your sunglasses on because 
[INDENT][INDENT][INDENT][INDENT]the future is so bright [/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-15
```

juancho@juancho-Satellite-C845:~$ uname -r
3.8.0-32-generic
juancho@juancho-Satellite-C845:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  457G   95G  339G  22% /
none                         4,0K     0  4,0K   0% /sys/fs/cgroup
udev                         940M  4,0K  940M   1% /dev
tmpfs                        190M  832K  189M   1% /run
none                         5,0M     0  5,0M   0% /run/lock
none                         949M  320K  948M   1% /run/shm
none                         100M   20K  100M   1% /run/user
/dev/sda1                    228M   78M  138M  37% /boot
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-image- 
ii  linux-image-3.8.0-30-generic              3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-31-generic              3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-32-generic              3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-30-generic        3.8.0-30.44                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-31-generic        3.8.0-31.46                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-32-generic        3.8.0-32.47                            i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                       3.8.0.32.50                            i386         Generic Linux kernel image
juancho@juancho-Satellite-C845:~$ dpkg -l | grep linux-headers-
ii  linux-headers-3.8.0-30                    3.8.0-30.44                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-30-generic            3.8.0-30.44                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                    3.8.0-31.46                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic            3.8.0-31.46                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                    3.8.0-32.47                            all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic            3.8.0-32.47                            i386         Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                     3.8.0.32.50                            i386         Generic Linux kernel headers
juancho@juancho-Satellite-C845:~$ ls -la /boot
total 75708
drwxr-xr-x  4 root root     2048 oct 15 16:44 .
drwxr-xr-x 23 root root     4096 oct 14 15:14 ..
-rw-r--r--  1 root root   926429 ago 22 15:26 abi-3.8.0-30-generic
-rw-r--r--  1 root root   926513 sep 10 14:28 abi-3.8.0-31-generic
-rw-r--r--  1 root root   926513 oct  1 16:08 abi-3.8.0-32-generic
-rw-r--r--  1 root root   160908 ago 22 15:26 config-3.8.0-30-generic
-rw-r--r--  1 root root   160908 sep 10 14:28 config-3.8.0-31-generic
-rw-r--r--  1 root root   160909 oct  1 16:08 config-3.8.0-32-generic
drwxr-xr-x  5 root root     1024 oct 14 15:15 grub
-rw-r--r--  1 root root 16695910 oct 14 15:14 initrd.img-3.8.0-30-generic
-rw-r--r--  1 root root 16699691 oct 14 15:15 initrd.img-3.8.0-31-generic
-rw-r--r--  1 root root 16702006 oct 15 16:44 initrd.img-3.8.0-32-generic
drwxr-xr-x  2 root root    12288 may 10 17:07 lost+found
-rw-r--r--  1 root root   176764 dic  5  2012 memtest86+.bin
-rw-r--r--  1 root root   178944 dic  5  2012 memtest86+_multiboot.bin
-rw-------  1 root root  2445814 ago 22 15:26 System.map-3.8.0-30-generic
-rw-------  1 root root  2445683 sep 10 14:28 System.map-3.8.0-31-generic
-rw-------  1 root root  2445627 oct  1 16:08 System.map-3.8.0-32-generic
-rw-------  1 root root  5373488 ago 22 15:26 vmlinuz-3.8.0-30-generic
-rw-------  1 root root  5372944 sep 10 14:28 vmlinuz-3.8.0-31-generic
-rw-------  1 root root  5375088 oct  1 16:08 vmlinuz-3.8.0-32-generic

```

---

### Post by Bashing-om on 2013-10-15
juanchorobles; By Golly .

All looks good .. !
In the future keep an eye on /boot and include cleaning it up with the light general house keeping.

If you agree, this I think concludes this situation that you had.

[INDENT][INDENT]whatcha think now ?
[/INDENT][/INDENT]

---

### Post by juanchorobles on 2013-10-16
yeah! i think everything is ok now!!  thanks for all your help!!!

---

### Post by Bashing-om on 2013-10-16
juanchorobles; Hey !

You are quite welcome; Keep in mind this is open source and ubuntu at it's best; We are all in this together. Thanks also to Jonathon and all the others who give of the time and knowledge.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by glamont-frontiernet on 2013-11-19
I had similar problems with an update of Libreoffice.  I'm more GUI oriented.  I used the Janitor from Ubuntu Tweak to clean up my system and it got rid of the whatever-it-was that was hanging things up.
Thanx,
Gavin

---

