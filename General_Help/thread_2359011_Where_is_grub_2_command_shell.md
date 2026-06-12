---
title: "Where is grub 2 command shell?"
date: 2017-04-19
forum: General Help
---

### Post by phu004 on 2017-04-19
Hi guys,

I remember in the system with legacy grub installed,  I could bring up the grub command shell by simply typing "grub" on the terminal,  then I can do stuff like:

    grub > root=(hd0,1)

    grub > setup (hd0)

    grub > quit

Now with grub2, it doesn't work any more (i.e the terminal doesn't recognize the 'grub' command). Can anyone tell me how do I bring up the command shell in grub2?

Thanks in advance.

Pan

---

### Post by yetimon_64 on 2017-04-20
If your grub boot screen is not showing up during boot you may need to press and hold down the "shift" key during boot to get it to show up.

If you do have a boot screen showing, when you boot the machine and the grub menu comes up, pressing "c" on the keyboard will bring you up that grub prompt.

Check for any instructions at the bottom of the grub boot screen; the options for editing entries, manually executing an entry and for bringing up the command line are usually noted there.

Regards, yeti.

---

