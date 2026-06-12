---
title: "Email, Evolution and GroupWise"
date: 2007-06-29
forum: General Help
---

### Post by green_earth on 2007-06-29
I'm trying to do a couple of things with regard to email in my now ubuntu laptop. I've configured evolution to work with my gmail account, and it works good. However the help system is non-existent in my install for some reason. Is there an easy way to get that to work? Selecting help in the menu or pressing F1 yields...nothing!

Also, I've not been able to install the Novell GroupWise Client for my work email. I have access to version 6.54 for linux. It is a tar.gz file, and I cannot get it to install, even in superuser mode. In the help portion of the GroupWise for linux documentation, it says its for Novell's (suse) linux or fedora core. But its also around one to two years old it looks like. Has anyone successfully installed it? Any tips?

I'm a total newbie, but am sure enjoying ubuntu. I've literally only played with Linux a couple of other times for a combined total of hours - but this I'm actually using. It feels good to kick MS to the curb, at least on my laptop!

Thanks for your input -

---

### Post by ralyon on 2007-07-12
I got mine working without much trouble the other day. A couple questions I have first:

1. Are the windows clients running 6.5? (Need to be running the same client versions server.)
2. Have you extracted the files from the file you downloaded? (Right click, extract here is easiest.)
3. Do you have the server IP addresses and port #? (On a win machine open the client and if it only asks for a password hit cancel and it will give you the option to enter a username and should have the server info here.)

If yes to all these question then in the folder you extracted go into the client and linux folder. There will be a deb file in there, open it and select install on the GDebi window. It may fail on the configuration, but the files will get installed and you can find the executable at /opt/novell/groupwise/client/bin/groupwise. Create a link and you should be good to go. :D

---

