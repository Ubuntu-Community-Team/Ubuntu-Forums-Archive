---
title: "Video chat amsnI"
date: 2007-04-04
forum: General Help
---

### Post by El Viejo Lobo on 2007-04-04
I have a Speedtouch 536 modem and a router + wireless linksys, one dektop PC and a Laptop too both computers have Edgy Eft as OS.
 My webcam is Logithec and it works (I can see my self).
I use aMSN  (Last version) and all what I get is a window that tells me that I have firewall or router blocking my video broadcasting. 
 Where is the problem and what is the way to make it work.
Thanks.

---

### Post by Maestro23 on 2007-04-04
Have  you checked here: [http://www.amsn-project.net/wiki/FAQ](http://www.amsn-project.net/wiki/FAQ)

---

### Post by El Viejo Lobo on 2007-04-04
I am only a few month after my first Ubuntu install. I learned a lot but yet I am new to it. I am not a computer professional I am a simple user that got fed up  of Security and formats in the land of Windows. Ubuntu is becoming very important to people like me. Now tell me how I can understand the following instructions. With Windows I had to know how do do a lot of other things but never had to look for the modem intestines.   

This is what you find in: [http://www.amsn-project.net/wiki/FAQ#I.27m_using_aMSN_behind_a_firewall.2C_or_using_IP-Masquerade._Sending_files_won.27t_work.2C_can_I_fix_it.3F](http://www.amsn-project.net/wiki/FAQ#I.27m_using_aMSN_behind_a_firewall.2C_or_using_IP-Masquerade._Sending_files_won.27t_work.2C_can_I_fix_it.3F)

 I'm using aMSN behind a firewall, or using IP-Masquerade. Sending files won't work, can I fix it?

In this case, the firewall may be blocking incoming connections. File transfers work this way: When you want to send someone a file, you send an invitation with your IP address and a port number. Then the remote client must connect to your IP:port to start the transfer.

The used port is usually 6891, 6892 and so on (first transfer is on port 6891,but if you start a new file transfer while the first one hasn't finished yet, then it will use 6892, and so on).

If using a firewall, you must make sure that it allows incoming connections to port 6891 (and next ones if you want to be able to make more than one transfer at the same time).

If you're inside a private network with private addresses, like 192.168.0.x, then it's more difficult to make file transfers work. You need to send the real internet address (you can enter it manually or tell aMSN to guess it from a web page), instead of the internal address, and tell the gateway (the computer with direct connection to the internet) to forward incoming connections to port 6891 to your computer inside the private network.

---

