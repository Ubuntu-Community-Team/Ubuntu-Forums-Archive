---
title: "Getting permanent access to system folders?"
date: 2008-04-25
forum: General Help
---

### Post by Muscar on 2008-04-25
Is there a way to get permanent access to the system folders?

Like the opt one, I'm trying to remove a Songbird folder, but I can't because it says permission denied.

And I'm the only one using this computer, so to easily access them, right away or to type my password, like you do when you open SPM


Thanks in advance
// Muscar

---

### Post by cmnorton on 2008-04-25
That's what sudo is for.  You might come to regret marking system folders, so you could have permanant access to them. I have a terminal emulator installed under opt. If I want to remove the installation and there is no uninstall (there isn't), then I sudo and remove the directory.

---

### Post by Muscar on 2008-04-25
> **cmnorton said:**
> That's what sudo is for.  You might come to regret marking system folders, so you could have permanant access to them. I have a terminal emulator installed under opt. If I want to remove the installation and there is no uninstall (there isn't), then I sudo and remove the directory.

Is there a way to use sudo without using the terminal?

---

### Post by chrisccoulson on 2008-04-25
> **Muscar said:**
> Is there a way to use sudo without using the terminal?

No, not at the moment. If you want to mess around with system folders, you will either have to use 'sudo whatever' from a terminal or use 'gksudo nautilus' to launch Nautilus as root.

And I would strongly advise against messing around with permissions on system folders for convenience so that you have full read-write access to everything. Recursively changing permissions will have some pretty bad effects (eg stop sudo from working at all). Plenty of other people on here have attempted it and ended up with completely borked machines. You've been warned ;)

---

### Post by Muscar on 2008-04-25
> **chrisccoulson said:**
> No, not at the moment. If you want to mess around with system folders, you will either have to use 'sudo whatever' from a terminal or use 'gksudo nautilus' to launch Nautilus as root.

And I would strongly advise against messing around with permissions on system folders for convenience so that you have full read-write access to everything. Recursively changing permissions will have some pretty bad effects (eg stop sudo from working at all). Plenty of other people on here have attempted it and ended up with completely borked machines. You've been warned ;)

ok, thank you

I'm just a bit confused when it comes to the terminal, as I'm pretty new to ubuntu

---

