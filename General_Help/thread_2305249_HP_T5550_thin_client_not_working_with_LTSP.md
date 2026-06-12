---
title: "HP T5550 thin client not working with LTSP"
date: 2015-12-04
forum: General Help
---

### Post by ivanpop on 2015-12-04
[COLOR=#111111][FONT=Ubuntu]I have Ubuntu 14.04 64-bit with LTSP installed, I'm connecting 5 computers to it and it's been working like that for about a year with no problems. I found an HP T5550 and I decided to use it in my network, but it can't seem to load Ubuntu. During booting I get the following message:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]longhaul: Option "enable" not set. Aborting. hda-intel 0000:00:01.1: no codecs found![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]and after that the screen goes black. Can the thin client be incompatible? I see it's using some VIA processor so maybe that's the problem. Regardless of that the thin client is working fine. I can connect with RDP to Windows and use it no problem, but I really want to boot from the LTSP.[/FONT][/COLOR]

---

### Post by newbie-user on 2015-12-04
If I remember correctly, there was a requirement for LTSP in a previous release (10.04, I think) that required the thin client CPU to support cmov and some other CPU flag, which the VIA processors didn't support. I had a bunch of T5135s that I couldn't use anymore because they didn't have the cmov flag. That might be what you're running into.

---

### Post by ivanpop on 2015-12-08
I guess that's the problem. So can I boot some live linux distribution on it? Lubuntu doesn't boot, obviously.
A browser and LibreOffice is everything I'm looking for.

---

### Post by newbie-user on 2015-12-08
I'm not sure using a current live distro would work, as newer kernels require the cpu to have the cmov flag. The only thing I can think of is trying to use 10.04 as LTSP and see if you can install more current versions of the browser and LibreOffice.

---

### Post by ivanpop on 2015-12-09
Using 10.04 as LTSP means that I will have to reinstall the currently running 14.04 LTSP server just for this client and this isn't an option. Maybe I can use some old live distro and boot the client from usb? I will have a browser, office and I will access the LTSP's files using shared folders.

---

### Post by ramesh24 on 2016-03-05
Hi, HP T5550 thin client comes with low graphic capability. Add the following lines into your lts.conf file at /var/lib/tftpboot/ltsp/i386 or amd64 (depends upon your client image).
[type mac address of your HP T5550 thin clietn]
 LDM_DIRECTX=true
 X_COLOUR_DEPTH=16
 XSERVER=vesa

# Disable video acceleration
 X_OPTION_01="\"NoAccel\""
 X_OPTION_02="\"DRI\"\"off\""

then test with HP T5550 thin client.

---

