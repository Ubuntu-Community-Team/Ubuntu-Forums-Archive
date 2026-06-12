---
title: "Graphical SCP Client?"
date: 2006-09-15
forum: General Help
---

### Post by Demio on 2006-09-15
Hello,

I'm in dire need of a graphical SCP client like WinSCP. Does anyone know one?

Nautilus and gFTP only support sftp and I don't use that :(

---

### Post by David Corrales on 2006-09-15
I found this link  which might help you [http://www.brandonhutchinson.com/Using_gFTP_with_ssh_sftp.html](http://www.brandonhutchinson.com/Using_gFTP_with_ssh_sftp.html)
Haven't tried it myself though :)

---

### Post by NetworkGuy on 2006-09-15
SECPanel is in the repositories.  It states it is a graphical front-end for SSH and SCP

---

### Post by palmettotiger on 2006-11-12
gFTP works rather well.  Easily found it in the packet manager program.  Installed and ran quite easily.  Took all of 45 seconds to go from command line ftping to gui-style.

Tried locating SECPanel...spent five minutes, couldn't find it.

So...recommend using the gFTP client.  Hope this helps.

---

### Post by mancho42 on 2007-02-26
For FTP I have been using the excellent FileZilla in (ugh) Windoze for a few years and now I see it is available in a linux version in the repositories :) 

I also use WinSCP3 in said Windoze boxes and would like to use a Linux version too so thank you for this thread :)

---

### Post by pdub on 2008-01-15
This is an old thread but I thought I would post a reply anyway.

If you click on the desktop and hit CTRL+L

then type

ssh://ipaddress_or_hostname

You should be prompted to authenticate.

Once authenticated, a nautilus browser will popup displaying the remote file system.

---

### Post by SylentBobNJ on 2008-01-22
Just for informational purposes, the above does not seem to work in Kubuntu Gutsy with Dolphin.

-SB

---

### Post by pdub on 2008-01-25
Sorry for not clarifying, I am running GNOME with Nautilus.

---

### Post by dr.akir on 2008-07-14
My thing is that I need to have a client where it is possible to use ssh keys (with passwords!) for authorization.

In the Windows-world WinSCP solves that like a charm!
Is any of the suggested solutions above capable of doing that?

Regards,

Rikard

---

### Post by dotslash on 2008-07-22
Pdub:

That was by far the best response to this question.  I found limitations using secpanel and some other tools out there just don't compare to how easy it is to use the internal browser.  I mean after all if a machine has ssh running, sftp should be no problem (assuming admins don't disable it).  Thanks again Pdub.

dot

---

### Post by scorp123 on 2008-07-22
> **SylentBobNJ said:**
> Just for informational purposes, the above does not seem to work in Kubuntu Gutsy with Dolphin.  In the KDE file manager you'd use fish://youruser@remotehost  ... works the same way.

---

