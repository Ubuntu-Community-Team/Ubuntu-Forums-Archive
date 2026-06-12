---
title: "Drivers for my network card."
date: 2008-01-31
forum: General Help
---

### Post by Rossg on 2008-01-31
Hey, I'm completely new to Linux and I'm in need of some serious help.I just installed a network card on my computer but all the drivers that came with it are for Windows.Now, I know I can use NdisWrapper to use the drivers (right?) but I don't know how.Like I said, I have pretty much no idea what I'm doing so try not to overwhelm me with a bunch of Linux stuff I'm not going to understand (or at least explain it)So anyway I figured this would be the best place to come for help and any help is really appreciated.

---

### Post by p_quarles on 2008-01-31
What make and model of card is it?

---

### Post by Rossg on 2008-01-31
Its a D-Link DWL-G510.

---

### Post by p_quarles on 2008-01-31
According to [this](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink), that card should work with a normal kernel module, and you shouldn't need to use ndiswrapper. Have you tried working with it yet?

If it doesn't work, you should only need to install or reconfigure the restricted drivers manager. If it's installed, you can configure it by using the "Restricted Drivers Manager" in the administration menu.

---

### Post by Rossg on 2008-01-31
When I open up the restricted drivers menu the only thing I see is 'Atheros Hardware Access Layer'. Where would I go from there?

---

### Post by mbrush on 2008-02-01
I don't know if it's relelvent, but my laptop has an Atheros chipset according to the command 'lspci'

There is something called 'madwifi' for my card, but it never compiled on my computer so I installed ndiswrapper and the gui for that and you just load the windows driver off the cd or whatever.

After that it should show up in the Network configuration program you use.

I'd prefer to be using the actual linux driver, but I'm too lazy to try again since ndiswrapper works fine.

There are a few other packages i installed on my laptop, now the "Roaming" works, so if I unplug the network cable it switches to my wifi network automatically.

Here are the packages I've installed to make it work:

ndiswrapper-common
ndiswrapper-utils-1.9
ndisgtk
wpasupplicant
network-manager-gnome
network-manager

All the packages should be available in Synaptic package manager

There might have been some config file changes too, can't remember.  I found a few useful howtos on google.


Good Luck

---

