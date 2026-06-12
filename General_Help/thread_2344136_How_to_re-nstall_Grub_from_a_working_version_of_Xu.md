---
title: "How to re-nstall Grub from a working version of Xubuntu?"
date: 2016-11-22
forum: General Help
---

### Post by jakemaverick911 on 2016-11-22
Hi

I've just transferred my system to a new SSD. Now I'm also running XP...from a separate drive originally, but as this new SSD is big enough I've copied XP across to it. Now the Grub menu won't let e boot into XP as it's obviously set up to look at the other hard drive....

Now I looked at a few threads where you can boot from Live CD and after a lot of faff and quite a bit of danger you can do it that way....I would have though though that there must be a much easier way to do that from within Xubuntu as I can boot to that just fine?

The other thing to mention is...which seems a bit odd to me....is that since I've gone to this new SSD Xubuntu takes a lot longer to boot up.....it seems to hang at the start screen for well over a minute, before finally prompting for the password....once it's into Xubuntu it all loads very quickly as you would expect from an SSD. So I'm also wondering is re-nstalling grub might also somehow fix that problem to or is there anything else that could be causing that?

Thanks
JM

---

### Post by oldfred on 2016-11-22
If BIOS there is just the reinstall of grub2's boot loader to MBR which also runs os-prober to find other systems.
Or you can do a full reinstall of grub-pc which also resets all scripts and changes all settings back to defaults.

But your boot is slow. My 10 year old laptop always booted in about 40 sec with Ubuntu, and 3 to 5 minutes with XP. XP's boot.ini has to have correct drive & partition info. And some internal info may not like being copied to another drive. Chkdsk required, but may not fully fix it.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 
    
New systems & your SSD need AHCI mode. And your Windows XP will not boot with AHCI on unless when you installed it you slipstreamed an AHCI driver. I turned off XP when I got my first SSD, as without AHCI trim does not work and then your SSD will get very slow. I was to the point of only one app still used in XP, booting took forever, many updates as I only booted once per week to run the one app. So SSD became more important then the one remaining app.

To see what is slow:
 Newer systems with systemd:
systemd-analyze blame

---

### Post by irongolem0982 on 2016-11-22
At the very least you could open terminal and try ```
sudo update-grub
``` and see if that fixes anything. like oldfred said XP doesnt like AHCI so it might not work.

Good Luck!!!

---

### Post by jakemaverick911 on 2016-11-23
> **irongolem0982 said:**
> At the very least you could open terminal and try ```
sudo update-grub
``` and see if that fixes anything. like oldfred said XP doesnt like AHCI so it might not work.

Good Luck!!!

thanks...i was hoping that would be the easiest way....it's added two entries for XP now...which is great, 'cept neither of them work....selecting either just sends the machine into constant high pitch beeping mode :-( which makes little sense to me as it did find both copies of xp....?

i've never used AHCI on any of my machines...when I have tried in the past I've always run into major problems, like losing TBs of data and things :-( so prob will never try that again....Xubuntu always seems to have run fine without it.

I'll go do what Old Fred said in a bit...thanks...but i gotta burn the disc on my other machine that is also in bits at the moment.

---

### Post by oldfred on 2016-11-23
For a very short time I would go into BIOS and turn off AHCI to boot Windows, then turn it on so trim worked for SSD. I had XP on my original MBR hard drive and Ubuntu on my SSD using gpt.
That did work, but it added even more hassle to trying to boot Windows just for one app. So XP was not worth keeping.

Also XP is not supported anymore by Microsoft. Probably not safe to use on Internet.

---

### Post by jakemaverick911 on 2016-11-23
yeah i know on XP....but bigger problem being NSA directly writing code for Windows since 7.....still like to use XP for a lot of things, I only really use Xubuntu for Internet, but want to keep XP here as a backup in case xubuntu goes wrong and i need to get online quickly.....

interesting what you say about AHCI and Trim- i have never heard that! my other machine is triple boot, W7, XP and xubuntu...and it's never been an isue as far as I can see.....it's only these past few motnhs that i have mnaged to upgrade to SSds....now in xp on that one health is down to 80% because of the Trim thing I know, even though the drive is 100% ok...but in Windows 7 it works fine.....is soemthing bad happening that i cannae see? and on slipstreaming- i've always run into problems trying to do that....but now that XP is up and running, it must be possible to make it AHCI compliant without having to re-install? if i ever wanted to go that way....but i dnt really see the point of it but you kind of worried me a bit now ;-)

---

### Post by oldfred on 2016-11-23
Some SSD info:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

---

### Post by jakemaverick911 on 2016-11-24
thanks Fred....had seen that but not had time to go through it yet, just too many things to do, never get around to everything ;-)

I just tried the boot repair disk and I immediately get this error

'unknown keyword in configuration file'

so no idea what to do now :-( suppose i'll have to try the live CD but bit reluctant in case that overwrites too much...

---

### Post by oldfred on 2016-11-24
Did you use Ubuntu live installer with Boot-Repair or download the Boot-Repair live.
I think the Boot-Repair live has not be updated for a couple of years, still based on Lubuntu 14.04.

---

### Post by jakemaverick911 on 2016-11-24
yeah i downloaded the separate boot repair disc, so that probably it! :-(

It is Xubuntu flavour latest version I'm using...it still seems bit buggy to me, i'm guessing my live CD won't do it for that either then?

looking in Gparted XP is on sdb3 and I have a yellow triangle with an exclamation mark in it....nothing to say what that means?

---

### Post by oldfred on 2016-11-24
That means gparted thinks it has issues.
Most often chkdsk if NTFS. Or newer Windows 8 or later hibernated or fast start up.

Some times gparted flags partitions that are correct like the bios_grub and Windows system reserved. But they must be unformatted, but then gparted says (incorrectly) that is not correct.

---

### Post by jakemaverick911 on 2016-11-26
Thanks! i didn't realise that you had replied as it was on the second page until now....

but i booted into XP on the other HD and it ran checkdisk and that seemed to have fixed it...but neither wd still boot from the grub menu. so i gave up in the end...and decided as i was so unlikely to use XP again accept in an emergency to get online just having it ont he second HD would be fine...and I wd manually switch in BIOS if i ever needed to boot to it.

So I wiped it off the SSD. Now I have bit of a different problem....:-( I'm in Gparted and what was once XP is now unallocated....but I can't seem to attach that free space to my Ext 4 partition now. I've tried formatting that to Ext 4 as well and tried to combine/ resize but it's not having it.....I think i might have to pull it up in Acronis via XP and try and do it that way.....but there must be a wayof doing it here? I think part of the problem is that now the swap partition is in between the Ext 4 and the unallocated.....I have enough space to run Xubuntu but I've got 31 + gig that not being used...as I have the bigger SSD now i really want to use it ;-)

thanks for your help folks

---

### Post by oldfred on 2016-11-26
That is part of reason I try to put swap as last partition, then it is always out of the way. Some make it first but with older MBR then it uses a primary partition.
Swap also is easy to delete & recreate as it has no data. But then you have to find new UUID and update fstab with new UUID.
You do have to use gparted from live installer as it will not let you edit mounted partitions.
Moving a partition has higher risk so have good backups. Any interruption of a partition move destroys it.

I normally keep / (root) at 25GB and then have a large data partition. Now that I have SSD I have several / on SSD, old /, new /, test / etc. and each mounts same data partition  on HDD, so I have same data in all of them. I still like to have a / on HDD just as another emergency boot.

---

### Post by jakemaverick911 on 2016-11-26
ah...i dnt think i ever had much of a choice as to where to put the swap  partition! i did a backup today though so i'll stick gparted disc in  the machine so it should boot to that 1st thing tomorrow.... i'll give  it a try, but i have no idea on "But then you have to find new UUID and  update fstab with new UUID."...so i hope it dnt screw up!

i wish i  cd afford another SSD and raid them or soemthing, i still pissed that  my SSD just died on me, first i ever bought, after a few months....weeks  of grief, and still int he aftermath of it...lost no end of data!

---

### Post by oldfred on 2016-11-26
Are you sure SSD is dead. With XP you never had AHCI on so it never ran trim.
What does Disks and in upper right corner icon is Smart Status. Does that show anything about drive?

If you delete & recreate swap:
       [URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
 sudo blkid -c /dev/null -o list 
# find UUID in above output, and copy & paste into fstab where old swap UUID is.
      
 sudo nano /etc/fstab 
    [URL="https://help.ubuntu.com/community/Fstab"]
[/URL]        
 Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by jakemaverick911 on 2016-11-27
well, all seems fine now....booted to gparted, bit off a faff- had to delete the swap, combine the partitions and then re-create the swap in the end....even turned AHCI on finally, not booted to XP yet...but I guess i wd need to turn ahci off again when i do that? but all seems to be working fine now...but still slow on startup....I'll work through that optimise ssd page when i get to it.

had a quick look at fstab link....um, i don't think i need to that now but does look a bit complicated.....i used to be a lot better on these things, i need to try and learn again.

well, i was pretty sure that SSD was dead...absolutely nothing from it, tried in several PCs, even Acronis in Windows could not see anything, even baked it....just nothing visible at all on it (it was a cheap Hectron brand, but just wasn't expecting it to completely die no warning whatsoever less than 3 months)....but i'm worried now, i mainly use XP on my other machine...but i also has Windows 7....i thought it was running Trim when i go into that, but if AHCI not on....is it going to die on me as well? :-( that SSD is an Intel, and there is a special programme that supposed to sort out Trim and optimise for me....I might have to risk turning AHCI on again....but in the past it has screwed up all my drives, not just OS but storage drives as well....and i have many Terrabytes in there!

---

### Post by oldfred on 2016-11-27
I do not know SSD well.
But I believe some of the newer better SSD now have more internal ways to do housekeeping. But best to read up on your specific model.
Some require you to download update to the SSD's internals, like updating UEFI/BIOS on PC.

---

### Post by jakemaverick911 on 2016-11-30
Thanks again. I will look when i get chance....i'm not familiar with SSds at all...

but i'm getting very worried again....I have been looking for a utility that will run in xubuntu that will constantly monitor SMART readings... I don't think there is anything? all i could find is GSmartControl...and I just ran that.....and it does not give great information on a lot of the values my SSD is showing pre-failure.......i'm not sure whether to believe that or not? in XP there is an Acronis prog i also use that tell me it's dying as well...but i discounted that as it is an old programme and I suspect it just can't handle SSDs, my alternative prog says it's alright...but with what happened with the last SSD and this now saying pre-failure I@m very worried....dunno what to do :-(

[http://askubuntu.com/questions/661830/enable-trim-for-kingston-ssdnow-v300-on-ubuntu-15-04](http://askubuntu.com/questions/661830/enable-trim-for-kingston-ssdnow-v300-on-ubuntu-15-04)

just found that, that is my drive- so i guess i don't need to do anything as it should be doing it all automatically? but still real slow on boot up....:-(

actually reviews here might explain some of it, wish i had read that b4 i bought :-(

[https://www.amazon.co.uk/Kingston-Technology-Solid-State-Drive/dp/B00A1ZTZOG](https://www.amazon.co.uk/Kingston-Technology-Solid-State-Drive/dp/B00A1ZTZOG)

---

### Post by oldfred on 2016-11-30
Your new swap will not get used unless you have updated fstab.
       to see GUID/partUUIDfor each device, post with code tags to preserve formatting:
sudo blkid -c /dev/null -o list 

Then open fstab and replace current UUID with UUID for swap from above.
      
 sudo nano /etc/fstab

---

### Post by jakemaverick911 on 2016-12-02
thanks, get ya now i think....just i'm not sure what to do....my brain prob not in this right now, but also looking at that page....I'm Xubuntu, so what commands do i use?

running 
 sudo nano /etc/fstab

i get:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=b0915daa-a4da-483b-a8c1-6bccc153cbec /               ext4    errors=remoun$
# swap was on /dev/sdb5 during installation
#UUID=2e6502b4-e7d6-4df9-9d88-7e07d65c75f2 none            swap    sw          $
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by oldfred on 2016-12-02
Did you run the blkid so you know new UUID of new swap?

Then you replace old UUID with new one. this should be old one, if you created new swap.
UUID=2e6502b4-e7d6-4df9-9d88-7e07d65c75f2

---

### Post by jakemaverick911 on 2016-12-12
> **oldfred said:**
> Did you run the blkid so you know new UUID of new swap?

Then you replace old UUID with new one. this should be old one, if you created new swap.
UUID=2e6502b4-e7d6-4df9-9d88-7e07d65c75f2

thank you....and so sorry for so long to reply, i've had a really terrible week and just not had the time to get my head into this :-(

i must be thick...but i just cannae get my head around what to do...I got fstab open in terminal...and trying to copy and paste that text over the bit for sdb2.....it just not working, and i can't figure how to edit that file.....? it's not like a normal text editor or anything.....sorry my brain just really not in gear at moment :-(

---

### Post by oldfred on 2016-12-12
It took me a bit to get used to nano.
It really is a text editor, not really gui.
You have to manually move cursor with arrow keys. Then you can paste.
If you try to click on a location and paste with the mouse, it just copies into where ever cursor is.

---

### Post by jakemaverick911 on 2016-12-12
ok thanks...got it figured now! just to be 100% sure though.... the line UUID=b0915daa-a4da-483b-a8c1-6bccc153cbec i need to delete, paste in UUID=2e6502b4-e7d6-4df9-9d88-7e07d65c75f2, save it and leave it at that? then when i reboot it will start using the swap file?

i dnt really understand how it is booting now if it's not using the swap file i created....i never did manage to get my head around exactly how linux works! ;-)

---

### Post by oldfred on 2016-12-12
I thought it should give an error if swap or entry in fstab not working.

Just replace UUID.
Or copy entire line & add # to convert to comment and edit new line. Then you can go back.
Or backup entire fstab.

---

### Post by jakemaverick911 on 2016-12-13
> **oldfred said:**
> I thought it should give an error if swap or entry in fstab not working.

Just replace UUID.
Or copy entire line & add # to convert to comment and edit new line. Then you can go back.
Or backup entire fstab.

yeah i backed it up....just not sure how to restore if it goes wrong!

and in that file i'm going to have to UUIDs now.....doing it now, hopefully machine wnt die...! ;-)

ok done, fingers crossed for the reboot! ;-)

ok, looks like now i'm screwed....:-(

rebooted, totally bricked my system, start screen for xubuntu started then just hung.....so i now booted in via the CD, thinking it should be easy job to bring up the backup via file manager and put it back....'cept i navigate to etc/ and there is no fstab! so i'm wondering if it is in the home directory now.....which i can't access as it's passworded? :-(

oh shoot...not awake yet! i was looking for fstab directory, there is not one...but there are the files! brought them up in mouspad....unfortunately all the backups are the same, there's 4 of them ?
but none of them was the original file ?

no problem i thought....have fstab open in mouspad, and i have the original entry on this thread...so did that...but it will not save! :-( anyway to override that?

ok i guess opening the file with sudo is my only option now, as that should allow me to save it? i just can't figure how to make that happen.....can't switch tot hat drive with no drive letters? ;-) i know there has to be an easy way to do it......

ok, looks like i sorted it now!

phew ;-)

just remembering how to open the file properly with sudo access did it...

still dnt understand exactly what happened there though :-( i was hoping that doing that would solve the long wait on boot up problem......it's abt 2 minutes i think...and most of the time the HD light ain't flashing, so i'm wondering what it is actually doing....

---

### Post by oldfred on 2016-12-14
When you boot, change grub menu entry on linux line to remove quiet splash. Then you see the processes it is running. Problems may be several lines above where it stops/pauses.

       Newer systems with systemd:
systemd-analyze blame
systemd-analyze critical-chain

---

### Post by jakemaverick911 on 2016-12-14
ah, interesting...running those tools i get

```
59.716s apt-daily.service
          8.878s NetworkManager-wait-online.service
           956ms [EMAIL="tor@default.servic"]tor@default.servic[/EMAIL]e
           764ms dev-sdb2.device
           372ms accounts-daemon.service
           368ms ModemManager.service
           276ms grub-common.service
           244ms apparmor.service
           196ms systemd-logind.service
           173ms apport.service
           162ms irqbalance.service
           157ms speech-dispatcher.service
           156ms ondemand.service
           147ms systemd-udevd.service
           142ms console-setup.service
           125ms lightdm.service
           112ms NetworkManager.service
           107ms tor.service
           107ms alsa-restore.service
           106ms rsyslog.service
           106ms lm-sensors.service
           102ms udisks2.service
           100ms systemd-user-sessions.service
            98ms pppd-dns.service
            95ms gpu-manager.service
            88ms upower.service
            82ms networking.service
            81ms avahi-daemon.service
            80ms binfmt-support.service
            78ms systemd-udev-trigger.service
            75ms keyboard-setup.service
            73ms polkitd.service
            70ms thermald.service
            62ms systemd-journald.service
            54ms systemd-tmpfiles-setup.service
            53ms plymouth-start.service
            42ms ureadahead-stop.service
            40ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
            38ms systemd-journal-flush.service
            36ms systemd-modules-load.service
            34ms systemd-update-utmp.service
            28ms systemd-timesyncd.service
            27ms systemd-tmpfiles-setup-dev.service
            23ms plymouth-read-write.service
            22ms proc-sys-fs-binfmt_misc.mount
            18ms wpa_supplicant.service
            16ms snapd.autoimport.service
            16ms resolvconf.service
            15ms hddtemp.service
            14ms systemd-sysctl.service
            12ms systemd-tmpfiles-clean.service
            12ms systemd-random-seed.service
            12ms ufw.service
            10ms dev-hugepages.mount
             8ms kmod-static-nodes.service
             8ms dev-mqueue.mount
             7ms systemd-update-utmp-runlevel.service
             6ms systemd-remount-fs.service
             6ms setvtrgb.service
             5ms plymouth-quit-wait.service
             4ms sys-kernel-debug.mount
             4ms rtkit-daemon.service
             2ms rc-local.service
             2ms sys-fs-fuse-connections.mount
             2ms systemd-rfkill.service
             1ms snapd.socket

```
```
graphical.target @1min 39.471s
&#9492;&#9472;multi-user.target @1min 39.471s
  &#9492;&#9472;getty.target @1min 39.471s
    &#9492;&#9472;getty@tty1.service @1min 39.471s
      &#9492;&#9472;rc-local.service @1min 39.451s +2ms
        &#9492;&#9472;network-online.target @1min 39.439s
          &#9492;&#9472;NetworkManager-wait-online.service @1min 30.559s +8.878s
            &#9492;&#9472;NetworkManager.service @1min 30.364s +112ms
              &#9492;&#9472;dbus.service @1min 30.290s
                &#9492;&#9472;basic.target @1min 30.240s
                  &#9492;&#9472;sockets.target @1min 30.240s
                    &#9492;&#9472;snapd.socket @1min 30.238s +1ms
                      &#9492;&#9472;sysinit.target @1min 30.235s
                        &#9492;&#9472;apparmor.service @439ms +244ms
                          &#9492;&#9472;local-fs.target @439ms
                            &#9492;&#9472;local-fs-pre.target @439ms
                              &#9492;&#9472;systemd-remount-fs.service @431ms +6ms
                                &#9492;&#9472;systemd-journald.socket @128ms
                                  &#9492;&#9472;-.slice @126ms
```

so i'm guessing          59.716s apt-daily.service
          8.878s NetworkManager-wait-online.service


are the problem bits?

other thing being...I see tor is definately loading there......so how am i still trackable? :-(

---

### Post by oldfred on 2016-12-14
Please use code tags on longer terminal or text output.
Easy to add in Forum's advanced editor and # icon.

Never used tor

Just for ref, from my system.

```
fred@Asusz97:~$ systemd-analyze blame
          7.860s NetworkManager-wait-online.service
           425ms systemd-fsck@dev-disk-by\x2duuid-a0c1c99f\x2d0f09\x2d4787\x2da7
           354ms dev-disk-by\x2duuid-212797b0\x2d0342\x2d44d8\x2da111\x2dd5ce82e
           246ms dev-sda6.device

```

```
graphical.target @9.232s
&#9492;&#9472;multi-user.target @9.232s
  &#9492;&#9472;minidlna.service @9.181s +50ms
    &#9492;&#9472;network-online.target @9.168s
      &#9492;&#9472;NetworkManager-wait-online.service @1.308s +7.860s
        &#9492;&#9472;NetworkManager.service @1.240s +61ms

```

Network or graphical seem to be what is slow on my system. But with SSD, and  delays intentionally set in UEFI and grub, so I have time to press keys, it shuts down & reboots in less than 30 sec.

---

### Post by jakemaverick911 on 2016-12-14
ok thanks, will try and remember to do that....

much clearer to see! so it seems apt-daily.service and the graphics is what is causing the problem.....that seems to be a ridiculous amount of time.....is there any way to change/ fix that?

---

### Post by oldfred on 2016-12-14
Are you using Wireless or Wired connection?
Is system up to date?
Do you have correct graphics driver?

But whatever issue may be, best to start new thread as title of this one is grub related. If you can narrow down issue, then start new thread with that issue in title.

---

### Post by jakemaverick911 on 2016-12-14
i'm on wireless<br><br>system up to date as far as i can tell....it did seem to have a problem d/l some updates for a while but i think that has cleared itself now<br><br>it's onboard graphics for this machine, intel chip.....it set that up automatically when xubuntu installed so i presume it must be correct<br><br>i think i'm just going to have to put up with it. i'll close this thread in a bit, seems lil point in starting a new one....thanks for the help ;-)

---

