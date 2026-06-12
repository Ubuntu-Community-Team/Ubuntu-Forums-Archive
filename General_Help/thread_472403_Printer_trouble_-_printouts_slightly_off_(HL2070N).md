---
title: "Printer trouble - printouts slightly off (HL2070N)"
date: 2007-06-13
forum: General Help
---

### Post by namityadav on 2007-06-13
I have a brother 2070N that I use with my Ubuntu laptop. This setup was working fine few months back. But recently all the printouts are slightly off on the Y axis. There is a slight empty space on top of the paper and the bottom gets cut off slightly.

My first reaction was, "I am sending A4 print requests on a US Letter paper". But I've checked printer-settings (gnome-cups-manager, using sudo) and have checked /etc/papersize. Everywhere it's set to Letter (Correctly). I made the printer print it's own configurations .. and it says that it is set to Letter too. Moreover the printer configuration printouts were not off.

Any suggestions?

---

### Post by dasunst3r on 2007-06-13
Here are a few documents to get you on your way to solving the problem:
[http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2070N)

You can get the alignmargins script and .ps file here: [http://www.linuxprinting.org/download/printing/](http://www.linuxprinting.org/download/printing/)

---

### Post by namityadav on 2007-06-13
Thanks a lot for the links. I checked the /usr/local/Brother/inf/brHL2070Nrc file, and it was set to A4. Setting it to Letter.

---

