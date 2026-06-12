---
title: "Ad-Hoc Network between Win 7 and Ubuntu"
date: 2015-03-19
forum: General Help
---

### Post by ski4 on 2015-03-19
I have a Win 7 System and just built an Ubuntu System……..they are 5 feet apart…….Both have wireless adapters and Internet Access…….I’d like to make an (in Windows 7 Terms) -----Ad-Hoc connection between the two systems in order to transfer files……I’m only now returning to Ubuntu after years away so I don’t know enough  to set it up…………Help!

---

### Post by lisati on 2015-03-19
*Thread moved to **General Help**.*

---

### Post by efflandt on 2015-03-19
Click on the little network or wireless icon in upper right and go to **Edit Connections...** Add a **Wi-Fi** connection. In the drop down list that says **Infrastructure**, select **Ad-hoc** (those are not just Windows terms). Set everything up there. You likely need to manually configure IP and netmask, you do not necessarily need gateway or nameserver(s) unless Windows ICS is enabled on an Internet connection that Windows has. Channels need to match.

Not sure if Windows ICS would automatically do DHCP for ad-hoc remotes like it does for Ethernet, but the IP for Linux would need to be in same network as any IP Windows ICS would assign to its wireless, and gateway and nameserver could be same as Windows ad-hoc IP. I have not done that using Windows ICS since connecting a (manually configured) Palm T/X ad-hoc to a WinXP laptop with ICS enabled for its Ethernet to cable modem many years ago. So I am a little rusty on details.

---

### Post by gordintoronto on 2015-03-19
What you want is a shared folder. It has nothing to do with Wi-Fi.

---

