---
title: "StartX problem"
date: 2007-10-27
forum: General Help
---

### Post by sp00kii on 2007-10-27
Hi,

i installed ubuntu 7.10 server and i installed with apt-get xinit, but unfortunately fails to start.

When i type in startx i get the following error:

xauth: creating new authority file /home/username/.serverauth.4064
xauth: /home/username.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/username/.Xauthority
xauth: error in locking authority file /home/username/.Xauthority
xauth: error in locking authority file /home/username/.Xauthority

X: cannot stat /etc/X11/X (no such file or directory) aborting giving up.
xinit: connection refused (errno 111): unable to connect to X server

Now, when i type the command xinit it says:
X: cannot stat /etc/X11/X (no such file or directory) aborting,  server error.

How can i install kde or gnome?

Any ideas about those error messages?

thanks in advance.

---

### Post by oldos2er on 2007-10-27
Ubuntu server doesn't come with X (GUI). You can install kde with "sudo aptitude install kubuntu-desktop ," or gnome with "sudo aptitude install ubuntu-desktop ." Hope this helps.

---

### Post by sp00kii on 2007-10-28
Hi,


 When i run the commands you told me i get the following:

could not find any package whose name or description matched ubuntu-desktop
same thing for kubuntu as well.

Any ideas please ....?


Thanks.

---

### Post by vcouture on 2008-02-17
This worked great for me - I got kde up and running on ubuntu server finally thanks!

---

