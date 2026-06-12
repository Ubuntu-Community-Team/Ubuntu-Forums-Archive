---
title: "unable to swicth on wifi"
date: 2008-05-11
forum: General Help
---

### Post by arun2312 on 2008-05-11
i have a fujitsu siemens laptop v3505

i need to intall this (link below)software to b able to switch on my wifi on windows...
[http://support.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=27C292FA-8305-47F9-B0B2-030FB266CFA9&OSID=665F4A20-6E31-43C3-82C2-D98CE773007C&Status=True&Component=Application%20-%20Tools%20and%20Utility](http://support.fujitsu-siemens.com/Download/ShowDescription.asp?SoftwareGUID=27C292FA-8305-47F9-B0B2-030FB266CFA9&OSID=665F4A20-6E31-43C3-82C2-D98CE773007C&Status=True&Component=Application%20-%20Tools%20and%20Utility)

but wat can i do to use my wifi on ubuntu?

p.s. ubuntu does recognise my wifi card(intel) the problem is am unable to switch it on
[IMG]http://i27.tinypic.com/2ur750k.jpg[/IMG]
[IMG]http://i27.tinypic.com/kafb79.jpg[/IMG]
how can i solve this problem? help plzzz:(

---

### Post by ibuclaw on 2008-05-11
First, open up a terminal:

What output do you get when you enter these three commands?

1)
```
iwconfig
```
2)
```
sudo lshw -C network
```
3)
```
lspci
```

If you can't cannot connect via ethernet cable, then save the output to a file, transport it to windows and post it when you come back online.

Regards
Iain

---

