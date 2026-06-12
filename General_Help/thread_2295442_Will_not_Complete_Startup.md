---
title: "Will not Complete Startup"
date: 2015-09-18
forum: General Help
---

### Post by mltriebe on 2015-09-18
My Kubuntu install was working fine then it started doing this on me.  I tried the recovery console with no luck but I am willing to redo anything I have already tried.

Please see the pic.

---

### Post by Bucky Ball on 2015-09-18
*Thread moved to **General Help**.*

Did you do an update then reboot and this happened? Install any new software? PPAs, drivers?

---

### Post by Bashing-om on 2015-09-18
mltriebe; Ho !

What results when booting older kernels ?

[INDENT][INDENT]proprietary drivers broke ?
[/INDENT][/INDENT]

---

### Post by mltriebe on 2015-09-18
I had just updated and I should have mentioned before I am running 15.04.

Mike

---

### Post by mltriebe on 2015-09-18
> **Bashing-om said:**
> mltriebe; Ho !

What results when booting older kernels ?

[INDENT][INDENT]proprietary drivers broke ?
[/INDENT][/INDENT]

Same thing with other kernels and I really don't recall if I have any proprietary drivers or how to check for them.  I do know the video drive is intel.

Mike

---

### Post by Bashing-om on 2015-09-18
mltriebe; Well, shoot 

So much for the thought of a broken proprietary driver; as Intel just works .

OK, my next thought is to see if you can boot to terminal. Once in terminal we have a means to investigate .
Boot to the grub boot menu. with the latest kernel selcted, press the 'e' key for edit mode -> boot parameters screen.
Arrow down and across to the terms "quiet splash vt_handoff"  replace these terms with the term "systemd.unit=multi-user.target" - without the quotes.
Key combo ctl+x to continue the boot process to TTY1 .
Log in here with your credentials .

Good so far ?

[INDENT][INDENT]now maybe we find out what is not going on
[/INDENT][/INDENT]

---

### Post by mltriebe on 2015-09-20
> **Bashing-om said:**
> mltriebe; Well, shoot 

So much for the thought of a broken proprietary driver; as Intel just works .

OK, my next thought is to see if you can boot to terminal. Once in terminal we have a means to investigate .
Boot to the grub boot menu. with the latest kernel selcted, press the 'e' key for edit mode -> boot parameters screen.
Arrow down and across to the terms "quiet splash vt_handoff"  replace these terms with the term "systemd.unit=multi-user.target" - without the quotes.
Key combo ctl+x to continue the boot process to TTY1 .
Log in here with your credentials .

Good so far ?

[INDENT][INDENT]now maybe we find out what is not going on
[/INDENT][/INDENT]

OK, then what?

Mike

---

### Post by Bashing-om on 2015-09-20
mltriebe; Great !

As you can get to this point, we know the system foundation is intact. We just have a problem in the upper layers.

From the terminal, let's see what happens, and errors reported when we start the GUI.
Terminal command:
```

systemctl isolate graphical.target

```

And you can look at the boot messages:
```

journalctl -xb

```

we try and see what the problem therein is.

[INDENT][INDENT]as we learn systemd
[/INDENT][/INDENT]

---

### Post by mltriebe on 2015-09-20
> **Bashing-om said:**
> ```

sudo systemctl isolate graphical.target

```

PolicyKit daemon disconnected from the bus.
We are no longer a registered authentication agent.

> **Bashing-om said:**
> 
And you can look at the boot messages:
```

journalctl -xb

```

To long, what am I looking for.

Mike

---

### Post by Bashing-om on 2015-09-20
mltriebe; Well !

Maybe my wires are crossed, or sumpthi'n - outdated ?

Let's try:
```

systemctl set-default -f  graphical.target

```

We are looking for errors in the journal, after the GUI starts . With a bit of research and homework I can learn how to filter the result of 'journalctl' . Will have to save that homework for when I reboot the system and boot up 15.04 .

[INDENT][INDENT]oh yeah -> that process of learning
[/INDENT][/INDENT]

---

