---
title: "No Wireless after custom kernel"
date: 2005-10-21
forum: General Help
---

### Post by kingsidy on 2005-10-21
I recently compiled the kernel 2.6.13.4 from kernel.org, everything works fine except for the fact that i do not see my wireless interface ETH1. So no wireless. 
Does anybody know how to reinstate the wireless back on my laptop (it is a Centrino), the wirelesscard is intel pro-wireless 2200 bg

---

### Post by Kyral on 2005-10-21
Was it supported in the kernel before you recompiled? (Ie, it "Just worked" without having to use MadWifi or NDiswrapper?)

---

### Post by kingsidy on 2005-10-21
eveything worked right out the box when i used the kernel propvided by ubuntu. I just wanted to try to compile one. so i went through the options but the eth1 interface is missing

---

### Post by Kyral on 2005-10-21
You probably forgot to compile in support for it in the kernel (Heck my kernel doesn't support my wireless right now because I forgot to compile it in)

Go back into the config and nail every option in the Wireless section. (Brute Force Method)

Or find out what kernel module the Ubuntu Kernel loads to get your wireless working and then compile that into your custom kernel

---

### Post by kingsidy on 2005-10-21
Ok i will try that again. i think that the default kernerl loads the madwifi drivers. i'll try compiling it again. Another question i have is that whenever i compile the kernel it takes away about 400mb of space. Now it adds up to a little over 1 gig (missing). Do you have any clue where the space went?

---

### Post by Kyral on 2005-10-22
It prolly all the files left behind in /usr/src/linux

cd there and try "make mrproper" and see what happens

---

### Post by ferdy on 2005-10-22
i have the same problem, the original Kernel come with linux-restricted-modules.
The modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcpcmcia, fcpcmcia_cs, fcusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

But i dont know, how integrate to the new kernel.

ferdy

---

### Post by TimelessRogue on 2005-10-22
I've got the same problem after a kernel upgrade to 2.6.12 ... eth1 and wireless worked from the get go with the Beezy pre-release but was immediately not available after the upgrade.  I went so far as to "downgrade" back the previous setup and eth1/wireless worked fine ... upgrading again resulted in loss of eth1/wireless.  Still trying to work things out.

By the way, this was with a Linksys WPC11 Ver 3 which worked "out of the box" so to speak with Hoary and the pre-release of Beezy.

Update:  After pondering this problem over a couple of double lattes, I sort of was able to recall exactly when it occurred and what had taken place immediately prior.  Since all was well after installing the Breezy pre-release and was still okay after upgrading to the final release, I remembered having used both Synaptic Package Manager and Update Manager several times after the first Breezy install.  It was immediately after one of these updates that I lost my wireless/eth1 connection.

In support of this theory, I am currently booted up with the Live CD and all is well with networking both wireless via eth1 and DSL via eth0 ... dial-up I'm not concerned with at this point.  Printer and all else seem to be totally okay too.

Now, I think I need to reinstall the final release from CD and then carefully monitor things as I update packages ... and definitely disable any automatic update feature!

So ... I'm off to it and will update this post with the results.

---

### Post by somuchfortheafter on 2005-10-22
you will need to recompile the drivers for this kernel, check out the package below
it may work without needing to recompile drivers :
[http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ipw2200-source](http://packages.debian.org/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=ipw2200-source)

if that doesnt work try this:
[http://ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+latest+driver](http://ubuntuforums.org/showthread.php?t=26623&highlight=ipw2200+latest+driver)
just stop when you get to wpa supplicant.

---

### Post by kingsidy on 2005-10-22
thanks for the repiles i will try somuchfortheafter's advice and see if that works.

---

### Post by kingsidy on 2005-10-25
i followed the how to and reinstalled the driver but no luck

---

