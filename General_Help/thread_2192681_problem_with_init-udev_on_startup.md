---
title: "problem with init-udev on startup"
date: 2013-12-09
forum: General Help
---

### Post by slgtheindividual on 2013-12-09
Ok so when I start up ubuntu now I get an error message which says something like

"scripts/init-udev/line 21/ nuke not found"

(I'm not sure exactly as it only shows up briefly) also after logging in I get a blank black screen for quite a while before it shows me my desktop.

I get the feeling this is all related to a (now fixed) problem I was having

[http://ubuntuforums.org/showthread.php?t=2187724](http://ubuntuforums.org/showthread.php?t=2187724)

any help would be greatly appreciated.

---

### Post by slgtheindividual on 2013-12-11
actually I made a mistake, it says "[COLOR=#000000]scripts/init-bottom/udev/line 21/ nuke not found"

[/COLOR]

---

### Post by Bashing-om on 2013-12-11
slgtheindividual; Hello, once more .

Let's see if this is the control file in question, and if there is a problem with it:
```

cat -n /usr/share/initramfs-tools/scripts/init-bottom/udev

```

[INDENT][INDENT]strange things do happen
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-12
hello again and thank you for your help again

```
~$ cat -n /usr/share/initramfs-tools/scripts/init-bottom/udev     1	#!/bin/sh -e
     2	
     3	PREREQS=""
     4	
     5	prereqs() { echo "$PREREQS"; }
     6	
     7	case "$1" in
     8	    prereqs)
     9	    prereqs
    10	    exit 0
    11	    ;;
    12	esac
    13	
    14	# Stop udevd, we'll miss a few events while we run init, but we catch up
    15	udevadm control --exit
    16	
    17	# move the /dev tmpfs to the rootfs
    18	mount -n -o move /dev ${rootmnt}/dev
    19	
    20	# create a temporary symlink to the final /dev for other initramfs scripts
    21	nuke /dev
    22	ln -s ${rootmnt}/dev /dev
    23	

```

---

### Post by Bashing-om on 2013-12-12
slgtheindividual' Welp,

Looks like someone has been editing system files !
Line 21 does not look like anything I have ever seen before.

Did you make a backup of the file prior to editing ? 
NO ??
Remind me once more what version you have installed:
```

lsb_release -a
uname -a

```

Version 13.04 looks like this:
> 
sysop@1304mini:~$ cat -n /usr/share/initramfs-tools/scripts/init-bottom/udev
     1  #!/bin/sh -e
     2  # initramfs init-bottom script for udev
     3
     4  PREREQ=""
     5
     6  # Output pre-requisites
     7  prereqs()
     8  {
     9          echo "$PREREQ"
    10  }
    11
    12  case "$1" in
    13      prereqs)
    14          prereqs
    15          exit 0
    16          ;;
    17  esac
    18
    19
    20  # Stop udevd, we'll miss a few events while we run init, but we catch up
    21  udevadm control --timeout=121 --exit || \
    22                echo "udev exit failed -- rc=$?"
    23
    24  # Move /dev to the real filesystem
    25  mount -n -o move /dev ${rootmnt}/dev
sysop@1304mini:~$


Looks like we are hitting close to home !

[INDENT][INDENT]got it by the tail
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-13
I'm not saying you're wrong, but I never edited that file (I tend not to mess with stuff when I don't know what it does lol) so I have no idea what happened.

Anyway here's the output:

```

~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
~$ uname -a
Linux slg-Aspire-E1-571 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64 GNU/Linux

```

---

### Post by Bashing-om on 2013-12-13
slgtheindividual; Hey !

Strange things happen !

Lemme have a bit to get caught up on the forum and I will (RE-)boot into my 13.10 install and see what that files looks like there.
(need to do the updates on that install, anyway)

[INDENT][INDENT]I'll Be Bacckk
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-13
slgtheindividual; I am back.

Now a bit of uncertaintly do exist:
Here is my 13.10 "udev" file:
```

sysop@1304mini:~$ cat -n /mnt/backup/udev-1310
     1  #!/bin/sh -e
     2
     3  PREREQS=""
     4
     5  prereqs() { echo "$PREREQS"; }
     6
     7  case "$1" in
     8      prereqs)
     9      prereqs
    10      exit 0
    11      ;;
    12  esac
    13
    14  # we cannot properly synthesize LVM LV change events with udevadm trigger, so
    15  # if we use LVM, we need to let it finish; otherwise we get missing LV symlinks
    16  # (LP #1185394)
    17  if [ -x /sbin/vgchange ]; then
    18      udevadm settle --timeout=121 || true
    19  fi
    20
    21  # Stop udevd, we'll miss a few events while we run init, but we catch up
    22  udevadm control --timeout=121 --exit || \
    23              echo "udev exit failed -- rc=$?"
    24
    25  # move the /dev tmpfs to the rootfs
    26  mount -n -o move /dev ${rootmnt}/dev
    27
    28  # create a temporary symlink to the final /dev for other initramfs scripts
    29  rm -rf /dev
    30  ln -s ${rootmnt}${udev_root} /dev
    31
sysop@1304mini:~$ 

```

And too confuse matters more: this is 12.04's ;
```

sysop@1304mini:~$ cat -n /mnt/backup/udev-1204
     1  #!/bin/sh -e
     2  # initramfs init-bottom script for udev
     3
     4  PREREQ=""
     5
     6  # Output pre-requisites
     7  prereqs()
     8  {
     9          echo "$PREREQ"
    10  }
    11
    12  case "$1" in
    13      prereqs)
    14          prereqs
    15          exit 0
    16          ;;
    17  esac
    18
    19
    20  # Stop udevd, we'll miss a few events while we run init, but we catch up
    21  udevadm control --timeout=121 --exit || \
    22          echo "udev exit failed -- rc=$?"
    23
    24  # Move /dev to the real filesystem
    25  mount -n -o move /dev ${rootmnt}/dev
sysop@1304mini:~$

```

-------------
Let's do this .. pending advisement from those of greater knowledge:
make a back up of the current "udev" file:
```

sudo cp /usr/share/initramfs-tools/scripts/init-bottom/udev /usr/share/initramfs-tools/scripts/init-bottom/udev-old

```
Now let's edit the file;
make line 21 and 22 like so:
```

 rm -rf /dev
 ln -s ${rootmnt}${udev_root} /dev

``` in the favorite text editor "gedit"; in accord with what my 13.10 install has.
```

gksudo gedit /usr/share/initramfs-tools/scripts/init-bottom/udev

```
save the file, exit back to terminal, reboot and see what happends.

OK, all looking good, now let's see what the package manager says:
```

sudo apt-get update
sudo apt-get upgrade

```
AND post back IF there are errors in the package management system. Still looking good ?
Once more (RE-)Boot, and tell me all is "finer than a frogs hair" !

[INDENT][INDENT]that's what I think
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-13
ok after editing the file I'm still getting the exact same error at startup and black screen.

---

### Post by slgtheindividual on 2013-12-13
also I tried to run an update after restarting but it stops at ```
 Ign http://gb.archive.ubuntu.com saucy-backports/universe Translation-en_GB100% [Waiting for headers] 
```

---

### Post by Bashing-om on 2013-12-13
slgtheindividual; Well, that ain't good !

Did something rewrite the file ?
What now is in it ?
```

cat /usr/share/initramfs-tools/scripts/init-bottom/udev

```

Don't know presently, but
[INDENT][INDENT]this may get deep
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-13
I don't think the file reverted:

```

~$ cat /usr/share/initramfs-tools/scripts/init-bottom/udev#!/bin/sh -e


PREREQS=""


prereqs() { echo "$PREREQS"; }


case "$1" in
    prereqs)
    prereqs
    exit 0
    ;;
esac


# Stop udevd, we'll miss a few events while we run init, but we catch up
udevadm control --exit


# move the /dev tmpfs to the rootfs
mount -n -o move /dev ${rootmnt}/dev


# create a temporary symlink to the final /dev for other initramfs scripts
rm -rf /dev
ln -s ${rootmnt}${udev_root} /dev

```

---

### Post by Bashing-om on 2013-12-13
slgtheindividual; Well, 
And at boot up you are still getting:
 "scripts/init-bottom/udev/line 21/ nuke not found" ??

AND the graphics driver is not loading ??
AND the package manager is not in a happy state ??

Maybe we are dealing now with more than one issue (??)

[INDENT][INDENT]sometimes I wonder -> othertimes ??
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-14
slgtheindividual; Hey ,

I am done for this session. Will take this back up later later in my AM.

take care 'till
[INDENT][INDENT]then[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-14
Yeah that's right, still the same error and still takes a while to start up after logging in. No problem, thank you for the help.

---

### Post by steeldriver on 2013-12-14
Some googling suggests there was at one point a debian bug (Bug#719914) opened that might have been relevant - but it seems to be a dead end

[http://lists.debian.org/debian-kernel/2013/09/msg00215.html](http://lists.debian.org/debian-kernel/2013/09/msg00215.html)

I can't understand much from that thread - possibly that the bug was opened wrongly against the initramfs-tools package and then punted when the maintainers of that package disowned it?

And yes I do think it is very likely related to your other thread about udev / procps packages

---

### Post by Bashing-om on 2013-12-14
cogitating !

---

### Post by Bashing-om on 2013-12-14
slgtheindividual; Still cogitating !
As though it is part of /usr/share/initramfs-tools, the scripts/init-bottom/udev is part of the udev package.
Let's look:
```

dpkg -l udev

```
and see where that leads us.

I am think'n and look'n

---

### Post by steeldriver on 2013-12-14
A good tack I think, Bashing-om - it might also be instructive to try

```
$ dpkg-query -S '/usr/share/initramfs-tools/scripts/init-bottom/'
```

which *I think* attempts to show *all* packages which have a claim on the file (a kind of reverse lookup version of what you're suggesting)

---

### Post by slgtheindividual on 2013-12-14
ok cool well I did both of those:

```

~$ dpkg -l udev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  udev           204-5        amd64        /dev/ and hotplug management daem
slg@slg-Aspire-E1-571:~$ dpkg -l udev
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-=================================================
ii  udev                   204-5            amd64            /dev/ and hotplug management daemon
~$ dpkg-query -S '/usr/share/initramfs-tools/scripts/init-bottom/'
plymouth, udev: /usr/share/initramfs-tools/scripts/init-bottom




```#

thank you both again for the help

---

### Post by Bashing-om on 2013-12-14
slgtheindividual; UNgood.

This is the version you should have installed to the system:
> 
You have searched for packages that names contain udev in suite(s) saucy-updates, all sections, and all architectures. Found 9 matching packages.

Exact hits

Package udev

saucy-updates (admin): /dev/ and hotplug management daemon 
204-0ubuntu19: amd64 i386


BUT, you have trustie's version installed !

It is back to studying how to downgrade "udev" to the proper version !

What have we got on the system to work with ?
```

ls -la /var/cache/apt/archives/ | grep udev

```
[INDENT]gotta start somewhere
[/INDENT]

---

### Post by slgtheindividual on 2013-12-14
I wonder why I have an old version?

I ran that and it just returned nothing 

```

~$ ls -la /var/cache/apt/archives/ | grep udev
~$ 

```

---

### Post by Bashing-om on 2013-12-14
slgtheindividual;

What you have installed is a newer version - not completely compatible.
As the file is not presently on your system, we can "wget" it.

Let me have a bit of time to review the other thread, and maybe get an idea as to what is going on;
Review a means to downgrade "udev" to the proper version.

[INDENT][INDENT]I'll be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-15
slgtheindividual; Update;

Have not to this time had the time for due consideration - my iron in many fires.
Following stelldriver's direction though, what returns from:
```

dpkg -l plymouth

```
Try'n to keep all our ducks in one row.

[INDENT][INDENT]think twice
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-15
that's ok, no problem.

ok I get the following:

```

~$ dpkg -l plymouth
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
ii  plymouth                        0.8.8-0ubuntu8       amd64                graphical boot animation and logger - main package

```

---

### Post by Bashing-om on 2013-12-15
slgtheindividual; Well;

Plymouth looks to be the correct version for saucy. 

I am getting closer to where I can focus on this.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-15
I guess we could start by looking at what ppas are active

```
grep -Er '^deb https?://ppa' /etc/apt/
```

and maybe

```
grep -r 'trusty' /etc/apt/
```

---

### Post by slgtheindividual on 2013-12-15
ok cool well that gives me 

```

~$ grep -Er '^deb https?://ppa' /etc/apt/
/etc/apt/sources.list.d/nvbn-rm-ppa-saucy.list.save:deb http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu saucy main
/etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main
/etc/apt/sources.list.d/nvbn-rm-ppa-saucy.list:deb http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu saucy main
/etc/apt/sources.list.d/ubuntu-wine-ppa-saucy.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main
grep: /etc/apt/trustdb.gpg: Permission denied
grep: /etc/apt/auth.conf: Permission denied

```

and then

```

~$ grep -r 'trusty' /etc/apt/
grep: /etc/apt/trustdb.gpg: Permission denied
grep: /etc/apt/auth.conf: Permission denied

```

but oddly, when I then run

```

~$ sudo !!
sudo grep -r 'trusty' /etc/apt/
[sudo] password: 
~$ 

```

---

### Post by Bashing-om on 2013-12-15
slgtheindividual; OK !

This Looks to be a continuation of that other thread.


> 
~$ dpkg -l procps udev libudev1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                   Version          Architecture     Description
+++-======================-================-================-=================================================
ii  libudev1:amd64         204-5            amd64            libudev shared library
ii  libudev1:i386          204-5            i386             libudev shared library
ii  procps                 1:3.3.3-2ubuntu9 amd64            /proc file system utilities
ii  udev                   204-5            amd64            /dev/ and hotplug management daemon


Let's see if any thing has changed:
Once more, what is the output of:
```

dpkg -l procps udev libudev1

```

We still looking at the 3rd party PPAs messing with us ? .. will see directly. For now let's see what versions are what.

[INDENT][INDENT]and away we go again
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-15
ok well here that is:

```

~$ dpkg -l procps udev libudev1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
ii  libudev1:amd64                  204-5                amd64                libudev shared library
ii  libudev1:i386                   204-5                i386                 libudev shared library
ii  procps                          1:3.3.3-2ubuntu9     amd64                /proc file system utilities
ii  udev                            204-5                amd64                /dev/ and hotplug management daemon

```

---

### Post by Bashing-om on 2013-12-15
Et al;
Sorry to have missed the steeldriver interjections.
Playing catchup.
Package versions should be; Per:
[http://packages.ubuntu.com/search?keywords=libudev1&searchon=names&suite=saucy-updates&section=all](http://packages.ubuntu.com/search?keywords=libudev1&searchon=names&suite=saucy-updates&section=all)
> 
Package udev
saucy-updates (admin): /dev/ and hotplug management daemon 
204-0ubuntu19: amd64 i386
XXXXX
Package libudev1
saucy-updates (libs): libudev shared library 
204-0ubuntu19: amd64 i386
XXXXX
Package procps
saucy-updates (admin): /proc file system utilities 
1:3.3.3-2ubuntu9: amd64 i386
##which is correct !


Which once more, begs the question, What is driving the installation of later/incompatible versions ? I do not see it presently in any of the software sources.
Open to suggestions !

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-16
even though we don't know what is causing the later packages to be installed is it possible to revert to the current package without breaking anything? Also, theoretically, since my package is a later one, if I were to just wait long enough would my package become the current one, with the error resolved?

---

### Post by Bashing-om on 2013-12-16
slgtheindividual; Welp;

As far as waiting for the packaging to catch up with what is installed.. That will only happen if you choose to upgrade to trusty.

What I have in mind presently is to downgrade those elevated packages to what saucy uses. As I do not know what caused the elevation to start with, Do not know what might break when we downgrade.

We will do this s l o w l y and carefully /// Disable the 3rd party sources... do the downgrades, update/upgrade the system with the 3rd party sources still not enabled, then ->
one at a time (re)enable a 3rd party source, see if anything breaks. run update/upgrade again, see if anything breaks, enable next 3rd party source -> repeat as often as it takes to see if anything does break and where (keeping a sharp eye on the packages that were downgraded to be consistent with suacy).

I know of nothing better to do at this time... We can wait and see if other wiser heads have a better option.

One thing for sure, got to make the package manager happy.


[INDENT][INDENT]If the package manager is not happy
[INDENT][INDENT][INDENT][INDENT]then nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-16
step by step sounds fine to me, hopefully nothing will break. What's first?

---

### Post by Bashing-om on 2013-12-16
slgtheindividual; OK,

Disable all 3rd party sources in Software Center -> other software;
```

sudo apt-get install udev=204-0ubuntu19
sudo apt-get install libudev1=204-0ubuntu19
sudo apt-get update
sudo apt-get upgrade

```
Check:
```

dpkg -l procps udev libudev1

```
All versions holding to "suacy ?

OK, now begin enabling the 3rd party sources - one at a time;
and see what results;
```

sudo apt-get update
sudo apt-get upgrade
dpkg -l procps udev libudev1

``` after enabling a source.

Let's see what happens.

[INDENT][INDENT]maybe yes,
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-17
Ok so I disabled all 3rd party PPA's then tried to install the two packages but both had dependency issues:

```

~$ sudo apt-get install udev=204-0ubuntu19
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 udev : Depends: libudev1 (= 204-0ubuntu19) but 204-5 is to be installed
E: Unable to correct problems, you have held broken packages.

~$ sudo apt-get install libudev1=204-0ubuntu19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libgphoto2-port10:i386 : Depends: libusb-1.0-0:i386 (>= 2:1.0.8) but it is not going to be installed
 libsane : Depends: udev (>= 0.88-1)
 libsane:i386 : Depends: udev:i386 (>= 0.88-1)
                Depends: libusb-1.0-0:i386 (>= 2:1.0.8) but it is not going to be installed
 procps : Depends: initscripts
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by Bashing-om on 2013-12-17
slgtheindividual; Shucks ;

No telling what you have on your system that requires the 32 bit libraries. But, let's see if we can satisfy the situation:
Let's look:
```

dpkg -l libusb-1.0-0:i386 ##(maybe ??)
dpkg -l libsane:i386
dpkg -l udev:i386
apt-cache depends libsane:i386
apt-cache rdepends libsane:i386

```
Maybe this will tell us what it will take.

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-17
I think it's adobe air that needed me to install 32 bit stuff (I didn't particularly want to but I needed air for a few things)

Ok cool well here's the output of that:

```

~$ dpkg -l libusb-1.0-0:i386
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version       Architecture  Description
+++-=================-=============-=============-=======================================
ii  libusb-1.0-0:i386 2:1.0.16-3    i386          userspace USB programming library

```

```

~$ dpkg -l libsane:i386
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name              Version       Architecture  Description
+++-=================-=============-=============-=======================================
ii  libsane:i386      1.0.23-0ubunt i386          API library for scanners

```

```

~$ dpkg -l udev:i386
dpkg-query: no packages found matching udev:i386

```

```

~$ apt-cache depends libsane:i386
libsane:i386
  Depends: <adduser:i386>
    adduser
  Depends: libsane-common:i386
    libsane-common
  Depends: udev:i386
    udev
  Depends: acl:i386
    acl
  Depends: libavahi-client3:i386
  Depends: libavahi-common3:i386
  Depends: libc6:i386
  Depends: libgphoto2-6:i386
  Depends: libgphoto2-port10:i386
  Depends: libieee1284-3:i386
  Depends: libjpeg8:i386
  Depends: libtiff5:i386
  Depends: libusb-1.0-0:i386
  Depends: libv4l-0:i386
  PreDepends: multiarch-support:i386
    multiarch-support
  Suggests: avahi-daemon:i386
    avahi-daemon
  Suggests: <hpoj:i386>
  Suggests: hplip:i386
  Suggests: libsane-extras:i386
  Suggests: sane-utils:i386
  Replaces: libsane-extras
  Replaces: libsane-extras:i386
  Replaces: libsane
  Breaks: libsane

```

```

~$ apt-cache rdepends libsane:i386
libsane:i386
Reverse Depends:
  wine1.7-i386:i386
  libreoffice:i386
  xsane:i386
  wine1.4-i386:i386
  scanbuttond:i386
  sane:i386
  pike7.8-sane:i386
  libsane-perl:i386
  libreoffice:i386
  libksane0:i386
  libgnomescan0:i386
  simple-scan:i386
  sane-utils:i386
  sane-utils:i386
  python3-imaging-sane-dbg:i386
  python3-imaging-sane:i386
  python-imaging-sane-dbg:i386
  python-imaging-sane:i386
  libsane-dev:i386
  libsane-dbg:i386
  libsane-common:i386
  libsane
  libsane
  hplip:i386
  colord:i386
  sane-utils
  libsane-common

```

Thank you again for all the help

---

### Post by Bashing-om on 2013-12-17
slgtheindividual; Yuk !

Don't look good for the home team !

What you have installed:
> 
ii  libusb-1.0-0:i386 2:1.0.16-3    i386          userspace USB programming library

Is all that is available, nothing before suacy, and nothing after sauce (updates, no)
> 
You have searched for packages that names contain libusb-1.0-0 in suite(s) saucy, all sections, and all architectures. Found 4 matching packages.
Exact hits
Package libusb-1.0-0
saucy (libs): userspace USB programming library 
2:1.0.16-3: amd64 i386


dpkg says:
> 
Depends: libusb-1.0-0:i386 (>= 2:1.0.8)
 I would think it is satisfied by version 2:1.0.16-3 as the symbol ">=" means greater than or equal.

OK, let's look some more, why is the package manager hollering about the 32 bit libraries:
```

dpkg --print-architecture
dpkg --print-foreign-architecture

```
What happens when you try to (re-)install  libsane ?
```

sudo apt-get install --reinstall libsane

```

Look'n to find out why it no workie for us.

---

### Post by slgtheindividual on 2013-12-17
Ok I did all that:
(I assume you meant 'architectures' so I put that)
```

~$ dpkg --print-architecture
amd64
~$ dpkg --print-foreign-architecture
dpkg: error: unknown option --print-foreign-architecture


Type dpkg --help for help about installing and un-installing packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;


Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
~$ dpkg --help
Usage: dpkg [<option> ...] <command>


Commands:
  -i|--install       <.deb file name> ... | -R|--recursive <directory> ...
  --unpack           <.deb file name> ... | -R|--recursive <directory> ...
  -A|--record-avail  <.deb file name> ... | -R|--recursive <directory> ...
  --configure        <package> ... | -a|--pending
  --triggers-only    <package> ... | -a|--pending
  -r|--remove        <package> ... | -a|--pending
  -P|--purge         <package> ... | -a|--pending
  --get-selections [<pattern> ...] Get list of selections to stdout.
  --set-selections                 Set package selections from stdin.
  --clear-selections               Deselect every non-essential package.
  --update-avail <Packages-file>   Replace available packages info.
  --merge-avail <Packages-file>    Merge with info from file.
  --clear-avail                    Erase existing available info.
  --forget-old-unavail             Forget uninstalled unavailable pkgs.
  -s|--status <package> ...        Display package status details.
  -p|--print-avail <package> ...   Display available version details.
  -L|--listfiles <package> ...     List files `owned' by package(s).
  -l|--list [<pattern> ...]        List packages concisely.
  -S|--search <pattern> ...        Find package(s) owning file(s).
  -C|--audit                       Check for broken package(s).
  --add-architecture <arch>        Add <arch> to the list of architectures.
  --remove-architecture <arch>     Remove <arch> from the list of architectures.
  --print-architecture             Print dpkg architecture.
  --print-foreign-architectures    Print allowed foreign architectures.
  --compare-versions <a> <op> <b>  Compare version numbers - see below.
  --force-help                     Show help on forcing.
  -Dh|--debug=help                 Show help on debugging.


  -?, --help                       Show this help message.
      --version                    Show the version.


Use dpkg -b|--build|-c|--contents|-e|--control|-I|--info|-f|--field|
 -x|--extract|-X|--vextract|--fsys-tarfile  on archives (type dpkg-deb --help).


For internal use: dpkg --assert-support-predepends | --predep-package |
  --assert-working-epoch | --assert-long-filenames | --assert-multi-conrep |
  --assert-multi-arch.


Options:
  --admindir=<directory>     Use <directory> instead of /var/lib/dpkg.
  --root=<directory>         Install on a different root directory.
  --instdir=<directory>      Change installation dir without changing admin dir.
  --path-exclude=<pattern>   Do not install paths which match a shell pattern.
  --path-include=<pattern>   Re-include a pattern after a previous exclusion.
  -O|--selected-only         Skip packages not selected for install/upgrade.
  -E|--skip-same-version     Skip packages whose same version is installed.
  -G|--refuse-downgrade      Skip packages with earlier version than installed.
  -B|--auto-deconfigure      Install even if it would break some other package.
  --[no-]triggers            Skip or force consequential trigger processing.
  --no-debsig                Do not try to verify package signatures.
  --no-act|--dry-run|--simulate
                             Just say what we would do - don't do it.
  -D|--debug=<octal>         Enable debugging (see -Dhelp or --debug=help).
  --status-fd <n>            Send status change updates to file descriptor <n>.
  --status-logger=<command>  Send status change updates to <command>'s stdin.
  --log=<filename>           Log status changes and actions to <filename>.
  --ignore-depends=<package>,...
                             Ignore dependencies involving <package>.
  --force-...                Override problems (see --force-help).
  --no-force-...|--refuse-...
                             Stop when problems encountered.
  --abort-after <n>          Abort after encountering <n> errors.


Comparison operators for --compare-versions are:
  lt le eq ne ge gt       (treat empty version as earlier than any version);
  lt-nl le-nl ge-nl gt-nl (treat empty version as later than any version);
  < << <= = >= >> >       (only for compatibility with control file syntax).


Use `dselect' or `aptitude' for user-friendly package management.
~$ dpkg --print-foreign-architectures
i386
~$ sudo apt-get install --reinstall libsane
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 7,471 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ saucy/main libsane amd64 1.0.23-0ubuntu3 [3,786 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ saucy/main libsane i386 1.0.23-0ubuntu3 [3,685 kB]
Fetched 7,471 kB in 25s (293 kB/s)                                             
(Reading database ... 394701 files and directories currently installed.)
Preparing to replace libsane:amd64 1.0.23-0ubuntu3 (using .../libsane_1.0.23-0ubuntu3_amd64.deb) ...
Unpacking replacement libsane:amd64 ...
Preparing to replace libsane:i386 1.0.23-0ubuntu3 (using .../libsane_1.0.23-0ubuntu3_i386.deb) ...
Unpacking replacement libsane:i386 ...
Setting up libsane:amd64 (1.0.23-0ubuntu3) ...
Setting up libsane:i386 (1.0.23-0ubuntu3) ...
Processing triggers for libc-bin ...
~$

```

---

### Post by Bashing-om on 2013-12-17
slgtheindividual; Well !

That all says there is no problem !

Presently overall what does the package manager report ?
```

dpkg -C

```

Then may try and (re-)install libudev1=204-0ubuntu19 .

cause and effect, still wondering

---

### Post by slgtheindividual on 2013-12-18
ok sounds good, well that returns nothing:

```

~$ dpkg -C
~$ 

```

---

### Post by Bashing-om on 2013-12-18
slgtheindividua; Great,

A return of nothing is a good thing in this instamce.

I am looking..

[INDENT][INDENT]I'll Be Back
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-18
Ok, thank you, I'll be away for the next few hours but I'll get back to you asap.

---

### Post by Bashing-om on 2013-12-18
slgtheindividual; OK ,
As the package manager seems to think all is good;
With all 3rd party sources still disabled, let's see what results now:
```

sudo apt-get install libudev1=204-0ubuntu19

```

and go from there.
[INDENT]a firm oundation
[INDENT][INDENT][INDENT]is a nice thing to have
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-18
ok well that gave me:

```

~$ sudo apt-get install libudev1=204-0ubuntu19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libgphoto2-port10:i386 : Depends: libusb-1.0-0:i386 (>= 2:1.0.8) but it is not going to be installed
 libsane : Depends: udev (>= 0.88-1)
 libsane:i386 : Depends: udev:i386 (>= 0.88-1)
                Depends: libusb-1.0-0:i386 (>= 2:1.0.8) but it is not going to be installed
 procps : Depends: initscripts
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

### Post by Bashing-om on 2013-12-18
slgtheindividual; YUK !

OK, I am considering dropping down to a lower level with the package management system.
Let me consider "wgetting" that file from the pool, and "dpkg -i" to install it.
As "apt-get" refuses to install, I can not be sure no breakage will occur or where, with applying "dpkg"!
Multi-Arch is supposed to be fully supported now . Why we are experiencing these problems remains a mystery to me.

Any others' input is welcome.

[INDENT][INDENT]why Oh why
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-18
Ok no problem.

---

### Post by Bashing-om on 2013-12-19
slgtheindividual; Hey ,

I have been re-think'n this sloppyation. How about taking a different tack on this> Rather than trying to downgrade the packages to what is appropriate ; may I suggest we try and "revert" the 3rd party PPAs to whatever might be available in the repository - if the package manager will let us - and rather than breaking something, lets selectively remove the 3rd party software until such time as we can get the system stable.

It is your system and you are the administrator, we will do what ever you think is in the best interest of your system.
A) we can "force" the package downgrade and probably break what ever application is holding the system to those elevated versions;
B) Revert what applications we can to those in the repository and remove all others. (Re-)install what applications that you need to have, watching to see which installs those later version packages.

If it is plan A, to get our references in a readily available place, post the output of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```

Breaking things to see what happens, just is not the best trouble shooting technique; in my humblest of opinions .
[INDENT]What I think[/INDENT]

---

### Post by steeldriver on 2013-12-19
Bashing I was waiting to see how your previous attempts played out, but I have been thinking along the same lines (possibly re-enabling the 2 ppas and then installing and running ppa-purge?)

You could do just the nvbn-rm one first (I have no idea what that is) if you want to try to preserve your wine installation

---

### Post by Bashing-om on 2013-12-19
@steeldriver;
I do think reverting the PPAs is the better course. I did, however, have in mind to start with Wine, as I know it is supported in the repository. My think'n was that Wine the more likely application driving those packages to the later versions. If you want to start with "nvbn-rm"  - whatever that one is - I am all for that too ! I can not express how much I do enjoy working with you.

@ slgtheindividual; Either plan should work. I just can not see how probably causing breakage and complicating the situation is a good thing to do to isolate where the origins of the problem lies. But. that too will work out in the end.

The system is broke now as it is, we are just try'n

[INDENT][INDENT]to fix it !
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-19
@Bashing-om your persistence with these thorny problems is a credit to the forum

I'm always leery of making things worse - which sometimes results in (with hindsight) unnecessary tippytoeing - however at this point I think the gloves can come off - I doubt it really matters which ppa the OP chooses to purge first

---

### Post by slgtheindividual on 2013-12-19
Ok well I'm thinking we should go with A, as none of my third party stuff is essential so even if it breaks it isn't a huge deal, but I'd rather not remove everything and have to put it back later, just my personal preference. SO... In the spirit of 'A' I have the following output for you:

```

~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 13.10 _Saucy Salamander_ - Release amd64 (20131016.1)]/ saucy main restricted
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     6	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    11	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://gb.archive.ubuntu.com/ubuntu/ saucy universe
    17	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy universe
    18	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
    19	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
    27	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy multiverse
    28	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    29	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    37	deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu saucy-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu saucy-security main restricted
    41	deb http://security.ubuntu.com/ubuntu saucy-security universe
    42	deb-src http://security.ubuntu.com/ubuntu saucy-security universe
    43	deb http://security.ubuntu.com/ubuntu saucy-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu saucy-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu saucy partner
    51	
    52	## This software is not part of Ubuntu, but is offered by third-party
    53	## developers who want to ship their latest software.
    54	# deb http://extras.ubuntu.com/ubuntu saucy main
    55	
    56	

```

and

```

~$ cat /etc/apt/sources.list.d/*.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main
# deb http://ppa.launchpad.net/nvbn-rm/ppa/ubuntu saucy main
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/monster-rpg2/ubuntu saucy main #Added by software-center; credentials stored in /etc/apt/auth.conf
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/nitro/ubuntu saucy main #Added by software-center; credentials stored in /etc/apt/auth.conf
# deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/steam/ubuntu saucy main #Added by software-center; credentials stored in /etc/apt/auth.conf
# deb http://repo.steampowered.com/steam/ precise steam
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu saucy main

```

Thank you both for all of your input, I really appreciate it.

---

### Post by Bashing-om on 2013-12-19
slgtheindividual; OK ! Here is the deal,
Cards coming at you.

Still with all 3rd party sources disabled, try this and see what results !
```

cd /var/cache/apt/archives
wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
sudo dpkg -i libudev1_204-0ubuntu19.1_amd64.deb

```
If that goes well, then continue and see what can be done with "udev" :
```

wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19.1_amd64.deb
sudo dpkg -i udev_204-0ubuntu19.1_amd64.deb

```

Now let's see where we stand:
```

cd ## to return to home as the PWD
sudo apt-get update
sudo apt-get upgrade

```
Still to be dealt with is "libusb" as there are no other candidates, do not know at this time how that will play out. I hope now all versions match and the package manager is happy.

Next we can look at enabling 3rd parties - one at a time - and test test test to see what fails.

[INDENT][INDENT]this un is a big thing
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-19
Ok well I started that but it failed in the first step:

```

~$ cd /var/cache/apt/archives
~$ wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
--2013-12-20 04:38:01--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 91.189.92.200, 91.189.92.201, 194.169.254.10, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|91.189.92.200|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35896 (35K) [application/x-debian-package]
libudev1_204-0ubuntu19.1_amd64.deb: Permission denied


Cannot write to &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217; (Permission denied).
~$ sudo !!
sudo wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
 
--2013-12-20 04:38:10--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 91.189.92.201, 194.169.254.10, 91.189.92.156, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|91.189.92.201|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35896 (35K) [application/x-debian-package]
Saving to: &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217;


100%[============================================================================================================>] 35,896      --.-K/s   in 0.04s   


2013-12-20 04:38:11 (797 KB/s) - &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217; saved [35896/35896]


~$ sudo dpkg -i libudev1_204-0ubuntu19.1_amd64.deb
dpkg: warning: downgrading libudev1:amd64 from 204-5 to 204-0ubuntu19.1
(Reading database ... 394713 files and directories currently installed.)
Preparing to replace libudev1:amd64 204-5 (using libudev1_204-0ubuntu19.1_amd64.deb) ...
De-configuring libudev1:i386 ...
Unpacking replacement libudev1:amd64 ...
dpkg: error processing libudev1:amd64 (--install):
 package libudev1:amd64 204-0ubuntu19.1 cannot be configured because libudev1:i386 is at a different version (204-5)
dpkg: error processing libudev1:i386 (--install):
 package libudev1:i386 204-5 cannot be configured because libudev1:amd64 is at a different version (204-0ubuntu19.1)
Errors were encountered while processing:
 libudev1:amd64
 libudev1:i386

```

---

### Post by Bashing-om on 2013-12-20
slgtheindividual; Yikes !

Will have to do some research. I am under the impression that multi-arch is fully integrated in these later versions of the operating system.
Then why is the package manager screaming about the i386 (32 bit) packages (again !!) ?
Not in the repository !
> 
sysop@1304mini:~$ apt-cache search udev:i386
sysop@1304mini:~$ 



Not tonight .. but ->
[INDENT][INDENT]I'll Be Back[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-20
Ok no problem, thank you again.

---

### Post by Bashing-om on 2013-12-20
slgtheindividual; Morning !

Still a lookin' ; What do we have for the libraries installed now.
```

dpkg --get-selections | grep -i libudev

```
To be upfront, I am pretty well stuck at this point as to why the 32 bit libs are not configuring.
Make a sym Link ?? Do not know !

[INDENT]has to be a reason
[/INDENT]

---

### Post by slgtheindividual on 2013-12-20
morning to you too (although it's night here in the uk lol)

that gives me:

```

~$ dpkg --get-selections | grep -i libudev
libudev1:amd64					install
libudev1:i386					install

```

---

### Post by Bashing-om on 2013-12-20
slgtheindividual; Welp;

Seems there is a 32 bit libs package installed - do not see that in my 13.04 install.
What return from:
```

apt-cache search libudev1:i386

```
Maybe we can attack this from a different direction.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-20
Ok well I get nothing from that:

```

~$ apt-cache search libudev1:i386
~$

```

---

### Post by Bashing-om on 2013-12-20
slgtheindividual; Well,

I can throw my last thought out the window too.

I am back to the drawing board, see what else I can come up with.

quit is not 
[INDENT][INDENT][INDENT]in my nature
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-21
slgtheindividual; Hello,

Internet just now restored here .. so all is now good in my world !

Continuing along the plan A route. Let's consider what might happen if udev and libdev1 "were" to be removed from the system prior to (re-)installing the proper versions.
We are going to simulate what will be removed.
```

sudo apt-get purge -s libudev1
sudo apt-get purge -s udev

```
Looking before we jump.

We could force the install of the proper versions, but with what we have experienced with the 32 bit dependencies, I am not to fond of that idea.
So long as there is no interruption of your power source - or loss of internet connectivity - I expect it is doable to remove and (re-)install. I have yet to Bork some one else's system, I do not want yours to be a first ! I have faith in this smart operating system that this can be done, files that are in use will not be removed until replaced with those from the install .. in theory at least !

But, let us observe the 7 P's
[INDENT][INDENT]Prior Prudent Planning Prevents Pi** Poor Performance
[/INDENT][/INDENT] 

Still cogitating, but to this time I have not come up with a better alternative in order to proceed.

---

### Post by slgtheindividual on 2013-12-21
hmm gave me lots of errors:

```

$ sudo apt-get purge -s libudev1
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 bluez : Depends: libudev1 (>= 183) but it is not going to be installed
 consolekit : Depends: libudev1 (>= 183) but it is not going to be installed
 google-chrome-stable : Depends: libudev0 (>= 147) but it is not installable or
                                 libudev1 (>= 198) but it is not going to be installed
 gvfs : Depends: libudev1 (>= 183) but it is not going to be installed
 gvfs-daemons : Depends: libudev1 (>= 183) but it is not going to be installed
 initramfs-tools-bin : Depends: libudev1 (>= 183) but it is not going to be installed
 libatasmart4 : Depends: libudev1 (>= 183) but it is not going to be installed
 libdevmapper1.02.1 : Depends: libudev1 (>= 183) but it is not going to be installed
 libegl1-mesa : Depends: libudev1 (>= 183) but it is not going to be installed
 libegl1-mesa-drivers : Depends: libudev1 (>= 183) but it is not going to be installed
 libgbm1 : Depends: libudev1 (>= 183) but it is not going to be installed
 libgudev-1.0-0 : Depends: libudev1 (>= 183) but it is not going to be installed
 liblvm2app2.2 : Depends: libudev1 (>= 183) but it is not going to be installed
 libqextserialport1 : Depends: libudev1 (>= 183) but it is not going to be installed
 libqt5gui5 : Depends: libudev1 (>= 183) but it is not going to be installed
 libsolid4 : Depends: libudev1 (>= 183) but it is not going to be installed
 libusb-1.0-0 : Depends: libudev1 (>= 183) but it is not going to be installed
 mountall : Depends: libudev1 (>= 183) but it is not going to be installed
 pulseaudio : Depends: libudev1 (>= 183) but it is not going to be installed
 system-config-printer-udev : Depends: libudev1 (>= 183) but it is not going to be installed
 systemd-services : Depends: libudev1 (>= 183) but it is not going to be installed
 udev : Depends: libudev1 (= 204-5) but it is not going to be installed
 udisks : Depends: libudev1 (>= 183) but it is not going to be installed
 upstart : Depends: libudev1 (>= 183) but it is not going to be installed
 vlc-nox : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-core : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-input-evdev : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-intel : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-modesetting : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-nouveau : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-radeon : Depends: libudev1 (>= 183) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
~$ sudo apt-get purge -s udev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 alsa-base : Depends: udev
 bluez : Depends: udev (>= 170-1)
 checkbox : Depends: udev
 dmsetup : Depends: udev (> 141-2)
 gnome-bluetooth : Depends: udev (>= 154)
 initramfs-tools : Depends: udev (>= 147~-5)
 libnjb5 : Depends: udev
 libsane : Depends: udev (>= 0.88-1)
 libsane:i386 : Depends: udev:i386 (>= 0.88-1)
 libsolid4 : Depends: udev
 libudev1 : Breaks: libudev1:i386 (!= 204-0ubuntu19.1) but 204-5 is to be installed
 libudev1:i386 : Breaks: libudev1 (!= 204-5) but 204-0ubuntu19.1 is to be installed
 media-player-info : Depends: udev
 mountall : Depends: udev
 network-manager : Depends: udev
 plymouth : Depends: udev (>= 166-0ubuntu4)
 pulseaudio : Depends: udev (>= 143)
 systemd-services : Depends: udev (>= 175-0ubuntu23)
 ubuntu-drivers-common : Depends: udev (>= 204-0ubuntu4~)
 ubuntu-minimal : Depends: udev
 udisks : Depends: udev
 udisks2 : Depends: udev
 upower : Depends: udev
 xserver-xorg-core : Depends: udev (>= 149)
 xserver-xorg-input-synaptics : Depends: udev
 xserver-xorg-input-vmmouse : Depends: udev
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 libudev1 : Breaks: libudev1:i386 (!= 204-0ubuntu19.1) but 204-5 is installed
 libudev1:i386 : Breaks: libudev1 (!= 204-5) but 204-0ubuntu19.1 is installed
 udev : Depends: libudev1 (= 204-5) but 204-0ubuntu19.1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

well my internet connection and power are usually very reliable so I have no problem going ahead once all the bugs are ironed out

---

### Post by Bashing-om on 2013-12-21
slgtheindividual; Well,

We know we are going to rip the heart out of the operating system, and try and put it back !
However, I know of no better course of action.

All 3rd party software sources still disabled !

Here goes:
```

sudo apt-get purge libudev1
sudo apt-get purge udev
sudo apt-get install libudev1=204-0ubuntu19.1
sudo apt-get install udev=204-0ubuntu19.1
##clean the mess up
sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
##and now the biggy, we want to rebuild the ram image to reflect these changes
sudo update-initramfs -u

```

Wipe the sweat off the brow, and let's see what the result is:
Reboot:
```

sudo shutdown -r now

```

Should workie, hopefully ->
[INDENT][INDENT][INDENT]last long time
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-22
slgtheindividual;
Just checking, I am on pins and needles !

[INDENT][INDENT]concerned party to this
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-22
Sorry I've been away for the day, unable to get to my computer.

Well I tried but the very first command failed:
```

~$ sudo apt-get purge libudev1
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 bluez : Depends: libudev1 (>= 183) but it is not going to be installed
 consolekit : Depends: libudev1 (>= 183) but it is not going to be installed
 google-chrome-stable : Depends: libudev0 (>= 147) but it is not installable or
                                 libudev1 (>= 198) but it is not going to be installed
 gvfs : Depends: libudev1 (>= 183) but it is not going to be installed
 gvfs-daemons : Depends: libudev1 (>= 183) but it is not going to be installed
 initramfs-tools-bin : Depends: libudev1 (>= 183) but it is not going to be installed
 libatasmart4 : Depends: libudev1 (>= 183) but it is not going to be installed
 libdevmapper1.02.1 : Depends: libudev1 (>= 183) but it is not going to be installed
 libegl1-mesa : Depends: libudev1 (>= 183) but it is not going to be installed
 libegl1-mesa-drivers : Depends: libudev1 (>= 183) but it is not going to be installed
 libgbm1 : Depends: libudev1 (>= 183) but it is not going to be installed
 libgudev-1.0-0 : Depends: libudev1 (>= 183) but it is not going to be installed
 liblvm2app2.2 : Depends: libudev1 (>= 183) but it is not going to be installed
 libqextserialport1 : Depends: libudev1 (>= 183) but it is not going to be installed
 libqt5gui5 : Depends: libudev1 (>= 183) but it is not going to be installed
 libsolid4 : Depends: libudev1 (>= 183) but it is not going to be installed
 libusb-1.0-0 : Depends: libudev1 (>= 183) but it is not going to be installed
 mountall : Depends: libudev1 (>= 183) but it is not going to be installed
 pulseaudio : Depends: libudev1 (>= 183) but it is not going to be installed
 system-config-printer-udev : Depends: libudev1 (>= 183) but it is not going to be installed
 systemd-services : Depends: libudev1 (>= 183) but it is not going to be installed
 udev : Depends: libudev1 (= 204-5) but it is not going to be installed
 udisks : Depends: libudev1 (>= 183) but it is not going to be installed
 upstart : Depends: libudev1 (>= 183) but it is not going to be installed
 vlc-nox : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-core : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-input-evdev : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-intel : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-modesetting : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-nouveau : Depends: libudev1 (>= 183) but it is not going to be installed
 xserver-xorg-video-radeon : Depends: libudev1 (>= 183) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

but if I do as it suggests that also fails:

```

~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies.
 libudev1 : Breaks: libudev1:i386 (!= 204-0ubuntu19.1) but 204-5 is installed
 libudev1:i386 : Breaks: libudev1 (!= 204-5) but 204-0ubuntu19.1 is installed
 udev : Depends: libudev1 (= 204-5) but 204-0ubuntu19.1 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```

---

### Post by Bashing-om on 2013-12-22
slgtheindividual; Well !
OK,
I am to the point of forcing the issue:
```

sudo dpkg -i --force-remove-reinstreq libudev1_204-0ubuntu19.1
sudo dpkg -i --force-remove-reinstreq udev_204-0ubuntu19.1

```

I just do not know enough to do any better.

[INDENT][INDENT]fingers crossed
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-22
the first one gave me an error so I didn't run the second: 

```

~$ sudo dpkg -i --force-remove-reinstreq libudev1_204-0ubuntu19.1
 
dpkg: error processing libudev1_204-0ubuntu19.1 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libudev1_204-0ubuntu19.1

```

---

### Post by Bashing-om on 2013-12-23
slgtheindividual; Sheesshhh;

We can keep pounding away at plan A, I do have in mind something else to try and force the issue;
We can forego ever getting around the 32 bit library dependencies and go for plan B; A real pain, would be a lot quicker and cleaner to go for a plan C.

Plan C; Install Version 13.10 (sausy) that has those required libraries to install the 32 bit applications you need to use, then in April, or so, version upgrade to 14.04.

Plan A Continued:
What once more do we have on the system to work with:
```

ls -la  /var/cache/apt/archives/

```
Looking for "udev" and "libudev1" . Versions ? - If any -
So we know what we have to go and get to continue with my current thought procedure - that has the possibility of borking the system.

To me this has become a process of learning ... how the 32 bit libraries are now integrated into multi-arch.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-23
I'm already running 13.10 though.

```

~$ ls -la  /var/cache/apt/archives/
total 88
drwxr-xr-x 3 root root 77824 Dec 20 04:49 .
drwxr-xr-x 3 root root  4096 Dec 23 15:52 ..
-rw-r----- 1 root root     0 Oct 16 20:05 lock
drwxr-xr-x 2 root root  4096 Dec 20 03:41 partial

```

---

### Post by Bashing-om on 2013-12-23
slgtheindividual; OK !
My bad not remembering we are coping with 13.10.
Continuing plan A, let's try this !
I do have some heavy concern that the system may be borked (!); But, this is the last thing I can think of to try.


```

cd /var/cache/apt/archives
wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19.1_amd64.deb
sudo dpkg -i --force-remove-reinstreq libudev1_204-0ubuntu19.1
sudo dpkg -i --force-remove-reinstreq udev_204-0ubuntu19.1
sudo update-initramfs -u

```
That syntax now I am uncertain about, if the "dpkg -i" fails try it as:
```

sudo dpkg -i --force-remove-reinstreq libudev1=204-0ubuntu19.1
sudo dpkg -i --force-remove-reinstreq udev=204-0ubuntu19.1

```

something has got to give.
[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-24
ok well it basically worked until the dpkg commands (I tried both to be sure)

```

~$ cd /var/cache/apt/archives
/var/cache/apt/archives$ wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
--2013-12-24 05:03:46--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 91.189.92.201, 194.169.254.10, 91.189.92.156, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|91.189.92.201|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35896 (35K) [application/x-debian-package]
libudev1_204-0ubuntu19.1_amd64.deb: Permission denied


Cannot write to &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217; (Permission denied).
/var/cache/apt/archives$ sudo !!
sudo wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
 
--2013-12-24 05:03:57--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 91.189.92.201, 194.169.254.10, 91.189.92.156, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|91.189.92.201|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35896 (35K) [application/x-debian-package]
Saving to: &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217;


100%[======================================>] 35,896      --.-K/s   in 0.05s   


2013-12-24 05:03:57 (726 KB/s) - &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217; saved [35896/35896]


/var/cache/apt/archives$ sudo wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19.1_amd64.deb
--2013-12-24 05:04:12--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 194.169.254.10, 91.189.92.156, 91.189.92.200, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|194.169.254.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1039732 (1015K) [application/x-debian-package]
Saving to: &#8216;udev_204-0ubuntu19.1_amd64.deb&#8217;


100%[======================================>] 1,039,732   2.16MB/s   in 0.5s   


2013-12-24 05:04:12 (2.16 MB/s) - &#8216;udev_204-0ubuntu19.1_amd64.deb&#8217; saved [1039732/1039732]


/var/cache/apt/archives$ sudo dpkg -i --force-remove-reinstreq libudev1_204-0ubuntu19.1
dpkg: error processing libudev1_204-0ubuntu19.1 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libudev1_204-0ubuntu19.1
/var/cache/apt/archives$ sudo dpkg -i --force-remove-reinstreq libudev1=204-0ubuntu19.1
dpkg: error processing libudev1=204-0ubuntu19.1 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libudev1=204-0ubuntu19.1
/var/cache/apt/archives$ sudo dpkg -i --force-remove-reinstreq udev_204-0ubuntu19.1
dpkg: error processing udev_204-0ubuntu19.1 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 udev_204-0ubuntu19.1
/var/cache/apt/archives$ sudo dpkg -i --force-remove-reinstreq udev=204-0ubuntu19.1
dpkg: error processing udev=204-0ubuntu19.1 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 udev=204-0ubuntu19.1
/var/cache/apt/archives$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.11.0-14-generic

```

---

### Post by Bashing-om on 2013-12-24
slgtheindividual; Oh !

My bad again ! I see the error of my ways !
try it as:
edit: from the PWD "/var/cache/apt/archives"
```

sudo dpkg -i --force-remove-reinstreq libudev1_204-0ubuntu19.1_amd64.deb
sudo dpkg -i --force-remove-reinstreq udev_204-0ubuntu19.1_amd64.deb

```
Give it the correct file name ! - may bad bad bad -
As I fumble my way through my darkness.

Crossed fingers on many ways, let's see what breaks.

[INDENT][INDENT]high regards
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-24
I have been following this thread - I tried to reproduce your situation by installing the 2 ppas that we discovered into a saucy vm, bu the nearest I could find is that it is wine that installs the libudev1:i386, however even if I install wine1.7 the version never goes above **204-0ubuntu19.1**

```

$ sudo apt-get install --dry-run wine1.7 | grep udev
  libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386
  libtiff5:i386 libtinfo5:i386 libtxc-dxtn-s2tc0:i386 libudev1:i386
[B]Inst libudev1:i386 (204-0ubuntu19.1 Ubuntu:13.10/saucy-updates [i386])
Conf libudev1:i386 (204-0ubuntu19.1 Ubuntu:13.10/saucy-updates [i386])
[/B]
```

Nevertheless I wonder if it is worth trying to apt-get remove wine? Although I suspect the package system breakage won't let you do that, *maybe* if wine is the *only* thing requiring that package it will...

BTW Bashing-om's dpkg commands likely failed to execute because AFAIK dpkg -i needs the whole filename (including the .deb suffix)

---

### Post by Bashing-om on 2013-12-24
@ steeldriver; Glad you are keeping up with this one !

I am embarrassed at all the mistakes I am making, as well as the time factor and still no closure !
If that last "force" is ineffective -
Recon we will have to edit the control files to make it possible to remove the offending packages ??? 

Or as you say, find the package that is driving the libraries to the trusty version .. That too was my next thought ,, to selectively remove the PPAs and see what results.

Hey, we can do this
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-24
Ok well I tried it and still got errors:

```

~$ cd /var/cache/apt/archives
/var/cache/apt/archives$ sudo wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
 
--2013-12-24 19:50:38--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/libudev1_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 91.189.92.201, 194.169.254.10, 91.189.92.156, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|91.189.92.201|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 35896 (35K) [application/x-debian-package]
Saving to: &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217;


100%[======================================>] 35,896      --.-K/s   in 0.1s    


2013-12-24 19:50:38 (368 KB/s) - &#8216;libudev1_204-0ubuntu19.1_amd64.deb&#8217; saved [35896/35896]


/var/cache/apt/archives$ sudo wget http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19.1_amd64.deb
--2013-12-24 19:50:50--  http://gb.archive.ubuntu.com/ubuntu/pool/main/s/systemd/udev_204-0ubuntu19.1_amd64.deb
Resolving gb.archive.ubuntu.com (gb.archive.ubuntu.com)... 194.169.254.10, 91.189.92.156, 91.189.92.200, ...
Connecting to gb.archive.ubuntu.com (gb.archive.ubuntu.com)|194.169.254.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1039732 (1015K) [application/x-debian-package]
Saving to: &#8216;udev_204-0ubuntu19.1_amd64.deb&#8217;


100%[======================================>] 1,039,732   1.29MB/s   in 0.8s   


2013-12-24 19:50:51 (1.29 MB/s) - &#8216;udev_204-0ubuntu19.1_amd64.deb&#8217; saved [1039732/1039732]


/var/cache/apt/archives$ sudo dpkg -i --force-remove-reinstreq libudev1_204-0ubuntu19.1_amd64.deb
(Reading database ... 394713 files and directories currently installed.)
Preparing to replace libudev1:amd64 204-0ubuntu19.1 (using libudev1_204-0ubuntu19.1_amd64.deb) ...
Unpacking replacement libudev1:amd64 ...
dpkg: error processing libudev1:amd64 (--install):
 package libudev1:amd64 204-0ubuntu19.1 cannot be configured because libudev1:i386 is at a different version (204-5)
Errors were encountered while processing:
 libudev1:amd64
/var/cache/apt/archives$ sudo dpkg -i --force-remove-reinstreq udev_204-0ubuntu19.1_amd64.deb
dpkg: warning: downgrading udev from 204-5 to 204-0ubuntu19.1
(Reading database ... 394713 files and directories currently installed.)
Preparing to replace udev 204-5 (using udev_204-0ubuntu19.1_amd64.deb) ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
dpkg: dependency problems prevent configuration of udev:
 udev depends on libudev1 (= 204-0ubuntu19.1); however:
  Package libudev1:amd64 is not configured yet.
 consolekit (0.4.6-3+b1) breaks udev (<< 204-1) and is installed.
  Version of udev to be configured is 204-0ubuntu19.1.


dpkg: error processing udev (--install):
 dependency problems - leaving unconfigured
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Errors were encountered while processing:
 udev

```

---

### Post by Bashing-om on 2013-12-24
slgtheindividual; This is for a fact getting real old.

Going round and around with the 32 bit libraries (i386).
> 
cannot be configured because libudev1:i386

I do not know -in these later versions of the operating system - where/if they are installed; or how the integration is done into the 64 bit OS.
Let's see what we can do do find those relationships:
what returns:
```

ls -la /var/lib/dpkg/info/libudev*
grep -B3 -A10 libudev1:i386 /var/lib/dpkg/status

```

Has to exist somewhere, this should be the place in which to look !

[INDENT][INDENT]sometimes I wonder, other times
[INDENT][INDENT][INDENT]I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-24
ok no problem, that gives me:

```

$ ls -la /var/lib/dpkg/info/libudev*
-rw-r--r-- 1 root root  237 Dec 24 19:51 /var/lib/dpkg/info/libudev1:amd64.list
-rw-r--r-- 1 root root  216 Dec 10 17:09 /var/lib/dpkg/info/libudev1:amd64.md5sums
-rwxr-xr-x 1 root root  135 Dec 10 17:09 /var/lib/dpkg/info/libudev1:amd64.postinst
-rwxr-xr-x 1 root root  132 Dec 10 17:09 /var/lib/dpkg/info/libudev1:amd64.postrm
-rw-r--r-- 1 root root   49 Dec 10 17:09 /var/lib/dpkg/info/libudev1:amd64.shlibs
-rw-r--r-- 1 root root 3982 Dec 10 17:09 /var/lib/dpkg/info/libudev1:amd64.symbols
-rw-r--r-- 1 root root  231 Nov 11 20:14 /var/lib/dpkg/info/libudev1:i386.list
-rw-r--r-- 1 root root  214 Sep 23 13:25 /var/lib/dpkg/info/libudev1:i386.md5sums
-rwxr-xr-x 1 root root  135 Sep 23 13:25 /var/lib/dpkg/info/libudev1:i386.postinst
-rwxr-xr-x 1 root root  132 Sep 23 13:25 /var/lib/dpkg/info/libudev1:i386.postrm
-rw-r--r-- 1 root root   49 Sep 23 13:24 /var/lib/dpkg/info/libudev1:i386.shlibs
-rw-r--r-- 1 root root 3982 Sep 23 13:24 /var/lib/dpkg/info/libudev1:i386.symbols
$ grep -B3 -A10 libudev1:i386 /var/lib/dpkg/status
$ 

```

---

### Post by Bashing-om on 2013-12-24
slgtheindividual; That at least is something:

Let's see where this leads:
```

cat /var/lib/dpkg/info/libudev1:i386.list

```
While I am scratching my head why "/var/lib/dpkg/status" has a non-positive result/ not at all what I had expected//

This may be a VERY long output, but anything meaningful in respect to "i386" from (??):
```

grep -B3 -A10 "libudev1*" /var/lib/dpkg/status

```

[INDENT]shooting blanks
[INDENT][INDENT]and still in the dark
[/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-24
ok, the first one:

```

~$ cat /var/lib/dpkg/info/libudev1:i386.list
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libudev1
/usr/share/doc/libudev1/changelog.Debian.gz
/usr/share/doc/libudev1/copyright
/lib
/lib/i386-linux-gnu
/lib/i386-linux-gnu/libudev.so.1.3.5
/lib/i386-linux-gnu/libudev.so.1

```




the second one gives me so much output that I can't scroll to the top of my terminal to copy it all? I assume there is a way to do it but I don't know how?

---

### Post by Bashing-om on 2013-12-24
slgtheindividual; cogitating.

As to that great amount of output, that was why I asked for the 1st commands output "grep -B3 -A10 libudev1:i386 /var/lib/dpkg/status";

Tell you what, let's do a number like this to redirect the output to a file .. and then one can scroll through the file.
Those who really do know their stuff can filter the output down to something meaningful - but it ain't me - best I can do eye ball that file, looking to see what is.
```

grep -B3 -A10 "libudev1*" /var/lib/dpkg/status > ~/status-txt

```
The file "status-txt" is written to your desktop, and may be opened in many ways.. maybe best from your file manager of choice (if that file is not too big !), else one can page through it with the utility "less". Looking for references to "i386".
What I have in mind is to edit that file depending on what references are found to "i386" ; then maybe able to remove/install those packages !

[INDENT][INDENT]where there is a will THERE
[INDENT][INDENT][INDENT]is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-24
ok, that's useful to know for future reference too.
Well here's a copy of that file's text:

```

Multi-Arch: same
Source: qextserialport
Version: 1.2.0~rc1+git7-g3be3fbf-1
Depends: libc6 (>= 2.14), libgcc1 (>= 1:4.1.1), libqtcore4 (>= 4:4.7.0~beta1), libstdc++6 (>= 4.1.1), libudev1 (>= 183)
Pre-Depends: multiarch-support
Description: interface to serial ports for Qt-based apps - development files
 QextSerialPort provides an interface to old fashioned serial ports for
 Qt-based applications.
 .
 It allows one to use the serial port in a multi-platform way, much as Qt does.
Original-Maintainer: Lisandro Damián Nicanor Pérez Meyer <lisandro@debian.org>
Homepage: http://code.google.com/p/qextserialport/


Package: libgeoip1
--
Multi-Arch: same
Source: systemd (204-0ubuntu19.1)
Version: 1:204-0ubuntu19.1
Depends: libc6 (>= 2.2.5), libglib2.0-0 (>= 2.37.3), libudev1 (>= 183)
Pre-Depends: multiarch-support
Description: GObject-based wrapper library for libudev
 This library makes it much simpler to use libudev from programs already using
 GObject. It also makes it possible to easily use libudev from other
 programming languages, such as Javascript, because of GObject introspection
 support.
Homepage: http://www.freedesktop.org/wiki/Software/systemd
Original-Maintainer: Tollef Fog Heen <tfheen@debian.org>


Package: soprano-daemon
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 598
--
Multi-Arch: foreign
Version: 4.101-0ubuntu8b1
Replaces: bluez-audio (<= 3.36-3), bluez-input, bluez-network, bluez-serial, bluez-utils (<= 3.36-3), udev (<< 170-1)
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.1.1), libglib2.0-0 (>= 2.28.0), libreadline6 (>= 6.0), libudev1 (>= 183), libusb-0.1-4 (>= 2:0.1.12), upstart-job, module-init-tools, udev (>= 170-1), lsb-base, dbus, python3-dbus
Pre-Depends: dpkg (>= 1.15.7.2)
Suggests: bluez-hcidump
Breaks: udev (<< 170-1)
Conflicts: bluez-audio (<= 3.36-3), bluez-utils (<= 3.36-3)
Conffiles:
 /etc/bluetooth/main.conf 4c5ea920c35ec67225e01832e3276516
 /etc/bluetooth/proximity.conf b75823a140e00905d41465c380bf89fe
 /etc/bluetooth/serial.conf 5dcc15dd1153ddebbd41612da9b642e5
 /etc/bluetooth/audio.conf 6bc1fef4f5fe083d34e953ec3dd70bfd
 /etc/bluetooth/input.conf 4bebcedeed8770b1aea07eefc5c35a52
--
Source: xorg-server
Version: 2:1.14.3-3ubuntu2
Provides: xorg-input-abi-19, xorg-video-abi-14
Depends: xserver-common (>= 2:1.14.3-3ubuntu2), keyboard-configuration, udev (>= 149), libaudit1 (>= 1:2.2.1), libc6 (>= 2.17), libdrm2 (>= 2.3.1), libgcrypt11 (>= 1.4.5), libglapi-mesa, libpciaccess0 (>= 0.12.902), libpixman-1-0 (>= 0.30.0), libselinux1 (>= 2.0.82), libudev1 (>= 183), libxau6, libxdmcp6, libxfont1 (>= 1:1.4.2)
Recommends: libgl1-mesa-dri (>= 7.10.2-4)
Suggests: xfonts-100dpi | xfonts-75dpi, xfonts-scalable
Breaks: libgl1-mesa-dri (<< 7.10.2-4), libgl1-mesa-dri-experimental (<< 7.10.2-4), libxfixes3 (<< 1:5.0.1), libxi6 (<< 2:1.7.1.901), qt4-x11 (<< 4:4.8.0-1ubuntu2), unity (<< 7.0.2), utouch-frame (<< 2.1.0), utouch-geis (<< 2.2.3), xserver-xorg-input, xserver-xorg-input-2, xserver-xorg-input-2.1, xserver-xorg-input-4, xserver-xorg-input-7, xserver-xorg-input-joystick (<= 1:1.5.0-3), xserver-xorg-input-synaptics (<= 1.2.2-1ubuntu4), xserver-xorg-input-tslib (<= 0.0.6-3), xserver-xorg-input-vmmouse (<= 1:12.6.5-4ubuntu2), xserver-xorg-input-wacom (<= 0.10.5+20100415-1), xserver-xorg-video, xserver-xorg-video-1.0, xserver-xorg-video-1.9, xserver-xorg-video-2, xserver-xorg-video-4, xserver-xorg-video-5, xserver-xorg-video-6, xserver-xorg-video-cyrix (<= 1:1.1.0-8), xserver-xorg-video-i810 (<< 2:2.4), xserver-xorg-video-imstt (<= 1:1.1.0-7), xserver-xorg-video-nsc (<= 1:2.8.3-4), xserver-xorg-video-sunbw2 (<= 1:1.1.0-5), xserver-xorg-video-v4l (<< 1:0.2.0), xserver-xorg-video-vga (<= 1:4.1.0-8)
Conflicts: xserver-xorg-input-evtouch
Description: Xorg X server - core server
 The Xorg X server is an X server for several architectures and operating
 systems, which is derived from the XFree86 4.x series of X servers.
 .
 The Xorg server supports most modern graphics hardware from most vendors,
 and supersedes all XFree86 X servers.
--
Homepage: http://avahi.org/
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>


Package: libudev1
Status: install ok unpacked
Priority: important
Section: libs
Installed-Size: 118
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: systemd
Version: 204-0ubuntu19.1
Config-Version: 204-5
Depends: libc6 (>= 2.17)
Pre-Depends: multiarch-support
Description: libudev shared library
 This library provides access to udev device information.
Homepage: http://www.freedesktop.org/wiki/Software/systemd
Original-Maintainer: Tollef Fog Heen <tfheen@debian.org>


Package: libudev1
Status: install ok half-configured
Priority: important
Section: libs
Installed-Size: 93
Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Architecture: i386
Multi-Arch: same
Source: systemd
Version: 204-5
Config-Version: 204-5
Depends: libc6 (>= 2.17)
Pre-Depends: multiarch-support
Description: libudev shared library
 This library provides access to udev device information.
Homepage: http://www.freedesktop.org/wiki/Software/systemd


Package: libcfitsio3
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 1468
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
--
Version: 204-0ubuntu19.1
Replaces: logind, systemd (<< 198-1), ubuntu-system-service
Provides: logind
Depends: libacl1 (>= 2.2.51-8), libc6 (>= 2.17), libcap2 (>= 2.10), libdbus-1-3 (>= 1.1.1), libselinux1 (>= 2.0.65), libsystemd-daemon0 (>= 31), libudev1 (>= 183), udev (>= 175-0ubuntu23), dbus
Recommends: systemd | systemd-shim (>= 3)
Breaks: systemd (<< 198-1)
Conflicts: logind
Conffiles:
 /etc/dbus-1/system.d/org.freedesktop.locale1.conf 5893ab03e7e96aa3759baceb4dd04190
 /etc/dbus-1/system.d/org.freedesktop.hostname1.conf f55c94d000b5d62b5f06d38852977dd1
 /etc/dbus-1/system.d/org.freedesktop.login1.conf dad9f3cbe8feac9d6ae686a1da816b56
 /etc/dbus-1/system.d/org.freedesktop.timedate1.conf 682369fbf3de26b21e775732c89a2bbe
 /etc/systemd/logind.conf 24cc087eb0d0ac88d097c1b96420a999
Description: systemd runtime services
--
Multi-Arch: same
Source: libusbx
Version: 2:1.0.16-3
Depends: libc6 (>= 2.17), libudev1 (>= 183)
Pre-Depends: multiarch-support
Description: userspace USB programming library
 Library for programming USB applications without the knowledge
 of Linux kernel internals.
 .
 This package contains what you need to run programs that use this
 library.
Original-Maintainer: Aurelien Jarno <aurel32@debian.org>
Homepage: http://www.linux-usb.org/


--
Multi-Arch: same
Source: libusbx
Version: 2:1.0.16-3
Depends: libc6 (>= 2.17), libudev1 (>= 183)
Pre-Depends: multiarch-support
Description: userspace USB programming library
 Library for programming USB applications without the knowledge
 of Linux kernel internals.
 .
 This package contains what you need to run programs that use this
 library.
Original-Maintainer: Aurelien Jarno <aurel32@debian.org>
Homepage: http://www.linux-usb.org/


--
Source: xserver-xorg-video-ati
Version: 1:7.2.0-0ubuntu10
Provides: xorg-driver-video
Depends: libc6 (>= 2.17), libdrm-radeon1 (>= 2.4.39), libglamor0, libudev1 (>= 183), xorg-video-abi-14, xserver-xorg-core (>= 2:1.14.2.901-2ubuntu4~)
Suggests: linux-firmware
Description: X.Org X server -- AMD/ATI Radeon display driver
 This package provides the 'radeon' driver for the AMD/ATI cards. The
 following chips should be supported: R100, RV100, RS100, RV200, RS200,
 RS250, R200, RV250, RV280, RS300, RS350, RS400/RS480, R300, R350, R360,
 RV350, RV360, RV370, RV380, RV410, R420, R423/R430, R480/R481,
 RV505/RV515/RV516/RV550, R520, RV530/RV560, RV570/R580,
 RS600/RS690/RS740, R600, RV610/RV630, RV620/RV635, RV670, RS780/RS880,
 RV710/RV730, RV740/RV770/RV790, CEDAR, REDWOOD, JUNIPER, CYPRESS,
 HEMLOCK, PALM, SUMO/SUMO2, BARTS, TURKS, CAICOS, CAYMAN, ARUBA.
--
Multi-Arch: foreign
Version: 2.52
Replaces: upstart (<< 0.6.3-2)
Depends: makedev, udev, plymouth, coreutils (>= 7.1), libc6 (>= 2.9), libdbus-1-3 (>= 1.2.16), libnih-dbus1 (>= 1.0.0), libnih1 (>= 1.0.0), libplymouth2 (>= 0.8.1-3), libudev1 (>= 183)
Pre-Depends: dpkg (>= 1.15.7.2)
Breaks: initscripts (<< 2.88dsf-13.3), policycoreutils (<< 2.0.69-2ubuntu4), usplash (<< 0.5.47)
Conffiles:
 /etc/dbus-1/system.d/Mountall.Server.conf 91b1414af1257d2ef089f84a3e5c1ed1
 /etc/init/mtab.sh.conf 27aece82dbe70232d734d1dadfe87518
 /etc/init/mounted-proc.conf 07198659bd06c1442a35882b2fae05fc
 /etc/init/checkroot.sh.conf 3ea7f6ba450f431fd239e2b53a805216
 /etc/init/mountall-reboot.conf 43e3c229085a13005b0681a49b2bef51
 /etc/init/mounted-tmp.conf 289fa57d726885147a41b2b1f3695a29
 /etc/init/mounted-var.conf 02f90856c91a46e9cbed1c35b92fec6c
--
Multi-Arch: same
Source: libatasmart
Version: 0.19-2ubuntu1
Depends: libc6 (>= 2.14), libudev1 (>= 183)
Pre-Depends: multiarch-support
Description: ATA S.M.A.R.T. reading and parsing library
 A small and lightweight parser library for ATA S.M.A.R.T. hard disk
 health monitoring.
 .
 This package contains the shared library.
Homepage: http://0pointer.de/blog/projects/being-smart.html
Original-Maintainer: Utopia Maintenance Team <pkg-utopia-maintainers@lists.alioth.debian.org>


Package: doc-base
--
Architecture: amd64
Version: 1:2.7.3-0ubuntu3.1
Provides: xorg-driver-input
Depends: libc6 (>= 2.14), libmtdev1 (>= 1.1.0), libudev1 (>= 183), xorg-input-abi-19, xserver-xorg-core (>= 2:1.13.99.901)
Description: X.Org X server -- evdev input driver
 This package provides the driver for input devices using evdev, the Linux
 kernel's event delivery mechanism.  This driver allows for multiple keyboards
 and mice to be treated as separate input devices.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-input-evdev driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
--
Multi-Arch: same
Source: qtbase-opensource-src
Version: 5.0.2+dfsg1-7ubuntu11.1
Depends: fontconfig, libc6 (>= 2.14), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.3.5), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libjpeg8 (>= 8c), libpng12-0 (>= 1.2.13-4), libqt5core5 (= 5.0.2+dfsg1-7ubuntu11.1), libqt5dbus5 (= 5.0.2+dfsg1-7ubuntu11.1), libstdc++6 (>= 4.1.1), libudev1 (>= 183), libx11-6, libx11-xcb1, libxcb-glx0, libxcb-icccm4 (>= 0.3.9), libxcb-image0 (>= 0.3.9), libxcb-keysyms1 (>= 0.3.9), libxcb-randr0 (>= 1.3), libxcb-render-util0 (>= 0.3.8), libxcb-render0, libxcb-shape0, libxcb-shm0, libxcb-sync0, libxcb-xfixes0, libxcb1, libxi6 (>= 2:1.2.99.4), libxrender1, zlib1g (>= 1:1.1.4)
Pre-Depends: dpkg (>= 1.15.6~), multiarch-support
Description: Qt 5 GUI module
 Qt is a cross-platform C++ application framework. Qt's primary feature
 is its rich set of widgets that provide standard GUI functionality.
 .
 The QtGui module extends QtCore with GUI functionality.
Homepage: http://qt-project.org/
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>


Package: locales
--
Architecture: amd64
Source: kde4libs
Version: 4:4.11.3-0ubuntu0.1
Depends: libc6 (>= 2.14), libqt4-dbus (>= 4:4.7.0), libqt4-xml (>= 4:4.7.0), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.7.0), libstdc++6 (>= 4.1.1), libudev1 (>= 183), udev
Recommends: udisks2, upower
Suggests: media-player-info
Breaks: kde-config-tablet (<< 1.2.5)
Description: Solid Library for KDE Platform
 Solid is a device integration framework. It provides a way of querying and
 interacting with hardware independently of the underlying operating system.
 .
 This package is part of the KDE Development Platform libraries module.
Homepage: http://solid.kde.org/
Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
--
Architecture: amd64
Source: system-config-printer
Version: 1.4.2+20130920-0ubuntu1.1
Depends: libc6 (>= 2.14), libcups2 (>= 1.6.0), libglib2.0-0 (>= 2.12.0), libudev1 (>= 183), libusb-1.0-0 (>= 2:1.0.8), python-cups (>= 1.9.55), python-dbus, python-cupshelpers
Description: Printer auto-configuration facility based on udev
 A CUPS printer configuration tool and status applet.
 .
 This package provides udev rules and callouts for auto-setup of
 print queues (Plug'n'Print) and for automatic disabling and
 re-enabling print queues when the printer gets disconnected and
 reconnected.
Original-Maintainer: Otavio Salvador <otavio@ossystems.com.br>


Package: libphysfs1
--
Multi-Arch: same
Source: mesa
Version: 9.2.1-1ubuntu3
Depends: libc6 (>= 2.14), libdrm-nouveau2 (>= 2.4.38), libdrm-radeon1 (>= 2.4.31), libdrm2 (>= 2.4.38), libegl1-mesa (= 9.2.1-1ubuntu3), libelf1 (>= 0.142), libgbm1 (>= 7.11~1), libgcc1 (>= 1:4.1.1), libgl1-mesa-dri (= 9.2.1-1ubuntu3), libllvm3.3, libopenvg1-mesa (>= 7.9~) | libopenvg1, libstdc++6 (>= 4.6), libudev1 (>= 183), libwayland-client0 (>= 1.0.2), libwayland-server0 (>= 1.0.2), libx11-6 (>= 2:1.4.99.1), libxext6, libxfixes3, libglapi-mesa (= 9.2.1-1ubuntu3)
Pre-Depends: multiarch-support
Description: free implementation of the EGL API -- hardware drivers
 This package contains the EGL native platform graphics interface library.
 EGL provides a platform-agnostic mechanism for creating rendering surfaces
 for use with other graphics libraries, such as OpenGL|ES and OpenVG.
 .
 This package contains the drivers required for hardware accelerated rendering
 of EGL-based graphics libraries, such as OpenGL|ES and OpenVG.
Homepage: http://mesa3d.sourceforge.net/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
--
Source: gudev-sharp-1.0
Version: 0.1-3
Depends: cli-common (>= 0.5.1), libglib2.0-cil (>= 2.12.10-1ubuntu1), libgudev-1.0-0 (>= 146), libmono-corlib4.0-cil (>= 2.10.1)
Description: GObject-based wrapper library for libudev -- CLI bindings
 gudev-sharp is a set of CLI bindings for libgudev, which is a GObject-based
 wrapper library for libudev.
 .
 This package contains the managed CLI bindings for gudev-sharp, which are
 needed to run CLI applications which use this library.
Original-Maintainer: Debian CLI Libraries Team <pkg-cli-libs-team@lists.alioth.debian.org>
Homepage: https://www.launchpad.net/gudev-sharp


Package: wesnoth-1.10-sotbe
Status: install ok installed
Priority: optional
Section: games
--
Architecture: amd64
Source: initramfs-tools
Version: 0.103ubuntu1.1
Depends: libc6 (>= 2.4), libudev1 (>= 183)
Description: binaries used by initramfs-tools
 This package contains binaries used inside the initramfs images generated
 by initramfs-tools.
Original-Maintainer: Debian kernel team <debian-kernel@lists.debian.org>


Package: folks-common
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 64
--
Multi-Arch: same
Source: lvm2 (2.02.98-6ubuntu1)
Version: 2:1.02.77-6ubuntu1
Depends: libc6 (>= 2.14), libselinux1 (>= 1.32), libudev1 (>= 183), dmsetup (>= 2:1.02.77-6ubuntu1)
Pre-Depends: multiarch-support
Breaks: lvm2 (<< 2.02.66)
Conflicts: libdevmapper1.02
Description: Linux Kernel Device Mapper userspace library
 The Linux Kernel Device Mapper is the LVM (Linux Logical Volume Management)
 Team's implementation of a minimalistic kernel-space driver that handles
 volume management, while keeping knowledge of the underlying device layout
 in user-space.  This makes it useful for not only LVM, but EVMS, software
 raid, and other drivers that create "virtual" block devices.
 .
--
Multi-Arch: same
Source: lvm2
Version: 2.02.98-6ubuntu1
Depends: libc6 (>= 2.14), libdevmapper-event1.02.1 (>= 2:1.02.74), libdevmapper1.02.1 (>= 2:1.02.77), libudev1 (>= 183)
Pre-Depends: multiarch-support
Description: LVM2 application library
 This package contains the lvm2app shared library. It allows easier access
 to the basic LVM objects and provides functions to enumerate, create or
 modify them.
Homepage: http://sources.redhat.com/lvm2/
Original-Maintainer: Debian LVM Team <pkg-lvm-maintainers@lists.alioth.debian.org>


Package: python3-defer
Status: install ok installed
--
Multi-Arch: foreign
Version: 1.0.4-8ubuntu1
Replaces: devicekit-disks
Depends: libatasmart4 (>= 0.13), libc6 (>= 2.14), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libdevmapper1.02.1 (>= 2:1.02.20), libglib2.0-0 (>= 2.37.3), libgudev-1.0-0 (>= 146), liblvm2app2.2 (>= 2.02.98), libparted0debian1 (>= 2.2-1), libpolkit-gobject-1-0 (>= 0.99), libsgutils2-2 (>= 1.27), libudev1 (>= 183), udev, dbus
Recommends: policykit-1, hdparm, dosfstools, ntfs-3g, eject, cryptsetup-bin
Suggests: xfsprogs, reiserfsprogs, mdadm
Breaks: libgdu-gtk0 (<< 2.28), libgdu0 (<< 2.28)
Conflicts: devicekit-disks
Conffiles:
 /etc/avahi/services/udisks.service a0372c812d283ec1973c2461afd64774
 /etc/dbus-1/system.d/org.freedesktop.UDisks.conf ed1fcf897e31049909a921f2b4cfd026
Description: storage media interface
 The udisks daemon serves as an interface to system block devices,
 implemented via D-Bus. It handles operations such as querying, mounting,
--
Source: consolekit (0.4.6-3)
Version: 0.4.6-3+b1
Replaces: udev (<< 204-1)
Depends: libacl1 (>= 2.2.51-8), libc6 (>= 2.4), libck-connector0 (= 0.4.6-3+b1), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libglib2.0-0 (>= 2.31.8), libpolkit-gobject-1-0 (>= 0.94), libudev1 (>= 183), libx11-6, zlib1g (>= 1:1.1.4), dbus (>= 1.1.2)
Recommends: libpam-ck-connector
Breaks: udev (<< 204-1)
Conffiles:
 /etc/logrotate.d/consolekit 94c8a5d4828b67bcabe2e9ef0d301921
 /etc/X11/Xsession.d/90consolekit 628cccb5bdaaf3388da6b09c02eb07c8
 /etc/ConsoleKit/seats.d/00-primary.seat eb3f3c54b501dbdaf38dbc38a4ee91fe
 /etc/dbus-1/system.d/ConsoleKit.conf 9a2dbb48a49638bf1cb1b5ff90755a29
Description: framework for defining and tracking users, sessions and seats
 ConsoleKit is a system daemon for tracking what users are logged
 into the system and how they interact with the computer (e.g.
--
Version: 31.0.1650.63-1
Replaces: google-chrome
Provides: google-chrome, www-browser
Depends: gconf-service, libasound2 (>= 1.0.23), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.11), libcairo2 (>= 1.6.0), libcups2 (>= 1.4.0), libdbus-1-3 (>= 1.2.14), libexpat1 (>= 1.95.8), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.3.9), libgcc1 (>= 1:4.1.1), libgconf-2-4 (>= 2.31.1), libgcrypt11 (>= 1.4.5), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.18.0), libgtk2.0-0 (>= 2.24.0), libnspr4 (>= 1.8.0.10), libnss3 (>= 3.14.3), libpango1.0-0 (>= 1.22.0), libstdc++6 (>= 4.6), libudev0 (>= 147) | libudev1 (>= 198), libx11-6 (>= 2:1.4.99.1), libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxi6 (>= 2:1.2.99.4), libxrender1, libxss1, libxtst6, ca-certificates, libcurl3, lsb-base (>= 3.2), xdg-utils (>= 1.0.2), wget
Pre-Depends: dpkg (>= 1.14.0)
Conflicts: google-chrome
Description: The web browser from Google
 Google Chrome is a browser that combines a minimal design with sophisticated technology to make the web faster, safer, and easier.


Package: banshee-extension-coverwallpaper
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 62
--
Version: 1.10-0ubuntu7
Replaces: startup-tasks, system-services, sysvinit, upstart-compat-sysv, upstart-job
Provides: startup-tasks, system-services, upstart-compat-sysv, upstart-job
Depends: libc6 (>= 2.15), libdbus-1-3 (>= 1.2.16), libjson-c2 (>= 0.10), libnih-dbus1 (>= 1.0.0), libnih1 (>= 1.0.0), libudev1 (>= 183), sysvinit-utils, sysv-rc, initscripts, mountall, ifupdown (>= 0.6.10ubuntu5), libjson0 (>= 0.10-1.1ubuntu1), debianutils (>= 4)
Suggests: python3, graphviz, bash-completion, upstart-monitor
Breaks: friendly-recovery (<< 0.2.13), libc6 (<< 2.12.1-0ubuntu12)
Conflicts: lxcguest, startup-tasks, system-services, sysvinit, upstart-compat-sysv, upstart-job
Conffiles:
 /etc/bash_completion.d/upstart 080f7eee4a3f3e5f76197eaa581fb4da
 /etc/X11/Xsession.d/00upstart 46b4576b1f2ceffb2450a88d58786b95
 /etc/X11/Xsession.d/99upstart d150fce36cf22f5504e4dbc89b4826e0
 /etc/logrotate.d/upstart 070767086a27883ec119e1dde779a856
 /etc/dbus-1/system.d/Upstart.conf 64be74cddb0c74b7d98202b40389784c
 /etc/upstart-xsessions ec9aa92a5c50938479d711daa9ee774a
--
Version: 2.0.8-1
Replaces: vlc (<< 1.1.0)
Provides: mp3-decoder
Depends: liba52-0.7.4, libasound2 (>= 1.0.16), libass4 (>= 0.9.7), libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavc1394-0 (>= 0.5.3), libavcodec53 (>= 6:0.8.3-1~) | libavcodec-extra-53 (>= 6:0.8.7), libavformat53 (>= 6:0.8.3-1~) | libavformat-extra-53 (>= 6:0.8.7), libavutil51 (>= 6:0.8.3-1~) | libavutil-extra-51 (>= 6:0.8.7), libbluray1, libc6 (>= 2.16), libcddb2, libcdio13 (>= 0.83), libcrystalhd3, libdbus-1-3 (>= 1.2.16), libdc1394-22, libdca0, libdirac-encoder0, libdirectfb-1.2-9, libdvbpsi8 (>= 1.0.0), libdvdnav4 (>= 4.2.0+20120524), libdvdread4, libebml3, libfaad2 (>= 2.7), libflac8 (>= 1.3.0), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.2.1), libfribidi0 (>= 0.19.2), libgcc1 (>= 1:4.1.1), libgcrypt11 (>= 1.4.5), libgnutls26 (>= 2.12.17-0), libgpg-error0 (>= 1.10), libkate1 (>= 0.3.0), liblircclient0, liblua5.1-0, libmad0 (>= 0.15.1b-3), libmatroska5, libmodplug1, libmpcdec6 (>= 1:0.1~r435), libmpeg2-4, libmtp9 (>= 1.1.0), libncursesw5 (>= 5.6+20070908), libogg0 (>= 1.1.0), libopus0, libpng12-0 (>= 1.2.13-4), libpostproc52 (>= 6:0.8.3-1~) | libpostproc-extra-52 (>= 6:0.8.7), libproxy1 (>= 0.4.7), libraw1394-11, libresid-builder0c2a, libsamplerate0 (>= 0.1.7), libschroedinger-1.0-0 (>= 1.0.10), libshout3, libsidplay2, libsmbclient (>= 3.0.24), libspeex1 (>= 1.2~beta3-1), libspeexdsp1 (>= 1.2~beta3.2-1), libssh2-1 (>= 1.2), libstdc++6 (>= 4.6), libswscale2 (>= 6:0.8.3-1~) | libswscale-extra-2 (>= 6:0.8.7), libtag1c2a (>= 1.7), libtheora0 (>= 1.0), libtinfo5, libtwolame0, libudev1 (>= 183), libupnp6 (>= 1.4.3), libv4l-0 (>= 0.5.0), libvcdinfo0 (>= 0.7.21), libvlc5 (>= 2.0.0), libvlccore5 (>= 2.0.2), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libx264-123, libxml2 (>= 2.7.4), libzvbi0 (>= 0.2.11), zlib1g (>= 1:1.2.0.2)
Pre-Depends: dpkg (>= 1.15.6~)
Description: multimedia player and streamer (without X support)
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG-2, MPEG-4,
 DivX, MOV, WMV, QuickTime, WebM, FLAC, MP3, Ogg/Vorbis files, DVDs, VCDs,
 podcasts, and multimedia streams from various network sources.
 .
 VLC can also be used as a streaming server that duplicates the stream it
 reads and multicasts them through the network to other clients, or serves
 them through HTTP.
 .
--
Architecture: amd64
Version: 0.8.0-0ubuntu1.1
Provides: xorg-driver-video
Depends: libc6 (>= 2.4), libdrm2 (>= 2.4.38), libudev1 (>= 183), xorg-video-abi-14, xserver-xorg-core (>= 2:1.13.99.901)
Description: X.Org X server -- Generic modesetting driver
 This package provides a generic modesetting driver.
 .
 More information about X.Org can be found at:
 <URL:http://www.X.org>
 .
 This package is built from the X.org xf86-video-modesetting driver module.
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>


Package: texlive-font-utils
--
Architecture: amd64
Version: 1:1.0.9-2ubuntu1
Provides: xorg-driver-video
Depends: libc6 (>= 2.15), libdrm-nouveau2 (>= 2.4.38), libdrm2 (>= 2.4.25), libudev1 (>= 183), xorg-video-abi-14, xserver-xorg-core (>= 2:1.14.2.901-2ubuntu4~)
Recommends: libgl1-mesa-dri (>= 9.0)
Description: X.Org X server -- Nouveau display driver
 This driver for the X.Org X server (see xserver-xorg for a further description)
 provides support for NVIDIA Riva, TNT, GeForce, and Quadro cards.
 .
 This package provides 2D support including EXA acceleration, Xv and
 RandR.  3D functionality is provided by the libgl1-mesa-dri package.
 .
 This package is built from the FreeDesktop.org xf86-video-nouveau driver.
Homepage: http://nouveau.freedesktop.org/wiki/
--
Architecture: amd64
Multi-Arch: same
Version: 1.18.2-0ubuntu1
Depends: libc6 (>= 2.14), libglib2.0-0 (>= 2.37.3), libudev1 (>= 183), gvfs-daemons (>= 1.18.2-0ubuntu1), gvfs-daemons (<< 1.18.2-0ubuntu1.1~), gvfs-libs (= 1.18.2-0ubuntu1), gvfs-common (= 1.18.2-0ubuntu1)
Suggests: gvfs-backends, gvfs-backends-goa
Breaks: brasero (<< 2.28.0-2), libgdu0 (<< 2.28.1-3), libglib2.0-0 (<< 2.30), rhythmbox (<< 0.12.6-2)
Description: userspace virtual filesystem - GIO module
 gvfs is a userspace virtual filesystem where mounts run as separate
 processes which you talk to via D-Bus. It also contains a gio module
 that seamlessly adds gvfs support to all applications using the gio
 API. It also supports exposing the gvfs mounts to non-gio applications
 using fuse.
 .
 This package contains the GIO module that lets applications use gvfs
--
Architecture: i386
Multi-Arch: same
Version: 1.18.2-0ubuntu1
Depends: libc6 (>= 2.7), libglib2.0-0 (>= 2.37.3), libudev1 (>= 183), gvfs-daemons (>= 1.18.2-0ubuntu1), gvfs-daemons (<< 1.18.2-0ubuntu1.1~), gvfs-libs (= 1.18.2-0ubuntu1), gvfs-common (= 1.18.2-0ubuntu1)
Suggests: gvfs-backends, gvfs-backends-goa
Breaks: brasero (<< 2.28.0-2), libgdu0 (<< 2.28.1-3), libglib2.0-0 (<< 2.30), rhythmbox (<< 0.12.6-2)
Description: userspace virtual filesystem - GIO module
 gvfs is a userspace virtual filesystem where mounts run as separate
 processes which you talk to via D-Bus. It also contains a gio module
 that seamlessly adds gvfs support to all applications using the gio
 API. It also supports exposing the gvfs mounts to non-gio applications
 using fuse.
 .
 This package contains the GIO module that lets applications use gvfs
--
Architecture: amd64
Version: 2:2.99.904-0ubuntu2
Provides: xorg-driver-video
Depends: libc6 (>= 2.17), libdrm-intel1 (>= 2.4.38), libdrm2 (>= 2.4.30), libpciaccess0 (>= 0.8.0+git20071002), libpixman-1-0 (>= 0.30.0), libudev1 (>= 183), libx11-6, libx11-xcb1, libxcb-dri2-0, libxcb-util0 (>= 0.3.8), libxcb1, libxv1, libxvmc1, xorg-video-abi-14, xserver-xorg-core (>= 2:1.14.2.901-2ubuntu4~)
Description: X.Org X server -- Intel i8xx, i9xx display driver
 This package provides the driver for the Intel i8xx and i9xx family
 of chipsets, including i810, i815, i830, i845, i855, i865, i915, i945
 and i965 series chips.
 .
 This package also provides XvMC (XVideo Motion Compensation) drivers
 for i810/i815 and i9xx and newer chipsets.
 .
 This package is built from the X.org xf86-video-intel driver module.
Homepage: http://www.x.org/
--
Version: 9.2.1-1ubuntu3
Replaces: libegl1-x11
Provides: libegl1-x11
Depends: libc6 (>= 2.14), libdrm2 (>= 2.4.25), libgbm1 (>= 7.11~1), libudev1 (>= 183), libwayland-client0 (>= 1.0.2), libwayland-server0 (>= 1.0.2), libx11-6, libx11-xcb1, libxcb-dri2-0 (>= 1.8), libxcb-xfixes0, libxcb1
Pre-Depends: multiarch-support
Recommends: libegl1-mesa-drivers
Conflicts: libegl1-x11
Description: free implementation of the EGL API -- runtime
 This package contains the EGL native platform graphics interface library.
 EGL provides a platform-agnostic mechanism for creating rendering surfaces
 for use with other graphics libraries, such as OpenGL|ES and OpenVG.
 .
 This package contains modules to interface with the existing system GLX or
 DRI2 drivers to provide OpenGL via EGL.  The libegl1-mesa-drivers package
--
Source: gvfs
Version: 1.18.2-0ubuntu1
Replaces: gvfs (<< 1.10.1-1), gvfs-backends (<< 1.8.1-1)
Depends: libc6 (>= 2.14), libglib2.0-0 (>= 2.37.3), libgudev-1.0-0 (>= 146), libsecret-1-0 (>= 0.7), libsystemd-login0 (>= 31), libudev1 (>= 183), libudisks2-0 (>= 2.0.91), x11-utils, udisks2, gvfs-libs (= 1.18.2-0ubuntu1), gvfs-common (= 1.18.2-0ubuntu1)
Recommends: dbus, policykit-1-gnome, gvfs
Suggests: gvfs-backends, gvfs-backends-goa
Breaks: brasero (<< 2.28.0-2), gvfs (<< 1.10.1-1), gvfs-backends (<< 1.8.1-1), libgdu0 (<< 2.28.1-3), libglib2.0-0 (<< 2.28.6-2), rhythmbox (<< 0.12.6-2)
Description: userspace virtual filesystem - servers
 gvfs is a userspace virtual filesystem where mounts run as separate
 processes which you talk to via D-Bus. It also contains a gio module
 that seamlessly adds gvfs support to all applications using the gio
 API. It also supports exposing the gvfs mounts to non-gio applications
 using fuse.
 .
--
Version: 204-0ubuntu19.1
Config-Version: 204-5
Replaces: systemd-services (<< 202-0ubuntu6)
Depends: libacl1 (>= 2.2.51-8), libblkid1 (>= 2.19.1), libc6 (>= 2.17), libkmod2 (>= 5~), libselinux1 (>= 2.0.65), libudev1 (= 204-0ubuntu19.1), sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), lsb-base (>= 3.0-6), util-linux (>= 2.16)
Recommends: usbutils, pciutils
Conffiles:
 /etc/udev/udev.conf ae415f84e2967eff580089fb08aa0a61
 /etc/udev/rules.d/README 3b6de9f3f911176734c66903b4f8735c
 /etc/init/udev.conf b4fb63a560e94cacf94765c9a371db99
 /etc/init/udevmonitor.conf b541dfb5aa4958e9a5336ecaec00ca15
 /etc/init/udev-finish.conf 28ebb3ad2d2c6ca545d72f3f0769f448
 /etc/init/udev-fallback-graphics.conf b8bfe7164e10cd0e53494b243c5728b1
 /etc/init/udevtrigger.conf 651ff2421dde80be7ce7ccbf7fa8cf18
 /etc/init.d/udev 1ee6bb477e677542ea41fd3d83b6bb1e
--
Multi-Arch: same
Source: mesa
Version: 9.2.1-1ubuntu3
Depends: libc6 (>= 2.14), libdrm2 (>= 2.4.3), libgl1-mesa-dri, libudev1 (>= 183), libwayland-client0 (>= 1.0.2), libwayland-server0 (>= 1.0.2), libxcb-dri2-0, libxcb1
Pre-Depends: multiarch-support
Description: generic buffer management API -- runtime
 This package contains the GBM buffer management library.  It provides a
 mechanism for allocating buffers for graphics rendering tied to Mesa.
 .
 GBM is intended to be used as a native platform for EGL on drm or openwfd.
Homepage: http://mesa3d.sourceforge.net/
Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>


Package: qtchooser
--
Architecture: amd64
Version: 1:4.0-0ubuntu6
Provides: pulseaudio-module-hal, pulseaudio-module-rygel-media-server, pulseaudio-module-udev
Depends: libasound2 (>= 1.0.24.1), libc6 (>= 2.15), libcap2 (>= 2.10), libdbus-1-3 (>= 1.1.1), libfftw3-single3, libltdl7 (>= 2.4.2), liborc-0.4-0 (>= 1:0.4.17), libpulse0 (= 1:4.0-0ubuntu6), libsamplerate0 (>= 0.1.7), libsndfile1 (>= 1.0.20), libspeexdsp1 (>= 1.2~beta3.2-1), libsystemd-login0 (>= 31), libtdb1 (>= 1.2.7+git20101214), libudev1 (>= 183), libx11-6, libx11-xcb1, sysv-rc (>= 2.88dsf-24) | file-rc (>= 0.8.16), adduser, lsb-base (>= 3.2-13), libpam-systemd, udev (>= 143), libasound2-plugins
Recommends: pulseaudio-module-x11, gstreamer0.10-pulseaudio, rtkit, pulseaudio-utils
Suggests: pavumeter, paman, pavucontrol, paprefs, pulseaudio-module-raop, pulseaudio-esound-compat
Conflicts: libltdl3 (<< 1.5.24-1)
Conffiles:
 /etc/init.d/pulseaudio df2873ee4f4673d53e3562a0de6e8aa0
 /etc/xdg/autostart/pulseaudio.desktop f241e9ea5e8d02e727e29075ec57d873
 /etc/xdg/autostart/pulseaudio-kde.desktop fd20c58d32035e908a0866784e4e3511
 /etc/default/pulseaudio 777f75f5521eab11c647da5c55544b1b
 /etc/dbus-1/system.d/pulseaudio-system.conf 43aae9c1b1204b4cbb56530377924579
 /etc/pulse/default.pa 615fc52a0797d685091f2f27b99865e5

```

---

### Post by Bashing-om on 2013-12-24
slgtheindividual; Welp;

I am looking and it is to me as confusing an issue as ever - and maybe more so - .

But, here looks to be the rub:
> 
Package: libudev1
Status: install ok unpacked
Priority: important
Section: libs
Installed-Size: 118
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: same
Source: systemd
Version: 204-0ubuntu19.1
[color=red]Config-Version: 204-5[/color]

Compounding matters even more:
> 
Package: libudev1
Status: install ok half-configured
Priority: important
Section: libs
Installed-Size: 93
Maintainer: Debian systemd Maintainers <pkg-systemd-maintainers@lists.alioth.debian.org>
Architecture: i386
Multi-Arch: same
Source: systemd
Version: 204-5
[color=red]Config-Version: 204-5[/color]



looking at what I have seen in respect to most dependency for libudev1 is " libudev1 (>= 183)":
> 
Source: consolekit (0.4.6-3)
<snip>
Version: 31.0.1650.63-1
Replaces: google-chrome
Provides: google-chrome, www-browser
Depends: -->>libudev0 (>= 147) | libudev1 (>= 198),

XXX

Package: texlive-font-utils
<snip>
Architecture: i386
Depends: -->>libudev1 (>= 183)
<snip some more>
and then there is this !
--
Version: 204-0ubuntu19.1
Config-Version: 204-5
Depends: -->> libudev1 (= 204-0ubuntu19.1) (mine !!!)


When I am fresher in my AM I will look at this and see what I can make of it.

[INDENT][INDENT]maybe the light will shine
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-12-26
slgtheindividual; As I continue to struggle with this !

I do not understand the fact that there are 2 instances of "libudev1" installed, nor (!!) how the system differentiates between them, as each has the same name.
Presently I have no recommendation to make - I do have an idea - Before I make a proposal, what is the result of ? :
```

grep -B3 -A10 "libudev1*" /var/lib/dpkg/available
grep -B3 -A10 libudev1 /var/lib/dpkg/available
grep "Package:\ libudev1*" /var/lib/dpkg/available

```

I still have in mind to make an edit to the control file(s).

[INDENT][INDENT]keep'n the 7 P's in mind
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-12-26
Bashing-on, where are you seeing 2 versions installed? what catches my eye is that the 204-5 config is **not** installed - from the Debian Policy Manual

> 
D.2.4 Config-Version

If a package is not installed or not configured, this field in dpkg's status file records the last version of the package which was successfully configured. 


Have you tried removing wine (and all its dependencies)? That should remove the i386 versions which may simplify things

If that doesn't help (or packages won't remove because of the current state) then how about trying dpkg with --force-downgrade or --force-bad-version? That might be a little safer than manually editing control files.

---

### Post by Bashing-om on 2013-12-26
@ steeldriver; Appreciate the fact someone is watching over my shoulder.

I am undecided on a best practice. Removing the source of the 32 bit libs would go a long way to finding a solution. And as stated earlier, I too think that the culprit is likely to be Wine.

This says to me there are 2 versions not completely installed:
From the output of: "grep -B3 -A10 "libudev1*" /var/lib/dpkg/status" :
> 
Package: libudev1
Status: install ok unpacked
Priority: important
Section: libs
[color=red]Installed-Size: 118[/color]

bk

Package: libudev1
Status: install ok half-configured
Priority: important
Section: libs
[color=red]Installed-Size: 93[/color]

To this time I have not been able to isolate the versions. I am about at my wit's end to downgrade "libudev1" and "udev" to the proper versions for the saucy install.

Any insight is highly appreciated, There is a lot I do not know about the checks and balances in place by the package management system. Believe me I hold great respect for those checks/balances.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by slgtheindividual on 2013-12-27
Hi all, I'm sorry I've been absent for a while. Basically this all came to a head when I turned my computer on a day or so ago and I could no longer either connect to the internet or produce any sound (the sound options had only 'dummy' available.) I ended up doing a complete reinstall of 13.10 from an installation usb I had because I needed the internet urgently, luckily all my problems are now fixed and my files were all safely backed up elsewhere so I'm now in the process of restoring everything. I'm sorry at the somewhat unsatisfying end of never solving the root problem, the internet really forced my hand. I just want to thank you all again for your persistence with this.

---

### Post by Bashing-om on 2013-12-27
slgtheindividual; Whewewhh,

The nuclear solution always works ! Pleased all is back to normal, and no - all this was not in vain as we did learn a bit about this wonderful operating system.

[INDENT][INDENT]'till next time -
[INDENT][INDENT][INDENT]happy trails to you
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

