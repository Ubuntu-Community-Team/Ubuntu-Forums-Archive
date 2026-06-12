---
title: "How to uninstall Private Internet Access, a vpn"
date: 2016-02-13
forum: General Help
---

### Post by jerry50 on 2016-02-13
I'm having trouble with PIA.  They (support peeps) gave me a new password telling me that this would fix the problem, but it hasn't.  So I'm thinking I need/want to unload this and start from scratch.  What do I type into the terminal?  OH...I'm using ubuntu 15.10.

---

### Post by verymadpip on 2016-02-14
Hi there.
How did you install PIA?
I used this :
[https://www.privateinternetaccess.com/forum/discussion/18003/openvpn-step-by-step-setups-for-various-debian-based-linux-oss-with-videos](https://www.privateinternetaccess.com/forum/discussion/18003/openvpn-step-by-step-setups-for-various-debian-based-linux-oss-with-videos)

To me it looks like you could uninstall the openvpn bits, reinstall them & then go through the set up again.  *Don't uninstall your network manager*.
From what I can tell, looking at the step-by-step, PIA doesn't actually install anything, it's just config information copied to a folder to use in the set up of the VPN.

Seriously though, I'm not much of a networking person so you may want to hold off for some better advice than mine.

---

### Post by jerry50 on 2016-02-14
Thanks for the input.  I finally found a way around the issue and it is up and running.  Problem solved.

---

### Post by oldos2er on 2016-02-14
Please post the solution if you could. It helps others who may be having the same problem.

---

### Post by QDR06VV9 on 2016-02-14
Sorry I don't mean to jump in here but it is easy to unistall.
Here is how I uninstall the PIA VPN
Their install instructions just install the needed networkworking tools IE: OpenVpn and python 2.7 with their install script, It then installs all their config files to </etc/NetworkManager/system-connections>.
Now I have had to navigate to the **/etc/NetworkManager/system-connections** as administartor and Delete all the **"PIA**" config files **"ONLY" _Do Not remove any other files in that folder_.**
But most of the time you can just edit your NetWork Manager by clicking on it And Select the **"EDIT" Option**, and hand delete all the **"PIA"** entries in there.
Hope This helpful to others...
Regards

---

