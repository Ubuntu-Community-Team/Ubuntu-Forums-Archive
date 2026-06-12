---
title: "38 linux image generic, headers, and headers generic - removal of 36?"
date: 2015-08-05
forum: General Help
---

### Post by Ace..... on 2015-08-05
I'm having a clean out, with the help of Slint.
It has identified that I'm thoroughly bloated with old kernels.

What is the best method of removing all 3 elements x 36

Earliest is 3.2.0-23
latest is 3.2.0-88

this guy is apparently an ubuntu genius:
[https://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/](https://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/)

He suggests:
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

---

### Post by ruzekle on 2015-08-05
Here's a more thorough tutorial:

[http://markmcb.com/2013/02/04/cleanup-unused-linux-kernels-in-ubuntu/](http://markmcb.com/2013/02/04/cleanup-unused-linux-kernels-in-ubuntu/)

Otherwise, I've noticed that this should work, but the tutorial is much older.

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

---

### Post by v3.xx on 2015-08-05
Try
```
sudo apt-get autoremove
```
Autoremove is now removing kernels in 12.04 for me.

---

### Post by matt_symes on 2015-08-06
Hi

Be careful when using one liners like this from the Internet as they can be brittle.

They break on my system when using the kernel ppa (I manually install new kernels when can) and they can also return false positives.

I've never really understood why more accurate search patterns are not passed into the initial query of the dpkg database to help eliminate the potential of false positives.

BTW apt will not autoremove manually installed kernels unless you set them to be removed as such.

Kind regards

---

### Post by deadflowr on 2015-08-06
Personally I never use any remove/purge command suggested that wants to use the -y flag.
That means you can never do a quick review of what will happen and are at the whims of the command.
(Way too many users have done so, and then realized after the fact that the command removed quite a bit more then they intended.)

Instead I replace it with the -s flag (for simulate).
That way you'll see exactly what would have happened if you ran it with the -y flag, but without actually done so.

But that's me, to each his own.

---

### Post by VMC on 2015-08-06
This is the one I use:
```
dpkg -l linux-* | awk /^ii/{ print } | grep -v -e 3.19.0-25 | grep -e [0-3]| xargs sudo apt-get -y purge --dry-run
```

Notice the grep arguments 0-3. If you have lib6 installed, which I do, then the original one-liner wants to remove lib6.
Make sure you first use the "dry-run" . Then if it removes the kernels that you want, then remove the "dry-run".

As mentioned above, I like this [link]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/"). Try each section of the command to get a feel for whats its doing.

---

### Post by leunam12 on 2015-08-06
I use Ubuntu Tweak, click on Janitor and click old kernels and then Clean. That is after I image my system partition of course.

---

### Post by Ace..... on 2015-08-06
Thanks everybody :)

After reading through your advice, I finally settled upon:
```
[COLOR=#000000][FONT=courier bold]dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge[/FONT][/COLOR]
```

I noted that two members recommended this tutorial and command.
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

I have to say, it was a concise masterclass.
The command was built in sections, allowing the user to try each section, to gain a better understanding of the command.
The penultimate stage, was the dry run.

After this, I had the confidence to run it.

It took a long time...... I left it running after 30 minutes, and came back to find it complete.

There was too much code for it all to be stored in terminal.
Here is the final section:

I've highlighted two elements.
fglrx_updates.ko:....... suggesting I reinstall using DKMS (?)

And I may need to re-run boot loader (grub)
Does it just mean: reboot the system?

I've not rebooted yet..... I'm just running Backup..... it'll take another 40 minutes to complete
```

-------- Uninstall Beginning --------
Module:  fglrx-updates
Version: 13.350.1
Kernel:  3.2.0-87-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


fglrx_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-87-generic/updates/dkms/
 - Original module
**[COLOR=#0000cd]   - No original module was found for this module on this kernel.[/COLOR]**
**[COLOR=#0000cd]   - Use the dkms install command to reinstall any previous module version.[/COLOR]**


depmod.............


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-87-generic /boot/vmlinuz-3.2.0-87-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-87-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-87-generic /boot/vmlinuz-3.2.0-87-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
**[COLOR=#0000cd]The link /vmlinuz.old is a damaged link[/COLOR]**
**[COLOR=#0000cd]Removing symbolic link vmlinuz.old [/COLOR]**
**[COLOR=#0000cd] you may need to re-run your boot loader[grub][/COLOR]**
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-3.2.0-87-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-87-generic /boot/vmlinuz-3.2.0-87-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-87-generic /boot/vmlinuz-3.2.0-87-generic

```

---

### Post by Ace..... on 2015-08-06
Following on from my last post, re the removal command.

After backing up, I rebooted.
Fine...... no problems..... in fact it is better.
Previously ubuntu would not 'reset' - I had to switch off and reboot manually - reset now works..... and it's very quick!

I still only have sound at the login screen...... the drum roll plays.
Once Ubuntu Xubuntu loads, I lose the sound.

Could that be related to the [COLOR=#000000]fglrx issue reported in my previous post?
Reinstall using DKMS?

EDIT: just checked FSlint - largest package installed is fglrx updates 259.7M

It's bizarre - pulse audio control shows sound is being played (in the bar monitor).... it's just not coming out of the speakers.

Other than that...... success!

Thank you everybody

:)[/COLOR]

---

### Post by v3.xx on 2015-08-06
I would of liked to to know if autoremove would work, oh well :)  Your other question are unrelated, maybe better to start another thread.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by matt_symes on 2015-08-06
Hi

Running the dpkg, sed pipeline on my machine, it wants to remove linux-libc-dev:amd64.

```
matthew-laptop:/home/matthew:6 % dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'
linux-headers-3.16.0-45
linux-headers-3.16.0-45-generic
linux-headers-4.0.0-040000
linux-headers-4.0.0-040000-generic
linux-headers-4.1.0-040100
linux-headers-4.1.0-040100-generic
linux-headers-4.1.1-040101
linux-headers-4.1.1-040101-generic
linux-image-3.16.0-45-generic
linux-image-4.0.0-040000-generic
linux-image-4.1.1-040101-generic
linux-image-extra-3.16.0-45-generic
**linux-libc-dev:amd64**
matthew-laptop:/home/matthew:6 %
```

Passing that to apt-get purge want's to remove 70 packages, many of them not kernel header and images packages....

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d'  | xargs sudo apt-get purge --assume-no

........

The following packages will be REMOVED
  build-essential* comerr-dev* g++* g++-4.8* gnome-common* gtk-doc-tools*
  krb5-multidev* libatk-bridge2.0-dev* libatk1.0-dev* libatkmm-1.6-dev*
  libblkid-dev* libbluetooth-dev* libc6-dev* libcairo2-dev*
  libcairomm-1.0-dev* libcurl4-gnutls-dev* libdbus-glib-1-dev* libexpat1-dev*
  libfontconfig1-dev* libfreetype6-dev* libgcrypt11-dev* libgdk-pixbuf2.0-dev*
  libglib2.0-dev* libglibmm-2.4-dev* libgnutls-dev*
  libgstreamer-plugins-base1.0-dev* libgstreamer1.0-dev* libgtk-3-dev*
  libgtk2.0-dev* libgtkmm-2.4-dev* libgtkmm-3.0-dev* libjpeg-dev*
  libjpeg-turbo8-dev* libjpeg8-dev* libkrb5-dev* liblightdm-gobject-1-dev*
  libmount-dev* libmysqlclient-dev* libncurses5-dev* libpam0g-dev*
  libpango1.0-dev* libpangomm-1.4-dev* libpcre3-dev* libpng12-dev*
  libpulse-dev* librsvg2-dev* librtmp-dev* libssl-dev* libstdc++-4.8-dev*
  libtiff5-dev* libtool* libxft-dev* libxklavier-dev*
  linux-generic-lts-utopic* linux-headers-3.16.0-45*
  linux-headers-3.16.0-45-generic* linux-headers-4.0.0-040000*
  linux-headers-4.0.0-040000-generic* linux-headers-4.1.0-040100*
  linux-headers-4.1.0-040100-generic* linux-headers-4.1.1-040101*
  linux-headers-4.1.1-040101-generic* linux-headers-generic-lts-utopic*
  linux-image-3.16.0-45-generic* linux-image-4.0.0-040000-generic*
  linux-image-4.1.1-040101-generic* linux-image-extra-3.16.0-45-generic*
  linux-image-generic-lts-utopic* linux-libc-dev* uuid-dev* zlib1g-dev*
  zoneminder*
0 to upgrade, 0 to newly install, 72 to remove and 0 not to upgrade.
After this operation, 1,114 MB disk space will be freed.
Do you want to continue? [Y/n] N
Abort.

```

I'm pretty sure that's not what the original coder of the pipeline expected and i why i don't tend to run commands from the Internet blindly. It's due to the false positive of linux-libc-dev:amd64.

This is one i started playing around with at 6am this morning.

```

dpkg -l 'linux-*image*-[0-9].*' 'linux-*headers*-[0-9].*' | awk -v umr=$(uname -r) ' BEGIN { gsub("-[A-Za-z]+$","",umr) }; $1 ~ "ii|rc" && $2 !~ umr {print $2}' | xargs sudo apt-get purge --assume-no
```

```
matthew-laptop:/home/matthew:6 % dpkg -l 'linux-*image*-[0-9].*' 'linux-*headers*-[0-9].*' | awk -v umr=$(uname -r) ' BEGIN { gsub("-[A-Za-z]+$","",umr) }; $1 ~ "ii|rc" && $2 !~ umr {print $2}' | xargs sudo apt-get purge --assume-no
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-generic-lts-utopic* linux-headers-3.16.0-45*
  linux-headers-3.16.0-45-generic* linux-headers-4.0.0-040000*
  linux-headers-4.0.0-040000-generic* linux-headers-4.1.0-040100*
  linux-headers-4.1.0-040100-generic* linux-headers-4.1.1-040101*
  linux-headers-4.1.1-040101-generic* linux-headers-generic-lts-utopic*
  linux-image-3.16.0-45-generic* linux-image-4.0.0-040000-generic*
  linux-image-4.1.1-040101-generic* linux-image-extra-3.16.0-45-generic*
  linux-image-generic-lts-utopic* linux-signed-image-3.13.0-53-generic*
  linux-signed-image-3.13.0-55-generic* linux-signed-image-3.13.0-58-generic*
0 to upgrade, 0 to newly install, 18 to remove and 0 not to upgrade.
After this operation, 945 MB disk space will be freed.
Do you want to continue? [Y/n] N
Abort.
```

But even then, i think it's too brittle to use at the moment (the wildcards to dpkg and the regex to gsub) and it also wants to remove linux-image-generic-lts-utopic. That's to be expected as it's removing all utopic kernels but still may not be what is wanted

So i'll stick to the method that has never let me down.

Kind regards

---

### Post by Ace..... on 2015-08-06
> **v3.xx said:**
> I would of liked to to know if autoremove would work, oh well :)  Your other question are unrelated, maybe better to start another thread.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Sorry V3.xx ...... yes I've started another thread on sound, in multimedia.

Thanks for the help

:)

---

### Post by VMC on 2015-08-06
> **matt_symes said:**
> Hi

Running the dpkg, sed pipeline on my machine, it wants to remove linux-libc-dev:amd64.

...

That's what I was referring too in my post. I think if you squeeze down the search from 0-9 to 0-3 you won't see the "linux-libc-dev:amd64"come up. I'm thinking the "64" comes from the 0-9. But yes, I always do a  dry-run before I pull the trigger.

---

### Post by matt_symes on 2015-08-06
Hi

> **VMC said:**
> That's what I was referring too in my post. I think if you squeeze down the search from 0-9 to 0-3 you won't see the "linux-libc-dev:amd64"come up. I'm thinking the "64" comes from the 0-9. But yes, I always do a  dry-run before I pull the trigger.

Does using 0-3 work with 4.xxxx kernels ? The best way to deal with issues like that is to get dpkg-query only to return header and image packages to pass to the rest of the pipeline in the first place.

Well done for performing a dry run. If only more people did.

Kind regards

---

### Post by VMC on 2015-08-07
> **matt_symes said:**
> Does using 0-3 work with 4.xxxx kernels ? The best way to deal with issues like that is to get dpkg-query only to return header and image packages to pass to the rest of the pipeline in the first place...

Good question, and glad you brought it up. I haven't installed any linux 4 kernels yet. I'll keep an eye on it once I do.

---

