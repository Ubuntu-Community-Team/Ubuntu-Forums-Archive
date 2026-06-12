---
title: "Wubi-7.04-Beta Bug Reports"
date: 2007-03-29
forum: General Help
---

### Post by ago on 2007-03-29
If you think you found a bug, use this thread to report it. Please read the [Wubi Forum FAQ](http://ubuntuforums.org/showthread.php?t=396526) first. Also check the forum to see if the problem has already been addressed/is known. Avoid using this thread to ask for support, open a new topic instead. Be as descriptive as possible. Confirmed bug will be added to the project pages, this thread is used as a preliminary "filter" (do not even think about skipping it...).

---

### Post by celsus on 2007-05-04
1)  FAQs state:

"Minefields are experimental builds to test new prerelease features, if you want something that is supposed to work then forget about minefield builds and use the latest official wubi version. If you do not mind a bumpy ride and want to help us debugging, by all means try the latest minefield build (you will see it announced in a dedicated thread)."

 -- [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html) links to wubi-7.04-minefield2.exe; I can't find any other version of the wubi installer!
The instructions for "How do I install on a machine with no internet connection?", "How can I use a manually downloaded ISO?", and "How do I install Kubuntu/Xubuntu/Fluxbuntu?" all seem to be inaccurate; installer did not recognize the latest (as of 5/3/07) alternate iso for Xubuntu and downloaded ubuntu-7.04-alternate-i386.iso rather than the ubuntu-7.04-beta-alternate-i386.iso indicated for extant .isos in the instructions.  Without internet access, the installer froze.

2)  I let wubi-minefield download ubuntu-7.04-alternate-i386.iso and installed wubi to D:, the original 20GB IDE HD that came with my eMachines T1220. D: is not part of a RAID, it is not compressed; it isn't even fragmented, but it won't boot. Grub can't find /WUBI/BOOT/MENU.LST (I see a menu.lst in boot and another in its subdirectory, wingrub) and terminates with error message 17 (after apparently looking for it on A: ).  Others have had the same problem.

---

### Post by ecology2007 on 2007-05-04
>   -- [http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html) links to wubi-7.04-minefield2.exe; I can't find any other version of the wubi installer!
There is no final build for ubuntu 7.04 yet. You can safely use this link if you can not wait.
> installer did not recognize the latest (as of 5/3/07) alternate iso for Xubuntu and downloaded ubuntu-7.04-alternate-i386.iso rather than the ubuntu-7.04-beta-alternate-i386.iso indicated for extant .isos in the instructions.This are the iso we are using, they will remains the same at least for 4 or 5 months :
[Ubuntu] 
[http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso)
[Kubuntu] 
[http://releases.ubuntu.com/kubuntu/feisty/kubuntu-7.04-alternate-i386.iso](http://releases.ubuntu.com/kubuntu/feisty/kubuntu-7.04-alternate-i386.iso)
[Xubuntu] 
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/xubuntu-7.04-alternate-i386.iso)

---

### Post by celsus on 2007-05-04
Thanks for the response.  So how do I obtain the wubi installer which will recognize the .isos for which you provided the links, or is that minefield2?  How can wubi be installed to D: without the grub loader terminating with error 17?

---

### Post by ecology2007 on 2007-05-04
Grub is an external project, we are aware of error 17.
Your drive may be compressed or fragmented.

start menu->execute->cmd

The faulty files in that case are initrd and linux. You can download contig.
[http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx](http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx)
 You can use for analyse
 ```
contig -s -a c:\wubi 
```then 
 ```
contig -s c:\wubi 
```To be sure your wubi folder is not compressed 
```
 compact /u /s c:\wubi\
```To be sure your whole c drive is not compressed
```
 compact /u /s c:
```

---

### Post by PersistentLurker on 2007-05-10
Here's a bug in Wubi 7.04-test1 in stage 3.

I downloaded the installer, started the install, and selected Xubuntu. The download, virtual disk creation, and bootloader configuration went on without issue.

When I rebooted and selected "Ubuntu" in ntdlr, the initrd booted up but dropped to a shell prompt shortly after giving the following error (extracted from logs):
```

Failure: 
Could not find any file needed to boot...
The bootlader is probably pointing to the wrong file/folder
Please check that the 'find' kernel parameter in menu.lst
points to the correct location
```

The logs are attached.


**My theory:**

I've done a bit of tracing through the scripts, and here is my understanding of what's going on:

Things start out well. ntdlr does its thing, grub does its thing, the kernel boots and runs the /init script in the initrd. /init is basically error-free all the way up to the line:
```
run_scripts /scripts/init-bottom
```
which apparently leads to the execution of /scripts/init-bottom/lupin, which eventually leads to the execution of the get_iso function in /scripts/lupin-functions. $SETUPISO is not defined, so get_iso goes searching for the iso. It starts in /host/wubi/install/, successfully finds /host/wubi/install/xubuntu-7.04-alternate-i386.iso, and calls is_setup_iso, also in /scripts/lupin-functions.

This is when things get hairy. is_setup_iso successfully mounts the iso on /cdrom, and then runs a number of tests. It runs:
```
[ -e /cdrom/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-15-generic*.deb ]
```
and this test fails. The directory /cdrom/pool/main/l/linux-source-2.6.20/ exists, but it only contains linux-libc-dev_2.6.20-15.27_i386.deb. So is_setup_iso fails.

get_iso proceeds valiantly, checking a large number of other files and directories, spewing a large number of log entries in the process, encountering and trying xubuntu-7.04-alternate-i386.iso a second time. But it ultimately fails.



**My thoughts:**

[LIST]
[*]The iso downloaded by Wubi and the initrd bundled with it refuse to cooperate. That is most certainly a bug that most certainly should be fixed ;).
[*]The test that failed looks like a kludge IMHO, being dependent on the existence of a file that isn't designed to indicate the kernel version. Perhaps looking at the kernel image bundled in the iso is a more reliable test (if this is possible)?
[/LIST]

Hope this helps, devs. Good luck!

---

### Post by ago on 2007-05-10
Those are the relevant lines:

+ [ -e /cdrom/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-15-generic*.deb ]
+ return 12

I haven't personally tested Xubuntu. If Xubuntu uses the same kernel as the official Ubuntu alternate ISO, but it does not include the package we test for, then yes, that is a bug and we will have to find another way to detect the kernel which will work across all ISOs. Suggestions welcome. If the kernel is actually different then it is also a bug, but a different one, since that would mean that we cannot support Xubuntu at the moment (only alternate ISOs with the same kernel as official ubuntu can be installed by wubi, it would of course be possible to compile a dedicated version of wubi).

---

### Post by PersistentLurker on 2007-05-10
Regarding the possibility that Xubuntu is using its own kernel: I compared the kernel Lupin seems to be using (C:\wubi\boot\linux) with a /casper/vmlinuz file in the Xubuntu iso downloaded by Wubi. They match, byte-for-byte.

I don't know how much that means, though ...

---

### Post by ago on 2007-05-10
PersistentLurker in this case we need a way to find out the kernel version within an ISO which works across all ISO.
[https://bugs.launchpad.net/lupin/+bug/87997](https://bugs.launchpad.net/lupin/+bug/87997)

---

### Post by PersistentLurker on 2007-05-11
OK, I tested the new minefield 0.6. It does not work either; it gives the same exact error as did test1.

Attached are comparisons between the old log files I attached in my original message and the new log files. Both lupin.log and zenigata.log showed differences, but only the lupin.log entires look like they are relevant to the problem.

I'll try it again later and see if I can take a closer look at what files is_setup_iso is looking at.

BTW: I've been looking into identifying kernel versions by looking at the kernel image itself, and I have some results. I have found that kernels (i386 ones, anyway) have a magic string "HrdS" at offset 0x202, and they also contain a plain-text kernel version string; the Ubuntu kernel has the string "2.6.20-15-generic (root@palmer) #2 SMP Sun Apr 15 07:36:31 UTC 2007". I've had less success, however, determining *where* to find this string. The closest I came was reading [Documentation/i386/boot.txt]("http://www.mjmwired.net/kernel/Documentation/i386/boot.txt") in the kernel source, which describes how to find the kernel version string, but the current Ubuntu kernel is not consistent with that description (although the VectorLinux v5.8 kernel is).

Maybe it would be enough, however, just to look for this magic string and grep the entire image for the wanted version string. It's a bit of a kludge, but my instinct is that the chance of false positives (i.e. kernel images that contain a different kernel's version string) is very low.

Anyway, HTH, good luck!

---

### Post by ago on 2007-05-11
Is there a file called /cdrom/dists/feisty/main/binary-i386/Packages?
Does it contain a line "Package: linux-image-2.6.20-15-generic"?

---

### Post by PersistentLurker on 2007-05-11
> **ago said:**
> Is there a file called /cdrom/dists/feisty/main/binary-i386/Packages?
Yes.

> **ago said:**
> Does it contain a line "Package: linux-image-2.6.20-15-generic"?
No. In fact, it doesn't even contain any instance of "linux-image" or "2.6.20-15-generic".

I decided to do a grep of the entire iso for "2.6.20-15-generic", and I got some matches. The results are in the attached "version references.txt".

I've done some more work into reading the actual kernel image, if we still want to consider that option. I've thrown together a preliminary script that does this: the attached "kchk.sh". It determines if a given kernel image matches the currently running kernel. I've tested it under the lupin initrd and under a livecd for another distro, and under both environments I've tested it against the ubuntu kernel image and the livecd's kernel image. In all cases, it gave correct results. It's promising.

---

### Post by ago on 2007-05-11
Do you have the same references also in regular ISO? Kubuntu etc? (I cannot check now) . The code looks good and it works on my quick test. If anything the test is now too stringent, k_release (uname -r) might be enough for what we need. Never thought about grepping the actual kernel.

the simplified version of the test might be

grep -q $(uname -r) kernel || return ${ERR_INVALID_ISO}

Is the kernel location always the same across ISOs?

---

### Post by PersistentLurker on 2007-05-11
> **ago said:**
> Do you have the same references also in regular ISO? Kubuntu etc? (I cannot check now) .

I'll go download the other ISOs and check them out.


> **ago said:**
> The code looks good and it works on my quick test. If anything the test is now too stringent, k_release (uname -r) might be enough for what we need. Never thought about grepping the actual kernel.

the simplified version of the test might be

grep -q $(uname -r) kernel || return ${ERR_INVALID_ISO}

I'm glad the code is useful! :D

Regarding the test being too stringent, here's my 2 cents: This code is going to be encountering all kinds of ISOs and all kinds of kernel images, sometimes due to user error, sometimes due bugs in Wubi and elsewhere. And I could compile an kernel unusable with the installer that would pass the "k_release" test.

lupin will eventually be used by those users who have the least tolerance for failures. Robustness and error recovery beyond what seems necessary strikes me as a good goal, at least for the long-term.

But, you have way more experience and knowledge about this than I do, so I'm not in the position to make judgments here. :-# I'm just a Lurker - sort of ;).


> **ago said:**
> Is the kernel location always the same across ISOs?

:lol: I was about to ask you that. I'll look at the ISO's and report.

---

### Post by ago on 2007-05-11
Can you please test minefield 0.7?
More interesting, I am not sure that ensuring kernel consistency is strictly necessary... Provided the installer can go through, it will install a new kernel that will be used on reboot...

---

### Post by PersistentLurker on 2007-05-11
> **ago said:**
> Can you please test minefield 0.7?

A new minefield already! Dang, this place moves fast! :D

Good to see that the infamous error 17 is fixed. Nice work!

OK, I'm testing it now ...

---

### Post by PersistentLurker on 2007-05-11
Sorry to say that minefield 0.7 doesn't work. And I think I know why. Here are the relevant log entires:
```
+ mount -t iso9660 /host/wubi/install/xubuntu-7.04-alternate-i386.iso /cdrom
+ [ -e /cdrom/.disk/info ]
+ [ -e /cdrom/install/vmlinuz ]
+ return 12
```

On the Xubuntu ISO, the kernel image is located at /casper/vmlinuz, not /install/vmlinuz.

I'll restart my investigation of the other two ISO's to see what they look like in terms of kernel image location and kernel version references.

---

### Post by ago on 2007-05-11
Are you sure you are using the alternate ISO? In the one I have I do not see any casper folder...

---

### Post by PersistentLurker on 2007-05-11
> **ago said:**
> Are you sure you are using the alternate ISO? In the one I have I do not see any casper folder...

This is the ISO downloaded by Wubi, and Wubi names it "xubuntu-7.04-alternate-i386.iso". But I must say, I'm getting mighty suspicious that I'm looking at the wrong file. The ISO I have is 565 MB. Looking directly at the filelistings on the mirror download sites, I'm seeing 565 MB listed as the size of the regular "desktop" ISO and 686 MB listed as the size of the "alternate" ISO. I'll download the Xubuntu alternate ISO manually and see how that works out.

---

### Post by ago on 2007-05-11
You are right the URL is wrong. At the moment md5 is disabled so we did not check. Will resubmit always with name 0.7.

---

### Post by ago on 2007-05-11
Done please download wubi again

---

### Post by PersistentLurker on 2007-05-11
OK, trying now.

---

### Post by PersistentLurker on 2007-05-11
All of my previous posts in this forum were made under WinXP. This post is the first one made under this new Wubi-installed Xubuntu system.

In short: it worked! \\:D/

Ago, sorry to have caused you all of this aggravation. I should have checked the md5sums. That's a habit I used to have. Moral: don't trust a filename to indicate actual file contents when working with beta software!

Now I can go to sleep, very content.

Thanks a lot, ago, for the help and for making this very slick piece of software. And thanks to the Xubuntu community for making a disto that's already impressing me.

Have a good one, everyone.

---

### Post by steve196 on 2007-05-29
This one does not create a boot menu entry

---

### Post by steve196 on 2007-05-29
Added a boot menu entry by hand.
> j:\wubi\boot\winboot\grldr = "wubi"


This one lands in a weird windows error about a missing kernel.

---

### Post by ago on 2007-05-29
Check whether you have grldr in the right the same folder(s) that contain ntldr

---

### Post by steve196 on 2007-05-29
Copied everything grub to c: . Now it shows its boot menu, but after that there is error 17. Somehow this grub never finds anything there is on drive J (which is a normal IDE HD with one ntfs partition, but larger than 137 GB)

---

### Post by ago on 2007-05-29
Steve, there are a few test utilities here [http://ubuntuforums.org/attachment.php?attachmentid=33363&d=1180054219](http://ubuntuforums.org/attachment.php?attachmentid=33363&d=1180054219) (fstest.bat in particular), please see the sticky thread on grub and report your results in there,

---

### Post by ago on 2007-05-29
This build is going to be the base for the next release (test3). 

Please test it out and report any success/failure.

---

### Post by prototask on 2007-06-05
I'm a noob with Linux and Wubi, I would love to try Wubi but my install stops after a few minutes saying "Writing configuration files". It continued to display this message for 24 hours before I finally kill the process, any ideas? I'm trying to install on a AMD 1.8GHZ, 512MB ram, 80GB HDD with 20GB free, nVidia FX5600XT, running Windows XP Home. I'm trying to use ubuntustudio using Wubi test3, I also tried the latest minefield, still no luck. HELP!!!:sad:

---

### Post by Epilonsama on 2007-06-06
> **prototask said:**
> I'm a noob with Linux and Wubi, I would love to try Wubi but my install stops after a few minutes saying "Writing configuration files". It continued to display this message for 24 hours before I finally kill the process, any ideas? I'm trying to install on a AMD 1.8GHZ, 512MB ram, 80GB HDD with 20GB free, nVidia FX5600XT, running Windows XP Home. I'm trying to use ubuntustudio using Wubi test3, I also tried the latest minefield, still no luck. HELP!!!:sad:

You should try installing Ubuntu or Xubuntu if you have performance issues.

---

### Post by ago on 2007-06-06
> **prototask said:**
> I'm a noob with Linux and Wubi, I would love to try Wubi but my install stops after a few minutes saying "Writing configuration files". It continued to display this message for 24 hours before I finally kill the process, any ideas? I'm trying to install on a AMD 1.8GHZ, 512MB ram, 80GB HDD with 20GB free, nVidia FX5600XT, running Windows XP Home. I'm trying to use ubuntustudio using Wubi test3, I also tried the latest minefield, still no luck. HELP!!!:sad:

Can you try the minefield? [http://cutlersoftware.com/ubuntusetup/devel/minefield](http://cutlersoftware.com/ubuntusetup/devel/minefield)

---

### Post by prototask on 2007-06-07
That did it, I am now using ubuntustudio and all is well with the world. Thanks for your help.:D

---

### Post by farbror_vattenmelon on 2007-07-14
I have problem after installation of ubuntu (Wubi-7.04.03.exe)

I have 4 HDDs on my computer, 2 s-ata and 2 p-ata . Windows XP is installed on one s-ata disk and works nice. I have installed ubuntu on my Masterdisk of one of my P-ata, and it seem to hang when i select ''Ubuntu' in the boot-menu


[IMG]http://rappo.gtagaming.com/upload/files/28_1184470649.gif[/IMG]

I have waited 40 minutes and it still show this text, so Why can't it boot on that disk?

---

### Post by ago on 2007-07-15
Try wubi 7.04.04. Some more esoteric discs/controllers might not be supported.

---

### Post by farbror_vattenmelon on 2007-07-15
I have tried Wubi-7.04.04.exe now and installed Ubuntu on the same disk that i have WinXP, but on different partitions because it doesn't fit on my C-disk.

Come futher this time, But errors still occure . And it doesn't do anything more than the pictures shows


[IMG]http://rappo.gtagaming.com/upload/files/87_1184502235.png[/IMG]

---

### Post by ago on 2007-07-15
I do not think it's a wubi specific error, see for instance

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112132](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112132)

Try to boot from the live cd and see if it works

---

### Post by ago on 2007-07-15
see [http://ubuntuforums.org/showpost.php?p=3023683&postcount=2](http://ubuntuforums.org/showpost.php?p=3023683&postcount=2)

---

### Post by farbror_vattenmelon on 2007-07-15
I added the line irqpoll now and installation ended great, BUT now it can't find ubuntu when i try to boot on it :D , Guess i'm stupid, but it thought wubi-installer should be easier to use than LiveCD that is included in ubuntu.

[img]http://rappo.gtagaming.com/upload/files/83_1184528375.png[/img]

---

### Post by ago on 2007-07-15
hmm the line in c:\wubi\boot\grub\menu.lst should read

kernel **/wubi/boot/**vmlinuz....

Did the installation finish properly? Or did you hard rebooted?

---

### Post by farbror_vattenmelon on 2007-07-15
The installation went fine i guess. it says something that the system will get rebooted or something, And i just watched. I have un-installed it now and gonna try it again some day.

---

### Post by mbs on 2007-09-07
I have used wubi with previous versions but downloaded the new installer yesterday and got the following message

find --set-root /wubi/linux
    Error 17: File not found

My hard disk was defragmented and there was no compression, but what I ended up discovering was that there was an extra folder that was not included in the grub comments

it should be... find --set-root /wubi/boot/linux

and all of the other commands also.  

The last change was initrd was called initrd.gz

I don't know where these files are in GRUB but I had a hard time changing them

Is this from a previous install or is this a bug that is affecting other people?

---

### Post by ago on 2007-09-07
What version of wubi are you using? Can you make sure it is the one from the website (7.04.04)?

---

### Post by mbs on 2007-09-07
I downloaded the latest wubi downloader from the wubi website two days ago.

I wonder if the previous install left some remnant of a grub file somewhere that is messing things up.  I manually deleted the previous install.

---

### Post by ago on 2007-09-07
> **mbs said:**
> I downloaded the latest wubi downloader from the wubi website two days ago.

I wonder if the previous install left some remnant of a grub file somewhere that is messing things up.  I manually deleted the previous install.

That might explain it. Check under C:\ D:\ E:\... for files like menu.lst, grldr, wubildr...

---

### Post by mbs on 2007-09-07
> **ago said:**
> That might explain it. Check under C:\ D:\ E:\... for files like menu.lst, grldr, wubildr...

That worked!

---

