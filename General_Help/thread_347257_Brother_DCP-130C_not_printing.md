---
title: "Brother DCP-130C not printing"
date: 2007-01-27
forum: General Help
---

### Post by pseudo_nz on 2007-01-27
After finally giving up on my canon printer, I got a brother, which got full marks on linuxprinting.org.

I downloaded the drivers and followed the instructions on the brother page linked to from linuxprinting, although the first time I tried installing the LPR part of it I got an error message saying a folder couldn't be created because the parent folder didn't exist.  I created the parent folder and tried again and the install went smoothly.

Both the localhost page that came with the software and the KDE system setting page are showing the new printer, but when I sent something to print, it hung on processing.  When I sent a testpage from the localhost page, it told me that the printer wasn't connected.

Everything is plugged in and set up correctly, as far as I can see.  Has anyone dealt with anything like this?

---

### Post by Soarer on 2007-01-27
I use Gnome, not KDE, so there may be differences. I would not download the driver though. In CUPS, most of the Brother printers I clicked already had the driver loaded. I have installed a few printer with CUPS and the installed drivers and they... just worked.

Maybe try CUPS rather than LPR?

---

### Post by pseudo_nz on 2007-01-30
Thanks for the reply, sorry it took me so long to get back to this thread.

I installed the LPR drivers and then a CUPS wraparound program, as per the instructions on the driver page [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html") and thought when it didn't work that it must have had something to do with the fact I'd created a folder with nothing in it during the installation process.

A bit more digging after my impatient post and I found a FAQ that fixed the problem [here]("http://solutions.brother.com/linux/sol/printer/linux/linux_faq-2.html#50")

I was trying to manage the printer through the Settings panel, when I should have been using the localhost command in my web browser.

I also found the answer to another problem in the same FAQ (the top 2cm of my pages were being missed), and it was just as easily fixed.

Brother is certainly a lot more friendly towards linux users than Canon!

---

