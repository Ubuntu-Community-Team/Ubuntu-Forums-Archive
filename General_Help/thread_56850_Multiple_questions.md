---
title: "Multiple questions"
date: 2005-08-14
forum: General Help
---

### Post by i30i3i3y on 2005-08-14
I've got a few small niggles with ubuntu. They're not problems so I've classed them as questions :-D. Rather than make a thread for each one I'll just bullet point em here.

1) When I boot my sound doesnt work. I need to open the sound control panel and mute then unmute the master volume for me to get sound. (ESS Allegro PCI Alsa Mixer)

2) My fstab has entries to automount  my windows partitions. Sometimes it shows two shortcuts to the mounted filesystems on my desktop and sometimes it doesn't. what gives?

3) I have a HP Omnibook XE3 and have downloaded a perl script to enable the one touch buttons. I need to run '/home/bobby/perl/omke.pl -k 1' as root. Is there anyway I can have the system do this automatically at startup? Itried using the System>Preferences>Session>Startup thing but that doesn't work.

Ubuntu has made me give up windows, I never thought that day would come!

---

### Post by jasmuz on 2005-08-14
Hello there; some answers to your questions:

1- To save your Alsa settings, after you unmute, close and type in the terminal sudo alsactl

2-Yes, Ubuntu sometimes loads my NTFS partition to my desk with an icon and sometime it dosent, dont know why yet.

3-For that you would have to make a script to run at boot.

---

### Post by i30i3i3y on 2005-08-15
[QUOTE=jasmuz]Hello there; some answers to your questions:

1- To save your Alsa settings, after you unmute, close and type in the terminal sudo alsactl

2-Yes, Ubuntu sometimes loads my NTFS partition to my desk with an icon and sometime it dosent, dont know why yet.

3-For that you would have to make a script to run at boot.[/QUOTE]
 How would I go about writing a script that runs at boot?

---

### Post by jasmuz on 2005-08-16
Cant help you there, but try reading or asking around for basic bash scripting.

---

