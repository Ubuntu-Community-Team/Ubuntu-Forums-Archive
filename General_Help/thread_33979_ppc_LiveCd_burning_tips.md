---
title: "ppc LiveCd burning tips"
date: 2005-05-13
forum: General Help
---

### Post by foulmouth on 2005-05-13
I haven't been able to successfully burn a working livecd. I have tried burning with several different methods I was just wondering what way was effective for my fellow os x/mac users.

---

### Post by ipixel on 2005-05-16
My method:

1) Downloaded the 'live' image from the GERMAN ftp site, using 'Trasmit' (a popular ftp client). My main problem was that using Safari or the Finder always seemed to time out.

2) Launched 'Disk Utility' - inside "Utilities" folder, inside your "Applications". 

3) Dragged the downloaded ".iso" image onto the Disk Utility window.

4) Selected the image name on the list, and clicked the 'Burn' button.

Worked like a charm. I was able to burn both Ubuntu and Kubuntu without any problems.

Currently using MacOS X 10.4 (Tiger) - and Kubuntu!  \\:D/

---

### Post by keithpeter on 2005-05-17
Hello

I managed to get a live cd working as follows...

1) Downloaded the iso from [http://se.releases.ubuntu.com/5.04/ubuntu-5.04-live-powerpc.iso](http://se.releases.ubuntu.com/5.04/ubuntu-5.04-live-powerpc.iso) (I'm in UK) on a fast connection at work - burnt iso as a file to a cd-r on a Windows laptop (XP admin rights won't allow burning images)

2) Copied iso to desktop on my iBook and tried to use Disk Utility (X 10.3.9) to burn the iso to a cd-r. No luck. Disk Utility crashes. This is a documented feature of _some_ macs.

3) Downloaded the Missing Media Burner ([http://homepage.mac.com/rnc/.Public/MissingMediaBurner.zip](http://homepage.mac.com/rnc/.Public/MissingMediaBurner.zip)) and installed the program

4) Changed CD/DVD system preferences to 'ignore' when inserting a blank disc

5) In Missing Media Burner, selected the iBook cd burner, set the driver to 'generic mmc', selected 'Data/burn iso' in the Select Format drop down, ticked the Use Superuser and Show Command options, dragged the iso into the window, put a blank cd-r in, typed my password and hit burn! About 7 minutes later, I had an iso disc

Hope that helps. Now - will the 'live' cd work the iBook modem and can the live cd access the hard drive at all?

---

### Post by ReneB on 2005-05-19
I too had no luck with OS X 10.3.9 Disk Utility.  Roxio Toast Titanium didn't work either. The app. FireStarter FX worked for me.  I actually found out about it on one of the Ubuntu FAQ pages.

Good luck

rene

ps: I tried this as posted above "Dragged the downloaded ".iso" image onto the Disk Utility window." but that didn't work in 10.3.9

---

### Post by sgmorr on 2005-05-20
I second the motion for Firestarter FX. Worked great. Just downloaded the iso to my desktop and drug it over onto Firestarter FX.

---

