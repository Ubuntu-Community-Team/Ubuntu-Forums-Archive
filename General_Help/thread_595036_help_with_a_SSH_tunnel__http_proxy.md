---
title: "help with a SSH tunnel / http proxy"
date: 2007-10-28
forum: General Help
---

### Post by Darth_tater on 2007-10-28
i travel quite frequently, and often find myself at many public hot spots.  i want to set up an SSH tunnel so that my traffic will be encrypted.

i managed to get a SSH server setup on the port that i want (non standard to help limit brute force attacks) and punch a hole in my firewall.

i can connect to the SSH server from anywhere, but for some reason i am having trouble getting the SOCKS / http proxy up an running.

i successfully connect to the SSH server and set PuTTY to forward a specific port, but when i go to configure firefox to connect to PuTTY on the specific port, i get the error that states:

"fire fox is set to connect to a proxy server that is actively refusing connections"  


im just guessing, but i think this means the HTTP request is not being handled properly on the server side?


any help you could give would be *much* appreciated.

---

