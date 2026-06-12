---
title: "Nothing starts at bootup"
date: 2006-12-14
forum: General Help
---

### Post by bay-bee on 2006-12-14
Hey, I've been trying and trying but haven't found the solution.
When I boot my ubuntu server(edgy, all the latest patches and updates), nothing gets started, I have to manually log in and start the daemons I want it to run. How do I change/choose what I want to be auto started? On my laptop everything works fine and things run at bootup, I've tried to compare the systems but haven't found the difference. I think this probably has to do with edgy running this new "upstart" instead of init, but I don't understand how to use it, and why it works on one machine and not the other, if anyone has some tips on how I can troubleshoot this.

---

### Post by taurus on 2006-12-14
What are the apps or daemons that you have to start by hand?

---

### Post by bay-bee on 2006-12-14
I have to start sshd, samba, dhcp3-server, apache, webmin, xinetd, I do however believe named(bind) gets started, eventhough I don't really care(I dont use it atm)

---

