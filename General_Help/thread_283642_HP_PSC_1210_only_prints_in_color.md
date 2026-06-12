---
title: "HP PSC 1210 only prints in color"
date: 2006-10-24
forum: General Help
---

### Post by bobonthenet on 2006-10-24
I am having a problem with my HP PSC 1210 printer.  When I go to print plain black text it prints it out using the color cartridge instead of the black cartridge.  I've tried changing the settings for the printer to get it to print in black and white but nothing I have tried in "system>administration>printing" seems to work.  I know when I first started using ubuntu the printer worked fine and I don't print all that often.  Lately because of school I have been needing to print a lot.  I only just noticed the problem but it may have been caused by something that happened several months ago since my last print attempt.

---

### Post by ahaslam on 2006-10-24
Ensure that 'hplip' is installed & enabled at boot.

Use the toolbox (/usr/bin/**hp-toolbox**) to adjust your settings.

To add yourself as a user, open a terminal and enter:
[B]sudo adduser cupsys shadow
sudo /etc/init.d/cupsys restart[/B]


Tony.

---

### Post by bobonthenet on 2006-10-24
OK there must be something that I do not understand here.  When I try to configure the printer using /usr/bin/hp-toolbox I get an error message with just about everything I click.

---

### Post by bobonthenet on 2006-10-25
OK it started to work after I restarted my computer.  Not sure what was wrong there but it fixed itself upon restarting.  Thank you so much for this fix.  Printing at school is very expensive, of course I am out of color ink now.

---

