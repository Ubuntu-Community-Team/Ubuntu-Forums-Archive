---
title: "Printing To Network Printer"
date: 2008-01-18
forum: General Help
---

### Post by norwestdata on 2008-01-18
Good Morning Everyone!

I am running Ubuntu 7.10 and I am trying to setup my network printer.  The printer I am trying to use is an HP Photosmart D7160 and it's attached via USB to a Windows XP Home computer on my network.

I am having some difficulty getting it to work on the Ubuntu system.  Do I need to have Samba server running on the Ubuntu system for this to work?  I am familiar with Samba and I am able to see the Windows XP computer and Printer on the Network.  But when I try to print a test page it does not print.  

I've searched for specific documentation on this and have tried several different ways to set this up but with no luck.

Can someone with a little more experience than me assist me with getting this working.  I've also noticed that when I use the printer setup wizard, when it asks me to select my printer. It does not give me an option for a HP Photosmart D7160.  The closest one I find is the D7100 series.  Shouldn't this work?  

Any help would be appreciated.  I don't think this will take very long to setup with the right help.

Thanks

:)

---

### Post by patrickaupperle on 2008-01-18
I am having a similar problem. I have a psc 1400 series connected to a win xp machine. when I try to print to it, it does not print. If I check the printer on my win xp machine it sees the document waiting to be printed. but it does not print.

---

### Post by norwestdata on 2008-01-18
> **patrickaupperle said:**
> I am having a similar problem. I have a psc 1400 series connected to a win xp machine. when I try to print to it, it does not print. If I check the printer on my win xp machine it sees the document waiting to be printed. but it does not print.

I just tried to set it up again and I can see both the computer and the printer in the drop down in the printer setup wizard.  When I select the printer it fills in the appropriate field with the smb:// URL to the printer.   Then I click on Print Test Page and it just tells me the job was submitted but still no print.  I did a netstat to check and see if Samba is up and it does show it running, I can also see all computers on my network in the Network browser.  All of them run Windows XP Home except mine.   I've checked and the printer is also set to shared on the Windows XP machine that it is attached to.

---

### Post by AsoSako on 2008-01-18
Can anyone please help out with this?  I am having the exact same problem here with an HP Officejet 5510.

---

### Post by norwestdata on 2008-01-19
any help at all would be great?

---

### Post by Dirigo on 2008-03-15
I am having this same problem as well.  Does anone have any ideas?

---

### Post by Kerry_W on 2008-03-15
try going to the windows machine and make sure that printer spooling is turned on

---

### Post by Dirigo on 2008-03-15
Yes.  Printer spooling is checked.

---

