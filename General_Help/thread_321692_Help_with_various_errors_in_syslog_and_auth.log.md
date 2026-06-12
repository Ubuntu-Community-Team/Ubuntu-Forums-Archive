---
title: "Help with various errors in syslog and auth.log"
date: 2006-12-19
forum: General Help
---

### Post by dannyboy79 on 2006-12-19
I am getting various errors in various places and I was hoping that someone, anyone can help me trouble shoot any of them??? 

1. sendmail[25639]: My unqualified host name (localhost) unknown; sleeping for retry
Dec 18 00:52:08 localhost sendmail[25639]: unable to qualify my own domain name (localhost) -- using short name. Is this entry in my syslog bad?? I can say that I don't have a domain name yet but since my router supports using dyndns I was going to get a free one soon, will this solve this?

2. nmbd[5177]: [2006/12/18 00:55:09, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(172)
Dec 18 00:55:09 localhost nmbd[5177]:   process_name_refresh_request: unicast name registration request received for name WINXP<20> from IP 192.168.0.4 on su$
Dec 18 00:55:09 localhost nmbd[5177]: [2006/12/18 00:55:09, 0] nmbd/nmbd_incomingrequests.c:process_name_refresh_request(173)
Dec 18 00:55:09 localhost nmbd[5177]:   Error - should be sent to WINS server.
this is in my logs all the time, over and over. i didn't think i needed to set up a wins server? i recently installed bind or bind9 or something or other because I heard it helps samba work and I think that's when this message started happening? I also know that my winxp box is the domain master and when it's not on, my samba doesn't work, from my xbox, the network that all my computers are attached to don't even show up? is there a way to make my ubuntu box be a backup domain master? this is my smb.conf currently:
   domain master = no
    local master = no
    preferred master = no
    os level = 35
    idmap uid = 10000-20000
    idmap gid = 10000-20000
    announce version = 5.0
also, i have a laptop on this network also, why isn't this ubuntu box getting "process_name_refresh_request" from that box???

3. this shows up in my /var/log/auth.log;
Dec 16 12:04:26 localhost sm-mta[8103]: OTP unavailable because can't read/write key database /etc/opiekeys: No such file or directory. what does this mean??? it shows up once an hour?? 

4. i can say that I installed tripwire but haven't followed thru with it's configuration (creating database etc etc) and that's why I get this message in my /var/log/messages;
Dec 17 08:09:00 localhost tripwire[12560]: Integrity Check Failed: File could not be opened. so I just need to finish the config of tripwire and that should go away I think?

5. i get this message all the time;
hda: lost interrupt
Dec 18 00:40:56 localhost kernel: [17179713.848000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Dec 18 00:40:56 localhost kernel: [17179713.848000] hda: drive_cmd: error=0x04 { AbortedCommand }
Dec 18 00:40:56 localhost kernel: [17179713.848000] ide: failed opcode was: 0xef
Dec 18 00:40:56 localhost kernel: [17179713.848000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Dec 18 00:40:56 localhost kernel: [17179713.848000] hda: drive_cmd: error=0x04 { AbortedCommand }
Dec 18 00:40:56 localhost kernel: [17179713.848000] ide: failed opcode was: 0xef
Dec 18 00:40:56 localhost kernel: [17179713.868000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Dec 18 00:40:56 localhost kernel: [17179713.868000] hda: drive_cmd: error=0x04 { AbortedCommand }
Dec 18 00:40:56 localhost kernel: [17179713.868000] ide: failed opcode was: 0xef
Dec 18 00:40:56 localhost kernel: [17179713.868000] hda: drive_cmd: status=0x51 { DriveReady SeekComplete Error }
Dec 18 00:40:56 localhost kernel: [17179713.868000] hda: drive_cmd: error=0x04 { AbortedCommand }
and after I gogled it many people say to ignore it, that's it's not a big deal. this is my dvd burner and it works fine. it's brand new. it the Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive by NEC. what do you think?

any help with any of this would be great. i know it's asking a lot but I just figured if I made a thread for each it would be harder and it's possible that the problems are related so if someone answers one they may be able to say, hey, this problem will go away when you fix this other one. so thanks again if you can help.

---

### Post by dannyboy79 on 2006-12-25
bump, please anyone?

---

### Post by McQuaid on 2007-01-04
I can't really help sorry, but I just wanted to comment on those DriveReady SeekComplete Errors.

Yes, it's correct, if it is your dvd/cdrom drive, just ignore them.  BUT, if it's a harddrive I wouldn't ignore them, as when I had those errors shortly afterward my drive died.

I say this because I noticed hda in those errors.  Are you sure hda is your dvd rom drive and not your harddrive?  hdc is usually the dvd/cdrom drive.

For example if I: dmesg | grep hdc
[17179576.596000]     ide1: BM-DMA at 0xa808-0xa80f, BIOS settings: hdc:pio, hdd:pio
[17179578.572000] hdc: HL-DT-ST DVDRAM GSA-4040B, ATAPI CD/DVD-ROM drive
[17179578.980000] hdc: ATAPI 32X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)

As you can see, hdc is my dvd drive which is usually the default.  You can't be too careful with your hard drives so it's good to double check.  Good luck in your other issues.

---

### Post by dannyboy79 on 2007-01-05
i do appreciate the comments and yes I am sure that hda is my dvd drive as it is hooked to ide0 channel as the master. this is because i found that when I switched my dvd burner from being a slave to being the master on the first ide channel I get no errors when burning. this may just be a coinsident but I am coaster free for a while now. thanks again for your comments.

---

