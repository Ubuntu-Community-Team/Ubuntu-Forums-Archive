---
title: "A bunch of questions!"
date: 2007-06-21
forum: General Help
---

### Post by justino on 2007-06-21
Hi all,

I'm pretty new to linux (well I've played with it off and on, but never as a main os) and I've got a few questions about ubuntu and some little nuisances that I've discovered...

1.  Every time I connect to my wireless it asks me for the password and then asks me to create a keychain password... I would really rather just have it remember the password on it's own (read: without me actually having to lift a finger)...  Any suggestions?

2.  I'm actually dual booting with vista (probably part of the reason why I'm running two oses) and I was wondering if there was a way to automatically mount my ntfs windows partition.  I can do to the places menu, select computer, and double click on the volume and it does it for me (once I enter the password), but I would also like it to do this automatically.

3.  Lastly!  I've somehow screwed things up while playing around with beryl, and the virtual desktop settings...  The cube effect was annoying me , so I turned it off, and then turned off the virtual desktops (since I don't mind cluttering up one :)) but then the toolbars at the bottom and top of the screen started to flicker... then the computer locked... when I log in now it just gives me the desktop with the menu bars...

If I change the session to be the gnome failsafe it works fine, is there a way to copy this session's settings back into my normal one (and then I can start tinkering again).

Ha, anyone got any helpful tips ? :)

Thanks!

Justin

---

### Post by swisscow on 2007-06-21
As regards the key manager asking for a key everytime you start the wireless there is a fix somewhere on these forums (had a quick look but can#t find the link - sorry). It works fine but after a reinstall when the key manager asked for a password I just pressed return (i.e. left the password blank) and now no more problems!

If you want to go down this route you can delete your current key manager settings (again, a search on these forums will yield results) then when you fire up again, and it asks for a new password, you can just do what I did.

Don't know too much about any security implications for this but only I use my computer so I'm not that worried.

---

### Post by HermanAB on 2007-06-21
To automount the ntfs partition, you have to add a line to the /etc/fstab file.

See 'man fstab', 'man mount' and google.

Sorry, I cannot tell you exactly how off hand, I'll have to go and read up too and I have no use for that...

Cheers,

Herman

---

