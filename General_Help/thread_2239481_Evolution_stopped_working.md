---
title: "Evolution stopped working"
date: 2014-08-14
forum: General Help
---

### Post by cigtoxdoc on 2014-08-14
Evolution died when it go some new e-mail.  Cannot start with launcher.  When I start from command line, I get following messages:
john@john-Vostro-3500:~$ evolution

(evolution:16085): camel-WARNING **: Failed to initialize NSS SQL database in sql:/etc/pki/nssdb: NSS error -8187

(evolution:16085): GLib-GObject-WARNING **: cannot register existing type 'CamelEwsStore'

(evolution:16085): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion 'G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(evolution:16085): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion 'G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(evolution:16085): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion 'G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(evolution:16085): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

How do I get evolution working again?

Thank you, John

---

### Post by bratstejskal on 2014-08-14
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1347437](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1347437)

---

### Post by cigtoxdoc on 2014-08-15
Thank you very much for your help.  I followed the link you suggested.  The first part of the intructions did not work, as others had noted.  What did work was to completely remove evolution and use the #9 post in that thread:

evolution_3.13.4-1_amd64.deb Edit (406.2 KiB, application/x-debian-package)

I was able to build my own deb from git clone from [https://git.gnome.org/evolution](https://git.gnome.org/evolution) (and -ews and -common as well as gnome-common) and it seemed to work. I attached my .deb (warning, it will break apt supposedly) if anyone wants to compare.
affects: 	evolution &#8594; evolution (Ubuntu) 

After I downloaded and installed the deb file, evolution came back without a problem.

John

---

### Post by bratstejskal on 2014-08-20
Note: the fix has been published to the PPA. Fabien must have rebuilt the .deb on his end. I am using his .deb built a few days ago on the PPA and it's a lot better. I would uninstall my patch (sudo apt-get remove evolution-ews && sudo apt-get update && sudo apt-get install evolution-ews should do it) and update normally through APT.

---

