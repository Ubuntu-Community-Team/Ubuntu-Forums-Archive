---
title: "Very slow printing on DYMO LabelWriter 450"
date: 2020-03-23
forum: General Help
---

### Post by timafh on 2020-03-23
[COLOR=#242729][FONT=Arial][FONT=inherit]I have a problem with label printing on my Ubuntu 19.10 workstation and on my Raspian Buster target.

I know that this is the Ubuntu forum - since I have the problem on both platforms, I assume it will be a general problem.
[/FONT]
[FONT=inherit]When I start a print on a Dymo LabelWriter 450 Turbo with CUPS and drivers from [matthiasbock/dymo-cups-drivers]("https://github.com/matthiasbock/dymo-cups-drivers") it takes about 6-7 seconds until the print starts.
The printing itself is then very slow. At the end of printing, the printer pauses for about 1-2 seconds and then advances the last piece of the label.
[/FONT]
[FONT=inherit]System is a Raspberry Pi 4 with Raspian - but I have the exact same problem on a current Ubuntu on my workstation.
[/FONT]
[FONT=inherit]The quirks file from [8-10 Sec delay between jobs DYMO 450 Turbo USB]("https://github.com/apple/cups/issues/5521") is integrated and doesn't help. Setting usb no-reattach doesn't help either.
[/FONT]
[FONT=inherit]Does anyone know about this problem or have an idea where I could tackle this problem?
[/FONT]
[FONT=inherit]I would be happy about every idea and every suggestion![/FONT]
[/FONT][/COLOR]

---

