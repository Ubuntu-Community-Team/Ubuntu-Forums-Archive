---
title: "Unknown LVS Attribute"
date: 2016-02-19
forum: General Help
---

### Post by Brett_Hanekom on 2016-02-19
I have Ubuntu 15.10 installed and I am using LVM to create a raided thin pool logical volume. All has gone well and I can for the installation and the thin pool is working as expected in normal use. When I started doing some testing on what would happen on loss of a disk and then restoring that same disk to the machine i noticed that I have a new attribute on the 9th bit. During normal use the attributes are twi-aotz--, but when I have restored the device I have the following attributes twi-aotzM-. I have looked at the manpages ([http://manpages.ubuntu.com/manpages/wily/en/man8/lvs.8.html](http://manpages.ubuntu.com/manpages/wily/en/man8/lvs.8.html)) , but there is no reference to the M in bit 9. in my tdata and tmeta there were lower case m's, but running a check and repair has removed those. Can anyone help me with what this M means and if I should be concerned about?

---

