---
title: "If I install ubuntu with other ubuntu boot drives in the PC, what will happen to them"
date: 2014-05-08
forum: General Help
---

### Post by sdowney717 on 2014-05-08
Will it destroy their ability to boot ubuntu?

I have say 2 drives.
One currently boots ubuntu ok.
I plug in a USB drive, I want to install ubuntu onto the USB drive.

Will doing that cause the other drive to no longer boot when the USB drive is removed and I reboot the PC?

---

### Post by oldfred on 2014-05-08
Any install of grub should add all other system to its grub menu with os-prober.

But with more than one drive, better to keep boot loaders separate. So if installing to an external drive you want the install in the external to have its boot loader in the MBR (or efi partition if UEFI) of external drive.
Then when external is plugged in you get a menu to boot either external or internal. If you have set boot order in BIOS to boot external first and internal second and then remove external, it will just default to internal drive.

If you use Something Else, you get an option on which drive (do not use partitions) to install the grub2 boot loader.

Second screen shot is to a gpt partitioned SSD, that I had hoped to add to a new UEFI system. So I have both an efi partition for future use and a bios_grub partition for Ubuntu to boot in BIOS mode. It has 12.04 in sdd3 as my current working and I am installing 14.04 so I can configure it as my new working system, but still have 12.04 as another way to boot.

---

### Post by sdowney717 on 2014-05-08
Hi, well your post is not telling me how to do this.
Pretend I am a computer and need explicit directions :D

Otherwise your just pontificating.

Reading your post leaves me wondering what to do.

I am leaning towards, I MUST unplug the others drives or it will cause them to be messed up direction.?
I have done this before, and somehow grub messes up the grub on the other drive and will no longer work.

well, failure installing ubuntu when using an external usb drive with an IDE drive inside.
So maybe need to install as IDE drive in the PC.

here is screenshot of the error.
Claims UUID is messed up?

Is there an easy way to fix or give up, reinstall with drive actually in the PC?

Took screen of fstab, while in liveusb
the fstab matches??? So what is going on, why cant it boot?

[http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc)

going to try this

so if it says this, was it broken?
> Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7416957/](http://paste.ubuntu.com/7416957/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
]

Nope, did not work.
So reboot liveusb and do a reinstall, first item in list, see if this works.
Is it really this hard to fresh install 14.04?
I suppose I can install 13.10 and upgrade to 14.04. In the past I have had to do that.

Nope, that did not work. Installer gets to end and was taking forever.
So clicked open tiny window and error after error regarding you have kept broken packages.

So unpluged computer and doing a full wipe and reinstall with drive inside the PC
Will it work, I do not know...

Here is screen of partioner.

Which is identical to when IDE drive was sitting in the usb drive box.

Nope, so will just have to reinstall the disk in the PC for which it is intended which is 40 minutes away in a boat.

Odd dont you think?
This board here is Asus P5QC. I unplugged all the SATA dirves.
I plugged in an IDE drive.
Installs ok I suppose.
But can not boot.
Gives various suggestions.

main error is UUID, 
dev/disk/by-UUID/ long string etc...  does not exist.
Well it does exist!

Thanks for the help. I WILL make it work again, but probably not here on this board.
Ubuntu software and the board will not just work with an IDE drive. Surprised me.

It is kind of odd, but I chrooted into the install and try a simple update and all it does is errors.

Could the download of ubuntu I did  be corrupted?
```
ubuntu@ubuntu:~$ sudo mount /dev/sdXY /mnt
mount: special device /dev/sdXY does not exist
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev &&
> sudo mount --bind /dev/pts /mnt/dev/pts &&
> sudo mount --bind /proc /mnt/proc &&
> sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get update
Err http://extras.ubuntu.com trusty InRelease
  
Err http://security.ubuntu.com trusty-security InRelease                    
  
Err http://us.archive.ubuntu.com trusty InRelease                           
  
Err http://us.archive.ubuntu.com trusty-updates InRelease
  
Err http://us.archive.ubuntu.com trusty-backports InRelease
  
Err http://extras.ubuntu.com trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com trusty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# sudo apt-get update
sudo: unable to resolve host ubuntu
Err http://us.archive.ubuntu.com trusty InRelease
  
Err http://us.archive.ubuntu.com trusty-updates InRelease
  
Err http://us.archive.ubuntu.com trusty-backports InRelease
  
Err http://security.ubuntu.com trusty-security InRelease
  
Err http://extras.ubuntu.com trusty InRelease
  
Err http://us.archive.ubuntu.com trusty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-updates Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com trusty-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://extras.ubuntu.com trusty Release.gpg
  Could not resolve 'extras.ubuntu.com'
Err http://us.archive.ubuntu.com trusty-backports Release.gpg
  Could not resolve 'us.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/InRelease  

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/InRelease  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/Release.gpg  Could not resolve 'extras.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:/# 

```

---

### Post by sdowney717 on 2014-05-08
Maybe it is not the release I got, but maybe a beta?

How would I change the sources list?

```
root@ubuntu:/# sudo apt-get upgrade
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gir1.2-rb-3.0 librhythmbox-core8 rhythmbox rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugins
The following packages will be upgraded:
  app-install-data bash compiz compiz-core compiz-gnome compiz-plugins-default
  cups-browsed cups-filters cups-filters-core-drivers dpkg firefox gettext
  gettext-base gir1.2-freedesktop gir1.2-glib-2.0 iputils-arping iputils-ping
  iputils-tracepath libasprintf-dev libasprintf0c2 libcompizconfig0
  libcupsfilters1 libdecoration0 libdpkg-perl libelf1 libfontembed1
  libgettextpo-dev libgettextpo0 libgexiv2-2 libgirepository-1.0-1
  libido3-0.1-0 libjbig0 libnautilus-extension1a liboxideqt-qmlplugin
  libselinux1 libssl1.0.0 libtiff5 libunity-core-6.0-9 linux-generic
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-headers-generic linux-image-3.13.0-24-generic
  linux-image-extra-3.13.0-24-generic linux-image-generic linux-libc-dev
  nautilus nautilus-data openssl python3-software-properties
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets rsync software-center
  software-properties-common software-properties-gtk unity unity-greeter
  unity-services webapp-container webbrowser-app
61 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 116 MB of archives.
After this operation, 15.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libcupsfilters1 amd64 1.0.52-0ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libfontembed1 amd64 1.0.52-0ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main cups-browsed amd64 1.0.52-0ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main cups-filters-core-drivers amd64 1.0.52-0ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main cups-filters amd64 1.0.52-0ubuntu1.1
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main bash amd64 4.3-7ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dpkg amd64 1.17.5ubuntu5.2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libselinux1 amd64 2.2.2-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main dpkg amd64 1.17.5ubuntu5.2
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libssl1.0.0 amd64 1.0.1f-1ubuntu2.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libasprintf-dev amd64 0.18.3.1-1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libasprintf0c2 amd64 0.18.3.1-1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgettextpo-dev amd64 0.18.3.1-1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgettextpo0 amd64 0.18.3.1-1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgexiv2-2 amd64 0.10.0-1ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libido3-0.1-0 amd64 13.10.0+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libssl1.0.0 amd64 1.0.1f-1ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main iputils-ping amd64 3:20121221-4ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main gettext-base amd64 0.18.3.1-1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-freedesktop amd64 1.40.0-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libgirepository-1.0-1 amd64 1.40.0-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-glib-2.0 amd64 1.40.0-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libelf1 amd64 0.158-0ubuntu5.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libjbig0 amd64 2.0-2ubuntu4.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libtiff5 amd64 4.0.3-7ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-3.13.0-24-generic amd64 3.13.0-24.47
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main iputils-tracepath amd64 3:20121221-4ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main openssl amd64 1.0.1f-1ubuntu2.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main app-install-data all 14.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libcompizconfig0 amd64 1:0.9.11+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main openssl amd64 1.0.1f-1ubuntu2.1
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-gnome amd64 1:0.9.11+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-plugins-default amd64 1:0.9.11+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libdecoration0 amd64 1:0.9.11+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main compiz-core amd64 1:0.9.11+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main compiz all 1:0.9.11+14.04.20140423-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main gettext amd64 0.18.3.1-1ubuntu3
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main rsync amd64 3.1.0-2ubuntu0.1
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main iputils-arping amd64 3:20121221-4ubuntu1.1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libnautilus-extension1a amd64 1:3.10.1-0ubuntu9
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main unity-greeter amd64 14.04.10-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic amd64 3.13.0.24.29
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic amd64 3.13.0.24.29
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main firefox amd64 29.0+build1-0ubuntu0.14.04.2
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libdpkg-perl all 1.17.5ubuntu5.2
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main unity amd64 7.2.0+14.04.20140423-0ubuntu1.2
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main libunity-core-6.0-9 amd64 7.2.0+14.04.20140423-0ubuntu1.2
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main unity-services amd64 7.2.0+14.04.20140423-0ubuntu1.2
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-image-extra-3.13.0-24-generic amd64 3.13.0-24.47
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic amd64 3.13.0.24.29
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus-data all 1:3.10.1-0ubuntu9
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main nautilus amd64 1:3.10.1-0ubuntu9
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main software-properties-common all 0.92.37
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main software-properties-gtk all 0.92.37
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main python3-software-properties all 0.92.37
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main webapp-container amd64 0.23+14.04.20140422-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.13.0-24 all 3.13.0-24.47
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-headers-3.13.0-24-generic amd64 3.13.0-24.47
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ trusty-security/main linux-libc-dev amd64 3.13.0-24.47
  Could not resolve 'security.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqt-qmlplugin amd64 1.0.0~bzr501-0ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main qtdeclarative5-ubuntu-ui-extras-browser-plugin amd64 0.23+14.04.20140422-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main webbrowser-app amd64 0.23+14.04.20140422-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets all 0.23+14.04.20140422-0ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main software-center all 13.10-0ubuntu4.1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.3-7ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg_1.17.5ubuntu5.2_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libs/libselinux/libselinux1_2.2.2-1ubuntu0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.0.0_1.0.1f-1ubuntu2.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/libasprintf-dev_0.18.3.1-1ubuntu3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/libasprintf0c2_0.18.3.1-1ubuntu3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/e/elfutils/libelf1_0.158-0ubuntu5.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/j/jbigkit/libjbig0_2.0-2ubuntu4.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff5_4.0.3-7ubuntu0.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups-filters/libcupsfilters1_1.0.52-0ubuntu1.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups-filters/libfontembed1_1.0.52-0ubuntu1.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/libgettextpo-dev_0.18.3.1-1ubuntu3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/libgettextpo0_0.18.3.1-1ubuntu3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gexiv2/libgexiv2-2_0.10.0-1ubuntu2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/ido/libido3-0.1-0_13.10.0+14.04.20140423-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.13.0-24-generic_3.13.0-24.47_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/iputils/iputils-ping_20121221-4ubuntu1.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext-base_0.18.3.1-1ubuntu3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/gir1.2-freedesktop_1.40.0-1ubuntu0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/libgirepository-1.0-1_1.40.0-1ubuntu0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gobject-introspection/gir1.2-glib-2.0_1.40.0-1ubuntu0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/iputils/iputils-tracepath_20121221-4ubuntu1.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_1.0.1f-1ubuntu2.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_3.1.0-2ubuntu0.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-ubuntu/app-install-data_14.04.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libcompizconfig0_0.9.11+14.04.20140423-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.9.11+14.04.20140423-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins-default_0.9.11+14.04.20140423-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.9.11+14.04.20140423-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.9.11+14.04.20140423-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.9.11+14.04.20140423-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-browsed_1.0.52-0ubuntu1.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-filters-core-drivers_1.0.52-0ubuntu1.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/c/cups-filters/cups-filters_1.0.52-0ubuntu1.1_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_29.0+build1-0ubuntu0.14.04.2_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.18.3.1-1ubuntu3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/i/iputils/iputils-arping_20121221-4ubuntu1.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.17.5ubuntu5.2_all.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1a_3.10.1-0ubuntu9_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/u/unity-greeter/unity-greeter_14.04.10-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity_7.2.0+14.04.20140423-0ubuntu1.2_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/u/unity/libunity-core-6.0-9_7.2.0+14.04.20140423-0ubuntu1.2_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/u/unity/unity-services_7.2.0+14.04.20140423-0ubuntu1.2_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-24-generic_3.13.0-24.47_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.13.0.24.29_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.24.29_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-24_3.13.0-24.47_all.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.13.0-24-generic_3.13.0-24.47_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.13.0.24.29_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.13.0-24.47_amd64.deb  Could not resolve 'security.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_3.10.1-0ubuntu9_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_3.10.1-0ubuntu9_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-common_0.92.37_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/software-properties-gtk_0.92.37_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-properties/python3-software-properties_0.92.37_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/webbrowser-app/webapp-container_0.23+14.04.20140422-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/o/oxide-qt/liboxideqt-qmlplugin_1.0.0~bzr501-0ubuntu2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/webbrowser-app/qtdeclarative5-ubuntu-ui-extras-browser-plugin_0.23+14.04.20140422-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/webbrowser-app/webbrowser-app_0.23+14.04.20140422-0ubuntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/w/webbrowser-app/qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets_0.23+14.04.20140422-0ubuntu1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_13.10-0ubuntu4.1_all.deb  Could not resolve 'us.archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ubuntu:/# 

```

---

### Post by monkeybrain20122 on 2014-05-08
> **sdowney717 said:**
> Will it destroy their ability to boot ubuntu?

I have say 2 drives.
One currently boots ubuntu ok.
I plug in a USB drive, I want to install ubuntu onto the USB drive.

Will doing that cause the other drive to no longer boot when the USB drive is removed and I reboot the PC?

No, as long as you install the bootloader in the external drive rather than the internal one (default is internal,say /dev/sda, you have to install it in the external, say /dev/sdb) You should choose manual install ('something else') and the option to install bootloader is at the bottom of the page.

Edited: It is a simple operation, I have no clue what you have gotten yourself into.

---

### Post by sdowney717 on 2014-05-08
> **monkeybrain20122 said:**
> No, as long as you install the bootloader in the external drive rather than the internal one (default is internal,say /dev/sda, you have to install it in the external, say /dev/sdb)

I chrooted into this and cant do a thing with it.:p
Wonder why?
I went to ubuntu sources web and generated a new list, overwrote the old, still nothing.

[http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)

Actually I am beyond mad about the whole thing, now  I am curious as to what is going on.

---

### Post by monkeybrain20122 on 2014-05-08
> **sdowney717 said:**
> Hi, well your post is not telling me how to do this.
Pretend I am a computer and need explicit directions :D

Otherwise your just pontificating.

Reading your post leaves me wondering what to do.

I am leaning towards, I MUST unplug the others drives or it will cause them to be messed up direction.?
I have done this before, and somehow grub messes up the grub on the other drive and will no longer work.

See his third screenshot. You can unplug the drive but you don't have to.

---

### Post by sdowney717 on 2014-05-08
> **monkeybrain20122 said:**
> See his third screenshot. You can unplug the drive but you don't have to.

yes, Well, I unplugged all the drives. Something perhaps about this more modern board and this older 200gb IDE drive?

The drive works and installs on the board at the boat far away.
The drive did work here fine running as a usb drive on the P5QC board. 
But the install something odd going on just does not work.

---

### Post by monkeybrain20122 on 2014-05-08
> **sdowney717 said:**
> I chrooted into this and cant do a thing with it.:p
Wonder why?
I went to ubuntu sources web and generated a new list, overwrote the old, still nothing.

[http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php)

???

I have installed in external drives many, many times. It is a simple operation, I have no idea why you make it so complicated. :)

Let's start again. Boot from a live usb. Attach the external drive, then install as you would normally, when it comes to choosing "install alongside ..." etc, choose "something else" and choose the external drive (say /dev/sdc, /dev/sda is usually your internal hard drive, /dev/sdb your live usb, but anyway you will see that in the partition layout)** Important:** install bootloader in external drive (/dev/sdc, say, the default is /dev/sda,--the internal drive), see the bottom of **oldfred**'s third screenshot. Then continue, that's it.

---

### Post by sdowney717 on 2014-05-08
> **monkeybrain20122 said:**
> ???

I have installed in external drives many, many times. It is a simple operation, I have no idea why you make it so complicated. :)

Let's start again. Boot from a live usb. Attach the external drive, then install as you would normally, when it comes to choosing "install alongside ..." etc, choose "something else" and choose the external drive (say /dev/sdc, /dev/sda is usually your internal hard drive, /dev/sdb your live usb, but anyway you will see that in the partition layout)** Important:** install bootloader in external drive (/dev/sdc, say, the default is /dev/sda,--the internal drive), see the bottom of **oldfred**'s third screenshot. Then continue, that's it.

I posted screens, for some reason it does not work.
I did the something else on the partitioner.
I also tried 13.10.

So I do not know why I get constant error of

/dev/disk/by-UUID/ long string...... does not exist error.

When I did this install with the boat computer, I had it here at the house, and was able to get it working.
I do recall something troubling back then too, might look in my prior threads to find that.
I might have to bring the PC home again.

---

### Post by sdowney717 on 2014-05-08
[http://www.blogs.digitalworlds.net/softwarenotes/?p=178](http://www.blogs.digitalworlds.net/softwarenotes/?p=178)

here is someone's solution to the same error I get.

No help there.

I did find the problem, but I dont know how to fix it?
The UUID in fstab and gparted are identical for all 3 partitions.

BUT, when it boots, the UUID error 'drive does not exist', shows a UUID that is not related at all to the IDE drive.

So how is grub somehow referencing a UUID that it shoud not, and how to fix it?

I looked through all the drives in gparted, and that uuid is not anywhere that I can find?

I am trying this chroot update grub
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

No good, still gives a UUID error after chroot and updating grub.
Now the UUID that is missing has changed to a new number.

---

### Post by oldfred on 2014-05-08
Post a new BootInfo report.

Are you sure grub installed to MBR of external drive is the one that is updated and not a partition nor another drive? Or is there some issue that is preventing grub from correctly writing into the MBR of the external drive?

It seems like a grub mismatch.

---

### Post by sdowney717 on 2014-05-08
> **oldfred said:**
> Post a new BootInfo report.

Are you sure grub installed to MBR of external drive is the one that is updated and not a partition nor another drive? Or is there some issue that is preventing grub from correctly writing into the MBR of the external drive?

It seems like a grub mismatch.

Pretty sure, It is sdc and I updated grub to sdc.
What I can  do for you is
disconnect all internal drives again.
reboot live usb.
redo boot repair with new Bootinfo report.

Where is it picking up that oddball UUID from?

ok done here it is. will reboot and report back.

Nope still same type uuid error

showing the screen with error

Looking at the uuid in the boot report,  this time they match.
So it says the drive  does not exist. Why is that? My feeling is the motherboard and this drive?

---

### Post by oldfred on 2014-05-08
I found this in my notes:

 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"
Also check that drive is hd0 and grub in same drive.

AHCI is the prefered mode now. And is required for SSD to use trim as I understand it. But my XP would not boot with AHCI, so I finally turned XP off.

---

### Post by sdowney717 on 2014-05-08
Interesting, yes the bios is set to AHCI.

Will change and report back.

Nope, still same error.
turned off AHCI
set to compatable, sata as ide.

I am not too woried right now because I KNOW this drive works with the other main board.
I will know a lot more tommorow when I reinstall with drive attached to that mainboard.

This drive was working fine on this board. I would bring drive home from boat and do updates.
It just will not boot this drive on this board with ubuntu.

this mainboard is Asus P5QC and the IDE drive is WD2000.
I run ubuntu trusty on this board installed with sata II drive just fine.

---

