---
title: "Serious, show-stopping Synaptic error"
date: 2007-03-11
forum: General Help
---

### Post by Redeyes_Gambit on 2007-03-11
First of all, thank you to anyone who has taken the time to drop in on this little post :) . The support of these forums is what has made Ubuntu great, and without the support of the community (YES YOU!) it wouldn't be near what it is today.

OK, on to my issue:

I installed VMWare player through Automatix, but apparently it didn't complete the install fully (Edit: jackrobinson points out this is not Automatix's fault, but rather that the VMWare player in the Ubuntu Multiverse is busted.). Now every time I launch Synaptic and try to install something it tries (unsuccessfully) to finish installing VMWare Player. It blocks the installation of everything else and I cannot remove VMWare Player because Synaptic wants to finish installing it first.

I cannot remove VMWare player through Automatix because it fails as well.

I cannot use the .tar file of VMWare player to remove VMWare player because it won't remove the .deb version.

I cannot install the .tar version of VMWare player until the .deb version is removed.

I cannot install any .deb package, update my computer, or use Synaptic or apt-get until I chunk the partial VMWare Player and Apt can get on with its little life. Thus I think you can see why I am just a tad unsettled ;) .

A speedy reply would be appreciated beyond words.

---

### Post by jackrobinson on 2007-03-11
post the result of the following command:
```
sudo apt-get remove vmware-player
```
it was not automatix. The vmware-player package in Ubuntu multiverse has been broken since ages and no one has fixed it. automatix simply pulls it from the official ubuntu repos.

---

### Post by xopher on 2007-03-11
[flame]DON'T USE AUTOMATIX :GRR:[/flame]

Well, basically what you need to do, is force the removal of vmware-player, alternatively force the install.

First you could try to do a: ```
sudo dpkg --configure -a
```

If that doesn't help, try forcing the removal of it:

```
sudo dpkg --purge --force-all <packagename>
```

(you should read more about the different force options: dpkg --force-help)

---

### Post by Redeyes_Gambit on 2007-03-11
Lol, good to know. Chances are I would have gotten this fixed and tried to re-install it through Synaptic ROFL.

```

greg@ubuntu-laptop:~$ sudo apt-get remove vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151947 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Edit:

Sorry if my phrasing made it sound like I was blaming Automatix. I really love Automatix and count it among the best tools one can install on Ubuntu. I simply figured it was Automatix since that is how I installed VMWare player. I shall happily adjust the phrasing of my above post to better reflect my intentions.

Edit2:

Ahh, thanks for the tip Xopher! I figured there had to be a force option somewhere.

---

### Post by jackrobinson on 2007-03-11
> **Redeyes_Gambit said:**
> Lol, good to know. Chances are I would have gotten this fixed and tried to re-install it through Synaptic ROFL.

```

greg@ubuntu-laptop:~$ sudo apt-get remove vmware-player
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  vmware-player
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  vmware-player
0 upgraded, 0 newly installed, 1 to remove and 12 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 32.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151947 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--remove):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
do the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo apt-get remove vmware-player
```
The Automatix Forum is a good place to ask automatix related questions:
http:://www.getautomatix.com/forum

---

### Post by fdrake on 2007-03-11
did you install the vmware player's kernel modules first. vmware is dependent on this package. you have to install first the modules first to install the player .

---

### Post by fdrake on 2007-03-11
try this:
sudo apt-get install vmware-player-kernel-modules-2.6.17-10
sudo aptitude reinstall vmware-player

---

### Post by jackrobinson on 2007-03-11
> **fdrake said:**
> try this:
sudo apt-get install vmware-player-kernel-modules-2.6.17-10
sudo aptitude reinstall vmware-player

apt-get is broken. unless the offending package is removed, nothing new can be installed or removed.

---

### Post by Redeyes_Gambit on 2007-03-11
Hm, it appears there is no joy in mudville. The force option did not work. VMWare player is still there :( .

```

greg@ubuntu-laptop:~$ sudo dpkg --purge --force-all vmware-player
(Reading database ... 151947 files and directories currently installed.)
Removing vmware-player ...
Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                   failed
invoke-rc.d: initscript vmware-player, action "stop" failed.
dpkg: error processing vmware-player (--purge):
 subprocess pre-removal script returned error exit status 1
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                          done
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player

```

Is my syntax incorrect?

Edit:

jackrobinson is correct. I cannot add the vmware-player-kernel-modules-2.6.17-10 because apt is ker-busticated. However they were installed already anyway. Thanks for the suggestion!

---

### Post by Tobster on 2007-03-11
I had the same problem... this is my forum were the Ubuntu Gods help me  :):popcorn: 

Prob best to go towards the end....  You need to re-install the Source code and save it then it will work again.  The link to my forum is:

[http://www.ubuntuforums.org/showthread.php?t=350295&highlight=source](http://www.ubuntuforums.org/showthread.php?t=350295&highlight=source)

Toby

---

### Post by fdrake on 2007-03-11
?
sudo aptitude install vmware-player-kernel-modules-2.6.17-10

---

### Post by jackrobinson on 2007-03-11
> **Redeyes_Gambit said:**
> Hm, it appears there is no joy in mudville. The force option did not work. VMWare player is still there :( 
just follow my instructions in post#5.

---

### Post by Redeyes_Gambit on 2007-03-11
> **jackrobinson said:**
> do the following:
```
sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm
sudo apt-get remove vmware-player
```
The Automatix Forum is a good place to ask automatix related questions:
http:://www.getautomatix.com/forum

That did it! VMWare Player removed. Many, many, many thanks!

---

### Post by Redeyes_Gambit on 2007-03-11
Op, just noticed something. Automatix isn't working now. Tried re-installing, removing then re-installing, completely removing and re-installing... Nothing. When I launch automatix I get this:

```

greg@ubuntu-laptop:~$ automatix2
Starting
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 68, in ?
    main = main_ui()
  File "/usr/lib/automatix2/main_interface.py", line 12, in __init__
    self.build_interface()
  File "/usr/lib/automatix2/main_interface.py", line 50, in build_interface
    self.generate_menus()
  File "/usr/lib/automatix2/main_interface.py", line 104, in generate_menus
    self.generate_catalog_model()
  File "/usr/lib/automatix2/main_interface.py", line 365, in generate_catalog_model
    icon= gtk.gdk.pixbuf_new_from_file(list.icon)
gobject.GError: Failed to open file '/usr/share/icons/Tango/24x24/devices/multimedia-player-ipod-video-black.png': No such file or directory
greg@ubuntu-laptop:~$ 

```

I would post on the automatix forums but they are having issues currently (server 500 errors)

Could this have been caused by our little  

"sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm" ?

---

### Post by jackrobinson on 2007-03-12
> **Redeyes_Gambit said:**
> Op, just noticed something. Automatix isn't working now. Tried re-installing, removing then re-installing, completely removing and re-installing... Nothing. When I launch automatix I get this:

```

greg@ubuntu-laptop:~$ automatix2
Starting
Traceback (most recent call last):
  File "/usr/bin/automatix.py", line 68, in ?
    main = main_ui()
  File "/usr/lib/automatix2/main_interface.py", line 12, in __init__
    self.build_interface()
  File "/usr/lib/automatix2/main_interface.py", line 50, in build_interface
    self.generate_menus()
  File "/usr/lib/automatix2/main_interface.py", line 104, in generate_menus
    self.generate_catalog_model()
  File "/usr/lib/automatix2/main_interface.py", line 365, in generate_catalog_model
    icon= gtk.gdk.pixbuf_new_from_file(list.icon)
gobject.GError: Failed to open file '/usr/share/icons/Tango/24x24/devices/multimedia-player-ipod-video-black.png': No such file or directory
greg@ubuntu-laptop:~$ 

```

I would post on the automatix forums but they are having issues currently (server 500 errors)

Could this have been caused by our little  

"sudo rm -f /var/lib/dpkg/info/vmware-player.postrm
sudo rm -f /var/lib/dpkg/info/vmware-player.prerm" ?
do the following:
```
sudo apt-get update
sudo apt-get upgrade

```
and now run automatix2

---

### Post by tinyneutrino on 2007-03-19
I've never had a Synaptic problem before (4 years with Ubuntu Gnome) - Today I installed the latest on a friends' desktop and the Synaptic won't show the repositories. When I hit "Settings-Repositories"  it will only open up the "Properties" gui.

My sources.list is fine, I get all my repositories and updates no problem and can aptitude, apt, dpkg, anyway.....get my packages, but I can't edit lists through Synaptic.

I was wondering if anyone else has come across this problem.  I've removed Synaptic and reinstalled but the same problem occurred.

---

