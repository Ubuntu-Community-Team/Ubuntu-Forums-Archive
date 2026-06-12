---
title: "Update problems"
date: 2007-01-23
forum: General Help
---

### Post by dnccnd on 2007-01-23
I am having some problems with the orange Upgrade icon that appears on the top right menu whenever a new update is available.

When I click on it the following massega appears in a small window:

[FONT="Tahoma"]E: dpkg was interruped, you must manually run 'dpkg --configure -a' to correct the problem.[/FONT]

followed by this other message in another small window:

[FONT="Tahoma"]Could not upgrade the system! Fix broken pakages first.
[/FONT]

If I move the mouse over the orange Update icon this message is displayed:

[FONT="Tahoma"]A error occured, please run Package manager from the right-click or apt-get on a terminal to see what is wrong. The error message was: 'Error: BrokenCount > 0'[/FONT]

I tried to run the command [FONT="Tahoma"]dpkg --configure -a[/FONT] in Terminal but then I get the message: [FONT="Tahoma"]dpkg: requested operation requires superuser privilege[/FONT]

I tried also to open Synaptic and when I click on reload to get the latest updates I get the following message in a small window:

[FONT="Tahoma"]The following problems were found on your computer:
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)[/FONT]

Does anybody have idea about what is going on in my computer? :confused: 

Thank you for any help you might provide.

---

### Post by taurus on 2007-01-23
Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
```

---

### Post by dnccnd on 2007-01-23
Great! It worked!

I had to fik a broken pakage from Synaptic by upgrading it and then everything came back to normal...

Thanks a lot!

---

