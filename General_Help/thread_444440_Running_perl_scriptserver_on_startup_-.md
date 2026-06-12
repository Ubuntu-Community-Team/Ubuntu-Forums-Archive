---
title: "Running perl script/server on startup -"
date: 2007-05-15
forum: General Help
---

### Post by jgrimm on 2007-05-15
Hokay folks - for today's /different/ question:

*grins*

I'm a not-too-shabby perl programmer who's recently made the big leap over to Ubuntu - for the last six, seven months or so, I've become firmly ingrained in this OS - absolutely fabulous.

However - 

I've written a little perl module.  Nothing special - a little server that sits and listens for localhost connections on an internal port.  There is absolutely /nothing/ exciting or frightening about it.  Works great, in fact, does exactly what it was meant to do.

What I /want/ to do, though, is have this script start as part of the startup processes for this linux box.  The trouble comes in that, when started as a user, when I log the user off, the process dies - not unexpected for a user-level process.  This process, though, just needs to sit in the background and run, indpenant of whether I'm logged in to this machine or not.

Being unfamiliar with startup scripting in linux...

... how do I get this script to run on boot, rather than on login?  I seem to remember there being a linux equivalent to autoexec.bat from the old DOS days, but the only thing I can find that isn't making me twitch (like initppd is - ) is .bashrc... which only, of course, fires on login.

How can I set this up?  Utterly lost. :)   Thanks folks, in advance!

Grimm

---

### Post by MontanaMax on 2007-05-15
I think the /etc/init.d is the place to put the script and link, but I never tried it myself - I decided to go the .bashrc route for what I needed.

There is a good howto here:

[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)

it also has links to several other discussion threads for more info.

Good luck!

---

