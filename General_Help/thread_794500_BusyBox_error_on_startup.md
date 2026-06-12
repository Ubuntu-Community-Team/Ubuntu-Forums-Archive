---
title: "BusyBox error on startup"
date: 2008-05-14
forum: General Help
---

### Post by Bungeeman on 2008-05-14
Hello, I am new to wubi and ubuntu but I have always wanted to try Linux so I thought that this would be the way to go.
I installed wubi and it seemed to go well and I was asked to reboot which I did however after what seemed to be a good start (I got a nice orange ubuntu graphic going back and forth) the boot up stopped with this message 
"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (Ash)
Enter 'help' for a list of commands
(initramfs)"
I typed in help for all the good that did.
After three hours of staring at this and getting nowhere I did something I never do, I pulled the plug. I know, I know, but what else was I supposed to do as I couldn't get rid of the error screen. So I rebooted in to windows xp and did a disc check, no problems found I then shut down properly and I tried ubuntu again, same result. I then uninstalled wubi and ubuntu and started again same result.I am now very unhappy as I thought that this might be a way of getting away from the Windows thing but obviously not as you can say what you like about windows but I have never had these kind of problems.
Can anyone help.

---

### Post by ago on 2008-05-14
Do you have multiple hard disks? If not run chkdsk /r from windows.

---

### Post by Bungeeman on 2008-05-15
Thanks for your reply and Yes I have two Hard Discs and I am running chkdsk as I send this.

---

### Post by ago on 2008-05-15
Then try also: [https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

Pls let me know if it works.

---

### Post by Bungeeman on 2008-05-15
Sorry if I am being a bit thick, but which part of the page you link goes to do you want me to try?

---

### Post by ago on 2008-05-15
Booting problems: Error 21, Selected disk does not exist

---

### Post by Bungeeman on 2008-05-15
Thanks I have to go to the dentist now Ahhhhhh.
But I will try it as soon as I come back in an hour.

---

### Post by Bungeeman on 2008-05-15
Hello again.
After the chkdsk I tried ubuntu again same result as before
"BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (Ash)
Enter 'help' for a list of commands
(initramfs)".
I then had to pull the plug again,(I hate doing that)to leave the error screen. Is there another way to leave the error screen incidentally? As I do not want to try ubuntu again as I keep having to pull the plug on my pc and I don't want to do that as I know the damage it can cause and I don't want to ruin my pc just to try ubuntu out..
Anyway the folder mentioned in the post you linked me to:- c:\ubuntu\disks\boot\grub\menu.lst. is empty I even showed hidden files and it is empty. There is a menu list in "c:\ubuntu\install\boot\grub" and another in:-
"c:\ubuntu\winboot" but I can't open them anyway.
Any further help would be appreciated but as I say I will not be booting ubuntu again until I have some confidence it will work as I am not willing to destroy my pc just to rid myself of windows.

---

### Post by Exhale. on 2008-05-15
I had the same problem aswell, But i did this part from the Ubuntu page

> If the boot problem happens after the Ubuntu installation (after second reboot) and you have multiple disks, sometimes the disk order at boot is wrong (it is a known bug: [WWW] [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8497)). In such cases, edit c:\ubuntu\disks\boot\grub\menu.lst. You have to change all the lines "root (hdX,Y)/ubuntu/disks" to "root ()/ubuntu/disks". Also edit the line that starts with "#groot=(hdX,Y)/ubuntu/disks" to "#groot=()/ubuntu/disks".

And it works fine now.

Also. Type "reboot" no "" and it should reboot your computer

---

### Post by Bungeeman on 2008-05-15
Thanks but that is the page that Ago sent me to and the folder mentioned in that is empty. Thanks anyway for answering.

---

### Post by Exhale. on 2008-05-15
Maybe uninstall and re install then? 

Cause i was getting the exact problem.
Did that, and now it works perfectly fine.

But dont just unplug. type reboot

---

### Post by Bungeeman on 2008-05-15
I have now uninstalled and installed three times and had the same result each time. Much as it pains me to say, I think that I might have to carry on with windows until this is more stable, or at least easier and safer to install as I have looked through the forums and this seems to happen a lot to a lot of people (including you it seems) too many for me to have much confidence in it. Unless of course someone can solve this for me.Thanks again for your help.

---

### Post by ago on 2008-05-15
> **Bungeeman said:**
> Thanks but that is the page that Ago sent me to and the folder mentioned in that is empty. Thanks anyway for answering.

Then it means that the linux side installation did not take place.

At the busybox type 

cat /casper.log

and post here any error message you see (you can scroll with shift+pgup). Pay attention to errors with mount commands.
You did not install in raid or encrypted disk, correct?

---

### Post by Bungeeman on 2008-05-15
Thanks for sticking with me.
Last part first. You are correct in that I did not install in raid or encrypted disk. 
Now, I typed cat/casper.log as you said and I did not have to scroll up or down as there was only one line I quote:-
cat/casper.log/bin/sh:cat/casper.log:not found.
While at the BusyBox I rebooted a few times and tried all the other options that are offered when you press ESC during loading, and none of them worked.

---

### Post by ago on 2008-05-15
there is a space between cat and /casper.log

---

### Post by Yondergod22 on 2008-05-16
try this: [https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623)
it didn't work for me, but I don't think I did it right, good luck though.
also to restart on the busybox screen, you can press ctrl-alt-del

---

### Post by Bungeeman on 2008-05-16
Reply to ago,
Sorry I didn't notice the space (Duh!)
I think that you are right in that Linux has not installed properly as this is what I got when I typed your command properly.
**init:/init:1 cannot open dev/sdd No Medium Found.**
There was a long list of files like this only the sdd part was replaced with **sde, sdf, scdo, scd1, sdc.** etcetera. There was also one similar,
**init:/init:1 cannot open dev/fdo No such device found.**
Then right at the bottom it reported the following:-
**Unable to find a medium containing a live file system. **

---

### Post by ago on 2008-05-16
Look for mount errors on sda and sdb (the 2 hard disks).

grep sda /casper.log
grep sdb /casper.log

---

### Post by Bungeeman on 2008-05-16
I appreciate you trying to help but I'm sorry you are losing me now. I have looked in the list of errors and I cannot find a mention of these files at all.
I think that maybe this is getting a lot more complicated than I thought it would be. I thought that it would be a simple install and try out ubuntu before maybe using it instead of windows but I don't think that is going to happen do you? I want an OS that does it's job behind the scenes without my having to do this much work. Do you think that this is fixable or should I just call it quits?
Thank you

---

### Post by ago on 2008-05-16
what is the output of 

cat /proc/partitions

---

### Post by Bungeeman on 2008-05-16
Now you really have lost me what are you talking about? I don't even know what cat /proc/partitions is so I certainly don't know the output of it. Sorry

---

### Post by ago on 2008-05-17
Type that at the prompt and post the output. Basically it appears that either some of your disks/partitions cannot be seen or they cannot be mounted.

---

### Post by Bungeeman on 2008-05-17
Now that I understand here goes:-

[COLOR="Red"]Major[/COLOR]  .. [COLOR="Blue"]Minor [/COLOR]  [COLOR="Lime"]Blocks [/COLOR]    ....... Name
[COLOR="Red"]8[/COLOR]      ......... [COLOR="Blue"]0[/COLOR]      .... [COLOR="Lime"]195360984[/COLOR] ..  sda
[COLOR="Red"]8[/COLOR]      ......... [COLOR="Blue"] 1[/COLOR]     .... [COLOR="Lime"]192709376[/COLOR] ..sda1
[COLOR="Red"]8[/COLOR]      ........ [COLOR="Blue"]16[/COLOR]     .... [COLOR="Lime"]117246528[/COLOR]  .. sdb
[COLOR="Red"]8[/COLOR]      ......... [COLOR="Blue"]17[/COLOR]     .... [COLOR="Lime"]117242338 [/COLOR] .sdb1

I hope that helps

---

### Post by ago on 2008-05-18
grep sda1 /casper.log -A2 -B2
grep sdb1 /casper.log -A2 -B2

---

### Post by Bungeeman on 2008-05-18
I typed your commands at the BusyBox initramfs prompt and got nothing it just went back to the initramfs prompt

---

### Post by ck09 on 2008-05-18
Hi I'm having the same problem.  Installed Ubuntu 8.04 within Vista, rebooted and have the splash screen for about 2 mins before the busybox appears.

Has been some years since I used linux and decided to give this a try after it received some coverage on BBC News ([http://news.bbc.co.uk/1/hi/technology/7358483.stm](http://news.bbc.co.uk/1/hi/technology/7358483.stm))

Seems linux has some way to go yet.  Forcing users to utilise a command prompt is something Microsoft abandoned with DOS 6.22 many years ago.

I'll attempt a couple of commands if you have any suggestions and think this can be resolved quickly.  Unlike the other user I have a single partition; two RAID 0 drives.

Thanks

major minor blocks name
8 0 312571224 sda
8 1 56196 sda1
8 2 15728640 sda2
8 3 609351680 sda3
8 16 312571224 sdb

cat /casper.log indicates no medium with a file system exists
grep sda /casper.log = blank
grep sdb /casper.log = blank

---

### Post by ago on 2008-05-19
(Software) raid 0 is not supported.

You can try to mount the partitions manually and see if you can reach the ubuntu folder

mkdir -p /tmpmnt

#sda1
mount /dev/sda1 /tmpmnt
ls /tmpmnt/ubuntu
umount /tmpmnt

#sdb1
mount /dev/sdb1 /tmpmnt
ls /tmpmnt/ubuntu
umount /tmpmnt

...

---

### Post by Bungeeman on 2008-05-19
Hello ago I am not really sure who your last post was meant to be for however.
**I tell you what let's not and say we did eh**? 
I am more than a little fed up with this. It is taking to long (Nearly a week now)it is much to complicated, and now you say that I have to manually mount the partitions, I don't think so thanks all the same. I have installed Windows on at least 10 machines up to now and never had anything like these problems.
As the other poster has said I think that ubuntu et al has a very long way to go before I would allow it to be running my pc, windows is bad enough but this is appalling. So I think that I will stop now before this dubious OS does some serious damage to my computer.
Thanks for all your help AGO and I hope to try again in the future but it won't be any time soon.
Cheers!
Bye.

---

### Post by KB918 on 2008-05-20
Ok.  Well, I still want to give this a try.  I already have a Mac that works perfect (not trying to be a Mac fanboy or beat up on windows or Linxu, but its true.  Bungeeman should give it a try if he has that many problems.)  Anyway, like I said, I will still try.

We have the same problems and I also have RAID0 in my machine which is active as I try to install Ubuntu.  Will that cause this problem?  I don't really need the RAID0 mounted.  I didn't even install on the RAID but instead on a 160g partition all to itself.

I followed some of your commands Ago and they are every similar to Bungeeman's

For the cat /casper.log I received this

cp: custom-installation/initrd-override/*: No such file or directory
+ modules=
megaraid
aacraid
libata
sd_mod
scsi_mod
ehci0hcd
uhci-hcd
ohci-hcd
libusual
usb-storage
ahci
ata_piix
pata_sis
pdc_adma
sata_inic162x
sata_mv
sata_nv
sata_promise
sata_qstor
sata_sil24
sata_sil
sata_sis
sata_svw
sata_sx4
sata_uli
sata_via
sata_vsc
nls_utf8
nls_cp437
nls_iso8859-1

/init: /init:  1:  cannot open /dev/scd0:  No medium found
/init: /init:  1:  cannot open /dev/scd0:  No medium found
/init: /init:  1:  cannot open /dev/scd0:  No medium found
/init: /init:  1:  cannot open /dev/scd0:  No medium found
/init: /init:  1:  cannot open /dev/scd0:  No medium found

(this portion is repeated about 20 something times, so I won't waste my time with that.  Its exactly the same all the same down.)

Last it says Unable to find a medium containing a live file system

When I typed grep scd0 /casper.log, it just repeated "/init: /init:  1:  cannot open /dev/scd0:  No medium found" about another 20 times the same as before

I typed cat /proc/partitions and I got this

major  minor   # blocks               name

8          0             312571224       sda
8          1             156280288       sda1
8          2             156288352       sda2
8          16           312571224       sdb
8          17           625139712       sdb1
8          32           312571224       sdc
8          33           626137664       sdc1


Typing grep sda1 /casper.log -A2 -B2 did nothing for me as well.  I assume that was more specified for his computer though, but gave it a shot anyway

Well, I am new to Linux and have no clue what most of this means.  I know that is deals with HDDs and that one of the other guys problems might have been that he has his floppy enabled when he doesn't have one, but, hey, like I said, i have no clue, haha.  That's why I'm here to learn

Thanks

I think I typed all that correctly btw...

"KB"

---

### Post by ago on 2008-05-21
Wubi should try to mount all your partitions EXCEPT the ones on raid. I assume that sdb adn sdc are the raid array. But sda1 sda2 should be accessible and provided you installed wubi in there it should find it or at least spit some error message. Hence the first thing is to try to mount sda1 and sda2 manually.

mkdir /sda1
mount /dev/sda1 /sda1
ls /sda1/ubuntu

mkdir /sda2
mount /dev/sda2 /sda2
ls /sda2/ubuntu

See if you can mount and browse to the ubuntu folder. Also please post the output of

cat /proc/cmdline

---

### Post by AvvY on 2008-10-13
I am having a similar issues to the OP.

I downloaded the 8.04.1 i386 iso. (has been md5 checked as well as confirming it with the torrent and my torrent client. I have burned 2 copies to blank DVD (since I didn't have a spare blank CD-R) and I got the same Busy Box prompt from a cold boot (I am NOT using Wubi). I then burnt the ISO to a CDR (slow burn speed and verified) and I still get the same Busy Box prompt (again I am NOT using Wubi, this is from booting the CD to run the live distro).

I have run linux on this hardware config before (4+ years ago - including older versions of Ubuntu) so I know it should all work. To confirm I am (at the moment) NOT trying to install Ubuntu, simply to run the Live distro from the disc - even when I chose to check the disc for errors I get the same Busy Box screen.

Thanx

---

### Post by KEE on 2008-10-13
yes what the hell is going on=S i am getting an error on start  after that automatic check on start up!!! is a bad update, cause i just recently updated gutsy 7.10? then  i turned off the os to switch to windows to play a game ( the game plays better on windows for some reason) =S...came back to ubuntu and it did a check and told me of an error(dont remember what error cause it still went through to the os but i am afraid once i power down its not going to start up again =( i am going to make a separate post if they are no answers here( sorry if i am intruding on the poster, i just felt part of this error )

---

### Post by ago on 2008-10-13
There are several reasons for busybox, please see the troubleshooting section of the WubiGuide: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Those using versions << 8.04, should uninstall and install 8.04 or 8.10 as earlier versions are not supported.

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

