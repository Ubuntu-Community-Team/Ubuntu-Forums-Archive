---
title: "Unable to change default printer settings using UI (found workaround but not solved)"
date: 2019-01-04
forum: General Help
---

### Post by mikeymikec on 2019-01-04
Lubuntu 18.04 LTS 64-bit
Printer: Epson WF-3520, Epson's recommended driver installed in the way they recommend.

If I go into [http://localhost:631](http://localhost:631) or System Tools > Printers > WF-3520 > Properties > Printer Options, it has the print quality option set to 'Standard'.  However, if I go to print from literally any app (let's take leafpad for example, but Thunderbird, Firefox and LibreOffice all exhibit the same issue), the print quality option is set to 'High' by default.

I made some headway by modifying .cups/lpoptions, which I found about from here:
[https://ubuntuforums.org/showthread.php?t=1893247&p=11526540#post11526540](https://ubuntuforums.org/showthread.php?t=1893247&p=11526540#post11526540) 
Which allows me to change the settings that any app then immediately picks up on.

What I find puzzling though is that if I delete that file, System tools > Printers and localhost:631 is entirely unaffected, and changing settings via either interface apparently does not do anything to that file, and then changing options via localhost:631 or through system tools works fine (ie. all apps can see the changes being made).

---

