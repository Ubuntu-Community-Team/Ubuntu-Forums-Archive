---
title: "Bootmenu entry missing after Boot Repair"
date: 2015-03-11
forum: General Help
---

### Post by mickeyG1 on 2015-03-11
[FONT=Arial][SIZE=2]Howdy, 

new here so: if i posted in the wrong place please be so kind as to redirect me to the appropriate place ;)

Problem: at the end of the online upgrade from my desktop version of Ubuntu 12.04 to Ubuntu 14.04LTS i was requested to reboot... pre bootmenu splash turned out 3 error msg and then after selecting Ubuntu 14.04 in my boot menu once agin 3x error msg followed by "press ENTER to continue.."
The entire boot process was extremely long ( over a minute and a half ) so the next day i decided to try Boot Repair. Popped a Ubuntu 12.10 Secure Mix live dvd in the box and started the included Boot Repair program.

Here the Boot-Info file BEFORE "repairing": [http://paste.ubuntu.com/10573814/](http://paste.ubuntu.com/10573814/)

After running the Boot Repair prog using the "recommended repair" options ( no user intervention ) i was no longer able to reboot to desktop Ubuntu 14.04 because the menu entry was gone...

Here the Boot-Info file AFTER "repairing": [http://paste.ubuntu.com/10573839/](http://paste.ubuntu.com/10573839/)

I would be truly thankful if somebody were nice enough to take a peek at these files and point me in the right direction, i've been searching round the net and can't seem to find what i'm looking for...

Thanks in advance,
mike[/SIZE][/FONT]

---

### Post by oldfred on 2015-03-11
It looks like you have both Ubuntu and Debian. And you reinstalled grub for the old Debian install in sda8 to the MBR, not the Ubuntu install? Not sure if you selected that in Boot-Repair or that just happened to be what it chose. With multiple installs best not to use any auto fix but use advanced mode and select install and select drive to install grub boot loader into.

It also looks like you have a separate /boot in sda5 for Ubuntu.
And Ubuntu  install is in sda7.

But you have Ubuntu's newer grub installed to partition boot sectors (PBR) not MBR.

Try using advanced mode and install Ubuntu's grub to MBR. Be sure to tick separate /boot.
If not you may have to use the full uninstall/reinstall of grub advanced option.

---

### Post by mickeyG1 on 2015-03-12
Thanks Oldfred, sorry i didnt reply in a timely fashion, but i had early shift and at some point a guys gotta sleep ;) Will try that. After i get some time off i will complete a more thorough report of exactly what happened. It appears to have been a combination of not actualising the third party package repos and installing, whereupon i promptly got served with the tex-common pckg install-fail. Furthermore i opted during installation for keeping the previously existing grub files as opposed to replacing them when asked... When i later tried the grub purge and reinstall, the tex-common error prohibited the reinstall. Thanks again for your answer, mike

---

