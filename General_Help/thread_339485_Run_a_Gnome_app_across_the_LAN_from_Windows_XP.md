---
title: "Run a Gnome app across the LAN from Windows XP"
date: 2007-01-15
forum: General Help
---

### Post by MikeLeone on 2007-01-15
I have this Gnome app on a Ubuntu 6.06 server that I would like to have available to my Windows clients on my LAN. I don't want to run the Gnome app locally on my Windows hosts; I want to run the app across the LAN, but from Windows XP hosts.

How would I do that? We're already SSHing to this server to do CLI work, but now I'd like to be able to access this Gnome app (tinyCA, a way of managing SSL certs) from my Windows boxes. I don't want to dual boot the Windows boxes, or anything like that. Ideally, I'd like to set an icon on the Windows boxes that points to the server and that particular app, just as I would in Windows. I realize that may not be completely feasible.

Can anyone point me to some details of what is required, and how?

Thanks

---

### Post by crispy_420 on 2007-01-16
Right now you running other apps as command right?

There is an option to run apps with gui over network. I think the command is:

ssh -X <username>@<ip address>

I'm assumming you are already using PuTTy on your windows boxes.

As far as an icon to run with a click, it may be possible but I'm not sure how.

---

### Post by kpatz on 2007-01-16
If the app can run in a command-line interface mode (no GUI), the ssh command above would work, using PuTTY or similar.

If you want the Gnome app to show a GUI on the XP box, you'll have to install an X server on the XP box, such as Cygwin.

---

