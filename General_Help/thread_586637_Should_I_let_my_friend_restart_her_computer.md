---
title: "Should I let my friend restart her computer?"
date: 2007-10-22
forum: General Help
---

### Post by dab on 2007-10-22
Hi,
 
 I copied down a number of alarming messages upon updating Ubuntu from 7.04 to 7.10 (this is in g-mail, because I know that I will be able to at-least access this info with a ubuntu disc that I (hope) have lying around... ) -- I know that the computer will continue to be stable if left on.
 I'm going to work in about an hour and I don't know whether I should leave the computer on to fix what's going on or not. I think every thing should be OK -- but I'm a little edgy (heh, ... not gusty, nor feisty) about what happens when I restart. All this after installing some junk to get an mp3 player working...

 The only reason I'm worried is because of the trouble I've had with even minor updates and my friend's encounters with Grub Error 22 -- which looks a lot like the Blue Screen Of Death from windows -- giving her nightmares and myself migraines from the raster burn of looking deeply within the monitor to divine what might be the computers' soul (at least that's what it looks like to her). And it all was a matter of changing a 0 to a 1 in a grub's menu.lst file.

 Anyway, can anyone let me know if I should be as alarmed as I am (or could be, once I get home from work?),

 Thanks alot,

 Dominick


BTW: I transcribed this (and not very well) from the console window -- copy and paste disabled in a gui! -- ubuntu's just so seamlessly interfaced with the cli most of the time that I went crazy and just decided to type it all down for your analytical pleasure. The alarming stuff, to moi, is *italicized*. 

(Reading database ... 108107 files and directores currently installed)
Removing initramfs-tools ...
- Hide quoted text -


On 10/22/07, D B <d _ @gmail.com> wrote:

    Preconfiguring packages...
    (Reading database ... 116869 files and directories currently installed.)
    *Removing* apparmor-utils ...
    *Removing* apparmor ...
    Unloading AppArmor profiles : done.
    update-initramfs: deferring update (trigger activated)
    *Removing* brltty-x11 ...
    *REmoving* brltty ...
    *Removing* ubuntu-minimal ...
    *Removing* console-setup ...
    *Remving* discover1 ...
    *Removing* f-spot ...
    Removing *ubuntu-desktop* ...
    Removing foomatic-db-hpijs ...
    *Removing* gnome-volume-manager ..
    *removing* gnome-mount ...
    *Removing* gnome-session ...
    *Removing* gnome-power-manager ...
    *Removing* grub ...
    Removing gthumb ...
    *Removing* update-notifier ...
    REmoving sound-joicer...
    Removing network-manager-gnome...
    Removing network-manager
     * stopping network connection manager NetworkManager
     ... done.
    * Stopping network events dispatcher NetworkManagerDispatcher
     ... done.
    *Removing* hal-device-manager ...
    *Removing* hwdb-client-gnome
    *Removing* hwdb-cleint-common...
    *Removing* hal-cups.utils...
    *Removing* hal ...
     * Stopping Hardware abstraction layer hald
     ... done.
    Removing hpijs ...
    Removing hplip ...
    *Removing* linux-restricted-modules-2.6.20-16-generic ...
    *Removing* linux-image-2.6.20-16-generic ...
    Copunt not find postrm hook script [update-grub].
    Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
    The link /vmlinuz.old is a damaged link
    *Removing* symbolic link vmlinuz.old
    Unles you used the optional flag in lilo
     you may need to re-run your boot loader[lilo]
    The link in /initrd.img.old is a damaged link
    *Remvoing* symbolic link vmlinuz.old
    Unless you used the optional flag in lilo
     you may need to re-run your boot loader[lilo]
    *Removing* pcmciautils ...
    Removing rhythmbox ...
    Removing libmtp6 ...
    Remvoing xsane ...
    Removing libsane ...
    REmoving libgphoto2-2 ...
    *Remvoing* usplash-theme-ubuntu
    update-initramfs: deferring update (trigger activated)
    *Removing* usplash ...
    update-initramfs: deferring update (trigger activated)
    *REmoving* linux-generic ...
    *Removing* linux-restricted-modules-generic ...
    *Remvoing* linux-restricted-modules-2.6.22-14-generic ...
    *Removing* linux-image-generic ...
    *Removing* linux-ubuntu-modules-2.6.22-14-generic ...
    update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    find: /lib/firmware/2.6.22-14-generic: No such file or directory
    Removing*** linux-image-2.6.22-14-generic*** ...
    WARN: Preceeding with removing running kernel image.
    Could not find postrm hook script [update-grub].
    Looked in: '/bin', '/sbin', '/usr/bin', '/usr/sbin'
    The link /vmlinuz is a damaged link
    *Removing* symbolic link vmlinuz
     *you may need to re-run your book loader[grub]*
    The link /initrd.img is a damaged link
    *Removing* symblic link initrd.img
     *you may need to re-run your boot loader[grub]*   -- _I have forgotten how--how?_
    Remvoing libdiscover1 ...
    Removing udev ...
    *Removing* initramfs-tools ...
    dpkg: volumid: dependency problems, but remving anyway, *_as you request:_* -- _really, I requested it?_
     initramfs-tools depends on volumeid
    Removing volumid ...
    Processing triggers for initramfs-tools ...
    Processing triggers for libc6 ...
    ldconfig deferred processing now taking place
    Selecting previously deselected package discover-data.
    (Reading database ... 108021 files and directories currently installed.)
    Unpacking discover-data (from .../discover-data_2.2007.06.11ubuntu4_all.deb) ...
    Selecting previously deselected package libdiscover2.
    Unpacking libdiscover2 (from .../libdiscover2_2.1.1-3_i386.deb) ...
    Selecting previously deselected package discover.
    Unpacking discover (from .../discover_2.1.1-3_i386.deb) ...
    Selecting previously deselected package usbmgr.
    Unpacking usbmrg (from .../usbmgr_1.0.0-6_i386.deb) ...
    Setting up discover-data (2.2007.06.11ubuntu4 ) ...
    Setting up libdiscover2 (2.1.1-3) ...

    Setting up discover (2.1.1-3) ...

    Setting up usbmgr (1.0.0-6) ...

    Processing triggers for lib6 ...

    ldconfig deferred processing now taking place

    -- 
    --------------

_ Not removing e-mail signature..._

    "There's an old analogy to a cup of tea. If you want to drink new tea you have to get rid of the old tea that's in your cup, otherwise your cup just overflows and you get a wet mess. Your head is like the cup. It has a limited capacity and if you want to learn something about the world you should keep your head empty in order to learn it. It's very easy to spend your whole life swishing old tea around in your cup thinking it's great stuff because you've never really tried anything new." -- Lila: An Inquiry into Morals, pg 25 (Just something interesting I'm reading that I thought you might enjoy)

---

### Post by LanDan on 2007-10-22
dude, what have you been doing, you screwed

at least i hope you can fiend some comfort in that poetrie of yours when your friend comes back and finds out what happened

its possible ofcourse to still get everything back, but you need to know what you are doing then ;)

good luck!

---

### Post by larryfroot on 2007-10-22
Dan  Lan...

Have you got any practical advice at all re this guys problem? I haven't personally, but at least I don't wink at someone who may be in the smelly stuff. Its the guys first post, for god's sake...

---

### Post by LanDan on 2007-10-22
believe me, its a pile of ****

sorry to sound synical but if you look at was removed,

the most obvious to do is to simply re-install the packages that were removed and hope there will not be too many problems blocking a happy ending

he knows what is removed, so that is what should be re-installed.

the main thing is to re-install the kernel and the rest.

if you want to make a guess it will all end up the easy way is to start tasksel and then simply select the ubuntu-desktop

have fun ;)

---

### Post by PmDematagoda on 2007-10-22
Excuse, but how on earth can anything work when the kernel is removed?

How on earth did this process start dab?

If these processes are indeed true, then you will have a VERY long recovery ahead of you, it would be better if you re-installed everything as it may require about 3 months of solitary 24 hours recovery work from what I can see.

---

### Post by LanDan on 2007-10-22
> **PmDematagoda said:**
> Excuse, but how on earth can anything work when the kernel is removed?

How on earth did this process start dab?

If these processes are indeed true, then you will have a VERY long recovery ahead of you, it would be better if you re-installed everything as it may require about 3 months of solitary 24 hours recovery work from what I can see.

i would set my hopes on tasksel

---

### Post by Samhain13 on 2007-10-22
It may be a good idea to download and burn another ISO while the computer is still alive.

---

### Post by veratyr on 2007-10-22
Theoretically shouldn't this work to resolve any missing package issues for the base install of the system at least?

```
sudo aptitude install ubuntu-minimal ubuntu-standard
```

and whichever desktop package it is ie ubuntu-desktop, kubuntu-desktop or xubuntu-desktop.

```
sudo aptitude install ubuntu-desktop
```

---

### Post by dasunst3r on 2007-10-22
+1 for what veratyr advised.

---

### Post by dab on 2007-10-23
Thanks for the quick responses, guys.

 I'll let my friend shut down and start back up... veratyr, I followed your advice and I hope things work out for the better... 

 I have a copy of edubuntu around.

 Got no clue how to: "re-install the kernel," nor what I'm supposed to do with "tasksel" once it's started. 

PmDematagoda  	
_-_
Excuse, but how on earth can anything work when the kernel is removed?
 Isn't it funny--is it? The strange tank-like abilities of linux to keep on going even after something seemingly crazy has gone on.

 The best hope I've got is that whole (triggered event) thing -- maybe it's growing pains from 7.04 to 7.10? Perhaps it's just taking old stuff from 7.04 down? I've been thinking about it all day--that's my best guess.

How on earth did this process start dab?
 Depends on whatever the heck (triggered event) is? I'm not sure what's going on there.

If these processes are indeed true, then you will have a VERY long recovery ahead of you, it would be better if you re-installed everything as it may require about 3 months of solitary 24 hours recovery work from what I can see.
 Good--I enjoy a good recovery session--get more linux hours under my belt. The only problem is that, while I'm fiddling around, my friend is waiting to access her college classes.
-_-

Dan Lan

-- I enjoy your cynicism and could use every bit of reality about the problem I can get.

"its possible ofcourse to still get everything back, but you need to know what you are doing then "

 I haven't got a clue what I'm doing--yet.

--- Anyway, I'll let my friend decide what she wants to do, since it is her computer. She's worrying about the electric this computer sucks up (though it really doesn't suck up much juice when it's sleeping, try explaining that to her).

 Thanks again, guys,

 I may be back with some boot errors and/or screen shots if I can get one of the live cds I have lying around to run.

---

### Post by kah00na on 2007-10-23
My upgrade also had a few errors.  I chose NOT to download newer files from the internet.  I figured the CD would be enough and I'd update the rest later.  That didn't work so well.  I had to do an "apt-get install --broken" and I think that fixed most of my problems.

I just did another install tonight and chose to download newer packages from the web to see if it went any smoother.  It did.  I think after the next release, I'm only going to plan fresh installs the day it comes out and put off the upgrades till a few days later and choose to again download files from the web.  The install that just finished didn't have one error.

Try the "apt-get install --broken" on your computer and see if it helps any.

---

### Post by dab on 2007-10-24
Ok--I'm running Ubuntu 6.02 from a LiveCD I had around because grub responds with Error 15: File not found.
 It's not finding the initrd.gz files or the vmlinuz files, which I was warned about in that dialog.

 I think I will copy the two files from this disc and see what happens there.

 Is there a way to install packages to the hard drive as with "apt-get install --broken" ? Seems like that might be something to try..

 Anyone else got any advice on error 15, or another message in regard to the list in my first post?

---

