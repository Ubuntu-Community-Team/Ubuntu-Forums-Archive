---
title: "Wireless networking setup, Netgear WG311"
date: 2008-07-02
forum: General Help
---

### Post by Quotidian Minutia on 2008-07-02
I'm trying to set up a wireless network, and don't know what to do next.  I've been using a Netgear Wireless-G Modem Router DG834G successfully for a wired connection, but I now want to use my Netgear Wireless-G PCI Adapter WG311 for a wireless connection.  I've installed the Adapter, and done the whole ndiswrapper thing, seemingly succesfully. When I go to System>Administration>Windows Wireless Drivers, I've got the wg311v3 driver, and it says "Hardware present: yes".  But when I "edit wireless networks" through Network Manager, there's nothing there.  And when I go to System>Administration>Network there's only "Wired connection" and "Point to point connection" listed - ie no wireless connection.  I'm running Hardy.

What am I missing?

---

### Post by Gunman1982 on 2008-07-02
I don't have the card but maybe you can try the madwifi driver module instead of ndiswrapper. Check which version of the WG311 you have, you can find that information by opening a console and executing 'lspci | grep Ethernet' (without the '' of course).

---

### Post by sofasurfer on 2008-07-22
I have the axact same problem as Quotidian Minutia. I have WG311v.3.

---

