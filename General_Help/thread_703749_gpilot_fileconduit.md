---
title: "gpilot fileconduit"
date: 2008-02-21
forum: General Help
---

### Post by bmenge on 2008-02-21
Ok I have been looking and looking for resolutions to my problem on the forum and google.  I have found many options to try but keep getting very little result.  I am not all that interested in a sync to update my calendar or my email I want to write a java app that will calculate corrected race times and fuel millage etc, so all I need is the file transfer.   I have the most success with gplilot.  I have tried jpilot, gpilot, and kpilot.  I have the conduit enabled and was not getting any luck by dragging the file in to the appellate so I tried the java based gpilotinstall, that also did not work.  I then tried it from the terminal, this is where I at least was able to see what was going on.  I found a free game and tried it out.  

brian@brian-desktop:~$ gpilot-install-file /home/brian/downloads/C-ROID.PRC
gpilotd-Message: Activating object OAFIID:GNOME_Pilot_Daemon
fileconduit-Message: MyPDA1 completed 65537

I get the completed 65537 after a short pause and would think that it worked! but wait the palm has completed the sync and the dialog box that popped up has not gone away.  The gpilot dialog box never recognizes that I pressed the sync button.  

If I check log on the palm I get this info

gnome-pilot v2.0.15
On host Brian-desktop
Synchronization terminated


Just a side now...
The palm is a Zire 72 and does have a sd card slot so I thought that I would try to use the card reader on my printer but was having problems getting it to mount automatically.  I then used the mount command and got problems with the permissions.  I mounted the drive as follows

sudo mount /dev/sda /media/cfcard -rw

I don't remember the exact wording but got a message saying the drive was writeprotected but explicit write flags were given.  Still I could not write on the drive.  I figured this was a problem of its own and would go back to trying to get gpilot to work correctly

---

### Post by bmenge on 2008-02-23
Anyone got any idea?

---

### Post by jpantone on 2008-06-22
Install the pilot-link package. This is a command line utility which will do many things, particularly it will install pdb/prc files, and will simply fetch and store files from your desk/laptop.

the command (part of the above package) you are probably most interested in would be pilot-xfer

after installation use man pilot-link and man pilot-xfer

If you are using the gpilotd daemon, don't forget to either turn it off, or pause it, since it will intercept the sync, and foul up pilot-xfer.

My palm device (a LifeDrive) uses /dev/ttyUSB0 which would correspond to the "port" in the pilot-xxx commands (i.e. pilot-xfer -p /dev/ttyUSB0 ..... )

---

