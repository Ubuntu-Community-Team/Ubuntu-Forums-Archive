---
title: "Slow performance in fresh install of 20.04.01LTS"
date: 2020-11-03
forum: General Help
---

### Post by cable_guy on 2020-11-03
Hi

I have just installed Ubuntu desktop 20.04.01 LTS on my Hp microserver n40l

I've had previous versions of Ubuntu running on this machine for 10 years, running really well.

Since I have installed the latest version, I get slow performance for the following type of things:

- clicking various menus in the GUI, e.g. opening terminal, it takes nearly 40 seconds to open
- running apt-get upgrade, locally or remotely via SSH
- even unlocking the screen in the GUI takes seconds longer and I'd expect it to be instant

I've checked the is disk for bad sectors and don't see any bad sectors, could anyone please advise on a troubleshooting method for me?

---

### Post by ajgreeny on 2020-11-03
What is your hardware?

With the same machine for 10 years it's possible that Ubuntu 20.04 has simply become too resource hungry for that machine.

Show us the terminal output of*** inxi -Fzx*** for some useful hardware info.

---

### Post by cable_guy on 2020-11-03
[HTTPS://paste.ubuntu.com/p/KswYQPNW8w/](HTTPS://paste.ubuntu.com/p/KswYQPNW8w/)

I'm certain the hardware I have shouldn't be as painfully slow as it is, it took me 20 seconds to simply open that 2KB text file to paste !!

---

### Post by ajgreeny on 2020-11-03
What does command ```
free -mw
``` show as output?  I wonder if you have a memory leak from something running out of control.
I agree your hardware appears good enough, though you might be better with a different DE, such as Xfce as in Xubuntu.

If you try a different DE version like Xubuntu as a live system you may get a better idea of how that will run compared to Ubuntu with its higher resource reqiremenmts.

If that give us no real clues let's see what you get from command ```
top
```

---

### Post by HermanAB on 2020-11-03
If you want better speed on an older machine, install XFCE and ditch Gnome.

If you want the machine to fly like you just bought a new one, ditch Ubuntu and install Slackware or OpenBSD.  You'll be blown away by the difference.

---

### Post by cable_guy on 2020-11-03
> **ajgreeny said:**
> What does command ```
free -mw
``` show as output?  I wonder if you have a memory leak from something running out of control.
I agree your hardware appears good enough, though you might be better with a different DE, such as Xfce as in Xubuntu.

If you try a different DE version like Xubuntu as a live system you may get a better idea of how that will run compared to Ubuntu with its higher resource reqiremenmts.

If that give us no real clues let's see what you get from command ```
top
```

[HTTPS://paste.ubuntu.com/p/T6t5PKVyxk](HTTPS://paste.ubuntu.com/p/T6t5PKVyxk)

Top is showing nothing used, 2% CPU here and there.

---

### Post by cable_guy on 2020-11-03
> **HermanAB said:**
> If you want better speed on an older machine, install XFCE and ditch Gnome.

If you want the machine to fly like you just bought a new one, ditch Ubuntu and install Slackware or OpenBSD.  You'll be blown away by the difference.

I may have to. All I've ever used this machine for is a file server, downloading from newsgroups, and it's always flown. I've used a GUI in the past but admittedly ran most things via cli.  but it's now just as slow from the cli so I don't think it's the GUI causing the slow down.  I really am puzzled, no distribution should run this slow, it's bizarre.

I appreciate the other distribution suggestions though I wonder if my install is "corrupt" in some way o_0

---

