---
title: "running a script from an ftp server"
date: 2016-12-28
forum: General Help
---

### Post by rednecknerd2 on 2016-12-28
I am currently working on a multi part project. The final product is something I want to ship to a girl who is not very tech savvy. Because of that I need to be able to remote admin the device. This proves difficult because I will have no access once the device is shipped and the distance is far enough that visiting to fix it is not really an option either. The solution I have come up with is to pre configure the ssid of her network, then automatically log into a vpn being hosted on my network. from there she has access to an ftp server that is preloaded with a set of scripts that I can configure on my side. 

For example running a chron job at midnight to run a bash script file. normally this file would contain update "sudo apt-get update", but in the instance that we encountered an issue, I would be able to adjust the file and push updates to that machine. I know that this introduces certain security issues, but I cannot come up with a better idea for getting continuous access to a machine that I have no physical access, or network access. I am attempting to minimize security holes by both encrypting the system before shipping and keeping the ftp server from being accessible from the internet. 

If anyone knows the technique to make this happen it would be greatly appreciated, or if someone has a better idea for how to make my "backdoor" system work I am all ears.

---

### Post by SeijiSensei on 2016-12-28
I've installed servers in clients' offices that create an OpenVPN tunnel back to my network during boot.  Then I can just use SSH over the tunnel to manage the remote host.  This is pretty easy to set up with the [static-key approach]("http://openvpn.net/static.html").  The client establishes the tunnel via the "remote" directive in its configuration file under /etc/openvpn/.

---

