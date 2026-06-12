---
title: "Can't get updates. Help please?"
date: 2007-05-17
forum: General Help
---

### Post by paydaydaddy on 2007-05-17
Running Dapper Drake. I have the little orange update square showing. When I click on it I get a message telling me that I have broken software and I should run apt-get or synaptic to fix the problem. In the terminal I get this:

[ diamond@diamond:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2849kB of archives.
After unpacking 8192B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 118850 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.2 (using .../samba_3.0.22-1ubuntu3.3_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
diamond@diamond:~$ ]

In synaptic I get this:

[ E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb: subprocess new pre-removal script returned error exit status 102 ]

I guess samba is broken but I can't figure out the fix. Any clues from the Gurus?

---

### Post by zvacet on 2007-05-17
```
sudo dpkg --configure -a
```

---

### Post by paydaydaddy on 2007-05-17
I ran [ sudo dpkg --configure -a ] in a terminal. It returns nothing. What am I missing?

---

### Post by paydaydaddy on 2007-05-18
I guess it is one package that has to do with Samba that is broken. I found the package but so far have been unable to delete it.I think if I can figure out how to log in as administrator then I can manually delete it and then re-install. I will search the forum for clues. In the meantime, anybody that wants to jump in with helpful advice please do.

---

### Post by paydaydaddy on 2007-05-18
Here is the result of trying to remove samba so I could re-install.

diamond@diamond:~$ sudo apt-get --purge remove samba
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 119778 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--purge):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
diamond@diamond:~$

---

### Post by paydaydaddy on 2007-05-18
Anybody with any ideas?

---

### Post by paydaydaddy on 2007-05-18
I have been unable to delete the faulty file. I am near my wits end and am considering doing an complete re-install.

---

### Post by mbradlcu on 2007-05-19
if you haven't already seen this check out the following link.
[http://premrara.blogspot.com/](http://premrara.blogspot.com/)

Error 3:
The upgrade aborts now. Your system could be in unusable state. A recovery was run (dpkg --configure -a). installArchive() failed.

I checked the logs at /var/log/dist-upgrade. main.log reports the samba error (see Error 2). This is the fix to it:

# cd /etc/rc2.d/
# ls -al
(At this point, you need to check for the broken samba symlink. Remove the symlink.)
# rm K09samba
(Alternatively, use the unlink command.)

To continue with the dist-upgrade: update-manager --dist-upgrade

---

### Post by paydaydaddy on 2007-05-19
Thank you mbradlcu. I have been searching the forums for days and hadn't come up with the info. All fixed now.

---

### Post by stevand on 2007-05-21
I have a simmilar problem .... and I followed your thread instructions .....
and my folder   /etc/ contains 
rc0.d
rc1.d
rc2.d
rc3.d
rc4.d
rc5.d
rc6.d

and in rc6.d there is K19samba 


it looks  like this .....

ls -al
total 8
drwxr-xr-x   2 root root 4096 2007-02-17 11:09 .
drwxr-xr-x 118 root root 4096 2007-05-21 08:57 ..
lrwxrwxrwx   1 root root   13 2006-09-07 07:36 K01gdm -> ../init.d/gdm
lrwxrwxrwx   1 root root   17 2006-09-07 07:36 K01usplash -> ../init.d/usplash
lrwxrwxrwx   1 root root   17 2006-09-07 07:36 K11anacron -> ../init.d/anacron
lrwxrwxrwx   1 root root   13 2006-09-07 07:36 K11atd -> ../init.d/atd
lrwxrwxrwx   1 root root   14 2006-09-07 07:36 K11cron -> ../init.d/cron
lrwxrwxrwx   1 root root   16 2006-09-07 07:36 K19cupsys -> ../init.d/cupsys
lrwxrwxrwx   1 root root   15 2006-09-08 14:21 K19samba -> ../init.d/samba
lrwxrwxrwx   1 root root   22 2006-09-07 07:36 K20acpi-support -> ../init.d/acpi-support
lrwxrwxrwx   1 root root   14 2006-09-07 07:36 K20apmd -> ../init.d/apmd
lrwxrwxrwx   1 root root   20 2006-09-07 07:36 K20bittorrent -> ../init.d/bittorrent
lrwxrwxrwx   1 root root   14 2007-01-04 18:00 K20dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root   18 2006-09-07 07:36 K20festival -> ../init.d/festival
lrwxrwxrwx   1 root root   17 2007-02-17 11:09 K20hddtemp -> ../init.d/hddtemp
lrwxrwxrwx   1 root root   22 2006-09-07 07:36 K20hotkey-setup -> ../init.d/hotkey-setup
lrwxrwxrwx   1 root root   21 2006-09-07 07:36 K20laptop-mode -> ../init.d/laptop-mode
lrwxrwxrwx   1 root root   17 2006-09-07 07:36 K20makedev -> ../init.d/makedev
lrwxrwxrwx   1 root root   23 2006-09-07 07:36 K20nvidia-kernel -> ../init.d/nvidia-kernel
lrwxrwxrwx   1 root root   19 2006-09-07 07:36 K20powernowd -> ../init.d/powernowd
lrwxrwxrwx   1 root root   15 2006-09-07 07:36 K20rsync -> ../init.d/rsync
lrwxrwxrwx   1 root root   15 2006-09-07 07:36 K21acpid -> ../init.d/acpid
lrwxrwxrwx   1 root root   15 2006-09-07 07:36 K21hplip -> ../init.d/hplip
lrwxrwxrwx   1 root root   20 2006-10-29 22:01 K23ntp-server -> ../init.d/ntp-server
lrwxrwxrwx   1 root root   20 2006-09-07 07:36 K25hwclock.sh -> ../init.d/hwclock.sh
lrwxrwxrwx   1 root root   15 2006-09-07 07:36 K25mdadm -> ../init.d/mdadm
lrwxrwxrwx   1 root root   20 2006-09-07 07:36 K50alsa-utils -> ../init.d/alsa-utils
lrwxrwxrwx   1 root root   21 2006-09-07 07:36 K74bluez-utils -> ../init.d/bluez-utils
lrwxrwxrwx   1 root root   13 2006-09-07 07:36 K86ppp -> ../init.d/ppp
lrwxrwxrwx   1 root root   16 2006-09-07 07:36 K88pcmcia -> ../init.d/pcmcia
lrwxrwxrwx   1 root root   21 2006-09-07 07:36 K88pcmciautils -> ../init.d/pcmciautils
lrwxrwxrwx   1 root root   15 2006-09-07 07:36 K89klogd -> ../init.d/klogd
lrwxrwxrwx   1 root root   18 2006-09-07 07:36 K90sysklogd -> ../init.d/sysklogd
lrwxrwxrwx   1 root root   41 2006-09-07 07:36 S01linux-restricted-modules-common -> ../init.d /linux-restricted-modules-common
lrwxrwxrwx   1 root root   18 2006-09-07 07:36 S20sendsigs -> ../init.d/sendsigs
lrwxrwxrwx   1 root root   17 2006-09-07 07:36 S30urandom -> ../init.d/urandom
lrwxrwxrwx   1 root root   22 2006-09-07 07:36 S31umountnfs.sh -> ../init.d/umountnfs.sh
lrwxrwxrwx   1 root root   20 2006-09-07 07:36 S35networking -> ../init.d/networking
lrwxrwxrwx   1 root root   18 2006-09-07 07:36 S40umountfs -> ../init.d/umountfs
lrwxrwxrwx   1 root root   14 2006-09-07 07:36 S49evms -> ../init.d/evms
lrwxrwxrwx   1 root root   13 2006-09-07 07:36 S50lvm -> ../init.d/lvm
lrwxrwxrwx   1 root root   20 2006-09-07 07:36 S50mdadm-raid -> ../init.d/mdadm-raid
lrwxrwxrwx   1 root root   20 2006-09-07 07:36 S60umountroot -> ../init.d/umountroot
lrwxrwxrwx   1 root root   16 2006-09-07 07:36 S90reboot -> ../init.d/reboot



Question : can I do in the same way (unlink K19samba) and fix the problem ? please advise
thanks

---

### Post by mbradlcu on 2007-05-21
I believe so,, also you can run:
```
update-rc.d -f samba remove
```
this should remove any links in the rc.* dirs.
to add them back use:
```
update-rc.d {service_found_in_/etc/init.d/*} defaults
```

---

### Post by stevand on 2007-05-21
Hi ... there and thanks for the help ... still I think I generated more problems I did 

update-rc.d -f samba remove

and then icon for the update still flashes and when I click it gives me 

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://packages.freecontrib.org/plf/dists/dapper/Release.gpg:](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg:) Could not resolve 'packages.freecontrib.org'
[http://www.beerorkid.com/compiz/dists/dapper/Release.gpg:](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg:) The HTTP server sent an invalid reply header
[http://ubuntu.compiz.net/dists/dapper/Release.gpg:](http://ubuntu.compiz.net/dists/dapper/Release.gpg:) Could not resolve 'ubuntu.compiz.net'
[http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.gz:](http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages.gz:) Could not resolve 'ubuntu.compiz.net'
[http://packages.freecontrib.org/plf/dists/dapper/main/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/main/binary-i386/Packages.gz:) Could not resolve 'packages.freecontrib.org'
[http://packages.freecontrib.org/plf/dists/dapper/restricted/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/restricted/binary-i386/Packages.gz:) Could not resolve 'packages.freecontrib.org'
[http://packages.freecontrib.org/plf/dists/dapper/universe/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/universe/binary-i386/Packages.gz:) Could not resolve 'packages.freecontrib.org'
[http://packages.freecontrib.org/plf/dists/dapper/multiverse/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/multiverse/binary-i386/Packages.gz:) Could not resolve 'packages.freecontrib.org'
[http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i386/Packages.gz:) Could not resolve 'packages.freecontrib.org'
[http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary-i386/Packages.gz:) Could not resolve 'packages.freecontrib.org'
[http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz:](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Packages.gz:) Bad header line



This is even more confusing ... now ....any advice what to do ... and to get all thing in the bussiness as usuall

thanks

stevan

---

### Post by mbradlcu on 2007-05-21
I'm not sure if those package repos are still active. I would remove them and do a:
```
sudo  apt-get update
```

freecontrib packages are cool, but I think they're available through the universe or multiversity packages.
Is you system running dapper?

---

### Post by stevand on 2007-05-21
I did this ... it seems it runs dapper ...

sudo apt-get update
Password:
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release.gpg
  Could not resolve 'ubuntu.compiz.net'
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper Release
Ign [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
Err [http://ubuntu.compiz.net](http://ubuntu.compiz.net) dapper/main Packages
  Could not resolve 'ubuntu.compiz.net'
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:5 [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release.gpg
  The HTTP server sent an invalid reply header
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper Release
Ign [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
Err [http://www.beerorkid.com](http://www.beerorkid.com) dapper/main Packages
  Bad header line
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper Release

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:6 [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper Release [17.2kB]
Ign [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper Release
Hit [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper/main Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Could not resolve 'packages.freecontrib.org'
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/main Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/restricted Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/universe Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/multiverse Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/main Packages
  Could not resolve 'packages.freecontrib.org'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/restricted Packages
  Could not resolve 'packages.freecontrib.org'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/universe Packages
  Could not resolve 'packages.freecontrib.org'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/multiverse Packages
  Could not resolve 'packages.freecontrib.org'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  Could not resolve 'packages.freecontrib.org'
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  Could not resolve 'packages.freecontrib.org'
Fetched 17.4kB in 4s (3836B/s)
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/plf/dists/dapper/Release.gpg)  Co uld not resolve 'packages.freecontrib.org'
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/Release.gpg](http://www.beerorkid.com/compiz/dists/dapper/Release.gpg)  The HT TP server sent an invalid reply header
Failed to fetch [http://ubuntu.compiz.net/dists/dapper/Release.gpg](http://ubuntu.compiz.net/dists/dapper/Release.gpg)  Could not res olve 'ubuntu.compiz.net'
Failed to fetch [http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages](http://ubuntu.compiz.net/dists/dapper/main/binary-i386/Packages). gz  Could not resolve 'ubuntu.compiz.net'
Failed to fetch [http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Pa](http://www.beerorkid.com/compiz/dists/dapper/main/binary-i386/Pa) ckages.gz  Bad header line
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/main/binary-i38](http://packages.freecontrib.org/plf/dists/dapper/main/binary-i38) 6/Packages.gz  Could not resolve 'packages.freecontrib.org'
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/restricted/bina](http://packages.freecontrib.org/plf/dists/dapper/restricted/bina) ry-i386/Packages.gz  Could not resolve 'packages.freecontrib.org'
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/universe/binary](http://packages.freecontrib.org/plf/dists/dapper/universe/binary) -i386/Packages.gz  Could not resolve 'packages.freecontrib.org'
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/multiverse/bina](http://packages.freecontrib.org/plf/dists/dapper/multiverse/bina) ry-i386/Packages.gz  Could not resolve 'packages.freecontrib.org'
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/free/binary-i38](http://packages.freecontrib.org/plf/dists/dapper/free/binary-i38) 6/Packages.gz  Could not resolve 'packages.freecontrib.org'
Failed to fetch [http://packages.freecontrib.org/plf/dists/dapper/non-free/binary](http://packages.freecontrib.org/plf/dists/dapper/non-free/binary) -i386/Packages.gz  Could not resolve 'packages.freecontrib.org'
Reading package lists... Done
W: GPG error: [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de) dapper Release: The following sig natures couldn't be verified because the public key is not available: NO_PUBKEY A5D32F012649A5A9
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.

---

### Post by stevand on 2007-05-21
and it tells me when I go throug synaptic that one package is broken .....

also I think I run kernel 686 instead 386 ... like on my desktop copmuter .. 

is there anyway to fix this ?
thanks

---

### Post by mbradlcu on 2007-05-21
Hi,
thanks for the update,
seems you have a couple problems with your setup.
I don't know how to do it using the synaptic package manager but you'll need to edit your /etc/apt/sources.list and comment out any line referencing [http://ubuntu.compiz.net](http://ubuntu.compiz.net) and [http://www.beerorkid.com](http://www.beerorkid.com),, and [http://packages.freecontrib.org](http://packages.freecontrib.org), [http://apsy.gse.uni-magdeburg.de](http://apsy.gse.uni-magdeburg.de),, I use vi but you may want to use nano, eg:
```
sudo nano /etc/apt/sources.list
```

just put a "#" in the front of the offending lines.. the gpg issue is another problem but lets get it working first then we'll deal with that.

---

### Post by stevand on 2007-05-21
I did this ....

but still when I go through synaptic it tells me that I have 1 broken package 

what to do ?

---

### Post by stevand on 2007-05-21
moreover when I go to synaptic it tells me after I do option fix broken ....

and apply

E: /var/cache/apt/archives/samba_3.0.22-1ubuntu3.3_i386.deb: subprocess new pre-removal script returned error exit status 102

---

### Post by mbradlcu on 2007-05-21
humm, sorry I think I'm at a loss at this point,,

---

### Post by zvacet on 2007-05-21
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -[/B]




gpg --keyserver hkp://subkeys.pgp.net --recv-keys A5D32F012649A5A9
 gpg --export --armor  A5D32F012649A5A9 | sudo apt-key add -

---

### Post by stevand on 2007-05-22
I got this 

 gpg --keyserver hkp://subkeys.pgp.net --recv-keys A5D32F012649A5A9
gpg: requesting key 2649A5A9 from hkp server subkeys.pgp.net
gpg: key 2649A5A9: "apsy.gse.uni-magdeburg.de Debian Archive <michael.hanke@gmail.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
 gpg --export --armor A5D32F012649A5A9 | sudo apt-key add -
Password:
gpg: no ultimately trusted keys found
OK



then what else to do ?

---

### Post by Alhazred on 2007-05-24
Damn, I love these forums. I was having the exact problem and was just gearing up to post about it, but then came across this thread.

Anyway, many thanks to mbradlcu for providing the fix. It's this sort of thing that makes using Ubuntu so satisfying.

---

