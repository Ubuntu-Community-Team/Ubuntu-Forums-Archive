---
title: "Chromebook stuck after battery drains out"
date: 2014-12-21
forum: General Help
---

### Post by andrea48 on 2014-12-21
Hi i am almost a computer noob but with the help of [this comunity]("http://ubuntuforums.org/showthread.php?t=2220912") and utube i succed in installing Ubuntu on HP chromebook 14 (FALCO), wiping away the chromeOS. 
It worked great till yesterday, when the battery drains out completly and now i am not able to boot from seaBIOS anymore: one i try to give th CTRL + L comand i only get two noisy beaps from the mobo and the only thing i can do is to press (or wait for) CTRL + D and eventually reset chromeOS. The issue is [well-known]("http://jrs-s.net/2014/04/01/restoring-legacy-boot-linux-boot-on-a-chromebook/"), but the solution is to boot in chromeOS, that i can't do as i wiped it away times ago.
As i don't want to lose my data (the reset will wipe away Ubuntu to reinstall chromeOS) i want to now if it is possible to gain accesso to a shell or some where else where i can give this comand, which i think may do the trick - even if i have no idea what it does (if anyone have an hint...?):

```
**sudo crossystem dev_boot_usb=1 dev_boot_legacy=1**
```

As i say i am total noob, but i can't belive that i can't access seaBIOS only because the computer switched off as the battery was over :(

---

### Post by TheFu on 2014-12-21
This might be a dumb question, but can't you just charge the battery and everything will work?

They did recommend pulling the SSD, making a backup (somehow), replacing the SSH, then reloading chromeOS off a flash drive (there are instructions for that all over).  I don't own the required SSD connection do-hicky for the m2 SSD format. Hope I never need to do this myself, but I have daily, automatic, recoverable backups so wouldn't need to pull the SSD.

Once again, there is another use for backups which makes them completely worthwhile.  Backups are only 10% of the problem. Knowing how to restore really is the point - that is the other 90% and requires practice to get good at it.

For example, the backup from last night for my Chromebook: 
```

=== Backing up  c720 === 
StartTime 1419149587.00 (Sun Dec 21 03:13:07 2014)
EndTime 1419149667.09 (Sun Dec 21 03:14:27 2014)
ElapsedTime 80.09 (1 minute 20.09 seconds)
TotalDestinationSizeChange 44933798 (42.9 MB)

```
Less than 2 minutes, not a big deal, until it is needed and not available.

---

### Post by andrea48 on 2014-12-21
> **TheFu said:**
> This might be a dumb question, but can't you just charge the battery and everything will work?


This is a good point: the battery drained out before and i just plug the charger and everything worked. This time i close the lid an THEN plug the A/C: maybe there is a connection between closing the lid while the PC is frozen and the error i get?

I mean this time even if i fully charge the battery nothing happen :( 

Pulling the SSD is not an option for me: i don't have the grounded anti-static wrist strap, as i am unable (as i do on normal PCs) to unplug the battery before opening the case i am too afraid to get burned :):)

For the backup: the one you posted is a script for automate the backup? Is it going on the cloud or on xternal HD?

---

### Post by TheFu on 2014-12-21
I don't own an anti-static strap and haven't had any issues ever in 20+ system builds. Can't imagine being anywhere near any hot leads pulling the m2.ssd, but I don't really remember the internals of my chromebook. There's a youtube that could refresh my memory. ;)

Backups
That isn't a script - it is just the report of the successful backup and only for last night.  I keep 60 days of versioned backups for this machine, but only have some since Nov 13 for a specific reason. I'll post a longer report below.

The easiest explanation for my backup tool of choice, rdiff-backup, is [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)  You can setup local, LAN or WAN backups - it is completely up to you, where you have ssh access and storage to hold the backups.  Use crontabs to automate it.

```
# rdiff-backup --list-increment-sizes c720/
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Dec 21 03:13:07 2014         20.9 GB           20.9 GB   (current mirror)
Sat Dec 20 03:13:08 2014         5.47 MB           20.9 GB
Fri Dec 19 03:13:07 2014         5.16 MB           21.0 GB
Thu Dec 18 03:13:07 2014         5.58 MB           21.0 GB
Wed Dec 17 03:13:07 2014         5.37 MB           21.0 GB
Tue Dec 16 03:13:07 2014         4.29 MB           21.0 GB
Mon Dec 15 03:13:06 2014         4.06 MB           21.0 GB
Sat Dec 13 03:13:06 2014         62.7 MB           21.0 GB
Thu Dec 11 03:13:07 2014          141 MB           21.2 GB
Wed Dec 10 03:13:07 2014         89.5 MB           21.3 GB
Tue Dec  9 03:13:08 2014         4.87 MB           21.3 GB
Mon Dec  8 03:13:07 2014         3.92 MB           21.3 GB
Sun Dec  7 03:13:07 2014         12.6 MB           21.3 GB
Sat Dec  6 03:13:07 2014          337 MB           21.6 GB
Fri Dec  5 03:13:07 2014          330 MB           21.9 GB
.
.
.
Thu Oct 23 03:47:07 2014         69.4 MB           28.0 GB

```
Of course, since this is a netbook, I travel with it and after visiting certain countries feel the need to wipe the disk completely and restore everything from before the trip. That happened in early November. As you can see, the backup storage needed is a little more than a mirror would need - 10%-20% depending on the number of versions retained and if an OS reload happened.  There are a few other dates missing backups - I wasn't at home, so the backups didn't happen. Considering that the system has 128G of storage and that I don't backup any of the media on the system, 28G for all those backups is really a no-brainer, IMHO.

I backup to another machine and to a specific backup disk on the network. That disk is just for backups and holds backups for about 35 other machines - most are virtual machines and don't have too much storage - 4-8G.

---

### Post by andrea48 on 2014-12-21
Oki i will keep the SSD recover as last chance... And thanks for the backups hints, i ll study a little bit on the rdiff.

Anyway, it seems [to be]("http://www.reddit.com/r/chrubuntu/comments/21u7qf/legacy_boot_randomly_stopped_working/") a "boot flag" problem, any idea on how i can set them in a way they load the seaBIOS/legacyboot?
I mean maybe i can make the chromebook think i want to recover chromeOS and instead stop the process and reset the boot flags? Is this possible?

---

### Post by andrea48 on 2014-12-22
If i pull out the SSD is it possibile to reset the boot flag connecting it to another computer?

---

### Post by TheFu on 2014-12-22
> **andrea48 said:**
> If i pull out the SSD is it possibile to reset the boot flag connecting it to another computer?

Sure, but the hard part is the C720 SSD doesn't have a normal SATA interface. An adapter will be necessary to connect the m2.ssd to any other system.  Why would you need to reset the boot flag at all? I wouldn't touch it.  Any parition tool like gparted, parted or fdisk can toggle it.

---

### Post by andrea48 on 2014-12-22
> **TheFu said:**
>  Why would you need to reset the boot flag at all? I wouldn't touch it.  Any parition tool like gparted, parted or fdisk can toggle it.

Because from the reddit link i post, it seems that the whole problem is about the boot flag: somehow the baterry drain reset the partition flag and now i can't boot in seaBIOS. As a computer noob i thought that if i can set again the partition flag to boot from seaBIOS i may be able to use again my linux partition, without wipe anything away... 
(if i get the thing right, this is what this comand does:
 
```
**sudo crossystem dev_boot_usb=1 dev_boot_legacy=1**
```

as i am unable to enter a terminal, i may do it with gparted, after i have pulled out he whole SSD)...?

---

### Post by TheFu on 2014-12-22
Ah - that isn't the boot flag on the SSD - that is the boot flag for the BIOS.  I believe only ChromeOS can toggle it - but I could be wrong.
That command tells the machine to boot from USB and use BIOS (legacy, not EFI) to boot.

So .... I googled a tad.  Seems that you can boot any ubuntu on the chromebook (if you can), then run in live-CD mode, install crossystem [http://manpages.ubuntu.com/manpages/trusty/man1/crossystem.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/crossystem.1.html) and control the BIOS. The hard part will be getting any non-ChromeOS OS to boot, methinks.  I think the answer will be to create a chromeos factory reset boot flash drive and use that, which will wipe all data off the ssd.

---

### Post by andrea48 on 2014-12-22
> **TheFu said:**
> Ah - that isn't the boot flag on the SSD - that is the boot flag for the BIOS.  I believe only ChromeOS can toggle it - but I could be wrong.
That command tells the machine to boot from USB and use BIOS (legacy, not EFI) to boot.

So .... I googled a tad.  Seems that you can boot any ubuntu on the chromebook _**(if you can)**_,
Ah thanks it s all about the BIOS :(
Anyway thats the point, i am afraid i can't boot anything else than the chromeOS image recovery :( :(... But maybe there is omething i don't get and there is a way to make te chormebook belive i am using the image recovery and instead load a linux live...?
I mean, right now if i plug a live Ubuntu usb the system give me an error because the only thing it recognize is the chromeOS recovery flash drive (which i have but don't want to use cuz it will wipe everything).

---

### Post by andrea48 on 2015-01-19
UPDATE: there is actually a way to [boot seabios by dafault]("https://wiki.archlinux.org/index.php/Chromebook#Disabling_the_Hardware_Write_Protection"), in order to avoid the boot flags to reset. I am trying this on the chromebook14 and post something here... If anyone have already tryed please share :)

cheers

---

### Post by nadarockyraccoon on 2015-02-11
Unfortunately this method requires chromeos or another os booted on the comp capable of editing the gbb flags, honestly when this happened to me i just bit the bullet, kicked my self for not backing up that django project the night before and re-installed chrome. After that I did follow those instruction you posted and seabios boots automatically after a delay on the scary screen. Since then I have let my battery drain many a times without issues. _Do not attempt setting the GBB flags without removing the write protection, it will break seabios!_ [http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c720-chromebook]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c720-chromebook") shows you how to fix it though, also requires chrome.

---

### Post by TheFu on 2015-02-11
> **nadarockyraccoon said:**
> Unfortunately this method requires chromeos or another os booted on the comp capable of editing the gbb flags, honestly when this happened to me i just bit the bullet, kicked my self for not backing up that django project the night before and re-installed chrome. After that I did follow those instruction you posted and seabios boots automatically after a delay on the scary screen. Since then I have let my battery drain many a times without issues. _Do not attempt setting the GBB flags without removing the write protection, it will break seabios!_ [http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c720-chromebook]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c720-chromebook") shows you how to fix it though, also requires chrome.


Please clarify - when you say "chrome" - do you mean "chromeos" or the chrome web browser?

---

### Post by nadarockyraccoon on 2015-02-17
chromeos in both instances. It sounds like seabios is broken, and unfortunately the only way to fix it is flashing the bios. The instructins [here]("http://www.chromium.org/chromium-os/developer-information-for-chrome-os-devices/acer-c720-chromebook#TOC-Legacy-Boot-Doesn-t-Work") (just a section from the page posted above) can fix it, but you have to be booted into linux. Since it isn't possible to boot anything but chromeos without seabios, the only solution is to recover chromeos. If the data on the drive is that important you could purchase a [m.2 to usb converter]("http://www.aliexpress.com/item/USB-3-0-USB3-0-Female-to-NGFF-M-2-B-M-Key-Male-Adapter-Converter/32216780049.html?af=ppc&isdl=y&src=Google&albch=Google&aff_short_key=UneMJZVf&cv=1020800000009001&ptsid=1020000000013003&crea=51413220145&plac=&netw=g&device=c&aff_short_key=UneMJZVf&cv=1020000000013003&gclid=Cj0KEQiA6ounBRCq0LKBjKGgysEBEiQAZmpvAw4G89LYoKr56mTT6XFPGYABHWFuRI0xMEzBtbaWM-waAnYR8P8HAQ"), pull the drive and get everything off of it on another computer. This, like removing the write-protect screw, would void the warranty though.

Also The link posted does pertain to the hp chromebook  14 falco, even though it is labeled for the acer c720. This is where google sends you when researching developer mode for the falco because the information is the same for both.

---

