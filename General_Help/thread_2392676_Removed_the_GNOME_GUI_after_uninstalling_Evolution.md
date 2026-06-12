---
title: "Removed the GNOME GUI after uninstalling Evolution (18.04)"
date: 2018-05-23
forum: General Help
---

### Post by xceptone on 2018-05-23
Evenings all,

So after following the commands mentioned in: [https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution](https://askubuntu.com/questions/315640/how-do-i-completely-remove-evolution) to uninstall Evolution, I've also removed GNOME. So upon logging into my Ubuntu partition, was present with just the console to log in.

Since then, I've ran "sudo apt install gnome-session gdm3" which gave me most of the GUI but not all, dock, screen min max buttons missing  and few other bits.
I have ran also 
sudo update-alternatives --config gdm3.css
sudo apt-get install gnome-panel

Yet not success.

What else can I try, a repair of some sort?

---

### Post by PaulW2U on 2018-05-23
That link referred to a question that was asked nearly **five** years ago and referred to Ubuntu 13.04 which used a different desktop, i.e. Unity.

Try installing ubuntu-desktop. That should bring in (most of) your missing applications.

---

### Post by xceptone on 2018-05-23
Nevermind sorted it by doing the following:
$ sudo apt install tasksel
 Once the tasksel command is installed, begin the Gnome desktop installation by executing: $ sudo tasksel install ubuntu-desktop

---

### Post by kerry_s on 2018-05-23
sudo apt install ubuntu-desktop

---

