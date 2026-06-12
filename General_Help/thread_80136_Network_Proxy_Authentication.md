---
title: "Network Proxy Authentication"
date: 2005-10-21
forum: General Help
---

### Post by rotten on 2005-10-21
I'm setting up a desktop Ubuntu system in a big company where we have authentication based proxy servers to connection to the Internet.

No problem for me to get Firefox and GAIM working, but there is this option in Ubuntu under "system/preferences" that brings up a Network Proxy (tabbed) dialog box.

I assume this is for other system stuff to get out to Ubuntu for updates and the like.

How do I set user name/password for this proxy configuration?  Will it prompt me when it tries to go through?  I'm doubtful of this because it never has prompted me yet (and it never gets through).

Thanks for your help with this!

---

### Post by rotten on 2005-10-21
It would appear that if you set your "http_proxy" environment variable as described in the apt.conf man page, then run synaptic from the command line (or dselect or apt-get) you can get the proxy authenication to work.

You should be able to set your http_proxy environment variable in the start scripts for when you kick off X as well.  I haven't tried it yet.

---

