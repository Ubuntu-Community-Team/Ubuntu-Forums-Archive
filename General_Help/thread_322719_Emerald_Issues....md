---
title: "Emerald Issues..."
date: 2006-12-20
forum: General Help
---

### Post by FenixNR on 2006-12-20
Kubuntu Edgy. Nvidial GeForce 440m GO 64m, installed beryl with apt-get install beryl emerald (which installed all necessarys). I added a startup script so that I can just boot into beryl. Works great, except I don't have the emerald themes on. I typed emearld --replace and came up with the following errors:

jor opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

I might not have got it all copied, but thats the thing that kept showing while I tried to get it running. Any help would be greatly appreciated.

---

### Post by iamhugeinjapan on 2006-12-20
When you right click the Beryl Manager icon, do you get a choice of loading the Emerald Theme Manager? and do you have Emerald selected in the "Select Window Decorator" option?

---

### Post by FenixNR on 2006-12-21
Yes, I do, but it doesn't do anything.

---

### Post by FenixNR on 2006-12-22
Anyone?

---

### Post by xopher on 2006-12-22
> **FenixNR said:**
> Anyone?

Actually, I don't have a solution for you, no idea why emerald doesn't work for you, if you have everything installed correctly etc. Tried manually starting beryl?

A workaround for this might be to install heliodor (gnome), aquamarine (KDE), which uses the default themes of the desktop environment. Eg. Heliodor uses metacity themes. They are both be available from the beryl repositories.

so just do a

```
sudo apt-get install heliodor
```

or a 

```
sudo apt-get install aquamarine
```

then select that from beryl-manager.

Hope this helps

Edit: If you've had emerald installed before, you could try pruning it's configuration files from ~/.emerald too. Then reinstall it.

---

### Post by iGama on 2007-01-02
i just install heliodor (gnome) but it does not show in beryl manager what could it be?

---

### Post by Fixxxer on 2007-01-02
> **iGama said:**
> i just install heliodor (gnome) but it does not show in beryl manager what could it be?
Try logging out and then back in.

---

### Post by eviltang on 2007-01-02
I am not that familiar with linux/beryl/ubuntu, but I run ubuntu with beryl installed.  Have you tried running beryl-manager as root?

For example, open a terminal and try this:

```
sudo su root
```

Hit Enter, Type your Password, hit enter

Once you become root, in that terminal:
```
beryl-manager &
```

Hit Enter.

Let me know if this helps.

Eviltang

---

### Post by iGama on 2007-01-08
Its working :)

What is the difference betewen using Heliodor or chosing "GTK window decorator" in the Select window decorator section?

---

