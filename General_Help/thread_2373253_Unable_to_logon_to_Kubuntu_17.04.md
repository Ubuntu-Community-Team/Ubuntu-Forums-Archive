---
title: "Unable to logon to Kubuntu 17.04"
date: 2017-10-04
forum: General Help
---

### Post by bryan.sailer on 2017-10-04
Last night I installed Cisco Packet Tracer 7.1 but I was unable to launch the application.  After troubleshooting different settings only with Packet Tracer files I was unable to resolve my issue.  The next step I took was to uninstall Packet Tracer.  To accomplish this I performed the following commands:

```

sudo rm -r /opt/pt
sudo rm /usr/share/applications/pt6.desktop
sudo rm /usr/share/icons/hicolor/48x48/apps/pt6.png
``` 

After Packet Tracer was uninstalled I reinstalled the application.  When the installation completed I restarted my computer.  This is when my problem started.  The computer boots to the logon screen but when I logon an NVIDIA logo flashes on the screen then it goes back to the logon screen.  I accessed the command line and was able to logon.  Three error messages appeared on the screen identifying three of my partition needed to be scanned for errors.  First thing I tried was disabling the partitions in the fstab file and rebooting the computer.  This did not fix my problem.  I then uninstalled Packet Tracer but that did not fix my problem.  What other options can I try?

---

### Post by Rick St. George on 2017-10-04
This may be related to why you could not launch PT7;
[https://askubuntu.com/questions/944717/packet-tracer-7-1-wont-lauch-ubuntu-16-04-lts](https://askubuntu.com/questions/944717/packet-tracer-7-1-wont-lauch-ubuntu-16-04-lts)

You may have also corrupted / misconfigured the FSTAB file. For instruction on FSTAB file, see this link;
[URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab
[/URL]
How did you "disable the partitions" in FSTAB?  Did you simply comment them out? Or delete the line?

Are you sure the HD is OK? Can you run a diagnostics on the HD?

---

### Post by bryan.sailer on 2017-10-05
Rick,
Thank you for the link about Packet Tracer but that just happens to be the same forum I was following.  As far as the fstab file, I first tried commenting out the drives but that did not work.  Then I made a copy of the fstab file, naming it fstab.old, and removed all of the drives from the file.  When I rebooted the computer it still would not allow me to logon.  This morning I ran the "badblocks" command on my root drive.  When I left for work it was still running.  I will post the results when I get home later today.  Are there any other tests you recommend I use?

sudo badblocks -v /dev/sda

---

### Post by Rick St. George on 2017-10-05
Depending on the HD - Yes. Check the mfg for diag downloads to be run from a CD. For example, to test Seagate drives I have SeaTools on a CD. And you can also download a Generic version to check any HD, such as FlaconFour Ultimate Boot CD (April 2013), here is the Link, but be sure to download the FULL 4.61 ISO VERSION further down the page.
[https://falconfour.wordpress.com/2013/08/08/falconfours-ultimate-boot-cd-v4-61-patch/](https://falconfour.wordpress.com/2013/08/08/falconfours-ultimate-boot-cd-v4-61-patch/)

After Boot with this CD - Run MinixP (for GUI), then "HD TunePro" detailed, to find out condition of the drive.

Hope this helps! Have Peace as this too shall pass! You did make backups ... Right?

Rick

---

### Post by bryan.sailer on 2017-10-05
> **Rick St. George said:**
> Depending on the HD - Yes. Check the mfg for diag downloads to be run from a CD. For example, to test Seagate drives I have SeaTools on a CD. And you can also download a Generic version to check any HD, such as FlaconFour Ultimate Boot CD (April 2013), here is the Link, but be sure to download the FULL 4.61 ISO VERSION further down the page.
[https://falconfour.wordpress.com/2013/08/08/falconfours-ultimate-boot-cd-v4-61-patch/](https://falconfour.wordpress.com/2013/08/08/falconfours-ultimate-boot-cd-v4-61-patch/)

After Boot with this CD - Run MinixP (for GUI), then "HD TunePro" detailed, to find out condition of the drive.

Hope this helps! Have Peace as this too shall pass! You did make backups ... Right?

Rick

Yes, I have backups of my root drive, but the other HD's I had mounted to my home directory for Documents, Pictures, Music, and Videos.  Those are my storage drives for everything each with their own HD.  This setup keeps my root drive separate from my data.  I will download one of the applications and scan my HD's tonight.  Thank you for the help.

---

### Post by bryan.sailer on 2017-10-05
Well, I had trouble burning the image.  It would complete 95% then it failed.  I was still logged on to my computer through the terminal so I ran the update command.  Surprisingly I received an error saying that packages were missing.  So I ran ```
apt --fix-install 
``` and after the missing packages were installed I was able to logon again.

---

### Post by Rick St. George on 2017-10-06
So your problem is fixed! Right? Did your correct your FSTAB file?

If so, please mark your thread as Solved - Look above your first post under "Thread Tools".
If you can logon to your OS, be sure to burn that FalconFour CD as it will come in handy. And I would still verify the condition of your Hard Drives. For me, and I use my computer 6-8 hrs/day, they only last 3 years. 

Peace!
:popcorn:

---

