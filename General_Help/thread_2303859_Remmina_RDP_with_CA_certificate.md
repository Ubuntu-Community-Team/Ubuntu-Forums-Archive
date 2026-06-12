---
title: "Remmina RDP with CA certificate"
date: 2015-11-22
forum: General Help
---

### Post by Domie on 2015-11-22
For my work I need to connect to an external Windows desktop.
I used to do this with Remmina, without a problem with the following data: server, user and pass.

Now, they migrated to a new server. On my main Windows PC, they logged in and did the job. In my recycle bin, I fished out a CA certificate file. On my Windows laptop, I did the installation myself: I added this certificate, copied the data and encountered the message that the gatewayserver could not be verified. After adding this certificate as a trusted one, all worked.

On my Ubuntu laptop (and Linux Mint laptop also), there seems no possible way to make this work. I copied the certificate (after renaming to .crt) to /usr/local/share/ca-certificates, and did sudo update-ca-certificates, which added 1 certificate (which is also viewable in /etc/ssl/certs). When I try to connect to cloud.server.domain, nothing happens.

Protocol: RDP
server: cloud.server.domain (this varies on Windows, there it looks like a local reference "srv-rdg", but when I fill in this string, Remmina tells me "unable to connect to RDP server srv-rdg")
username: work\user
password: *****
Domain: blank (tried also "work" when username was only "user")

Security: negotiate (tries also RDP and TLS)

SSH: enabled and disabled: did nod work both, both tried tunnel via loopback device, checked and unchecked
SSH authentication
username: tried "work\user", "work", "user"
pass: ****
also tried "public key"
also tried identity file (and referred to the certificate)

When not using SSH, it keeps on trying with giving an error message after a few minutes
When using SSH, it gives after giving the password: SSH password authentication failed: Access denied. Authentication that can continue: publickey,keyboard-interactive

I have not a clue on how to solve this... I hope someone will?

---

### Post by Domie on 2015-11-23
Try other software? Vinagre also does not work.

---

### Post by cmcanulty on 2015-11-23
I struggled with this a lot for maintaining many library computers. First install dconf editor and then go to org-gnome-desktop-remote access then make sure it is enabled and encryption is disabled, other settings are also there. I also recommend remmina over vinagre. Also try installing xrdp as rdp is the native windows remote desktop app. Instead of using the repositories try doing it via this web page directions. Also make sure in windows services all the appropriate remote desktop services are enabled. I can never get ssh tunnel to work with remmina or vinagre but I can ssh or use vnc or rdp but never both.I set security to negotiate in remmina though one machine requires it set to rdp, go figure.Try that and see if anything else is needed. 

[http://scarygliders.net/x11rdp-o-matic-information/http://]("http://scarygliders.net/x11rdp-o-matic-information/http://")

---

### Post by Domie on 2016-01-28
Thanks, but encryption is enabled.

Problem is I can't let it connect...

---

### Post by cmcanulty on 2016-01-28
also try installing freerdp, then go to /home/.freerdp/certs and remove all, back them up first, worked for me, but encryption is an issue with ubuntu remote apps. seems crazy to not have it work but I have had no luck with it or ssh tunnels

---

