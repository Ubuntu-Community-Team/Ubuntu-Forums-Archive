---
title: "Network manager always tries to connect to nonexistent network."
date: 2014-05-18
forum: General Help
---

### Post by Paul_Jewell on 2014-05-18
I have had this issue for over a year but I never bothered to try to fix it. Every time I suspend/resume my laptop (rebooting actually does not cause the issue), network manager will automatically try to connect to an 'attwifi' network, and obviously never succeed. The network 'attwifi' is not listed in the list of networks on 'edit connections'. And once I found another file on ubuntu somewhere which also had a list of networks, and I checked there too and it was not there either. (one of you may mention to check this file, no problem, I just forgot its path offhand) I can manually choose another network and that goes ok. If anyone has suggestions please post.

---

### Post by ian-weisser on 2014-05-18
Enter the pertinent data into 'edit connections' (ESSID, MAC Address) and then *uncheck* 'connect automatically'

If you're not sure where to find the mac address of that network's router, use the command 'iwlist $interface scanning' to list everything your wi-fi card can see. My $interface is named wlan0, yours may differ.

---

### Post by sammiev on 2014-05-18
You can also select "Network Connections" and look for the name "attwifi" and delete it.

---

### Post by Paul_Jewell on 2014-05-20
sammiev, the network name is not in that list. 

ian, that was an interesting suggestion, except I do not know which mac address would work. There are none near me. (if you were not aware, 'attwifi' is a commercial wifi provider with acess points located at many places in NJ) Trying your suggestion with only the ESSID did not fix the issue.

---

### Post by sammiev on 2014-05-20
Look in Network Connections not Network Manager.

---

### Post by Paul_Jewell on 2014-05-26
Hello, sorry for the long reply. That is the same list that is launched when clicking on the 'edit connections' button on the network manager. In any case the network 'attwifi' does not appear in this list.

---

