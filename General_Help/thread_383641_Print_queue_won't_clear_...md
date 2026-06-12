---
title: "Print queue won't clear .."
date: 2007-03-13
forum: General Help
---

### Post by ebike on 2007-03-13
Hi All,

Ever since changing from Gentoo to Ubuntu (which was a great move by the way), I have had trouble printing. I am network printing to a HP 7150 printer via an Edimax print server.

I print to the server using the IPP protocol with the following URL:


> IPP://192.168.0.170:631/lpt1
I can print ok to the printer and the page is ejected, but the print queue is not cleared. I have to manually clear that print job from the queue to print the next item in the queue.

Can anyone help with this one. I have tried restarting cups, the print server etc ... but no joy.
I am using the default /etc/cups/cupsd.conf file.

Thanks.

---

### Post by ebike on 2007-03-30
bump!

---

### Post by acormack on 2007-03-30
Ebike

This sounds very odd.  Have you tried printing to other printers?  Does that work?

If you print to the printer direct via parallel/USB does that work?

I have never used an Edimax print server. What is the exact model number?

Alec

---

### Post by ebike on 2007-03-30
Hi, I can't make out a model number, but is has worked ok when this laptop was running gentoo. It has only been a problem under Ubuntu ... maybe a different version of cups? I have seen similar problems reported in the forum .. but no answers.

---

### Post by ElaneFreuyh on 2008-04-24
me too
this has been a royal pain in the ****- i just cant nail the problem or get it occur reliably.

Im using a HP laserjet 2100 attatched to an ADSL wireless router.

Every time I try to write the problem down in a forum post I realise that I can't describe it clearly enough to be of use.

are there any decent printer managemnt tools for ubuntu - i can't find anything under the applications menu that tells me about my printer.

:mad::mad:

---

### Post by ebike on 2008-04-24
I gave up on this issue with the Edimax print server, I ended up attaching the printer to another computer on my network, running the cups server on that printer by turning on sharing in the printer setup gui. It means I have to have that computer turned on to print from elsewhere in my network, not ideal, but manageable.....:confused:

---

