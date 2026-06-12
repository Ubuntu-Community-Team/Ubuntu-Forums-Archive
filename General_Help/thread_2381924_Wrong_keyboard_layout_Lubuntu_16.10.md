---
title: "Wrong keyboard layout Lubuntu 16.10"
date: 2018-01-06
forum: General Help
---

### Post by ianmanning on 2018-01-06
I want to change my keyboard to a UK layout. I don't know what it's currently set to, but there's no pipe character (I get a # if I hit the key to the left of the Z).

Can anyone tell me how I can permanently change my keyboard to a standard UK layout?

---

### Post by gemmathetechie on 2018-01-06
In Terminal you need to type in the code

```
sudo dpkg-reconfigure keyboard-configuration
```

and then you pick the correct keyboard layout for your PC.

I hope this helps!

I was assuming that you was needing the pipe for terminal usage?
If not, and the usage is just in the GUI you'll need to go through the system settings (I'm unsure what the settings would be called if you wanted to launch the settings from the terminal)

---

### Post by ianmanning on 2018-01-07
> **gemmathetechie said:**
> In Terminal you need to type in the code

```
sudo dpkg-reconfigure keyboard-configuration
```

and then you pick the correct keyboard layout for your PC.

I hope this helps!

I was assuming that you was needing the pipe for terminal usage?
If not, and the usage is just in the GUI you'll need to go through the system settings (I'm unsure what the settings would be called if you wanted to launch the settings from the terminal)

Thanks. It turns out the problem was that I was accessing the VM via the ESXi web console, which implements a keyboard that I can't work out how to configure. If I connect to the machine via VNC the keyboard is fine.

---

