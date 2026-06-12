---
title: "Gnome-RDP Problem"
date: 2007-04-28
forum: General Help
---

### Post by LanceM on 2007-04-28
I am trying to connect to a Windows 2000 server. Using Gnome-RDP for my remote connection I get the following error when I try to login:

X Error of failed request:  BadAtom (invalid Atom parameter)
  Major opcode of failed request:  23 (X_GetSelectionOwner)
  Atom id in failed request:  0x0
  Serial number of failed request:  3437
  Current serial number in output stream:  3437

I do get to the login screen when I connect but I get this error when I try to login.

Any idea what's going on?

Thanks

---

### Post by bingnet on 2007-12-05
Same here, only:

Serial number of failed request: 56
Current serial number in output stream: 56

Also a W2k server. Same result with tsclient and rdesktop on Gutsy - Gnome - Compiz.

---

### Post by elicoten on 2008-01-10
Same problem with a Windows xp server but error message only appears using the RDP [not v5] protocol. When I try 24-bit colour I get a different error message with both RDP and RDPv5 protocol about server not supporting 24bit falling back to 16bit.

Using Ubuntu Gusty Gnome.

---

### Post by jschaab on 2008-03-25
I'm having the same issue. tlclient launches, and connect to the server, displays the login screen, but when I try to actually login I get this error, and the remote desktop window just displays a blue screen with nothing on it. eventually it resets and tries to connect again, but the result is always the same.

---

### Post by LanceM on 2008-03-26
I ended up reinstalling Ubuntu and now it works. I wish I had found a better solution that than.

---

### Post by elicoten on 2008-03-26
For the time being I've been using the Microsoft Remote Desktop client available from the Microsoft Website with Wine. However, there are at least three versions of the Remote Desktop client on the Microsoft Website, this is the one I am using. [http://www.microsoft.com/downloads/details.aspx?familyid=80111F21-D48D-426E-96C2-08AA2BD23A49&displaylang=en](http://www.microsoft.com/downloads/details.aspx?familyid=80111F21-D48D-426E-96C2-08AA2BD23A49&displaylang=en)

If anyone has tried the others and knows if they work better then reply to this thread, but with the latest version of Wine that one works reasonably well. I would point out that in Wine you have to set the winscardsvr dll override for mstsc.exe if you want to use the local resources options, otherwise it crashes. But overall it seems to work fine.

---

### Post by LanceM on 2008-03-26
I didn't think of that. Probably would have solved my problem.

---

