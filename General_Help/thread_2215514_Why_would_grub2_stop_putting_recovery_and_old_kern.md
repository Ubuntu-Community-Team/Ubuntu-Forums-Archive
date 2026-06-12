---
title: "Why would grub2 stop putting recovery and old kernels into submenus?"
date: 2014-04-07
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-04-07
Grub used to put the menu lines for old kernels, and I think "recovery" as well into submenus, so they didn't clutter up the menu. Mine quit doing that. Can't say I noticed when it quit but my menu finally grew insanely large and the entries weren't in a very rational order. By that I mean the entries that would boot what I had on partition 6 for instance wouldn't all be grouped together but would have entries for OSs on other partitions intermingled.  I tried Grub Customizer. It deleted 2 entries automatically. But that left a lot and it looked like I was going to have to go through them very tediously one by one. The titles weren't much help because at the moment I have 3 different partitons with variations of 13.10.  So I purged all my old kernels and ran sudo update-grub and rebooted but there were still a ton of extra menu entries. Thought maybe I'd made a mistake and did it again. No change. Purged grub* (including grub customizer) entirely and reinstalled Grub-pc. Twice. No change. Purged grub* and deleted every file I could find with grub in the name. Then reinstalled grub-pc. Tried to reboot. I don't recall the exact error message but something like "no operating system found". Rescuatux cd (great utility disk) fixed that and now my grub menu has one entry for each of 5 bootable partitions (and the memtest entries, I believe). 

So I don't know what is going to happen when I next update a kernel.  Is it possible there is some "recommended" or plugin or helper program Grub needs to do the submenu thing? Or a setting somewhere that tells it to? Surely they didn't take that feature out?

---

### Post by ajgreeny on 2014-04-07
It's difficult to know exactly what you're getting in the grub menu so can you post back here the output of
```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
ls -l /boot | grep vmlinuz
``` which will show us exactly what kernels you have and OSs you see in grub.

Have you updated your machine from an earlier version of ubuntu as I understand that can cause the type of menu you mention, but as I have never done an upgrade but always a clean install, and I only ever keep two kernels on my system at any time, I am confused about what really happens in upgrades regarding kernels.

---

### Post by Dreamer Fithp Apprentice on 2014-04-07
Thanks, Ajgreeny.
> **ajgreeny said:**
> It's difficult to know exactly what you're getting in the grub menu so can you post back here the output of
```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
ls -l /boot | grep vmlinuz
``` which will show us exactly what kernels you have and OSs you see in grub.Remember that I've "fixed" it for the moment as described so this may not be helpful.
```
me@ubuntu:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'GNU/Linux' --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple
    menuentry 'GNU/Linux, with Linux 3.11.0-19-generic' --class gnu-linux --class gnu --class os $menue
    menuentry 'GNU/Linux, with Linux 3.11.0-19-generic (recovery mode)' --class gnu-linux --class gnu -
menuentry 'Ubuntu 13.10 (13.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'ospr
    menuentry 'Ubuntu (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry_id_option 'os
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (on /dev/sda1)' --class gnu-linux --class gnu --cla
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode) (on /dev/sda1)' --class gnu-linux -
    menuentry 'Ubuntu 13.10 (13.10) (on /dev/sda1)' --class gnu-linux --class gnu --class os $menuentry
menuentry 'Ubuntu 13.10 (13.10)' --class gnu-linux --class gnu --class os $menuentry_id_option 'ospr
    menuentry 'Ubuntu (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry_id_option 'os
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (on /dev/sda5)' --class gnu-linux --class gnu --cla
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode) (on /dev/sda5)' --class gnu-linux -
    menuentry 'Ubuntu 13.10 (13.10) (on /dev/sda5)' --class gnu-linux --class gnu --class os $menuentry
menuentry 'Ubuntu 12.04.4 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option
    menuentry 'Ubuntu, with Linux 3.2.0-60-generic (on /dev/sda7)' --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.2.0-60-generic (recovery mode) (on /dev/sda7)' --class gnu-linux --
menuentry 'Ubuntu 12.04.4 LTS (12.04)' --class gnu-linux --class gnu --class os $menuentry_id_option
    menuentry 'Ubuntu, with Linux 3.2.0-60-generic-pae (on /dev/sda8)' --class gnu-linux --class gnu --
    menuentry 'Ubuntu, with Linux 3.2.0-60-generic-pae (recovery mode) (on /dev/sda8)' --class gnu-linu
    menuentry 'Ubuntu, with Linux 3.2.0-60-generic (on /dev/sda8)' --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.2.0-60-generic (recovery mode) (on /dev/sda8)' --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae (on /dev/sda8)' --class gnu-linux --class gnu --
    menuentry 'Ubuntu, with Linux 3.2.0-59-generic-pae (recovery mode) (on /dev/sda8)' --class gnu-linu
me@ubuntu:~$ ls -l /boot | grep vmlinuz
-rw------- 1 root root  5669328 Mar 11 15:26 vmlinuz-3.11.0-19-generic
me@ubuntu:~$ 
```> **ajgreeny said:**
> Have you updated your machine from an earlier version of ubuntu . . . Yes. More than once.
> **ajgreeny said:**
>  . . . as I understand that can cause the type of menu you mention.Ah ha! That's probably the problem then. At the very least you've given me a lead to search. If you happen to have a citation to where you saw that, perhaps you can post the link, or in not, any info you can recall  that might help me find it with a search engine. If that is the problem that suggests to me I may have been on the right track to purge grub*, delete all the *grub* files I could find, reinstall grub-pc, and update-grub. Maybe I just need to find the devil that dwells in those details.

---

### Post by grahammechanical on 2014-04-07
I do not think that this applies to you but it might. For a time what was called Grub 2 was actually Grub 1.99. When we finally got Grub 2 we also got those sub-menus. I found that if I had an install of Ubuntu with the old Grub 1.99 and it got a kernel update which installed it version of Grub into the MBR then there was that very messy Grub menu that you refer to with many double entries. Furthermore, I think that in the process of updating the Grub configuration file the utility reads grub.cfg from all the other partitions to get information about the OS there and then overwrites those other grub.cfg so that the messed up grub.cfg is in all partitions.

The solution is to get into Ubuntu with Grub 2.0 and run

```
sudo update-grub
sudo grub-install /dev/sda
```

Do you think that you have an install of Ubuntu with Grub 1.99? Or some other distribution with Grub 1.99? It cannot handle Grub 2.0 configuration files with the sub menus.

Regards.

---

### Post by ajgreeny on 2014-04-07
Ialways use synaptic, which you may have to install first, to remove any unwanted kernels from my machine,

I search using name only for theversion numbers of unwanted kernels, eg in your case
3.2.0-
and then remove all the superfluous ones, leaving just 3.11.0-18 and 3.11.0-19.

As for recovery mode not showing, look at **/etc/default/grub** to see if you have a line **#GRUB_DISABLE_RECOVERY=true** without the # at the start. If it has no # you should add one and recovery mode will appear in grub again.

---

### Post by oldfred on 2014-04-07
Also if you used grub customizer, it creates new files in the grub script folder with its modifications. But then a reinstall of grub readds the standard grub scripts and you then have two copies of scripts running which creates duplicate entries.

Post this:
 ls -l /etc/grub.d

---

### Post by Dreamer Fithp Apprentice on 2014-04-08
Thanks, Grahammechanical.
> **grahammechanical said:**
> 
Do you think that you have an install of Ubuntu with Grub 1.99?
No, but I do have 2 installations of 12.04 which installed with 1.98, which was also called "2". They shouldn't have grub anymore, as I purged it in those installations, but since "purging" doesn't seem to delete all associated files, regardless of what the documentation implies, and given the mechanism you describe whereby problems can be propogated from an earlier installation of grub to a newer one -- yes, that very plausibly could be either A cause or THE cause of the problem.  The fact that nothing got rid of it until I hand deleted all those files and reinstalled grub from a Rescuatux CD seems consistent with that possibility.
> **grahammechanical said:**
> The solution is to get into Ubuntu with Grub 2.0 and run
```
sudo update-grub
sudo grub-install /dev/sda
```
Did that already. Didn't seem to help at the time. But if that is the right order I may have done it backwards.

If this was the culprit it sounds like what I"ve done should be enough to keep the problem from coming back, but I think I'll format those two partitions with 12.04 now and when I install something there I'll leave off installing a new bootloader and just update-grub from the system I'm on now to get the new system into the menu rather than just mindlessly accepting the defaults regarding a bootloader as I've tended to do in the past.


Thanks again, Ajgreeny.
> **ajgreeny said:**
> Ialways use synaptic  . . .  to remove any  unwanted kernels  . . . I used to do it that way.  Now I use  this in a script:```
sudo dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname  -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^  ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```That line's  not my work. If I'd tried to do it I'd have had to break it down into a  lot of short lines wtih intermediate variables to keep from getting lost  part way there. I think I got it from somebody as stackoverflow,  although I don't remember for sure. > **ajgreeny said:**
> As for  recovery mode not showing, look at **/etc/default/grub** to see if you have a line **#GRUB_DISABLE_RECOVERY=true**   without the # . . . Noted. Thanks.  I hadn't actually noticed   that was gone until you mentioned it.  I'd been more concerned about  not  getting proliferating entries again. Actually I don't have an **/etc/default/grub at all now - just some old ones I've renamed [B]/etc/default/grub-bak-date-time. And it seems to work without it.  I guess it's got some defaults built in**[/B]. But, yes, I should resurrect one of them after looking it over and maybe editing it.

Thanks, Oldfred.
> **oldfred said:**
> Also if you used grub  customizer, it creates new files in the grub script folder with its  modifications. But then a reinstall of grub readds the standard grub  scripts and you then have two copies of scripts running which creates  duplicate entries.Ah ha! I had already formed the impression  Grub Customizer had made things worse. Now that explains the mechanism  perfectly.
> **oldfred said:**
> Post this:
ls -l /etc/grub.d

```
$ ls -l /etc/grub.d
total 68
-rwxr-xr-x 1 root root  7850 Oct 23 16:48 00_header
-rwxr-xr-x 1 root root  5949 Aug 15  2013 05_debian_theme
-rwxr-xr-x 1 root root 11479 Oct 23 16:48 10_linux
-rwxr-xr-x 1 root root 10258 Oct 23 16:48 20_linux_xen
-rwxr-xr-x 1 root root 11531 Oct 23 16:48 30_os-prober
-rwxr-xr-x 1 root root  1426 Oct 23 16:48 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Oct 23 16:48 40_custom
-rwxr-xr-x 1 root root   216 Oct 23 16:48 41_custom
-rw-r--r-- 1 root root   483 Oct 23 16:48 README
```

Thanks a lot, guys! I've implemented all the changes these ideas imply. After I back this up with fsarchiver I'll probably try upgrading it tp 14.04, perhaps tomorrow. That's likely to bring a new kernel with it, so it will provide a good test.

---

### Post by Dreamer Fithp Apprentice on 2014-04-09
I hit a snag. I tried an approach to having a second grub menu as the default entry on the main one, so I could have a simple failsafe and discovered I'm missing the vmlinuz & initrd.img symlinks in / on 2 of my systems. I doubt it is related to this so I posted another thread:
[http://ubuntuforums.org/showthread.php?t=2215922&p=12982054#post12982054](http://ubuntuforums.org/showthread.php?t=2215922&p=12982054#post12982054)
But I thought I should mention it here because I'm holding off updating (and seeing if the proliferation menu entries problem is solved) until I figure that out.

---

### Post by oldfred on 2014-04-09
It is in the maintenance free entry, plus I and others have posted it many time.
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
Same here:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

I have always seen the links. I thought they were created with every new kernel install. When I un-install too many kernels, (I like to keep 2) but if only keep 1, then the backup link shows broken. Have not traced where links come from. I thought all Debian based distributions had links, not sure about others.

 apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

Does this do anything?
      
 #would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

---

### Post by Dreamer Fithp Apprentice on 2014-04-10
> **oldfred said:**
> It is in the maintenance free entry, plus I and others have posted it many time.
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
Same here:
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)That second might be the one I followed, at any rate, that's the general idea. And THAT is working quite well. > **oldfred said:**
> I have always seen the links. I thought they were created with every new kernel install. When I un-install too many kernels, (I like to keep 2) but if only keep 1, then the backup link shows broken. Have not traced where links come from. I thought all Debian based distributions had links, not sure about others.At Coldcritter64's suggestion, I just added the links by hand. And I have upgraded the kernel on 2  systems after doing that and the links do get updated automatically. So  whatever caused the links to not be there apparently didn't totally  disable whatever is supposed to maintain them. There's one piece of  residual weirdness there -- the .old links are to the new kernel, not the  old one. I don't see that as of any real consequence but I'll be curious  to see if it starts behaving the way I expected it to after a cycle or  two. So I have a stable, working simple menu and I can still get the  regular grub menu by pressing an arrow in the second it displays.> **oldfred said:**
> apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

Does this do anything?Pertaining to this issue, no, not unless a new kernel is installed - if one is I suspect that's when I get a new grub menu line. I run a login script that tells me how long it has been since I upgraded (or checked and found nothing to upgrade) and then offers to```
sudo apt-get update
sudo apt-get dist-upgrade
```. I upgrade whenever it's been more that 10 hours or so.

As for the original problem, it hasn't gone away. I now have duplicate entries for my main system and its recovery menu. I think the problem may originate in "update-grub" because:```
me@ubuntu:~$ sudo update-grub
[sudo] password for me: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
  No volume groups found
Found Ubuntu 13.10 (13.10) on /dev/sda1
Found Ubuntu 13.10 (13.10) on /dev/sda5
done
me@ubuntu:~$ 
```Notice that the first system it found - it found it twice.
I've confirmed that I did purge grub-customizer, but probably tomorrow I'm going to poke around looking for traces of it I can delete, if a better idea doesn't come along first. Right now, my best idea is to sleep on it and later apply massive amounts of coffee.

I'd like to figure this out before Trusty is trusted, but if I don't, maybe it'll go away when I upgrade. I don't plan to reinstall but to do the release upgrade. If it doesn't work, I've got my fsarchiver backups, and 2 ofher bootable partitions I can do the restore from.

Curious isn't it?

Thanks a lot, Old Fred.

---

### Post by oldfred on 2014-04-10
That would be typical of a duplicate 10_linux or it has each part of script twice inside it. Any hidden files?
Rule is any executeable file with 2 digits (numbers) & underscore in /etc/grub.d will be run in number order.

Or if you somehow had two identical kernels which I do not think is possible?

---

### Post by Dreamer Fithp Apprentice on 2014-04-11
> **oldfred said:**
> That would be typical of a duplicate 10_linux or . . .AAAAAAAAAHH!!! I did it to myself! Following my habit of making backup copies of anything before I alter it, as you can see:```
me@ubuntu:~$ ls /etc/grub.d/
00_header
05_debian_theme
05_debian_theme-bak-2014.04-Apr.09-Wed.AM.02.17.32
05_debian_theme.dpkg-old
10_linux
10_linux-bak-2014.04-Apr.08-Tue.PM.11.09.22
20_linux_xen
20_memtest86+
30_os-proberbarrell
30_uefi-firmware
40_custom
40_custom-bak-2014.04-Apr.09-Wed.AM.01.44.11
41_custom
README
me@ubuntu:~$
```The heck of it is, I knew the rule. Making a backup before modifying something is just such an automatic habit I never thought about it.

So I'll go through these and move or delete the ones that are redundant. Then to get rid of the duplication that has already occured I'll do what worked before - purge grub*, delete or move all the files I can find with grub in the name, install grub-pc. That will break it, but then Rescatux can fix it. Maybe by then there will be a new kernel to test it. Not going to start that tonight. Maybe tomorrow after a hogshead of coffee. By then I might see a simpler way.
 
Thanks a million, Oldfred.

---

### Post by oldfred on 2014-04-11
Stay in the habit of making backups, that is a good thing. :)

I did the same thing once.
So I then changed to put bkp_ or something at beginning of name instead of the end and then also turn off executeable bit. Either change should be enough.

 sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by Dreamer Fithp Apprentice on 2014-04-12
> **Dreamer Fithp Apprentice said:**
> to get rid of the duplication that has already occured I'll do what worked before - purge grub*, delete or move all the files I can find with grub in the name, install grub-pc. That will break it, but then Rescatux can fix it. Maybe by then there will be a new kernel to test it. Wasn't needed. After moving the offending files from grub.d, "sudo update-grub" was sufficient. I've upgraded kernels twice and each bootable filesystem has one main entry and one submenu. 100% solved. Thanks a bunch.

---

