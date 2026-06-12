---
title: "Seeking executable files used by GUI screens"
date: 2008-06-27
forum: General Help
---

### Post by decatur-linux on 2008-06-27
How do I determine which files / scripts are being executed by an icon / applet on a GUI screen?  

For example, if I click on the applet that shuts down the computer, there are icons for (1) log out, (2) lock screen, (3) switch user, (4) suspend, (5) hibernate, (6) reboot, and (7) shutdown.

How do (1) determine the GUI window that pops up when I click on that applet, and (2) the program or shell script that is run when I click on one of the seven icons in that GUI window?

Why do I want to know?  So that I can set up a cron file that will, for instance, shut down my computer at a certain time JUST AS ICON #7 WILL DO IT.  

Now, I am familiar with the SHUTDOWN and the POWEROFF commands and have implemented them in successful cron files.  However, I want to DUPLICATE what is being done by the SHUTDOWN icon; I want to make sure that I'm doing what is necessary for an orderly shutdown; if I didn't care I'd just hit the hardware power button.

But this is deeper than the above too.  When I open a .tar.gz file I open it with "Archive Manager"; but when I write a shell script I can't user the executable "Archive Manager"; I need to know the executable name for the program.

I have tried searching for ASCII text that I know is associated with each icon, but have been unable to determine the script or executable file.

Thanks for any help.

---

### Post by HalPomeranz on 2008-06-28
Truthfully I don't have a good method for this.  I mostly use the output of the ps command and look for programs that seem to have names related to whatever task I'm looking for.  Once I see some likely candidates I look at the system manual pages ("man programname") for confirmation that the program does what I think it does.  There probably is a document somewhere that describes what all the normal components of the Ubuntu desktop are and what they do, but I haven't been able to find it.

The short answer to your archive manager question, however, is that the underlying command is "tar".  Specifically "tar zxf file.tar.gz" will unpack a gzip-ed tar archive.

---

### Post by decatur-linux on 2008-06-28
Thanks, HalPomeranz, for your suggestions.  These may help in some situaltions. In other cases, I'm at a dead end.  For example, if I click on the "log off" icon in the upper right corner of the Ubuntu screen, this procedure does not allow me to look concurrently at the running procedures using "ps".

Other tricks I have tried, unsuccessfully I might add", is to search for an ASCII text or comment that I know is associated with the program I'm looking for.  I've decided to look into the process of writing an applet in Java or Perl to see if I can reverse engineer the applet to see the underlying command.  I have noticed in some cases I can right-click on the applet, select Properties, and SEE the name of the command, but in others it doesn't work.

I have never written a program or script that utilizes a GUI, so that would be another area to investigate.  I've looked at some of the source of XML processes but that has not been very enlightening.

Surely, there is a tool that will aid me in this search.  I can remember earlier versions of the main menu that had ONLY the executable name of the program, and it was confusing for a newbie unless he/she knew what the program did; now they have gone to the opposite extreme and give the functional name of the program and have omitted the actual name of the program.

If you think of other tips, please add them to this thread.

---

### Post by decatur-linux on 2008-06-29
Actually, I think I have answered my own question, by accident.

If you go to /user/share/applications you will see icons for all the applications that you have installed.  Select an icon...say Archive Manager...right-click on the icon and select Properties.  Now, select the Launcher tab; under Command you will find the executable program that is used when you click on this icon.

BTW, the Archive Manager is file-roller.

Thanks for your suggestions and help.

---

### Post by HalPomeranz on 2008-07-05
I was poking around on something else and happened into the /var/lib/gnome/Debian directory.  This seems to be where the links between many of the desktop menu items and their corresponding executables is stored.

---

