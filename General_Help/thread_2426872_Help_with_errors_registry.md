---
title: "Help with errors registry"
date: 2019-09-14
forum: General Help
---

### Post by shinusagi on 2019-09-14
Hello, before starting I want to clarify I am new to Ubuntu but I did already many things with the OS in order to tweak Ubuntu 18.04.3 LTS as I liked (installing some extensions)
I am getting 1 annoying error and there are 2 things I can't do

First of all, every time I enter Ubuntu I get an alert message about an error and prompt if I want to inform it or cancel, I choose inform but nothing happens, also I have no idea what the error is since I don't recognize neither an effect or cause from it, so I decided to upload the **Error Logs **I get to ask for help for you people who may know way more than me.

> 18:24:49 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
18:24:43 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
18:24:38 gdm-session-wor: gkr-pam: unable to locate daemon control file
18:24:11 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0

_**Those are the "Important Errors" the log is showing me**_, so please if you need me to add information to detail anything you could need in order to help me I will gladly do it.

Installed as in a physical PC on SSD, nothing virtualized, the PC Specs are these:
> MOBO ASUS M5 A788L-M (USB3)
CPU AMD FX 6300 Vishera
RAM DDR3 x 8GB (2x4 GB)
VGA Integrated ATI Radeon&#8482; HD 3000 GPU

About the 2 things I can't do I am not sure if throwing them here or another post but I will let them below, again no super important or errors but mainly config issues.

- I can't install privative drivers, using an integrather video card from ATI (Still can't get used to say AMD), Ubuntu tells me in the software config that there is nothing to download, should I try to manually download and install them from the AMD website?

- I can't change the GDM Login Screen, followed few tutorials and the picture I chose never shows up, not sure what I could be doing wrong, I will paste the command I use to open the config file and then the code block I use
> sudo gedit /etc/alternatives/gdm3.css
sudo gedit /usr/share/gnome-shell/theme/Yaru/gnome-shell.css
Any of those to open the file, seems to be the same but one is a redirection from the other, then change the block to this:
> #lockDialogGroup {
  background: #2c001e url(file:///usr/share/backgrounds/Claymore4.png);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center; }
At some point I deleted all except the Background line, then deleted the colour before he URL... still nothing happens, the picture never shows up and even the text dialog to type the password looks wrong, so I am running out of ideas.

Well, sorry for bothering you people but like most new people (or part of it I want to asume) I read a lot, checked many things and tweaked Ubuntu without asking, all alone and being thankfull for the guides the community already made but I want to fix at least the errors without crewing the OS and all he tweaks I already made (wich are mainly enabling extensions, seting on the Arc Menu, the Dash to Panel, Dash to Dock, etc)

Thanks beforehand for even reading this, and I hope someone can help me please.

---

### Post by QIII on 2019-09-14
Are you running Ubuntu as a guest in a VM, or are you running VMs on Ubuntu as the host?

What is your hardware configuration?  What "extensions" have you added?

---

### Post by shinusagi on 2019-09-14
I added in the first post the PC Specs, about the extensions basically those I typed in that post as well but I will list all of them here just in case:

- Gnome-Tweaks (did from Firefox as most guides explain), then from it:
Arc Menu
Dash to Dock
Dash to Panel
Desktop Icons
Extensions
Gno-Menu (Alternatedwith Arc Menu, still trying to figure wich one is better for me)
Removable Drive Menu
Transparent Gnome Panel

Basically the pack of stuf wich you can use from Tweaks and most people advice to install, I tried as well to install other things wich failed and then removed some repos like Plymouth Customizer and things like that. Anyway I can't think of something related to Plymouth since everything referent to Grub2 and Plymouth/Splash is working as a charm and the error I get is after I log in, even after few minutes, like... log in, do nothing, wait, error message pops up. Maybe the error log has nothing to do with it but I don't know and I would like to fix anyway whatever is wrong at this point.

---

