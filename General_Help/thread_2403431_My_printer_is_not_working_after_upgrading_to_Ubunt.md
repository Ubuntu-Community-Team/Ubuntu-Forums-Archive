---
title: "My printer is not working after upgrading to Ubuntu 18.04.1"
date: 2018-10-11
forum: General Help
---

### Post by Gins on 2018-10-11
Hi
My Ubuntu worked fine. The system asked me to upgrade to the latest version. I obliged and upgraded to 18.04.1 . Now I run Ubuntu 18.04.1 LTS.
Everything works fine except the printer. it worked fine all the time. I wrote letters using the word processor and printed.

 My printer is Epson XP 247.  I looked at Settings and the devices. I connected the printer and switched on the power. **It recognized the printer**. I installed  it. 

I can't print. Simply it does not recognize.[B] I write a letter using the word processor. I can't print it. The printer is dead although I installed it. 
[/B]
i connect the printer using the USB.

What is the problem? There are always untoward incidents when you upgrade. I upgraded my Ubuntu because it asked me to do so.

  Please help me.

---

### Post by jerome1232 on 2018-10-11
The first thing I would try is installing Epsons linux drivers

[http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)

---

### Post by Gins on 2018-10-11
Thanks Jeromy
I did it, It drew a blank. It asked the name of the printer and the operating system. I gave EPSON XP 247 and Linux. I read 'previous 20 items' and 'next 20 items' . Those are dead.
I struggled more than 6 hours yesterday.
**I don't know how to solve the problem.**

---

### Post by Gins on 2018-10-11
Hello Everybody
I have not solved the problem, 
**Your thoughts are very welcome,**

---

### Post by him610 on 2018-10-11
Sometimes updates do unintended things. Experienced a similar problem on a Brother MFC. Resolution involved completely deleting the original installed drivers then re-installing them after which it worked.

---

### Post by maglin2 on 2018-10-11
I have an Epson XP-425 for which the 18.04 automatically installed drivers failed.

```
sudo apt install printer-driver-escpr
```

is what worked for me.

If you have synaptic installed you can also find and install it that way.

PS I typed xp-247 and Linux into the link given above by jerome1232 and the first item offered was :

XP-243 245 247 &#8230;Printer Driver    Linux 1.6.30    ESC/P-R Driver (generic driver)    All language 09-28-2018

with a download button beside. Seems you need the hyphen.

---

### Post by dragonfly41 on 2018-10-12
Have you looked at printers listed in CUPS ..

[http://localhost:631/printers/?](http://localhost:631/printers/?)

---

### Post by Gins on 2018-10-12
Hello dragonfly41
The following  works.
[http://localhost:631/printers/?](http://localhost:631/printers/?)

The messages are  stopped and filter failed.
--------------------------------------------------------
Maglin2  suggested the follwoing:
sudo apt install printer-driver-escpr
It worked and installed some stuff.

Maglin2 is clever.
He cleverly said that I did not write XP-247 properly.
Now I did the way he suggested and it found the drivers.
I simply followed it.
[B]THE BOTTOM LINE IS  MY PRINTER  DOES NOT WORK.
THE  MESSAGES ARE 'FILTER FAILED' AND  'STOPPED'[/B]
Please help me.

The test page printing gave me the message 'stopped' and  when I tried to print from the word processor the message was 'filter failed'
What is the problem?

---

### Post by jerome1232 on 2018-10-12
I have had a similar issue in the past, but it was my wifes computer trying to print over the network to the one on mine that was getting the filter failed error. The issue was she had the wrong driver selected on her computer.

If you go to settings->devices->printers, try deleting the printer in there and re-adding it. Now that you have the epson device drivers installed AND whatever is in the repos installed you should have options to select for the driver.


Alternativly you might be able to adjust which driver it is using by going to settings->devices->printers --> additional settings -> right click your printer and click properties -> on the option that says "Make and Model" select change, browse into epson and find your printer model.

---

### Post by Gins on 2018-10-13
Thanks for the reply, jerome1232
I did what you have suggested, but to no avail.
-------------------------------------------------------------------------------------------------------------------------------------------------------------
Printer properties: EPSON XP-243 245 247 Series
Device: URI : usb://EPSON/XP-243%20245%20247%20Series?serial=583251433033313342&interface=1
Make and model: EPSON XP-243 245 247 Series , Epson Inkjet Printer Driver (ESC/P-R) for Linux

Printer state: Idle - Filter failed
----------------------------------------------------------------------------------------------------------------------------------------------------------------
**Please read the above details.**

I made several attempts using my word processor to print out a paper. The messages were 'Printing stopped' .
Your thoughts are very welcome.

---

### Post by jerome1232 on 2018-10-13
Well, maybe cups error log might help. Try and print something.

open a terminal (pressing ctrl+alt+t will open one)

Type in this command, tail is just a command that will display the last 10 lines of a file, in our case it's displaying the last 20 with the -n 20 switch. /var/log/cups/error_log is where cups logs error messages to.

```
tail -n 20 /var/log/cups/error_log
```

Copy all of the output out of the terminal (highlight it all, right click and copy. Or on the keyboard ctrl+shift+c)

Paste it into a reply here, make sure to wrap it in code tags (press the little button in the edit window that looks like a # symbol) This will increase readability for us.


As a side thought, where there multiple drivers listed for your printer model when you went to settings->devices->printers->additional settings-> change "make and model". 

For my printer there are multiple drivers available, I have to select the one that says "for cups". If you have more than one listed as I do, give them all a try.
[ATTACH=CONFIG]281328[/ATTACH]

---

### Post by dino99 on 2018-10-13
I have made lots of dist-upgrade in the past, and often got some unexpected issues until i checked for old settings left behind and orphan packages.
Remeber that a fresh install is often quicker and troubleless than doing rolling upgrades.

But run 'gtkorphan' and 'bleachbit' (as root, carefully select features) to clean the system.
Then reboot and go glancing at 'journalctl -b' to know about possible problem (highlited blank is a warning, red lines is an error)
When you are ready you can then test your printer job, after rebooting.

---

### Post by Papaduke on 2018-10-14
I have the exact same prob as Gins, it came right after upgrading to 18.04.1, my printer is Epson but a different model,  I do not know how to resolve but I suspect I might know why it happens... maybe the clever ones can make sense of it: because of upgrading through the new rollout upgrade rather than doing a fresh install, at some point during the upgrade we are informed that third party update will be disabled and can be re-enabled after the upgrade. So Bionic offers new options in Software & Updates >other software, you can tick the 'disabled on upgrade to Bionic' and one of them is download.ebz.epson. Once I update I get:

[LEFT][SIZE=2][FONT=Ubuntu Mono][COLOR=#0000cd]Get:11 [/COLOR][[COLOR=#0000cd]http://download.ebz.epson.net/dsc/op/stable/debian[/COLOR]]("http://download.ebz.epson.net/dsc/op/stable/debian")[COLOR=#0000cd] lsb3.2 Release.gpg [198 B][/COLOR][/FONT][COLOR=#0000cd]
[/COLOR][/SIZE]
[SIZE=2][FONT=Ubuntu Mono][COLOR=#0000cd]Ign:11 [/COLOR][[COLOR=#0000cd]http://download.ebz.epson.net/dsc/op/stable/debian[/COLOR]]("http://download.ebz.epson.net/dsc/op/stable/debian")[COLOR=#0000cd] lsb3.2 Release.gpg[/COLOR][/FONT][/SIZE]
[COLOR=#0000cd][SIZE=2][FONT=Ubuntu Mono]Reading package lists... Done  [/FONT] [/SIZE][/COLOR]
[SIZE=2][FONT=Ubuntu Mono][COLOR=#0000cd]W: GPG error: [/COLOR][[COLOR=#0000cd]http://download.ebz.epson.net/dsc/op/stable/debian[/COLOR]]("http://download.ebz.epson.net/dsc/op/stable/debian")[COLOR=#0000cd] lsb3.2 Release: The following signatures were invalid: E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56[/COLOR][/FONT][/SIZE]
[COLOR=#0000cd][SIZE=2][FONT=Ubuntu Mono]E: The repository 'http://download.ebz.epson.net/dsc/op/stable/debian lsb3.2 Release' is not signed.[/FONT]
[/SIZE][/COLOR]
[COLOR=#0000cd][SIZE=2][FONT=Ubuntu Mono]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/FONT][/SIZE][/COLOR]
[COLOR=#0000cd][SIZE=2][FONT=Ubuntu Mono]N: See apt-secure(8) manpage for repository creation and user configuration details.[/FONT][/SIZE][/COLOR]
[/LEFT]

I am no tecky but I venture a guess that the repository does not permit the update of the Epson driver for lack of secure certificate. Can anything be done about that? Many thanks for any help.

---

### Post by dragonfly41 on 2018-10-14
I have Y PPA Manager installed as a tool and under Advanced options
there is an option "Try to fix all GPG BADSIG errors!.
Might be worth trying.
Certainly a useful tool for PPA management.

---

### Post by Papaduke on 2018-10-17
I found a solution on [this Ask Ubuntu thread]("https://askubuntu.com/questions/1080720/printer-filter-failed/1080926#1080926") and it works for me.
Delete your printer, then 
```

sudo rmdir /usr/share/ghostscript/9.25/iccprofiles
  sudo apt-get install --reinstall libgs9-common

```
then install printer, that's it  :P

---

