---
title: "no space left on device"
date: 2007-03-17
forum: General Help
---

### Post by trav5 on 2007-03-17
Hi all. I cant startx because the 40G partition is full. I found this by googling [http://arun-prabha.com/wdpress/?p=301]("http://arun-prabha.com/wdpress/?p=301")  and there is 38 GB some where  in the /var/log dir. There are two hidden files . and .. that I think are backup scripts but I cant rm them. If this sounds right what do I do to remove them and prevent this from happening again. This is a fresh install only about a month old. Thanks for any help. I miss my Ubuntu:( .

---

### Post by Kateikyoushi on 2007-03-17
Enter the folder with nautilus and check which files are big in /var/log.

---

### Post by trav5 on 2007-03-17
> **Kateikyoushi said:**
> Enter the folder with nautilus and check which files are big in /var/log.

I may not have been clear but I cant start GDM. I will try from another os to look at that folder.

---

### Post by Kateikyoushi on 2007-03-17
Sorry I thought you deleted something already to be able to login.

Then try this from recovery mode.

>  sudo ls -a -l -h /var/log/

---

### Post by trav5 on 2007-03-17
> **Kateikyoushi said:**
> Sorry I thought you deleted something already to be able to login.

Then try this from recovery mode.

Thanks for the help! The files were messages.0, syslog.0, kernlog.0( I think dont have that in front of me). They were 13GB each. I deleted one and was able to log back in but it killed a lot of stuff(like my wireless usb, no longer seen with lsusb) and it will probably just be faster to reinstall. What do I do in the future to prevent it from creating these files in the first place? I have been using Edgy since it came out and have never had this problem until I did this install about a month ago when I got my video card.

---

### Post by Kateikyoushi on 2007-03-17
These files are small logfiles for me, probably looking into one would have given an answer why did these appear, keep an eye on them if you reisntall and post if something comes up.

---

### Post by trav5 on 2007-03-17
Ok I did a fresh install on a different partition so I could look at the files(the two that were left anyway). Here is a sample of the file kern.log.0.```
Mar 16 13:37:55 trav-desktop kernel: [17617999.820000] hda: packet command error: error=0x52 { EndOfMedia LastFailedSense=0x05 }
Mar 16 13:37:55 trav-desktop kernel: [17617999.820000] ide: failed opcode was: unknown
Mar 16 13:37:55 trav-desktop kernel: [17617999.820000] hda: packet command error: status=0x51 { DriveReady SeekComplete Error }
Mar 16 13:37:55 trav-desktop kernel: [17617999.820000] hda: packet command error: error=0x52 { EndOfMedia LastFailedSense=0x05 }
Mar 16 13:37:55 trav-desktop kernel: [17617999.820000] ide: failed opcode was: unknown

``` The only way I could see what was in it was using the cat command in the terminal because it was 13 GB. I did a ctrl c  because Im sure it would have went on for an hour or two. It appears that what ever the problem was it occurred  at 13:37 yesterday and repeated the error messages for a couple of hours until those three files were full. I did play an audio cd with soundjuicer about that time yesterday and noticed a few hours later that the processor was running like mad and closed soundjuicer and the proc went back to rest. A few hours after that I was going to download an iso and got a message there was no more space. Any ideas?

---

### Post by ghetto2ivy on 2007-04-17
Ditto problem here on Fiesty... Have you posted a bug to launchpad? kernal and syslog ar emain culprits but some others are over a few hundred megs. 

Steven

---

