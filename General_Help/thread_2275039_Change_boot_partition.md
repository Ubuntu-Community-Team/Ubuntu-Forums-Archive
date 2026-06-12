---
title: "Change boot partition"
date: 2015-04-23
forum: General Help
---

### Post by Cool_Javelin on 2015-04-23
I have Ubuntu 12.04 server installed on sdc1, and then I installed Fedora on partition sdc3.
I now have a dual boot system with Fedora listed on top as the default in GRUB, as expected.

I would like to change back to Ubuntu being the default, and eliminate the fedora partition altogether.

But while running Ubuntu when I look at /boot/grub/grub.cfg, I see no mention of Fedora.
On the other hand, looking in Fedora at /etc/grub2.cfg I do see the available boot options (Fedora and Ubuntu.)

How do I get the grub on sda1 active rather then the one on sda4?

Do I have to boot into fedora to make the changes?

Thanks, Mark.

---

### Post by cariboo on 2015-04-23
Use the following command to install grub on sda:

```
sudo grub-install /dev/sda
```

then run:

```
sudo update-grub
```

This should be done while running Ubuntu.

---

### Post by Cool_Javelin on 2015-04-24
Thanks cariboo:

Thanks for taking the time to reply to this.

I did finally get the solution, I needed to boot from the first partition on sdc1, vs another partition sdc3.

I booted the live CD and used the repair boot to make it rebuild the MBR and that did the trick.

Mark.

---

