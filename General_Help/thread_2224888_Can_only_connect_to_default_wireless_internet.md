---
title: "Can only connect to default wireless internet"
date: 2014-05-18
forum: General Help
---

### Post by Romeu_Tristo on 2014-05-18
I'm a new user of Linux (Lubuntu 14.04) and I'm having troubles figuring out how to connect to a new wireless internet.
When I installed Lubuntu I connected to my home wireless internet, and that works perfectly. Whenever I'm at home it connects automaticaly. But when I'm in another place, how can I connect to a wireless internet?
I have the "Manage Networks" in my panel, and when I click it, it shows me all the wireless internet available. I pick the one I want and a window pops up saying "This wireless network was encrypted. You must have the encryption key.". So I write down the internet password and click "Ok", but nothing seems to happen. I've tried this at different places with different internets and it doesn't work. So basically I can only connect to the internet I set as default on my Lubuntu installation process.
Can someone help me please?

---

### Post by Rex Bouwense on 2014-05-18
Not sure what you are asking for because there is no default wireless internet setting.
Please right click your NM applet in the LXPanel and ensure that both enable networking and enable wireless are both checked.
Then disconnect from your current connection.  Choose another wireless connection and connect to it.  Ensure that Caps Lock is not on if it is password protected.

---

### Post by Dennis N on 2014-05-18
Sounds like you installed your system using a wifi connection, so your information entered at installation time is being used now to automatically connect. Now you want to connect to other networks. 

You mention trying the **Manage Networks** panel plugin. I also tried that at first, it didn't work for me. You can remove this from the panel. Not needed.

What you want to use instead is called the **Network Manager applet** (nm-applet) which you do not see in the panel of a new installation since it is not running at startup (as it should be) on Lubuntu 14.04. 

Follow the steps in the link below to get it running at startup and have the icon show on the panel. You can then click the icon to connect to other networks.

[http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html](http://www.webupd8.org/2014/04/fix-lubuntu-1404-network-manager.html)

---

### Post by Romeu_Tristo on 2014-05-19
Dennis L, I've followed the steps you mentioned and the Network Manager  applet is now running at startup. I'll have to try to connect to another  internet to see if it works, so when I do that I'll post here saying if the problem was solved. Thanks for your help.

---

### Post by Romeu_Tristo on 2014-05-31
Problem solved. Thanks Dennis L for the advice.

---

