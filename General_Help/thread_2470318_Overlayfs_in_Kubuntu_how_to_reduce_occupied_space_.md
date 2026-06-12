---
title: "Overlayfs in Kubuntu: how to reduce occupied space after delete and deinstall"
date: 2021-12-25
forum: General Help
---

### Post by antondhdih on 2021-12-25
I am now running kubuntu 20.04 from a buyed USB stick as live OS. It is a 32 GB stick, but for the overlayfs only a small part of this is used.

I can see that the system had used this command:

mount -t overlay /cow / -o lowerdir=...,upperdir=/cow/upper,workdir=/cow/work

If I try such command, errors occur:

"/cow" not a special device.

And "/cow", and arguments to upperdir, workdir are not found in the directory tree. I cannot use them for any opration.

With the unfortunate ovelayfs I came without a warning into the state of "no space on device" errors.

I have deleted very many files in /bin, /usr/bin.
Without help. 

Some packages I have deinstalled, including the large package "akonadi". Now I am not able to deinstall more packages because aptitude, apt-get,*dpkg*do not work with error messages like:

"no space left on device" and others.

The overlay merged dir, which is "/", stays at used 100%.

All what I do does not influence the root "/" to be used 100%.

And*dpkg*does not work more because*dpkg*is dependent on akonadi.

And I cannot save my data.

The dir listing of the merged "/" shows equally all of the hard disks and USB sticks. It is not possible to determine which entries are from the deleted and deinstalled files resp. packages.

How can I reduce the 100% occupied space by the merged overlay in "/" ?

Regards
anton

---

### Post by DuckHook on 2021-12-26
Duplicate of [https://ubuntuforums.org/showthread.php?t=2470164](https://ubuntuforums.org/showthread.php?t=2470164) which has been closed.

Please don't post duplicate threads. It confuses those trying to help and dilutes community effort. You are permitted to bring your thread up to the top of the pile by *bumping* it every 12 hours.

---

### Post by DuckHook on 2021-12-26
> **antondhdih said:**
> I am now running kubuntu 20.04 from a buyed USB stick as live OS. It is a 32 GB stick, but for the overlayfs only a small part of this is used.
…I have deleted very many files in /bin, /usr/bin.
…
…And*dpkg*does not work more because*dpkg*is dependent on akonadi.

And I cannot save my data.
…
How can I reduce the 100% occupied space by the merged overlay in "/" ?

You have irrevocably damaged your LiveUSB OS. Since you do not specify which files you deleted in /bin and /usr/bin and probably do not remember them, your system is entirely broken.

I have never worked with the Kubuntu LiveUSB, but the principle behind all LiveUSBs are the same: the system files must not be messed with. And despite the "user" implication in /usr and /usr/bin, they contain critical system files, none of which should be changed or deleted. Your wholesale deletion of files in these directories has rendered your system broken and unstable. It cannot be saved at this point.

Here is what I recommend: given the fact that you are a new user, your existing LiveUSB OS cannot be salvaged. You will need to make a new LiveUSB stick and then try to salvage what data you can from your existing one.

To execute the following plan, you will need two new USB sticks.

[list=1]
[*]It is unnecessary to purchase a Kubuntu LiveUSB 20.04 stick. In fact, it is unwise to do so from a third party, since these can sometimes include malware. Instead, download the ISO directly from Canonical's site: [https://kubuntu.org/getkubuntu/](https://kubuntu.org/getkubuntu/)
[*]Since you are a new general user, stick with the LTS version (20.04). Do NOT use the standard version (21.10).
[*]Using whatever burning software you have (Windows?), burn a LiveUSB from the downloaded ISO image onto new stick #1.
[*]Boot into a LiveUSB environment using stick #1. *Make **NO** changes to this stick.* Do not repeat your earlier mistakes.
[*]From within this LiveUSB environment, install mkusb following the instructions in this link: [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) It is a good idea to read through this link very thoroughly before proceeding so that you are sure you understand the concepts and steps before you proceed further.
[*]Insert the empty USB stick #2.
[*]Following the instructions in the mkusb link, create another LiveUSB OS on stick #2 *using mkusb* but *being sure to choose the **persistence** option.*
[*]Once you have a LiveUSB successfully running on stick #2 (with persistence), you should now have a working USB stick that will install new apps and store data permanently.
[/list]
Above is the proper way to run a LiveUSB stick with persistence. The LiveUSB partition remains untouched and your new apps/data go into the unused portion of the stick. You can use any size stick you want and all of the remainder of the stick is available for storage.

You can now try recovering your old data by copying it from your broken LiveUSB stick.

:!:Note that USB sticks are not considered reliable for mission critical work. The data stored on them should never be considered important. Only use this method for stuff you won't mind losing.:!:

---

### Post by antondhdih on 2021-12-27
Many thanks to DuckHook.

I will follow your good advices the next time.

Now I continue trying to reduce the diskspace of the overlay /cow to mountpoint "/" root, for which df shows that it is occupied 100%.

Only "no disk space on device" is the problem.

 In my practice with Linux of 30 years I have succeeded with many difficulties.

Before of "no space on device" I have again and again downloaded and installed new software. I dont remember what all, this I regret. All regarding kmail, aptitude, etc.

By this I came -- without a warning message -- into "no space on device".

I have deleted in /bin etc only some of these software, I had installed before myself, no one that was on the bought USB OS originally.

In the last days I have made - on the built-in 2TB hard disk - my own overly system.

The lowerdir of the running system I have found, which is 
/cdrom/casper/filesystem.suashfs

I have found how the system had used this for its lowerdir in the loop device /dev/loop0

Thus I was able to copy this to my overlay system and to use for my overly system the same lowerdir as the original kubuntu.

My resultant merged overlay is of course much, much smaller than the (100% used) merged "/".

Now I am trying to discover on "/" which files are what.

There must be a way to tell which files on the 100% full overlay "/" can be deleted.

But all in all it is to say: for overlayfs there is more documentation needed and there are tools needed.

Thanks, Regards
anton

---

### Post by HermanAB on 2021-12-28
To run off a a USB stick or SD card, just do a normal install.  The overlay complication is not needed.

---

### Post by antondhdih on 2021-12-28
I am confused with your forms: 3 hours again I have written to you: my writing yesterday was not correct: one and only one original package I have partly deleted. It is "akonadi".
I do not know if this message was sent to you. I am for hours searching about that. I cannot find my text, I have written, I dont know how to copy, to save text written to you, you often state "SSO login", you never tell what SSO is. Please is there some user guide about Ubuntu Forums?
Regards
Anton

---

