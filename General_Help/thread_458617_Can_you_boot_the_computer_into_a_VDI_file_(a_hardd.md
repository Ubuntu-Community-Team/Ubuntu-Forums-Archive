---
title: "Can you boot the computer into a VDI file? (a harddrive made with Virtualbox)"
date: 2007-05-29
forum: General Help
---

### Post by chrisLACHCIK5084 on 2007-05-29
So I'm running my computer on limited harddrive space right now because of financial reasons (crappy job until I get situated, 20gb hdd, and very fast computer with lots of potential to be upgraded!) and I love using Virtualbox. I was just wondering if anyone in the forums knew if there was a way to boot a VDI file from the grub menu when you start up the computer? The VDI file is the "virtual drive information" that is created on your harddrive when you make a user in Virtualbox.

---

### Post by mdurham on 2007-05-30
Just think about it for a while!

---

### Post by Mr. Brownstone on 2007-05-30
The answer is no. The point of Virtual Machine software is so that you can run another OS *without* leaving your current one. If you're rebooting in order to run a VDI file, you might as well reboot and run Windows proper.

---

### Post by Bachstelze on 2007-05-30
No. And even if you could, there's very little chance it would work.

---

### Post by Shadoweater12081980 on 2007-05-30
The guest system requires all the goodness that VirtualBox supplies (virtual devices / memory etc). VirtualBox in turn needs to have certain services and applications available in order to work.

Cold booting to the guest system is not possible, if you need this functionality you will need to dual boot

---

