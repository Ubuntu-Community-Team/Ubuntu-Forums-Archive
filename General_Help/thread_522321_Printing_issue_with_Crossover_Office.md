---
title: "Printing issue with Crossover Office"
date: 2007-08-10
forum: General Help
---

### Post by truckinharry on 2007-08-10
Heres the deal I have Ubuntu 7.04 with Crossover Office 6.06, Microsoft Office 2003, and Canon Pixma ip1800 printer. I can print with the CUPS driver in any linux native application but, when I try to print from Word it shows the ip1800 but wont print to it. Does anyone know what might be the issue and possibly how to resolve this.

---

### Post by orwellus on 2007-08-17
Try this.

Go into the Systems>Administration>Printing.

Right click on the icon that has your printer name on it. When the menu pops up, click "Mark as Default" 

That should place a green checkmark over your printer, and the printer should say "ready". Close out of printing, and try printing from one of your Crossover Office applications (like Microsoft Word for example).

---

### Post by cybergal on 2007-08-24
> **truckinharry said:**
> Heres the deal I have Ubuntu 7.04 with Crossover Office 6.06, Microsoft Office 2003, and Canon Pixma ip1800 printer. I can print with the CUPS driver in any linux native application but, when I try to print from Word it shows the ip1800 but wont print to it. Does anyone know what might be the issue and possibly how to resolve this.

A bit off-topic, I know, but a friend is trying to set up this printer for me in Ubuntu 6.06 LTS and there don't seem to be CUPS drivers specific to this model.  Would you post a link where you found it; it might be helpful.  TIA

---

### Post by croco44-MN on 2008-04-06
Hi all- I assume that you have solved your problem or given up by now, as your post was a while ago, but I had a similar problem just recently when setting up crossover office on a pre-release of Hardy Heron, so I though I would reply. All of my printers showed up in my crossover apps but nothing appeared to happen when I printed to them. There was astonishingly little help online about this so I thought I would just let everyone know what worked for me. It appears as though crossover uses the KDE printing system- and does not complain if you do not have it installed when you set up crossover (a bug in my opinion). You must install "kdeprint" from synaptic to get printing to work in crossover apps. Best of luck.

---

