---
title: "Make LUKS ask for passphrase at boot to decrypt LVM volume group"
date: 2013-05-14
forum: General Help
---

### Post by cbSSS on 2013-05-14
Hi,

I'm installing Ubuntu Server 12.04.2 LTS so it can run OpenStack, and I have an 'OS' physical volume/volume group that automounts at boot, so the LUKS obviously asks for the passphrase for that at boot, but the 'cinder-volumes' physical volume & subsequent volume group doesn't have anything to mount, so I don't know how to make the prompt to decrypt it happen.

I want to enter the 'cinder-volumes' passphrase at boot, too- right after I decrypt the 'OS' pv/vg.

Can someone help me?

---

### Post by cbSSS on 2013-05-14
Found it:
/etc/crypttab

---

