---
title: "Strange Printer Config Problem"
date: 2008-07-02
forum: General Help
---

### Post by bobulator on 2008-07-02
~~~ THIS THREAD IS NOW SOLVED ~~~


Whenever I start up system-config-printer, the options and buttons are all greyed out. As a result, I'm unable to add any printers.

I'm guessing there's a problem communicating with the CUPS server, but apart from that I have no idea.

Thanks in advance,
Bob

---

### Post by brian_p on 2008-07-02
> **bobulator said:**
> Whenever I start up system-config-printer, the options and buttons are all greyed out. As a result, I'm unable to add any printers.

I'm guessing there's a problem communicating with the CUPS server, but apart from that I have no idea.

You could try replacing the cupsd.conf with cupsd.conf.default in /etc/cups and restarting cups. See where that gets you.

```
sudo mv /etc/cups/cupsd.conf /etc/cups/cupsd.conf.july2

```

```
sudo cp /etc/cups/cupsd.conf.default /etc/cups/cupsd.conf

```

```
sudo /etc/init.d/cupsys restart

```

---

### Post by bobulator on 2008-07-04
Well I'll be darned... 

I can't find a cupsd.conf or cupsys file at all.

It's quite possible this is the problem.

(i think i'll reinstall cups via synaptic)

---

### Post by bobulator on 2008-07-04
Turns out that cupsys was not actually installed, so I installed it and all's well.

---

### Post by brian_p on 2008-07-04
> **bobulator said:**
> Turns out that cupsys was not actually installed, so I installed it and all's well.

Well, your guess was correct - there was a problem communicating with the CUPS server. You were nearly there by yourself!

---

