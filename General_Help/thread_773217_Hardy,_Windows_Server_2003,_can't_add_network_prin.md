---
title: "Hardy, Windows Server 2003, can't add network printer"
date: 2008-04-28
forum: General Help
---

### Post by dartmusic on 2008-04-28
I'm running Hardy on a Thinkpad R31, I've been able to get it authenticated on our Windows server and was able to set up sudoers access.  

But, when I try to add a printer, I get all the way through the process (which, by the way, seems to work smoothly), but I get stopped every time when the system asks for my password.  I enter it, the same password I use to login, the same password I use for sudo, etc., but it continually asks over and over and never finishes adding the printer.

I edited the sudoers file (with visudo) to add the line %SERVERNAME\\domain^admins ALL(ALL) = ALL or whatever the syntax is.  It's correct as far as I can tell, since I couldn't do anything with sudo before I added the line.  And, obviously, I have domain admin privileges.

Anything I'm missing?  I've scoured these forums and googled, etc., but no dice.

Thanks!

---

