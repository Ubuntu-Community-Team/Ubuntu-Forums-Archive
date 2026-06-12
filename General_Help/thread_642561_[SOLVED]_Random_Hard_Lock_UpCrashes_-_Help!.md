---
title: "[SOLVED] Random Hard Lock Up/Crashes - Help!"
date: 2007-12-16
forum: General Help
---

### Post by WestCoastSuccess on 2007-12-16
I've been successfully using Ubuntu for about 9 months now - love it - but suddenly, Dec 6th, it started locking up on a random basis. The mouse freezes, the screen freezes and nothing works except hitting the reset button and rebooting (Ctrl+Alt+Backspace or Ctrl+Alt+F1 or Ctrl+Alt+Del do nothing).

I've checked every log I can find and none of them show anything what I"d consider relevant in the time around any of the crashes. I'd be happy to post any/all of them.

My system is an AMD X2 4600 with 4 GB OCZ DDR2 5-5-5-12 RAM, 3 X 320GB Seagate SATA 2 drives, 2 of which are in a RAID 0 array. Ubuntu runs from the other one.NVidia 7600 GS graphics card, firewire connection to a Motorola 6300 HD cable box (for MythTV). The board is an ASUS M2N32 Deluxe Wireless. 

I ran memtest86+ last night for about 7 hours and it passed all 10 tests 5 times with no errors. 

I booted via Ubuntu CD and used fsck to check the hard drives, with no errors reported.

I've closely monitored the temperature and it consistent at 40C for mobo and around 45C for CPUs. Graphics card steady around 60C.

I'm running Gutsy, fully updated, with Compiz and real time kernel. I also run MythTV and the computer gets used for recording purposes also via Ardour.

Really the only strange thing I see in dmesg is:

ieee80211_init: failed to initialize WME (err=-17)
[   49.023620] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   49.023655] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   49.023685] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   49.023731] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register


Unable to find anything useful regarding these error messages, and unclear if they're related. Note that while the mobo has built in wireless, I do not use it - I have a wired connection via a cable modem and I disable the wlan manually (and always have).

Until Dec 6th the system was rock solid - now, hard lock up after about every 2 hours (or less) of use. 

Can anyone point me in the right direction or suggest other tests I might run?

Many thanks!

---

### Post by WestCoastSuccess on 2007-12-21
UPDATE: after trying about everything I could think of (and hoping in vain for a response to my post...) it turned out to be a problem with the latest BIOS for my motherboard.

Specifically, for others who might encounter the same problem, BIOS v. 1503 for the Asus M2N-32 Deluxe appears pretty buggy. I downgraded to 1203 and everything seems fine now - no crashes/freezes/hard lock ups for a couple of days.

To change the BIOS with this board, I downloaded the version I wanted from the Asus website:

[http://support.asus.com/download/download.aspx?SLanguage=en-us](http://support.asus.com/download/download.aspx?SLanguage=en-us)

then copied it to a USB thumb drive (it's prudent to make sure nothing else is on the thumb drive first), leaving the thumb drive in the USB port.

I then rebooted the computer and hit the Delete key during boot up to enter the BIOS menu. Used the right arrow key to move to the Tools screen and selected Flash BIOS. Selected the drive letter that corresponded to the thumb drive and the BIOS version (1203) I downloaded appeared. Selected it and it installed and ran a check on itself.

Reboot and I was good to go.

---

### Post by DREMA on 2008-02-10
Heey, thanks I have the same problem and was looking for a solution, now I need to know what is wrong 'cause I don't want to downgrade my BIOS.
Maybe its a problem on the new kernel? How can I look the source of the problem? The logs didn't work as stated before.

---

### Post by WestCoastSuccess on 2008-03-02
Sorry for the delay responding.

Asus has since released new BIOS versions: 1603 and 1703 for this motherboard. I have tried neither - 1203 works great for me - so I don't know if they're as buggy as 1503 was.

Don't look at a BIOS in the same way as you would software releases: you don't need (and really wouldn't want to) keep up to date with every latest version. Usually the updates are to add compatibility with new CPUs.

Anyway, if you want a sure thing, go with 1203. If you experiment with 1603 or 1703, let us know how you fare!

Cheers!

---

