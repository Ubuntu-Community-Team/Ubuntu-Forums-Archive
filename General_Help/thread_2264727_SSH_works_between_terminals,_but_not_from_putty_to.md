---
title: "SSH works between terminals, but not from putty to server"
date: 2015-02-09
forum: General Help
---

### Post by sean79 on 2015-02-09
[FONT=Helvetica Neue]I am running Ubunutu 14.04 and have installed openssh-server. It is all default settings except for the one setting[/FONT]
PermitRootLogin yes
[FONT=Helvetica Neue]I can ssh between ubuntu clients, but when I try via puttyI get Network error: Connection timed out.[/FONT]
[FONT=Helvetica Neue]This is a test bed, and I don't care about security for this deployment, its all setup in vm's via vsphere, I can ping the clients, no problem

I turned off ufw as well. 
[/FONT]
[FONT=Helvetica Neue]Any Ideas?[/FONT]

---

### Post by TheFu on 2015-02-09
a) what do the log files show?
b) what are the exact IP addresses and netmasks involved?
c) might be useful to turn up the logs for the server and clients to see what is happening.

---

### Post by sean79 on 2015-02-09
I went back, and for some reason was no longer able to ping the server. I swear I was before. I created an interface on the same subnet as the host and then everything works now. I had a feeling it was a networking or firewall issue. I think I was just tired after working 3rd shift that I didn't see it correctly

Thank you for your help.

---

