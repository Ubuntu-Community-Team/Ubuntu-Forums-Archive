---
title: "Reason for preventing normal X access through telnet"
date: 2006-12-04
forum: General Help
---

### Post by sambitnayak on 2006-12-04
Hi folks,

As far as I know, to run remote X applications on a local ubuntu machine through telnet, we need to do that by setting "DisallowTCP" to false in /etc/X11/gdm/gdm.conf file.

My question is this : Why doesn't ubuntu allow normal X access through telnet like other Linux distributions or Solaris? For example, sometimes one needs to connect to a server and launch an application on it and then export the display to the local machine. For that, either one can use secure forwarding through ssh (ssh -X) or do the "DisallowTCP=false" trick. However, the former is not allowed by all servers and one normally does not have administrative privileges on the server machine. As for the latter, I understand it involves some security risks. It would be good if Ubuntu would allow the user to simply do a "export DISPLAY=<local machine display>" on the remote server and launch the X applications. Is there any specific reason not to allow this?

Thanks & Regards,
Sambit

---

