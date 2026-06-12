---
title: "vmware player configuration doesn't stick"
date: 2007-09-11
forum: General Help
---

### Post by the_dark_light on 2007-09-11
This is a problem which occurs with vmware player version 2, installed from tarballs.  It doesn't affect the version in the canonical commercial repo.  Problem is that newer distros seem to have some kind of I/O problem that I've only been able to resolve by using the newer version.

Installed from tarball ok (through the vmware-install.pl script)
Ran the vmware-config.pl script.  Followed the directions and compiled kernel modules and set network settings.

Runs fine until I reboot, running vmplayer produces this error:

> dan@mordor:~$ vmplayer
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


So the script needs to be run again, and then the program runs fine.  (I can provide the output from the script, if needed)

Does anyone have any ideas why the program is misbehaving? (Not that it's a big problem, just anoying)

---

### Post by Cornerville on 2007-09-13
I have been having the same problems with vmware also.  I have installed vmplayer and vmserver from both the tarball and via synaptic.  I have been looking for soluions to this and have not found any to date.  You can, however, avoid going through the whole configuration dialog if you enter this command

sudo  rm /etc/vmware/not_configured

It will restore the server until you boot again.  The same thing will happen when you reboot again, though, and you will have to invoke the command again.  

Hope this helps

---

### Post by dabl on 2007-09-13
Probably the command ```
/usr/bin/vmware-config.pl
``` needs to be prefixed with ```
sudo
```

Remember that the VMWare instructions with the tarball are for "generic Linux" and perhaps assume a root/admin user is doing the installation and configuring.   :)

---

### Post by the_dark_light on 2007-09-16
> **dabl said:**
> Probably the command ```
/usr/bin/vmware-config.pl
``` needs to be prefixed with ```
sudo
```

Remember that the VMWare instructions with the tarball are for "generic Linux" and perhaps assume a root/admin user is doing the installation and configuring.   :)

I had thought that at first, but the install script was running as root.

Thanks cornerville:

sudo rm /etc/vmware/not_configured

allows vmware to be run, but network settings don't work (vmware player reports that /dev/vmnet0 can't be opened and virtual ethernet will start disconnected)

According to the installer, the virtual devices were removed.

---

### Post by fisting_mayfield on 2007-09-17
Hi, I found a workaround, 

copy vmware-player-distrib/installer/services.sh from the vmware tar file
rename services.sh to vmware and cp it to /etc/init.d/
Make sure it's executable (sudo chmod 755 /etc/init.d/vmware)

i was stuck with the same problem for ages, but this has just solved it for me

(credit goes to OsuCowboy for the fix)


-Fist

---

### Post by Cornerville on 2007-09-25
> **fisting_mayfield said:**
> Hi, I found a workaround, 

copy vmware-player-distrib/installer/services.sh from the vmware tar file
rename services.sh to vmware and cp it to /etc/init.d/
Make sure it's executable (sudo chmod 755 /etc/init.d/vmware)

i was stuck with the same problem for ages, but this has just solved it for me

(credit goes to OsuCowboy for the fix)


-Fist

I tried this, but it did not work for me.  Same thing happened and I was able to clean it up with the 
Sudo rm /etc/vmware/not_configured command.  I still have network access afterwards.  Wish I knew how to keep this file from being inserted on reboot.  It is no big problem, just annoying.

---

### Post by cyb3rj on 2007-10-03
I'm having a similar problem.

I do not have a "not_configured" file.

I have a vmware and vmware-player file in /etc/init.d.

Every time I reboot, I have to rerun vmware-config.pl or I cannot run vmware-player.

Help?
:confused:

---

### Post by timcredible on 2007-10-03
i installed the latest vmplayer 2 weeks ago from the files on vmware's website.  i ran that script once, and it's worked fine ever since.  i'm using 6.10 though.  i tried installing it from synaptic, but got an error.

---

### Post by Cornerville on 2007-10-16
> **cyb3rj said:**
> I'm having a similar problem.

I do not have a "not_configured" file.

I have a vmware and vmware-player file in /etc/init.d.

Every time I reboot, I have to rerun vmware-config.pl or I cannot run vmware-player.

Help?
:confused:

Remove the vmware file and that should fix your problem

---

### Post by trobbins on 2007-10-16
I found the solution to this problem is to install the VMware "any any" patch.  Read all about it here:


[http://communities.vmware.com/message/76957](http://communities.vmware.com/message/76957)

Here is the contents of this message:

You can redistribute or translate text below as you want, in whole or in part, as long as it is clear that I wrote it. You can also fix grammatical errors during redistribution. Semantic modifications are not allowed without special permission.

========================================================

What is vmware-any-any-update ?

First, if you rely on support from VMware, or you are paying for it, just stop reading here. Unless VMware support told you to download that file and gave you instructions how to apply it, then DO NOT APPLY it. VMware support will not help you if you are running on unsupported host, and I'll not help you either. Now, if you can help yourself, you can continue reading. But you have been warned.

If you find that VMware, VMware Express, VMware Workstation or VMware GSX Server does not work on your Linux host, it is probably time to upgrade your VMware software. So before doing anything make sure that you are using latest product available for your license: VMware 2.0.4, VMware Express 2.0.4, VMware Workstation 3.2.1, VMware GSX Server 1.0.3, VMware GSX Server 2.5.1, VMware Workstation 4.5.2 or VMware GSX Server 3.1.0. Maybe it will fix problem for you, and you'll not have to apply vmware-any-any-update at all. It is especially important to upgrade from WS 3.2.0 to WS 3.2.1.

If you have still problem with building kernel modules, or if VMware application refuses to run complaining that your kernel is too new, it is time to download this patch. You can find latest version of patch at [http://platan.vc.cvut.cz/ftp/pub/vmware](http://platan.vc.cvut.cz/ftp/pub/vmware) , or at its mirror [ftp://ftp.cvut.cz/vmware](ftp://ftp.cvut.cz/vmware)

Filename of patch has form "vmware-<product>-<version>-update<sequence>.tar.gz" where <product> is currently "any" (it was ws/gsx in past; maybe it will be host/tools in future), <version> is currently also "any" (it was build number long ago when patch was not that universal), and <sequence> is just number starting at 1 and incremented with each release.

Download newest file which matches system you are using: currently it is simple, just grab latest vmware-any-any-update*.tar.gz file you can download.

After downloading unpack file into some directory, enter that directory and run "./runme.pl". After doing that run "vmware-config.pl", or, if you installed update on system which is supported by your product (though I do not understand why you installed product in this case) "vmware-config.pl -compile". Note that while original modules from VMware do not need C++ compiler, my updates need it, and won't build without - it is price I had to pay to get support for all these products from one source.

After that your kernel should not complain about problems with kernel modules anymore, and everything should run as on supported host.

And some general advices: if you are having problems with starting your '99 product on your '04 distribution, you should try 'LD_ASSUME_KERNEL=2.2.20 vmware' instead of pure 'vmware'. And make sure that your /tmp filesystem is not mounted with 'noexec' and that you have sufficient space there (several gigs at least).

That should be everything needed. If you want to know what really changed between releases, you can download older versions of patch from 'obsolete' subdirectory of [http://platan.vc.cvut.cz/ftp/pub/vmware](http://platan.vc.cvut.cz/ftp/pub/vmware). It contains all updates I ever released - since first one, which is more than 5 years old.

Petr Vandrovec, Prauge, Oct 30, 2004

---

### Post by georgefairbanks on 2007-12-09
> **Cornerville said:**
> Remove the vmware file and that should fix your problem

This worked for me.  I had two scripts in /etc/init.d -- both vmware and vmware-player.  I deleted the older one and things work ok again.

---

### Post by BABYNSCOTTY on 2008-07-22
HI IM HOPING SOMEONE CAN HELP!!! THIS IS REALLY WEIRD..I LOGGED INTO FACEBOOK AND THEN I SEEN UP IN THE LEFT HAND CORNER..(NEW FACEBOOK) SO I CLICKED ON IT AND MY PAGE CAME UP BLANK SO I TRIED TO GO BACK USING THE ARROW KEY AND THE PAGE DISPLAYS INCOMPATIBLE BROWSER WHEN I TRIED TO GO BACK OR LOGG BACK IN.. AND IT SAYS THE FOLLOWING U ARE USING AND INCOMPATIBLE BROWSER WHICH ISNT TRUE BECAUSE MY HUSBAND WAS ABLE TO LOG INTO HIS ACCOUNT WITH NO PROBLEM BUT HE DIDNT CLICK ON NEW FACEBOOK SO REMEMBER ANYONE ELSE CAN LOGG IN ACCEPT MYSELF...THANKS IF YOUR ABLE TO HELP OUT..I CANT LOGG IN WHAT SO EVER WITH OUT GETTING THIS MESSAGE BELOW...

 HERE I COPIED AND PAST WHAT THE PAGE SAYS


You are using an incompatible web browser.
We detect that you're using an old version Internet Explorer that doesn't work very well with Facebook..

To get the most out of Facebook, please upgrade or download one of the following browsers:

Note: The beta site is currently disabled in IE6 because it's all messed up and broken. Don't worry, we'll have it working IE6 soon.

Mozilla Firefox 
Opera 
Safari 
Microsoft Internet Explorer 
Flock

---

