---
title: "Which Printer how to for Kubuntu/XP two computer network?"
date: 2007-02-24
forum: General Help
---

### Post by Neobuntu on 2007-02-24
What is the recommended way to set up a printer for sharing when the home network uses two computers (one wireless laptop) and both using mainly (KDE) Kubuntu Dapper and both also dual boot XP. We are looking at a wireless (802.11g) printer server box so that perhaps the desktop can stay off and the location of the printer station can be anywhere in the house (but not if it opens a whole can of worms).

We would like to see either computer; booted in either OS, easily able to print. Have you done this?

Is this easier than it sounds, or is it complicated?

We are open to any suggestions (such as skip the print server.) We have access to other (HP) printer models if there should there be a problem and that's why we don't favor an (already) network ready printer. 

Experienced advice needed.

---

### Post by Neobuntu on 2007-02-26
I admit that I rarely print (my friends need this) but does anyone print with Kubuntu? Is there a problem?

---

### Post by wireddad on 2007-02-26
I have successfully setup a share printer via a XP machine.  The printer is hooked up via USB.  It seems to print fine.  Lately though the shared printer has been having issues that I have not checked.

[https://help.ubuntu.com/community/WindowsXPPrinter?action=print](https://help.ubuntu.com/community/WindowsXPPrinter?action=print)
Kubuntu is similar.

[http://www.idevelopment.info/data/Unix/Linux/LINUX_PrintingWindows2000FromRedHatLinuxSMB.shtml](http://www.idevelopment.info/data/Unix/Linux/LINUX_PrintingWindows2000FromRedHatLinuxSMB.shtml)
I'd followed this one and worked.

---

### Post by Neobuntu on 2007-02-26
That's helpful as there may be a time the printer in connected to the desktop and it is running XP. 

What about the other way around. What about when the desktop print server is normally running Kubuntu and then printing from the (networked) notebook running either XP or Kubuntu?

---

### Post by WW on 2007-02-26
Take a look at this page in the wiki: [https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by Neobuntu on 2007-03-01
Clarification: 

The desktop computer is both dual booted XP pro SP2 tweaked (only used when required) and Kubuntu (which is used the most). 

The 2nd computer (also connected to the router) is also XP dual with Kubuntu.

Therefore we could be on either computer with either OS and then trying to print through the other (or a network print server) which also could be booted XP or Kubuntu.

This creates several ways to skin the proverbial cat. 

How is this BEST done?

What difficulties exist if any?

Do you know if a "IPP" wireless print server box would cover all of these boot options/OS's?

Would I have two printers to choose from as the box with printer could be booted to either OS or  can it be represented as one either way? 

Which is less time consuming? Print server box or printer connected to the desktop (as print serving computer and that way on the LAN)?

If we set up an Ink jet and secondly a laser printer (less toner cost for black printing) would you recommend one on each computer or both on one and does it matter?

What has been your experience with a printer server box on your LAN and Kubuntu?

Thank you.

---

### Post by wireddad on 2007-03-01
Definitely sounds like a print server is your solution.  But I have not set one up...yet.  :(

---

### Post by Neobuntu on 2007-03-02
So far, I have files and a printer shared (on my 100BT LAN) from one computer; via Samba/Kubuntu. 

(I set a folder to be as shared in the two OS's per computer and on their "Desktop" each, and on both computers.)

The other (2nd) computer is accessing (with password) the shared folders, printer (and sharing it's own files too) both in XP (with ZoneAlarm on this 2nd computer; set to pass the print server host name which is the workstation and 1st computer) and also accessing files and the printer (and sharing it's folder) when booted (mainly) into Kubuntu too! Nice. Everything works.

Tomorrow, I will set the printer-sharing computer to share while running XP too. The second computer should then access all and share out it's respective OS folder while booted to either OS. 

So I guess everything works best using Samba type shares; in this case. 

I still don't know if an "IPP" printer setup would be better or if it's worth the cost of a separate wireless networked (IPP) print server appliance. Anyone use one? I think an "IPP" printer setup would also work with XP but I need clarification please. I note the new appliance type print server boxes (wireless) use IPP.

FILE SHARING:
I'm guessing, with my dual booting, I might as well use the file sharing via samba/smb and leave Linux native networking off. What do you think? What's up with the Zeroconf thing? Advantages?

---

### Post by Neobuntu on 2007-03-02
Thank you.

Please add any other good advice related to this.

---

