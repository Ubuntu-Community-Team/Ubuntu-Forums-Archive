---
title: "Dvdrip: Ripping dvd stops after just a few seconds with no error msgs"
date: 2007-04-15
forum: General Help
---

### Post by mkarr on 2007-04-15
First thing first, I have 2 computers, a pentium 2.4ghz and a amd2700+ with a gig of ram on both and with Ubuntu 6.10 installed on both. No longer than a month ago dvd::rip was working flawlessly on both computers. Nothing has changed with either computer except for installing the automatic updates thru apt.
           
Now when I start dvd::rip the dvd ripping process stops after just a few seconds with no reported errors. 

When I open up the detail plan I get this

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=29778&stc=1&d=1176661972[/IMG]

This is the log output I get:

Sun Apr 15 13:38:12 2007 Detected transcode version: 10002
Sun Apr 15 13:38:35 2007 Project file saved to '/media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New.rip'
Sun Apr 15 13:38:35 2007 Project temporary dir '/media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New/tmp' created
Sun Apr 15 13:38:35 2007 Project {name} created
Sun Apr 15 13:38:44 2007 Start job 'Read TOC (lsdvd|tcprobe)'
Sun Apr 15 13:38:44 2007 Start job 'Read TOC (lsdvd)'
Sun Apr 15 13:38:44 2007 Executing command: execflow lsdvd -a -n -c -s -v -Op /dev/hdc 2>/dev/null && echo EXECFLOW_OK
Sun Apr 15 13:38:44 2007 Not enabling PSU core, because this movie has only one PSU.
Sun Apr 15 13:38:44 2007 Not enabling PSU core, because this movie has only one PSU.
Sun Apr 15 13:38:44 2007 Not enabling PSU core, because this movie has only one PSU.
Sun Apr 15 13:38:44 2007 Start job 'Read TOC (tcprobe)'
Sun Apr 15 13:38:44 2007 Successfully read DVD TOC
Sun Apr 15 13:38:44 2007 Copying IFO files from /media/cdrom0 to /media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New/tmp/ifo
Sun Apr 15 13:38:45 2007 Job 'Read TOC (lsdvd|tcprobe)' finished
Sun Apr 15 13:38:45 2007 Job 'Read TOC (tcprobe)' finished
Sun Apr 15 13:38:45 2007 Job 'Read TOC (lsdvd)' finished
Sun Apr 15 13:38:55 2007 Start job 'Rip selected title(s) / chapter(s)'
Sun Apr 15 13:38:55 2007 Start job 'Process title #1'
Sun Apr 15 13:38:55 2007 Start job 'Rip - title #1'
Sun Apr 15 13:38:55 2007 Executing command: rm -f /media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New/vob/001//New-???.vob && execflow -n 19 tccat -t dvd -T 1,-1,1 -i /dev/hdc | dvdrip-splitpipe -f /media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New/tmp/New-001-nav.log 1024 /media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New/vob/001//New vob  | tcextract -a 0 -x ac3 -t vob | tcdecode -x ac3 | tcscan -x pcm && echo EXECFLOW_OK
Sun Apr 15 13:39:03 2007 Executing command: execflow tcprobe  -i /media/usbdisk/gtk-gnutella-downloads/complete/Movies/dvdrip-data/New/vob/001/ && echo EXECFLOW_OK
Sun Apr 15 13:39:03 2007 Job 'Rip - title #1' finished
Sun Apr 15 13:39:18 2007 Rip selected title(s) / chapter(s): 20% done.
Sun Apr 15 13:39:18 2007 Process title #1: 20% done.

I have the some problem on both computers no matter what dvd I am trying to rip. If anyone has any ideas what the problem might be,  I sure would appreciate the help. Thanks!

---

### Post by mkarr on 2007-04-15
Ok I guess I haven't tried to rip any dvds since I did the clean install of Edgy three months ago. Time has passed  a lot quicker than I thought.

---

### Post by svega85 on 2007-04-27
[COLOR=Black]I have the same problem but only with dvds that have copy protection i think but it puts out the same message [/COLOR]

---

### Post by svega85 on 2007-04-27
ok i think i figured it out i didn't have libdvdcss2 and it's not in synaptic so you have to install libdvdread3 then run ```
sudo sh /usr/share/doc/libdvdread3/install-css.sh
```

---

