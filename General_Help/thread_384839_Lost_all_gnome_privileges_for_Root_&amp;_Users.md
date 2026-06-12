---
title: "Lost all gnome privileges for Root &amp; Users"
date: 2007-03-14
forum: General Help
---

### Post by zachsandberg on 2007-03-14
Hey everyone. I was playing around in "users and groups" tonight, and somehow took away privileges in gnome to run any application that needs sudo, gksudo, root, etc.
I thought it was just the one user account affected that I was in, but I edited grub, to boot me into single user root, changed the root password on the CLI, then typed "GDM" to login as root to fix the permissions issue in "users-admin" but it says I have "no permissions to run "users-admin" even as root.   

I don't have the "users and groups" entry in the administration menu either.

This is a problem.

So, can anyone tell me what GNOME file is written to, to set access controls, and how can I change it, so at least in root, I can click the settings back for the user accounts? Keeping in mind I have the command line only for this until I can work in Gnome with privileges.

I greatly appreciate any suggestions.

Zach

---

### Post by aysiu on 2007-03-14
You can fix it by following these instructions:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

