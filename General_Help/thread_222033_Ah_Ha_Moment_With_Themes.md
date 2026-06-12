---
title: "Ah Ha Moment With Themes"
date: 2006-07-24
forum: General Help
---

### Post by OmShiva on 2006-07-24
I've been quite annoyed for a couple of weeks now that I had my desktop theme setup just to look beautiful, except for a couple of application such as synaptic and the gdm setup window, which would not take the looks of the rest of my desktop.It was horrible to see. It wasn't until I was in the shower a few minutes ago I realized that the problem was that those programs run as root while the themes installed in my home directory. I copied the files to  /usr/share/themes and everything is beautiful again. 

The embarrasing thing is I've been using linux for years...and it took me this long to connect the dots. :rolleyes:

---

### Post by prash@linuxitarian on 2006-07-24
Thanks for the tip! I was having the same problem too. Will try it out....

---

### Post by s_h_a_d_o_w_s on 2006-07-24
i tried but nautilus says I don't have the permission, how can I get it?

---

### Post by OmShiva on 2006-07-24
open gnome-terminal and type:

sudo nautilus

that will open a nautilus window for you as root. you will now have write access to your whole system. just make sure you close that nautilus window when your finished as you could erase your whole filesystem with one mistake. 

;)

---

### Post by OmShiva on 2006-07-24
> **prash@linuxitarian said:**
> Thanks for the tip! I was having the same problem too. Will try it out....

my pleasure....i wasn't for sure if i should post my dumbness, but i'm to see it help you out. :KS

---

### Post by s_h_a_d_o_w_s on 2006-07-25
thyanks so much! It looks good now!

---

### Post by testube_babies on 2006-07-25
Here's a one-stop command-line way to get this done:
```
sudo mv ~/.icons/* /usr/share/icons
sudo mv ~/.themes/* /usr/share/themes
```

---

### Post by Samuli on 2006-07-29
Here is a better way to do it:

[http://www.ubuntuforums.org/showthread.php?t=221021&highlight=theme+root](http://www.ubuntuforums.org/showthread.php?t=221021&highlight=theme+root)

---

### Post by AirRaven on 2006-07-29
Quick point- don't use "sudo" for running graphical applications like Nautilus. Use the command "gksu" ("gksudo" technically, but I've not seen any functional difference between the two) if you're in GNOME, or "kdesu" in KDE.

Running things with plain sudo can really mess things up.

---

### Post by testube_babies on 2006-07-29
EDIT:  I shouldn't have posted.  sorry.

---

