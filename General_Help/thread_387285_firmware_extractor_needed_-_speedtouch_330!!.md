---
title: "firmware extractor needed - speedtouch 330!!"
date: 2007-03-18
forum: General Help
---

### Post by smurphs on 2007-03-18
Hi,

I'm trying to set up my speedtouch 330 rev.4 in ubuntu 6.10 but I can't fing the firmware extractor for the firmware! The links to the binary just point to a file which is all characters. The source destination seems to work, but I've no idea how to compile it! (it said something about a missing .o file?)

Please help! 

much appreciated,

dylan
smurphs (#at#) freeuk.com

---

### Post by Docter on 2007-03-18
It's a binary so you have to save the file as a BIN file. If your browser doesnt give you the option automagically then right click and save link as...

Then you have to modify it's permissions to make it executable. Open a terminal and cd to the directory you saved the bin file:
```

#example
cd /home/user
chmod +x firmware-extractor
```

You're ready to continue.

---

### Post by smurphs on 2007-03-18
Thanks for the help, but I'm still drawing a blank. it's just saying firmware-extractor: unknown file. 

Has anyone got the two files to be extracted to save me going through this? They are speedtch-1.bin & speedtch-2.bin. 

Cheers

dylan

---

### Post by smurphs on 2007-03-18
aha! apparently the 2 files were in my windows directory so i copied them. I've followed millions of instructions but i get this when i use the tails command:

dyl@dyl-laptop:~$ tail -f /var/log/messages
Mar 18 17:38:19 dyl-laptop gconfd (root-4852): GConf server is not in use, shutting down.
Mar 18 17:38:19 dyl-laptop gconfd (root-4852): Exiting
Mar 18 17:40:56 dyl-laptop gconfd (root-4980): starting (version 2.16.0), pid 4980 user 'root'
Mar 18 17:40:56 dyl-laptop gconfd (root-4980): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 18 17:40:56 dyl-laptop gconfd (root-4980): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar 18 17:40:56 dyl-laptop gconfd (root-4980): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 18 17:40:56 dyl-laptop gconfd (root-4980): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 18 17:40:56 dyl-laptop gconfd (root-4980): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 18 17:41:56 dyl-laptop gconfd (root-4980): GConf server is not in use, shutting down.
Mar 18 17:41:56 dyl-laptop gconfd (root-4980): Exiting

anyone have a clue what's happening? please?

dyl

---

### Post by Docter on 2007-03-18
Thats the output of your syslog and it looks like a permissions issue. Is that what you get after you try the chmod command? It looks like my error.. I should have told you that the correct command is:

sudo chmod +x firmware-extractor

when you are in the same directory as your firmware extractor.

---

### Post by Docter on 2007-03-18
Looks like a permissions issue. My bad.

Move the file firmware-extractor to your home folder then open up a terminal.

cd to your home folder

sudo chmod +x firmware-extractor

enter your password.

---

### Post by smurphs on 2007-03-19
The output is what I'm getting when I use this command: 

tail -f /var/log/messages

I believe that's to check whether my modem is working. Which it's not. Bleedin' thing.

---

### Post by Docter on 2007-03-19
The 'tail -f /var/log/messages' command produces an updating display of your syslog in the terminal. You can get the same thing if  you go to System -> Administration -> Syslog on your Ubuntu desktop menus. In fact you should do that, click on where it says syslog and read through it to see if any obvious errors pop up. 

Is your firmware loading?

---

### Post by smurphs on 2007-03-21
Thanks for that. Yep the firmware is identified, and it even says adsl line up! however firefox doesn't find the web, neither does add/remove programs. This is the end of the log, if it means anything to you! There's something about eth0:, is that relevant?

Mar 21 09:34:45 dyl-laptop kernel: [17179622.316000] ATM dev 0: ADSL line is up (2272 kb/s down | 288 kb/s up)
Mar 21 09:35:28 dyl-laptop gconfd (dyl-4521): starting (version 2.16.0), pid 4521 user 'dyl'
Mar 21 09:35:28 dyl-laptop gconfd (dyl-4521): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar 21 09:35:28 dyl-laptop gconfd (dyl-4521): Resolved address "xml:readwrite:/home/dyl/.gconf" to a writable configuration source at position 1
Mar 21 09:35:28 dyl-laptop gconfd (dyl-4521): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar 21 09:35:28 dyl-laptop gconfd (dyl-4521): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar 21 09:35:28 dyl-laptop gconfd (dyl-4521): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar 21 09:35:30 dyl-laptop kernel: [17179667.576000] NET: Registered protocol family 10
Mar 21 09:35:30 dyl-laptop kernel: [17179667.576000] lo: Disabled Privacy Extensions
Mar 21 09:35:30 dyl-laptop kernel: [17179667.576000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 21 09:35:30 dyl-laptop kernel: [17179667.576000] IPv6 over IPv4 tunneling driver
Mar 21 09:35:35 dyl-laptop kernel: [17179671.152000] NTFS driver 2.1.27 [Flags: R/O MODULE].
Mar 21 09:35:35 dyl-laptop kernel: [17179671.156000] NTFS-fs warning (device sda1): parse_options(): Option iocharset is deprecated. Please use option nls=<charsetname> in the future.
Mar 21 09:35:35 dyl-laptop kernel: [17179672.328000] NTFS volume version 3.1.
Mar 21 09:35:36 dyl-laptop gconfd (dyl-4521): Resolved address "xml:readwrite:/home/dyl/.gconf" to a writable configuration source at position 0

---

### Post by Docter on 2007-03-21
You're getting closer.Your ADSL line is up and synchronised but your pppd device isn't yet starting. Continue from this tuturial from where it says "Secrets".

[http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html")

Once you have finished teh tute, rebooted and if it still doesnt work: reopen your system log and in the View menu click on Filter, in the filter box that pops up type "pppd" and see what messsages that throws up.


good luck

---

### Post by smurphs on 2007-03-22
Well shiver me timbers, I got it working! In the end I just needed the command 
sudo pppd call speedtch 
to get it running! I put it in the startup directory so it boots online now.

Thanks for your help, I would have given up long ago otherwise. Now if I can just work out how to make my wife use ubuntu instead of windows.... Got any magic dust handy? (or perhaps a sledge hammer!)

cheers

dyl

---

