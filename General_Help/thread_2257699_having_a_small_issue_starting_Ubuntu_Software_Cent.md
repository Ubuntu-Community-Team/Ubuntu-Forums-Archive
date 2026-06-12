---
title: "having a small issue starting Ubuntu Software Center"
date: 2014-12-21
forum: General Help
---

### Post by tcll5850 on 2014-12-21
the issue:
```

tcll@tcll-AY589AAR-ABA-a4317c:~$ software-center
ERROR:root:DebFileApplication import
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/__init__.py", line 4, in <module>
    from debfile import DebFileApplication, DebFileOpenError
  File "/usr/share/software-center/softwarecenter/db/debfile.py", line 25, in <module>
    from softwarecenter.db.application import Application, AppDetails
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 199, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 174, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named zorin
Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 54, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 199, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 174, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named zorin

```
this has been ever since I upgraded from zorin to ubuntu 14.04 before installing xubuntu-desktop...
but the software center has been working since just now...

I've tried $ sudo apt-get install --reinstall software-center
but of course that did nothing... heh


what else can I do??

thanks :)

EDIT:
before this gets mentioned, I don't want to reinstall, I'm asking what to do so I can avoid that.

---

### Post by TheFu on 2014-12-22
Try using gksudo.

---

### Post by tcll5850 on 2014-12-22
```
tcll@tcll-AY589AAR-ABA-a4317c:~$ gksudo software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 128, in <module>
    from softwarecenter.ui.gtk3.app import SoftwareCenterAppGtk3
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 54, in <module>
    from softwarecenter.db.application import Application
  File "/usr/share/software-center/softwarecenter/db/application.py", line 28, in <module>
    import softwarecenter.distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 199, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 174, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named zorin
tcll@tcll-AY589AAR-ABA-a4317c:~$
```

I need to remove the link to that non-existant zorin module.
and recently, everything's been thinking I've installed zorin when I havn't

where's all the text links for this so I can change them to xubuntu??

---

### Post by Yellow Pasque on 2014-12-22
I wonder if you somehow got a version of lsb-release package from zorin. Check:

```
lsb_release -a
sudo python /usr/lib/python2.7/dist-packages/lsb_release.py
apt-cache policy lsb-release
```

---

### Post by tcll5850 on 2014-12-22
WOW!
nice call...

```
tcll@tcll-AY589AAR-ABA-a4317c:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Zorin
Description:	Zorin OS 9
Release:	9
Codename:	trusty
tcll@tcll-AY589AAR-ABA-a4317c:~$ sudo python /usr/lib/python2.7/dist-packages/lsb_release.py
[sudo] password for tcll: 
{'RELEASE': '9', 'CODENAME': 'trusty', 'ID': 'Zorin', 'DESCRIPTION': 'Zorin OS 9'}
[]
tcll@tcll-AY589AAR-ABA-a4317c:~$ apt-cache policy lsb-release
lsb-release:
  Installed: 4.1+Debian11ubuntu6
  Candidate: 4.1+Debian11ubuntu6
  Version table:
 *** 4.1+Debian11ubuntu6 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

but how O.o

ok... how do I remove this??

---

### Post by Yellow Pasque on 2014-12-22
I suspect you still have zorin sources in apt. Look at your /etc/apt/sources.d/ files. I'd also suggest Synaptic as an alternative until you get Software Center running again.
```
sudo apt-get install synaptic
```

---

### Post by tcll5850 on 2014-12-22
thanks :)
just for the note, .../sources.list.d/ ;)

and yea, I've found what I guess is some leftovers when I upgraded to ubuntu14

- zorin-os-packages-precise.list
- zorin-os-packages-precise.list.distUpgrade
- zorin-os-packages-precise.list.save
- zorin-os-packages-trusty.list
- zorin-os-packages-trusty.list.save

I'd assume simply deleting these might break a few things that I'd have to remove manually...
how could I "purge" these??

oh heck Synaptic is already installed, thanks anyways. XD
let's check this out :3

EDIT:
don't answer my Q, as I believe that was your recommendation :P

---

### Post by tcll5850 on 2014-12-24
so apparently removing and reinstalling software-center doesn't work... I still get the error:
```
Traceback (most recent call last):
  File "/usr/sbin/update-software-center", line 38, in <module>
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 33, in <module>
    from softwarecenter.backend.scagent import SoftwareCenterAgent
  File "/usr/share/software-center/softwarecenter/backend/scagent.py", line 28, in <module>
    from softwarecenter.distro import get_distro, get_current_arch
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 199, in <module>
    distro_instance = _get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 174, in _get_distro
    module = __import__(distro_module_name, globals(), locals(), [], -1)
ImportError: No module named zorin
```

I've removed most everything required by Zorin PPAs with synaptic package manager...

I'm lost...
idk what to do -_-

---

### Post by Yellow Pasque on 2014-12-24
Hm. I guess lsb-release pulls information from files in base-files package, so let's look at output of:
```
apt-cache policy base-files
cat /etc/lsb-release
```

---

### Post by tcll5850 on 2014-12-24
```
tcll@tcll-AY589AAR-ABA-a4317c:~$ apt-cache policy base-files
base-files:
  Installed: 7.2zorin1
  Candidate: 7.2zorin1
  Version table:
 *** 7.2zorin1 0
        500 http://ppa.launchpad.net/zorin-os/packages/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
     7.2ubuntu5.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     7.2ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
tcll@tcll-AY589AAR-ABA-a4317c:~$ cat /etc/lsb-release
DISTRIB_ID=Zorin
DISTRIB_RELEASE=9
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Zorin OS 9"
tcll@tcll-AY589AAR-ABA-a4317c:~$ 

```

yea it's so tightly integrated, even my error messages report zorin...
it should report xubuntu or ubuntu

if I could apt-get remove, what would I remove??

---

### Post by TheFu on 2014-12-24
format c:

---

### Post by tcll5850 on 2014-12-24
@TheFu:
> **tcll5850 said:**
> before this gets mentioned, I don't want to reinstall, I'm asking what to do so I can avoid that.

I have a zorin 6 (Ubuntu 12.04) installation, which means it will take me 3 days to set everything up after upgrading to Ubuntu14.04, 
and another 2-3 days to customize everything on XFCE. (not calculating rest time or sleep)

my people can't wait for that.
I'm going to avoid formatting, and just fix the issues I have. (as they ARE fixable (Linux is far from the limited interface Windows offers))
I'd only reinstall if my kernel corrupted.

---

### Post by Yellow Pasque on 2014-12-24
There's your problem: the base-files package is from zorin. You need to switch to the ubuntu version. I have no idea if you're using anything from zorin sources, but synaptic makes it easy to figure that out. If you're not using zorinf packages, then get rid of the zorin sources and switch to ubuntu packages for any local/obsolete packages installed.

---

### Post by tcll5850 on 2014-12-24
O.o
I thought I did that...

ok...
what do I have to do there??

I've uninstalled everything used by the zorin PPAs except for what might render my compy unusable
(as stated earlier) :P

so, just...
how do I switch?? :/

EDIT:
oh wait, I wasn't connecting "base-files" as the actual thing from the ppa...
yea, how do I switch that??

---

### Post by raptir on 2014-12-24
You should be able force it to install the version from the Ubuntu repository.

```
sudo apt-get reinstall -t trusty base-files
```

I've only tried that with the install command for a non-installed package though, so I'm not sure how it will work with the reinstall command.

---

### Post by TheFu on 2014-12-24
When it comes to stuff like this, you can use **aptitude** (not apt-get) and often it will find issues and solutions to the dependencies better than any of the other programs. Be certain to remove any zorin packages before removing them from the APT sources.

OTOH, if this machine is important, spend the 45 min to backup everything important, then perform a fresh install (15 min) and restore the data, settings and packages without any zorin dependencies.  1st time, takes about an hour, and every other time it gets shorter and shorter ... I'm down to 30 min for a system restore now with a fresh OS, but all my programs, data and settings from any backup in the last 60days.  [http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview)

---

### Post by tcll5850 on 2014-12-25
still fails...

lemme use a little of my debug skills...

    module = __import__(distro_module_name, globals(), locals(), [], -1)

where:
>>> print distro_module_name
'zorin'

where does the 'zorin' string come from, and how can I change the source to 'ubuntu'??
because it should be either 'ubuntu' [color=gray](as this was an upgrade from [Zorin OS 6 (Ubuntu 12.04)] to [Ubuntu 14.04])[/color] or 'xubuntu' [color=gray](as I've installed xubuntu-desktop)[/color]

---

### Post by TheFu on 2014-12-27
I've never heard of anyone mixing distros like this, hence why the recommendation to fresh-install, then migrate the data and settings.  Sorry that you don't like it.  You are in completely new land going backwards Zorin-->Ubuntu.

If you solve it, please post a how-to for the other people who may be interested.

The way that I would attack this (assuming I wanted to know about the differences), is by performing 2 installations which I believe to be identical, just using Zorin and the equivalent Ubuntu.  Then perform a complete comparison between these two installations to see which files are different.  I would completely ignore /home and primarily worry about /etc, /var, and /usr .... binary file differences will likely happen just because there are newer versions of programs between the release dates for each.  Of course, if your specific installation had lots and lots of extra tools loaded, then the differences will be much greater.

If you don't want to be in this to do it 100 times, seriously, I'd just perform a fresh Ubuntu install and restore the settings, data and previously installed programs - about an hour of effort.  Be certain to NOT use the zorin sources in /etc/apt/ at all.

Good luck!

---

### Post by tcll5850 on 2014-12-27
I think I may have found the problem:
sudo add-apt-repository ppa:zorin-os/packages

this might be what's giving me zorin 9

last I tried that it failed...
though apparently not O.o

what I was trying to achieve there was a DE that would span both of my monitors...
that's when I found XFCE as the final

so I'm running 'apt-purge ppa:zorin-os/packages' as we speak :)

and plan to re-run 'sudo aptitude reinstall -t trusty base-files', which should fix everything ;)

EDIT:
```
tcll@tcll-AY589AAR-ABA-a4317c:~$ sudo aptitude reinstall -t trusty base-files
[sudo] password for tcll: 
The following packages will be REINSTALLED:
  base-files 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 5 not upgraded.
Need to get 0 B/70.2 kB of archives. After unpacking 0 B will be used.
(Reading database ... 423503 files and directories currently installed.)
Preparing to unpack .../base-files_7.2ubuntu5.1_amd64.deb ...
Unpacking base-files (7.2ubuntu5.1) over (7.2ubuntu5.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for cracklib-runtime (2.9.1-1build1) ...
Processing triggers for plymouth-theme-ubuntu-text (0.8.8-0ubuntu17.1) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-43-generic
Setting up base-files (7.2ubuntu5.1) ...
```

YAY!
last time I ran that, (7.2ubuntu5.1) was a zorin package.

let's see if software center works now =D

EDIT2: YES!
thanks for your help from earlier or I'd've never have figured it out! =3

---

