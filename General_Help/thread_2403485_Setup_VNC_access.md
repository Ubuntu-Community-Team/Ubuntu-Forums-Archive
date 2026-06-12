---
title: "Setup VNC access"
date: 2018-10-12
forum: General Help
---

### Post by mrcheesedude on 2018-10-12
I am seeking to setup VNC access to a Lubuntu PC I have setup, but I am having trouble figuring it out.
I have been using Ubunutu mostly, and have been able to get VNC to work on that OS quite easily.
I have followed these instructions to try and get this working for Lubuntu: [https://wiki.ubuntu.com/Lubuntu/RemoteDesktop](https://wiki.ubuntu.com/Lubuntu/RemoteDesktop)
But when I run the command: vino-preferences
I get the error: command not found
Anything I look up from here is getting more and more complicated,so I think I am missing something easy that I am not aware of.
Seeking assistance to find out what I am doing wrong so that I may enable VNC access on Lubuntu.
I am not requiring to use encryption, or Windows RDP, just to access the Lubuntu desktop from another PC on the same LAN.
Any suggestions appreciated.
Thanks.

---

### Post by cmcanulty on 2018-10-12
I had that same issue with xubuntu after 18.04 upgrade. First install vino. Mine was removed on upgrade without any notice. Also even after installing vino, the command "vino-preferences" doesn't work. Here is an easy workaround. Install dconf-editor then open it and go to org-gnome-desktop-remote access and turn off encryption. There are also several other remote options you can set in dconf-editor. However until you install vino, the remote-access doesn't show in dconf-editor.

---

