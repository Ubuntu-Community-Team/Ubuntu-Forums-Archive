---
title: "Downloaded Spreadsheet Not Opening from /tmp"
date: 2019-11-08
forum: General Help
---

### Post by SBFree on 2019-11-08
Hi
On a web page, I select link for spreadsheet and get a choice from Firefox
[INDENT]Open with (LibreOffice Calc) or
	Save File[/INDENT]
Selecting Open with ...
	[INDENT]starts LibreOffice but generates an error window with the message:
[INDENT]**/tmp/mozilla_scott0/valuation.csv does not exist**[/INDENT][/INDENT]
		
Using Nautilus to open /tmp/mozilla_scott0/
	[INDENT]shows the file is there but trying to open it gives the same error[/INDENT]
Using the Terminal to look at the file permssions suggests I own the file and have permission to read it:
	[INDENT]scott@SBdesk:/tmp$ ```
ls -l /tmp/mozilla_scott0
```
Outputs:	
[INDENT]
	**-r-------- 1 scott scott 1983 Nov  8 08:02 valuation.csv**
	scott@SBdesk:/tmp$[/INDENT][/INDENT]

I can copy the file to the desktop and open it with LibreCalc

It looks like I own and have R/W privileges for the directory where the file is.
	[INDENT]scott@SBdesk:/tmp$```
 ls -l /tmp
```
Outputs:	
[INDENT]**drwx------ 2 scott scott 4096 Nov  8 08:04 mozilla_scott0**[/INDENT][/INDENT]

Using a new install of Ubuntu 18.04.3 LTS, Firefox 70.0.1(64bit)

Any insights would be appreciated - Thanks in advance - scott

---

### Post by Holger_Gehrke on 2019-11-08
You might be using a snap of Libre Office. Programs packaged as snaps are confined and can't access most of the file system. To check whether your Libre Office is a snap check the output of 'snap list' in a terminal. 
If that is indeed the problem, then you can get an unconfined Libre Office (packaged in Debian packages, probably a few releases older than the snap - on my system 6.0.7 for the .deb and 6.3.3.2 for the .snap) by first removing the snap with 'snap remove libreoffice' and then installing the Debian packages with 'sudo apt install libreoffice'.

Holger

---

### Post by SBFree on 2019-11-09
Thank you Linux Sensei - OSU!
apparmor and snapd and using the LibreOffice Snap distribution seemed to be the problem.
I thought about seeing if I could alter the apparmor rules but instead removed the LibreOffice snap package and reinstalled LO with the following:
```
sudo snap remove libreoffice
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt install libreoffice
```

Thank you for your reply!

---

