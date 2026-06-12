---
title: "Opinion more than tech support..."
date: 2014-11-11
forum: General Help
---

### Post by frankennetbook on 2014-11-11
So this may be a somewhat long story so hopefully I can keep people to the end of it.
I am currently running Ubuntu 14.04 on an Acer One Aspire netbook which I have made changes to, it currently has a 1tb hard drive and more importantly i upgraded ram from 1gig to 1.5 the processor and motherboard are original 1.6gig.  And BIOS firmware.  Initially when I upgraded to 14.04 I had few "system encountered a problem messages"; I sent the bug reports and eventually they stopped.  I assumed that the bug reports led to bug fixes life goes on.  A couple weeks ago I got the black screen of death, and couldnt boot to grub and only had 12.04 live cd.  For some reason I didn't think to download 14.04 from another pc but regardless I tried to downgrade back to 12.04 which worked after a little bit of struggle. But nothing seemed to work properly, so I then had the insight to download 14.04 and boot via cd.  All worked and were up and running again.  But things just dont seem to want to run everything is pretty slow and lots of crashes and bugs.  ( I can go into detail if need be)

My question is: does this sound like strictly a software issue or could ageing and well used hardware be to blame?  

I had planned to upgrade to a new computer but I'm not sure where to go, ultrabook or regular laptop etc... 

Anyway.  Thanks for reading, and any insight would be greatly appreciated. 

Thanks

---

### Post by sudodus on 2014-11-11
It could be both hardware and software problems.

- Check the RAM with memtest
- Check the S.M.A.R.T. status of the HDD

Does the computer run well (without issues) when booted from a USB or CD/DVD drive? Try long enough to be able to compare to the performance from the installed system.

-o-

The problem might also be that the hardware does not cope with standard Ubuntu. You can try another (and lighter) flavour of Ubuntu: I think ***Lubuntu*** or ***Xubuntu*** work much better in a netbook than standard Ubuntu. Or try some other distro for example ***LXLE***, ***Knoppix*** or ***Puppy***.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by SagaciousKJB on 2014-11-11
What do you mean by the black screen of death?  Did your window manager drop to a shell prompt or did you get a kernel panic?

The first thing I would do after boot is run "dmesg" to see if there's any errors in there.  Most software that will encounter a problem will report it here.

---

### Post by tgalati4 on 2014-11-11
It's possible that the improvements have put a strain on the power circuitry and you are getting power dropouts and random behavior without clear error logs.

---

### Post by Habitual on 2014-11-11
Power Supply or flaky RAM.
IMO it's usually the physical components that need to be checked first.
Perhaps a fan on the Power Supply has some "dust bunnies" living there?

Open the case, inspect and clean appropriately. Examine fans.
Re-seat the components.
Swap the RAM from slot0 > slot1 and slot1 > slot0

check the logs!

Sorry, can a netbook be "opened"?

---

### Post by stalkingwolf on 2014-11-11
i have used lubuntu, xubuntu , zorin and mint13 mate on several net books. currently 2 hp minis and 2 asus 1005's. with no problems. Also an older acer aspire.  all work fine.  It is possible that yours just doesnt have the capability to run 14.04.  as suggested try a lighter distro.

---

### Post by frankennetbook on 2014-11-11
So I ran memory test and I will paste the picture of the screen I took.  Nothing in there jumps out at me as being an issue but I really wouldn't know for sure what I'm looking for on there.  I was unable to install Disk Utility receiving the following errors from terminal (which is the same error I get when I try to install anything, including when I tried to reinstall Software Centre when it wouldnt open).  


frankennetbook@frankennetbook-AOA150:~$ sudo apt-get install gnome-disk-utility
[sudo] password for frankennetbook: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-disk-utility is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up linux-image-3.13.0-39-generic (3.13.0-39.66) ...
Running depmod.
Failed to run depmod
dpkg: error processing package linux-image-3.13.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-39-generic:
 linux-image-extra-3.13.0-39-generic depends on linux-image-3.13.0-39-generic; however:
  Package linux-image-3.13.0-39-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.13.0-39-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.13.0-39-generic; however:
  Package linux-image-3.13.0-39-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-3.13.0-39-generic; however:
  Package linux-image-extra-3.13.0-39-generic is not configured yet.


dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.13.0.39.46); however:
  Package linux-image-generic is not configured yet.


dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-3.13.0-39-generic
 linux-image-extra-3.13.0-39-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

[ATTACH=CONFIG]257898[/ATTACH]


I had a feeling that the netbook may be coming to the end of its life expectancy, but wanted to get an opinion from someone who would know better and wasn't trying to sell me anything.  Also I've been looking at maybe getting an ultrabook or a laptop to replace this one, but am unsure of the steps for installing through uefi.  

In response to Habitual you can open the netbook I've done it replacing the screen harddrive and ram but if i remember correctly this model only accepts one ram card. 

Stalingwolf, I agree 14.04 might be too much for this.  Although I am running it on an old computer for my parents which has a single core processor (albeit 3+ghz and 4 gig ram)

And I will run dmesg

Thanks everyone

---

### Post by frankennetbook on 2014-11-11
dmesg result:
```

[   19.187703] ath: Regpair used: 0x65
[   19.273201] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   19.275671] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   21.931909] type=1400 audit(1415729956.087:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=767 comm="apparmor_parser"
[   21.931947] type=1400 audit(1415729956.087:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=767 comm="apparmor_parser"
[   21.931973] type=1400 audit(1415729956.087:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=767 comm="apparmor_parser"
[   21.950122] type=1400 audit(1415729956.107:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=767 comm="apparmor_parser"
[   21.950156] type=1400 audit(1415729956.107:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=767 comm="apparmor_parser"
[   21.951220] type=1400 audit(1415729956.107:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=767 comm="apparmor_parser"
[   21.958461] type=1400 audit(1415729956.115:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=766 comm="apparmor_parser"
[   21.958492] type=1400 audit(1415729956.115:18): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=766 comm="apparmor_parser"
[   21.965876] type=1400 audit(1415729956.123:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium" pid=766 comm="apparmor_parser"
[   22.154946] type=1400 audit(1415729956.311:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=775 comm="apparmor_parser"
[   22.873303] r8169 0000:02:00.0 eth0: link down
[   22.873454] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.874876] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.908858] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.910164] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.093381] wlan0: authenticate with 3c:ea:4f:9d:e0:61
[   24.099513] wlan0: send auth to 3c:ea:4f:9d:e0:61 (try 1/3)
[   24.101409] wlan0: authenticated
[   24.102239] ath5k 0000:03:00.0 wlan0: disabling HT/VHT due to WEP/TKIP use
[   24.102256] ath5k 0000:03:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   24.102265] ath5k 0000:03:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   24.105182] wlan0: associate with 3c:ea:4f:9d:e0:61 (try 1/3)
[   24.108095] wlan0: RX AssocResp from 3c:ea:4f:9d:e0:61 (capab=0x431 status=0 aid=2)
[   24.108901] wlan0: associated
[   24.109744] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   24.110079] cfg80211: Calling CRDA for country: CA
[   24.153944] ath: EEPROM regdomain: 0x807c
[   24.153954] ath: EEPROM indicates we should expect a country code
[   24.153960] ath: doing EEPROM country->regdmn map search
[   24.153966] ath: country maps to regdmn code: 0x3a
[   24.153973] ath: Country alpha2 being used: CA
[   24.153978] ath: Regpair used: 0x3a
[   24.153984] ath: regdomain 0x807c dynamically updated by country IE
[   24.153990] cfg80211: Regulatory domain changed to country: CA
[   24.153996] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.154004] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   24.154012] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   24.154019] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.154026] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.154034] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   27.176506] init: plymouth-upstart-bridge main process ended, respawning
[   27.244277] init: plymouth-upstart-bridge main process (1148) terminated with status 1
[   27.244346] init: plymouth-upstart-bridge main process ended, respawning
[   46.545277] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   46.545296] ata1.00: BMDMA stat 0x5
[   46.545313] ata1.00: failed command: READ DMA
[   46.545342] ata1.00: cmd c8/00:98:18:55:22/00:00:00:00:00/e0 tag 5 dma 77824 in
[   46.545342]          res 51/40:07:a8:55:22/00:00:00:00:00/e0 Emask 0x9 (media error)
[   46.545357] ata1.00: status: { DRDY ERR }
[   46.545367] ata1.00: error: { UNC }
[   46.561034] ata1.00: configured for UDMA/133
[   46.561090] sd 0:0:0:0: [sda] Unhandled sense code
[   46.561104] sd 0:0:0:0: [sda]  
[   46.561113] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   46.561124] sd 0:0:0:0: [sda]  
[   46.561132] Sense Key : Medium Error [current] [descriptor]
[   46.561146] Descriptor sense data with sense descriptors (in hex):
[   46.561153]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   46.561196]         00 22 55 a8 
[   46.561217] sd 0:0:0:0: [sda]  
[   46.561230] Add. Sense: Unrecovered read error - auto reallocate failed
[   46.561241] sd 0:0:0:0: [sda] CDB: 
[   46.561260] Read(10): 28 00 00 22 55 18 00 00 98 00
[   46.561279] end_request: I/O error, dev sda, sector 2250152
[   46.561372] ata1: EH complete
[   47.493371] audit_printk_skb: 123 callbacks suppressed
[   47.493385] type=1400 audit(1415729981.648:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1971 comm="apparmor_parser"
[   47.493417] type=1400 audit(1415729981.648:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1971 comm="apparmor_parser"
[   47.495272] type=1400 audit(1415729981.648:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1971 comm="apparmor_parser"
[   49.653757] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   49.653777] ata1.00: BMDMA stat 0x5
[   49.653794] ata1.00: failed command: READ DMA
[   49.653823] ata1.00: cmd c8/00:08:a8:55:22/00:00:00:00:00/e0 tag 18 dma 4096 in
[   49.653823]          res 51/40:08:a8:55:22/00:00:00:00:00/e0 Emask 0x9 (media error)
[   49.653838] ata1.00: status: { DRDY ERR }
[   49.653849] ata1.00: error: { UNC }
[   49.668590] ata1.00: configured for UDMA/133
[   49.668645] sd 0:0:0:0: [sda] Unhandled sense code
[   49.668658] sd 0:0:0:0: [sda]  
[   49.668668] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   49.668679] sd 0:0:0:0: [sda]  
[   49.668687] Sense Key : Medium Error [current] [descriptor]
[   49.668701] Descriptor sense data with sense descriptors (in hex):
[   49.668708]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   49.668751]         00 22 55 a8 
[   49.668771] sd 0:0:0:0: [sda]  
[   49.668784] Add. Sense: Unrecovered read error - auto reallocate failed
[   49.668796] sd 0:0:0:0: [sda] CDB: 
[   49.668803] Read(10): 28 00 00 22 55 a8 00 00 08 00
[   49.668840] end_request: I/O error, dev sda, sector 2250152
[   49.668978] ata1: EH complete
[   52.431076] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   52.431096] ata1.00: BMDMA stat 0x5
[   52.431114] ata1.00: failed command: READ DMA
[   52.431143] ata1.00: cmd c8/00:08:a8:55:22/00:00:00:00:00/e0 tag 25 dma 4096 in
[   52.431143]          res 51/40:08:a8:55:22/00:00:00:00:00/e0 Emask 0x9 (media error)
[   52.431158] ata1.00: status: { DRDY ERR }
[   52.431168] ata1.00: error: { UNC }
[   52.452693] ata1.00: configured for UDMA/133
[   52.452748] sd 0:0:0:0: [sda] Unhandled sense code
[   52.452761] sd 0:0:0:0: [sda]  
[   52.452770] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   52.452781] sd 0:0:0:0: [sda]  
[   52.452789] Sense Key : Medium Error [current] [descriptor]
[   52.452803] Descriptor sense data with sense descriptors (in hex):
[   52.452811]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   52.452853]         00 22 55 a8 
[   52.452874] sd 0:0:0:0: [sda]  
[   52.452887] Add. Sense: Unrecovered read error - auto reallocate failed
[   52.452899] sd 0:0:0:0: [sda] CDB: 
[   52.452906] Read(10): 28 00 00 22 55 a8 00 00 08 00
[   52.452942] end_request: I/O error, dev sda, sector 2250152
[   52.453072] ata1: EH complete
[   55.164370] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   55.164390] ata1.00: BMDMA stat 0x5
[   55.164408] ata1.00: failed command: READ DMA
[   55.164438] ata1.00: cmd c8/00:08:a8:55:22/00:00:00:00:00/e0 tag 28 dma 4096 in
[   55.164438]          res 51/40:08:a8:55:22/00:00:00:00:00/e0 Emask 0x9 (media error)
[   55.164453] ata1.00: status: { DRDY ERR }
[   55.164463] ata1.00: error: { UNC }
[   55.181115] ata1.00: configured for UDMA/133
[   55.181167] sd 0:0:0:0: [sda] Unhandled sense code
[   55.181181] sd 0:0:0:0: [sda]  
[   55.181190] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   55.181201] sd 0:0:0:0: [sda]  
[   55.181209] Sense Key : Medium Error [current] [descriptor]
[   55.181223] Descriptor sense data with sense descriptors (in hex):
[   55.181231]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   55.181273]         00 22 55 a8 
[   55.181294] sd 0:0:0:0: [sda]  
[   55.181307] Add. Sense: Unrecovered read error - auto reallocate failed
[   55.181318] sd 0:0:0:0: [sda] CDB: 
[   55.181326] Read(10): 28 00 00 22 55 a8 00 00 08 00
[   55.181361] end_request: I/O error, dev sda, sector 2250152
[   55.181453] ata1: EH complete
[   58.007720] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   58.007740] ata1.00: BMDMA stat 0x5
[   58.007758] ata1.00: failed command: READ DMA
[   58.007787] ata1.00: cmd c8/00:08:a8:55:22/00:00:00:00:00/e0 tag 5 dma 4096 in
[   58.007787]          res 51/40:08:a8:55:22/00:00:00:00:00/e0 Emask 0x9 (media error)
[   58.007802] ata1.00: status: { DRDY ERR }
[   58.007812] ata1.00: error: { UNC }
[   58.021473] ata1.00: configured for UDMA/133
[   58.021526] sd 0:0:0:0: [sda] Unhandled sense code
[   58.021539] sd 0:0:0:0: [sda]  
[   58.021549] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   58.021560] sd 0:0:0:0: [sda]  
[   58.021568] Sense Key : Medium Error [current] [descriptor]
[   58.021583] Descriptor sense data with sense descriptors (in hex):
[   58.021590]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   58.021632]         00 22 55 a8 
[   58.021653] sd 0:0:0:0: [sda]  
[   58.021666] Add. Sense: Unrecovered read error - auto reallocate failed
[   58.021678] sd 0:0:0:0: [sda] CDB: 
[   58.021685] Read(10): 28 00 00 22 55 a8 00 00 08 00
[   58.021720] end_request: I/O error, dev sda, sector 2250152
[   58.021802] ata1: EH complete
[   77.898318] perf samples too long (2555 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[   81.274793] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   81.274812] ata1.00: BMDMA stat 0x5
[   81.274828] ata1.00: failed command: READ DMA
[   81.274857] ata1.00: cmd c8/00:00:a8:ca:0e/00:00:00:00:00/e0 tag 1 dma 131072 in
[   81.274857]          res 51/40:3f:68:cb:0e/00:00:00:00:00/e0 Emask 0x9 (media error)
[   81.274872] ata1.00: status: { DRDY ERR }
[   81.274883] ata1.00: error: { UNC }
[   81.289593] ata1.00: configured for UDMA/133
[   81.289647] sd 0:0:0:0: [sda] Unhandled sense code
[   81.289661] sd 0:0:0:0: [sda]  
[   81.289670] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   81.289681] sd 0:0:0:0: [sda]  
[   81.289689] Sense Key : Medium Error [current] [descriptor]
[   81.289703] Descriptor sense data with sense descriptors (in hex):
[   81.289711]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   81.289753]         00 0e cb 68 
[   81.289774] sd 0:0:0:0: [sda]  
[   81.289786] Add. Sense: Unrecovered read error - auto reallocate failed
[   81.289809] sd 0:0:0:0: [sda] CDB: 
[   81.289814] Read(10): 28 00 00 0e ca a8 00 01 00 00
[   81.289833] end_request: I/O error, dev sda, sector 969576
[   81.289881] ata1: EH complete
[   84.505336] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   84.505356] ata1.00: BMDMA stat 0x5
[   84.505373] ata1.00: failed command: READ DMA
[   84.505402] ata1.00: cmd c8/00:08:68:cb:0e/00:00:00:00:00/e0 tag 11 dma 4096 in
[   84.505402]          res 51/40:08:68:cb:0e/00:00:00:00:00/e0 Emask 0x9 (media error)
[   84.505417] ata1.00: status: { DRDY ERR }
[   84.505427] ata1.00: error: { UNC }
[   84.521115] ata1.00: configured for UDMA/133
[   84.521168] sd 0:0:0:0: [sda] Unhandled sense code
[   84.521182] sd 0:0:0:0: [sda]  
[   84.521191] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   84.521202] sd 0:0:0:0: [sda]  
[   84.521210] Sense Key : Medium Error [current] [descriptor]
[   84.521224] Descriptor sense data with sense descriptors (in hex):
[   84.521232]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   84.521274]         00 0e cb 68 
[   84.521295] sd 0:0:0:0: [sda]  
[   84.521308] Add. Sense: Unrecovered read error - auto reallocate failed
[   84.521320] sd 0:0:0:0: [sda] CDB: 
[   84.521328] Read(10): 28 00 00 0e cb 68 00 00 08 00
[   84.521372] end_request: I/O error, dev sda, sector 969576
[   84.521414] ata1: EH complete
[   89.285577] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[   89.285597] ata1.00: BMDMA stat 0x5
[   89.285615] ata1.00: failed command: READ DMA
[   89.285644] ata1.00: cmd c8/00:08:68:cb:0e/00:00:00:00:00/e0 tag 28 dma 4096 in
[   89.285644]          res 51/40:08:68:cb:0e/00:00:00:00:00/e0 Emask 0x9 (media error)
[   89.285659] ata1.00: status: { DRDY ERR }
[   89.285669] ata1.00: error: { UNC }
[   89.301396] ata1.00: configured for UDMA/133
[   89.301451] sd 0:0:0:0: [sda] Unhandled sense code
[   89.301464] sd 0:0:0:0: [sda]  
[   89.301474] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[   89.301485] sd 0:0:0:0: [sda]  
[   89.301493] Sense Key : Medium Error [current] [descriptor]
[   89.301507] Descriptor sense data with sense descriptors (in hex):
[   89.301514]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   89.301558]         00 0e cb 68 
[   89.301579] sd 0:0:0:0: [sda]  
[   89.301591] Add. Sense: Unrecovered read error - auto reallocate failed
[   89.301603] sd 0:0:0:0: [sda] CDB: 
[   89.301611] Read(10): 28 00 00 0e cb 68 00 00 08 00
[   89.301652] end_request: I/O error, dev sda, sector 969576
[   89.301694] ata1: EH complete
[  113.671167] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  113.671188] ata1.00: BMDMA stat 0x5
[  113.671207] ata1.00: failed command: READ DMA
[  113.671236] ata1.00: cmd c8/00:08:20:08:10/00:00:00:00:00/e0 tag 29 dma 4096 in
[  113.671236]          res 51/40:08:20:08:10/00:00:00:00:00/e0 Emask 0x9 (media error)
[  113.671251] ata1.00: status: { DRDY ERR }
[  113.671261] ata1.00: error: { UNC }
[  113.684953] ata1.00: configured for UDMA/133
[  113.685008] sd 0:0:0:0: [sda] Unhandled sense code
[  113.685022] sd 0:0:0:0: [sda]  
[  113.685031] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  113.685042] sd 0:0:0:0: [sda]  
[  113.685050] Sense Key : Medium Error [current] [descriptor]
[  113.685065] Descriptor sense data with sense descriptors (in hex):
[  113.685072]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  113.685115]         00 10 08 20 
[  113.685135] sd 0:0:0:0: [sda]  
[  113.685148] Add. Sense: Unrecovered read error - auto reallocate failed
[  113.685160] sd 0:0:0:0: [sda] CDB: 
[  113.685167] Read(10): 28 00 00 10 08 20 00 00 08 00
[  113.685208] end_request: I/O error, dev sda, sector 1050656
[  113.685250] ata1: EH complete
[  116.359440] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  116.359459] ata1.00: BMDMA stat 0x5
[  116.359478] ata1.00: failed command: READ DMA
[  116.359507] ata1.00: cmd c8/00:08:20:08:10/00:00:00:00:00/e0 tag 30 dma 4096 in
[  116.359507]          res 51/40:08:20:08:10/00:00:00:00:00/e0 Emask 0x9 (media error)
[  116.359522] ata1.00: status: { DRDY ERR }
[  116.359533] ata1.00: error: { UNC }
[  116.373220] ata1.00: configured for UDMA/133
[  116.373273] sd 0:0:0:0: [sda] Unhandled sense code
[  116.373286] sd 0:0:0:0: [sda]  
[  116.373296] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  116.373307] sd 0:0:0:0: [sda]  
[  116.373315] Sense Key : Medium Error [current] [descriptor]
[  116.373329] Descriptor sense data with sense descriptors (in hex):
[  116.373337]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  116.373379]         00 10 08 20 
[  116.373400] sd 0:0:0:0: [sda]  
[  116.373413] Add. Sense: Unrecovered read error - auto reallocate failed
[  116.373424] sd 0:0:0:0: [sda] CDB: 
[  116.373432] Read(10): 28 00 00 10 08 20 00 00 08 00
[  116.373477] end_request: I/O error, dev sda, sector 1050656
[  116.373520] ata1: EH complete
[  232.820114] perf samples too long (5025 > 5000), lowering kernel.perf_event_max_sample_rate to 25000
[  300.404832] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  300.404847] ata1.00: BMDMA stat 0x5
[  300.404860] ata1.00: failed command: READ DMA
[  300.404882] ata1.00: cmd c8/00:00:30:8d:3a/00:00:00:00:00/e0 tag 0 dma 131072 in
[  300.404882]          res 51/40:df:50:8d:3a/00:00:00:00:00/e0 Emask 0x9 (media error)
[  300.404894] ata1.00: status: { DRDY ERR }
[  300.404902] ata1.00: error: { UNC }
[  300.420848] ata1.00: configured for UDMA/133
[  300.420902] sd 0:0:0:0: [sda] Unhandled sense code
[  300.420914] sd 0:0:0:0: [sda]  
[  300.420922] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  300.420932] sd 0:0:0:0: [sda]  
[  300.420939] Sense Key : Medium Error [current] [descriptor]
[  300.420950] Descriptor sense data with sense descriptors (in hex):
[  300.420956]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  300.420987]         00 3a 8d 50 
[  300.421004] sd 0:0:0:0: [sda]  
[  300.421014] Add. Sense: Unrecovered read error - auto reallocate failed
[  300.421024] sd 0:0:0:0: [sda] CDB: 
[  300.421031] Read(10): 28 00 00 3a 8d 30 00 01 00 00
[  300.421059] end_request: I/O error, dev sda, sector 3837264
[  300.421130] ata1: EH complete
[  310.616697] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  310.616713] ata1.00: BMDMA stat 0x5
[  310.616727] ata1.00: failed command: READ DMA
[  310.616750] ata1.00: cmd c8/00:00:00:82:3a/00:00:00:00:00/e0 tag 16 dma 131072 in
[  310.616750]          res 51/40:1f:e0:82:3a/00:00:00:00:00/e0 Emask 0x9 (media error)
[  310.616762] ata1.00: status: { DRDY ERR }
[  310.616771] ata1.00: error: { UNC }
[  310.632505] ata1.00: configured for UDMA/133
[  310.632573] sd 0:0:0:0: [sda] Unhandled sense code
[  310.632585] sd 0:0:0:0: [sda]  
[  310.632593] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  310.632602] sd 0:0:0:0: [sda]  
[  310.632609] Sense Key : Medium Error [current] [descriptor]
[  310.632620] Descriptor sense data with sense descriptors (in hex):
[  310.632626]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  310.632657]         00 3a 82 e0 
[  310.632674] sd 0:0:0:0: [sda]  
[  310.632684] Add. Sense: Unrecovered read error - auto reallocate failed
[  310.632695] sd 0:0:0:0: [sda] CDB: 
[  310.632701] Read(10): 28 00 00 3a 82 00 00 01 00 00
[  310.632730] end_request: I/O error, dev sda, sector 3834592
[  310.632796] ata1: EH complete
[  313.471057] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  313.471072] ata1.00: BMDMA stat 0x5
[  313.471086] ata1.00: failed command: READ DMA
[  313.471108] ata1.00: cmd c8/00:08:e0:82:3a/00:00:00:00:00/e0 tag 30 dma 4096 in
[  313.471108]          res 51/40:08:e0:82:3a/00:00:00:00:00/e0 Emask 0x9 (media error)
[  313.471120] ata1.00: status: { DRDY ERR }
[  313.471128] ata1.00: error: { UNC }
[  313.484802] ata1.00: configured for UDMA/133
[  313.484848] sd 0:0:0:0: [sda] Unhandled sense code
[  313.484859] sd 0:0:0:0: [sda]  
[  313.484867] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  313.484875] sd 0:0:0:0: [sda]  
[  313.484882] Sense Key : Medium Error [current] [descriptor]
[  313.484892] Descriptor sense data with sense descriptors (in hex):
[  313.484898]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  313.484928]         00 3a 82 e0 
[  313.484944] sd 0:0:0:0: [sda]  
[  313.484953] Add. Sense: Unrecovered read error - auto reallocate failed
[  313.484963] sd 0:0:0:0: [sda] CDB: 
[  313.484969] Read(10): 28 00 00 3a 82 e0 00 00 08 00
[  313.484995] end_request: I/O error, dev sda, sector 3834592
[  313.485052] ata1: EH complete
[  373.130401] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  373.130416] ata1.00: BMDMA stat 0x5
[  373.130430] ata1.00: failed command: READ DMA
[  373.130452] ata1.00: cmd c8/00:08:e0:82:3a/00:00:00:00:00/e0 tag 21 dma 4096 in
[  373.130452]          res 51/40:08:e0:82:3a/00:00:00:00:00/e0 Emask 0x9 (media error)
[  373.130464] ata1.00: status: { DRDY ERR }
[  373.130472] ata1.00: error: { UNC }
[  373.145154] ata1.00: configured for UDMA/133
[  373.145202] sd 0:0:0:0: [sda] Unhandled sense code
[  373.145213] sd 0:0:0:0: [sda]  
[  373.145220] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  373.145229] sd 0:0:0:0: [sda]  
[  373.145235] Sense Key : Medium Error [current] [descriptor]
[  373.145246] Descriptor sense data with sense descriptors (in hex):
[  373.145251]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  373.145281]         00 3a 82 e0 
[  373.145297] sd 0:0:0:0: [sda]  
[  373.145307] Add. Sense: Unrecovered read error - auto reallocate failed
[  373.145317] sd 0:0:0:0: [sda] CDB: 
[  373.145323] Read(10): 28 00 00 3a 82 e0 00 00 08 00
[  373.145350] end_request: I/O error, dev sda, sector 3834592
[  373.145409] ata1: EH complete
[  402.429072] nacl_helper_boo[6787]: segfault at 4052 ip 000104a0 sp bff6b7c0 error 6 in nacl_helper_bootstrap[10000+2000]
[ 8394.717304] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8394.717317] ata1.00: BMDMA stat 0x5
[ 8394.717325] ata1.00: failed command: READ DMA
[ 8394.717340] ata1.00: cmd c8/00:00:20:08:75/00:00:00:00:00/e0 tag 6 dma 131072 in
[ 8394.717340]          res 51/40:2f:e8:08:75/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 8394.717348] ata1.00: status: { DRDY ERR }
[ 8394.717353] ata1.00: error: { UNC }
[ 8394.733063] ata1.00: configured for UDMA/133
[ 8394.733123] sd 0:0:0:0: [sda] Unhandled sense code
[ 8394.733137] sd 0:0:0:0: [sda]  
[ 8394.733146] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8394.733158] sd 0:0:0:0: [sda]  
[ 8394.733166] Sense Key : Medium Error [current] [descriptor]
[ 8394.733180] Descriptor sense data with sense descriptors (in hex):
[ 8394.733188]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 8394.733230]         00 75 08 e8 
[ 8394.733251] sd 0:0:0:0: [sda]  
[ 8394.733263] Add. Sense: Unrecovered read error - auto reallocate failed
[ 8394.733275] sd 0:0:0:0: [sda] CDB: 
[ 8394.733294] Read(10): 28 00 00 75 08 20 00 01 00 00
[ 8394.733313] end_request: I/O error, dev sda, sector 7669992
[ 8394.733352] ata1: EH complete
[ 8469.393167] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 8469.393190] ata1.00: BMDMA stat 0x5
[ 8469.393218] ata1.00: failed command: READ DMA
[ 8469.393261] ata1.00: cmd c8/00:08:e0:82:3a/00:00:00:00:00/e0 tag 27 dma 4096 in
[ 8469.393261]          res 51/40:08:e0:82:3a/00:00:00:00:00/e0 Emask 0x9 (media error)
[ 8469.393281] ata1.00: status: { DRDY ERR }
[ 8469.393292] ata1.00: error: { UNC }
[ 8469.408872] ata1.00: configured for UDMA/133
[ 8469.408908] sd 0:0:0:0: [sda] Unhandled sense code
[ 8469.408915] sd 0:0:0:0: [sda]  
[ 8469.408920] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 8469.408926] sd 0:0:0:0: [sda]  
[ 8469.408930] Sense Key : Medium Error [current] [descriptor]
[ 8469.408938] Descriptor sense data with sense descriptors (in hex):
[ 8469.408941]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 8469.408963]         00 3a 82 e0 
[ 8469.408973] sd 0:0:0:0: [sda]  
[ 8469.408980] Add. Sense: Unrecovered read error - auto reallocate failed
[ 8469.408986] sd 0:0:0:0: [sda] CDB: 
[ 8469.408990] Read(10): 28 00 00 3a 82 e0 00 00 08 00
[ 8469.409008] end_request: I/O error, dev sda, sector 3834592
[ 8469.409049] ata1: EH complete
[ 8739.944091] ath5k: ath5k_hw_get_isr: ISR: 0x00040001 IMR: 0x00000000
[ 9596.112106] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 9596.112119] ata1.00: BMDMA stat 0x5
[ 9596.112133] ata1.00: failed command: READ DMA EXT
[ 9596.112152] ata1.00: cmd 25/00:00:00:4c:36/00:04:00:00:00/e0 tag 23 dma 524288 in
[ 9596.112152]          res 51/40:6f:88:4f:36/40:00:00:00:00/e0 Emask 0x9 (media error)
[ 9596.112163] ata1.00: status: { DRDY ERR }
[ 9596.112170] ata1.00: error: { UNC }
[ 9596.128906] ata1.00: configured for UDMA/133
[ 9596.128975] sd 0:0:0:0: [sda] Unhandled sense code
[ 9596.128986] sd 0:0:0:0: [sda]  
[ 9596.128994] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 9596.129003] sd 0:0:0:0: [sda]  
[ 9596.129010] Sense Key : Medium Error [current] [descriptor]
[ 9596.129021] Descriptor sense data with sense descriptors (in hex):
[ 9596.129027]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 9596.129058]         00 36 4f 88 
[ 9596.129074] sd 0:0:0:0: [sda]  
[ 9596.129085] Add. Sense: Unrecovered read error - auto reallocate failed
[ 9596.129095] sd 0:0:0:0: [sda] CDB: 
[ 9596.129102] Read(10): 28 00 00 36 4c 00 00 04 00 00
[ 9596.129130] end_request: I/O error, dev sda, sector 3559304
[ 9596.129219] ata1: EH complete
[ 9874.976166] usb 1-1: new high-speed USB device number 2 using ehci-pci
[ 9875.110102] usb 1-1: New USB device found, idVendor=04e8, idProduct=6860
[ 9875.110121] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9875.110135] usb 1-1: Product: SAMSUNG_Android
[ 9875.110147] usb 1-1: Manufacturer: SAMSUNG
[ 9875.110158] usb 1-1: SerialNumber: 8f1e7374
[ 9883.630169] systemd-hostnamed[7937]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[10060.047118] usb 1-1: USB disconnect, device number 2
```

---

### Post by tgalati4 on 2014-11-11
Read DMA errors are either failing hard disk circutiry, bad hard disk controller on the motherboard, or not enough power to run the chips.  Take the battery out and try to boot without the battery.  You might have a bad battery taking more current than it should.  Look at dmesg after booting on AC only.  Find another power supply.

---

### Post by DogMatix on 2014-11-11
I run a Acer One netbook (circa. 2008) albeit with only 1GB RAM and I switched from Ubuntu to Lubuntu at 12.04 and it gave it a new lease of life. Ubuntu does run but in an everyday scenario it's generally laggy.

Regarding Read DMA errors: have you run a SMART data check on your HDD from disk utilty?

---

### Post by oldos2er on 2014-11-11
> **frankennetbook said:**
>   For some reason I didn't think to download 14.04 from another pc but regardless I tried to downgrade back to 12.04 which worked after a little bit of struggle. 

As far as I know there is no officially supported downgrade procedure other than actually installing the older OS. Is that what you did?

---

### Post by DogMatix on 2014-11-11
I'd back-up and reinstall from scratch before I immediately assumed hardware as the downgrade route you mentioned would be very messy.

A 'stupid' question: is the new RAM you installed seated OK?

---

### Post by frankennetbook on 2014-11-11
I tried taking the battery out and only got one internal error message after starting up.  Which is way better than I've been getting.  Impressive also noticed the batter is damaged a bit, just the plastic.  

And I switched from windows xp to 12.04 and it was a huge performance improvement, other than recently.   

Still have issues of not being able to install anything but impressive improvement none the less!

---

