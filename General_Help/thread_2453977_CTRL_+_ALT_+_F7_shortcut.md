---
title: "CTRL + ALT + F7 shortcut"
date: 2020-11-20
forum: General Help
---

### Post by aliquo93 on 2020-11-20
Can someone explain what this combination does? I mistakenly pressed it on Ubuntu 20.10 and it showed me a screen with the same output of fsck (“clean” and the number of blocks)... now I am worried that it actually ran fsck on the mounted partition... can someone explain me what this shortcut does?

---

### Post by oldos2er on 2020-11-20
Ctrl + Alt + F1 through F7 switch through [TTYs.]("https://askubuntu.com/questions/66195/what-is-a-tty-and-how-do-i-access-a-tty") I believe the desktop GUI "lives" in F7.

---

### Post by Impavidus on 2020-11-20
ctrl+alt+F(1-7) allows you to switch between multiple consoles. One of them has the GUI, the others are text interfaces. The fsck output was left on one of them during the boot process. Nothing to worry about.

These consoles can be a nice way to fix your system when the GUI crashes.

---

### Post by aliquo93 on 2020-11-20
But why if I press CTRL + ALT + F7 it gives me the fsck output?

EDIT: Sorry didn’t see the last reply

---

### Post by tea for one on 2020-11-20
Ctrl Alt F1 > Login Page
Ctrl Alt F2 > GUI Desktop
Ctrl Alt F3 > TTY3
Ctrl Alt F4 > TTY4
Ctrl Alt F5 > TTY5
Ctrl Alt F6 > TTY6

---

### Post by DuckHook on 2020-11-20
> **tea for one said:**
> Ctrl Alt F1 > Login Page
Ctrl Alt F2 > GUI Desktop
Ctrl Alt F3 > TTY3
Ctrl Alt F4 > TTY4
Ctrl Alt F5 > TTY5
Ctrl Alt F6 > TTY6

It depends on the version. If I recall correctly, with Bionic, the Desktop was still F7.

---

### Post by tea for one on 2020-11-20
> **DuckHook said:**
> It depends on the version. If I recall correctly, with Bionic, the Desktop was still F7.

I don't have access to Bionic 18.04 but the OP mentioned 20.10.

Out of curiosity, are the keys the same for all the Ubuntu flavours (assuming the release is the same i.e. Ubuntu 20.10 & Kubuntu 20.10 etc)?

---

### Post by DuckHook on 2020-11-20
> **tea for one said:**
> …but the OP mentioned 20.10.
Of course. My bad.
> Out of curiosity, are the keys the same for all the Ubuntu flavours (assuming the release is the same i.e. Ubuntu 20.10 & Kubuntu 20.10 etc)?
Good question. I assume they are—after all, the console function should be tied to the base system and not the DE. But I've nuked my old VMs of alternate flavours so can't test right away.

---

### Post by deadflowr on 2020-11-20
The display managers gdm3 (Ubuntu's default) and sddm (Kubuntu/Lubuntu's default) use tty1/vt1 for the login screen.
Older Ubuntu and some flavors use/used lightdm, which used tty7/vt7 for the login screen.

As far as I remember gdm3 loads user session in a new console (vt2 and higher).
I think sddm runs much the same as gdm3.

And lightdm loads the first user session in the same tty/vt as the login screen.

I'm not sure which desktops or flavors still use lightdm by default.
Maybe Xubuntu?

I know unity desktop runs nicer in lightdm.
But that's probably more ascetically pleasing to me in a truthiness kind of way.

---

### Post by Impavidus on 2020-11-20
Xubuntu 20.04 still puts the GUI on tty7.

---

### Post by tea for one on 2020-11-20
> **Impavidus said:**
> Xubuntu 20.04 still puts the GUI on tty7.

Does Xubuntu use lightdm?

---

### Post by ajgreeny on 2020-11-20
> **tea for one said:**
> Does Xubuntu use lightdm?
Yes, it does us lightdm.

Xubuntu 20.10 also still uses tty7 for the GUI, so I wonder if it's just Ubuntu itself that has changed to anothet tty.

---

### Post by tea for one on 2020-11-20
Ubuntu used lightdm during the Unity years and then changed to gdm3 when gnome-shell became the default - 18.04 if I were to guess.

I suspect that the Ctrl Alt F1 > F7 changed at the same time.

---

### Post by ajgreeny on 2020-11-22
I have Ubuntu-20.10 installed as a VM in KVM and in that Ctrl+Alt+F1 is the login screen, ssdm, Ctrl+Alt+F2 is the GUI, and interestingly Ctrl+Alt+F7 is not a numbered tty but shows just the "***/dev/sda2: clean, 176550/1277592 files, 1948505/5111296 blocks***" info that is seen at boot just telling us that the filesystem is clean.

I had not realised that there had been any changes and if asked I would have presumed that the tty1-6 were just command-line ttys and tty7 was the GUI.
Why did a change occur, confusing many of us as this thread shows?
I presume there was a good reason.

---

