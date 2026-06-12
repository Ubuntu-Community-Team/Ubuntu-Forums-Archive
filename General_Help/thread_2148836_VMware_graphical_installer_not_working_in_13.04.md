---
title: "VMware graphical installer not working in 13.04"
date: 2013-05-26
forum: General Help
---

### Post by kill o matic on 2013-05-26
Just upgraded to raring and it seems the graphical installers for VMware Workstation and VMware Player (the current and several past versions) will no longer run. Both gksu and gksudo result in the process silently terminating almost immediately with no errors. They run just fine from the 12.10 live USB, but not the 13.04 one.

---

### Post by kupiakos on 2013-05-27
I have the same problem. I've spent the past hour investigating.

After opening up the installer and investigating it, it seems to be rooted in the vmispy.LoadGTK() being told to use the system's files instead of its own. Changing forceShipped=False to forceShipped=True in /tmp/vmis-XXXXX/install/vmware-installer/vmis/ui/__init__.py fixes the problem, but the actual process of the changes being used is a painful one - I opened the .bundle in a hex editor to prevent it from overwriting my changes (making sure to keep the number of bytes in the header the same)...but that is way too much effort to simply get a GUI >.<. It seems that it somehow is having trouble loading the system's Python-GTK libraries. I'll let you know if I find anything else.

---

### Post by kill o matic on 2013-05-27
It wouldn't happen to have anything with the traditional python-imaging (PIL) being replaced with the pillow fork, would it? I have no idea what that actually means mind you, but it was given as an explanation for another third-party tool throwing a brand new error with 13.04.

---

