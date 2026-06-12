---
title: "GDM login problem"
date: 2008-01-15
forum: General Help
---

### Post by tech.roberts on 2008-01-15
Using Gutsy with GDM login and all has been fine.  Yesterday I used the GUI configuration tool in System/Admin to reconfigure GDM to show the face browser.  I logged out and logged in as different user several times and this was working great.

 I shut down the computer and when I restarted it I now do not see the GDM login screen.  At about the same time I would expect a GDM login screen l I get a xdmcp login dialog screen.  Asks  me to ID a server, etc.   Not what I want.  I don't seem to be able to log in to X locally through GDM.  I restored my backup of gdm.conf but no change in the behavior.  I also restored the "factory default" copy of gdm.conf with no change to problem.

I can get to an X session by killing GDM then running startx from the command line. 

Any ideas?  Maybe gdm.conf is not where I should be looking.

---

### Post by jeffus_il on 2008-01-15
Run the Gdm utility again, and remove the XDMCP stuff.

---

### Post by AJB2K3 on 2008-01-15
I had this happen (without xdmcp stuff) after an update and required a reinstall of 7.10

---

### Post by jeffus_il on 2008-01-15
I wouldn't reinstall, it's like killing the patient to cure the illness. try looking at error logs, etc. and post more detail here.

---

### Post by tech.roberts on 2008-01-15
Thanks to jeffus_il.  Your suggestion to review the error logs led me to the solution. 

went to /var/log/gdm and looked at logs.  Error logs whowed me that the problem was with gdmchooser, specifically that the service was not known.  I returned to gdm.conf and checked for gdmchooser.  There was an entry but it was commented out and thus led me to believe that it was not the problem.   So I looked back in the /etc/gdm directory for other conf files and found, among others,  gdm.conf-custom.  I learned that this file is where the gdmsetup tool puts the changes you make.  I found a chooser=true line and deleted it.  This did not completely solve the problem as I was still unable to boot to a gdm login.  I got no login of any kind at this point.  So I went back into gdm.conf.custom and deleted all entries that were not bracketed headers.  This  solved the problem.  I boot to a gdm login screen now.

---

