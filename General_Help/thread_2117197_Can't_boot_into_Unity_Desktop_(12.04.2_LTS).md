---
title: "Can't boot into Unity Desktop (12.04.2 LTS)"
date: 2013-02-17
forum: General Help
---

### Post by ooleyguy on 2013-02-17
Howdy. I played around with GRUB Customizer and when I rebooted, I can't load Unity anymore (not that that is so terrible) but I can load into Gnome Classic and Cinnamon desktops just fine.

When I try Unity, all I get is the background and a mouse and I have to Ctrl+Alt+F1 to tell the system to reboot.

I tried 'sudo apt-get install unity', but it just tells me everything is installed.

Any ideas?

---

### Post by PJs Ronin on 2013-02-17
I had exactly the same problem this morning (no unity, no panels, just a mouse and background.  I 'solved' the problem by opening a terminal (ctrl-alt-t still worked) and issuing command:```
sudo unity --reset
```Still had some work to do after that, but at least the DE was back and running.

---

### Post by Bucky Ball on 2013-02-17
Hi ooleyguy,

I have deleted your duplicate thread which was in ***Desktop Environments.***

Please refrain from posting duplicate threads. It is confusing, dilutes community effort (and your chances of getting help) and is against forum rules. Here is a (non-exhaustive) list of reasons a thread may be closed from the ***Code of Conduct***:

[QUOTE=Code of Conduct]
    The thread has run it's course and posts have begun repeating themes
    The thread has degraded into an argument
    _The thread topic is a duplicate of another current and active thread_
    The thread is very old.
[/QUOTE]

Thanks and good luck,
BB

---

### Post by ooleyguy on 2013-02-18
Thank you, Bucky. I couldn't figure out how to delete that other post.
 
Thanks, Ronin. I will try that. I did it in a terminal I got to with CTRL-ALT-F1, but it just gave me a load of errors there.

---

### Post by Bucky Ball on 2013-02-18
> **ooleyguy said:**
> Thank you, Bucky. I couldn't figure out how to delete that other post.

You can't. ;)

---

### Post by PowerBarry43 on 2013-02-18
Hi

This is a bit like buying a new wheel to fix a flat tyre but you could try going to tty1 (CTRL+ALT+F1) and running

```
sudo apt-get purge ubuntu-unity
sudo apt-get install unity
```

but proceed with caution as apt-get purge will completely remove all configuration files associated with unity.

Hope this helps!

Barry

---

### Post by ooleyguy on 2013-02-19
Thanks all. Apparently using sudo unity --reset resets the root's unity or God's unity or the great pumpkin's unity, or anyone's unity but mine. I left the sudo off and I got Unity back.

---

