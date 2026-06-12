---
title: "Ubuntu server 7.10 only goes to Shell, is there no GUI?"
date: 2007-12-07
forum: General Help
---

### Post by hoist1138 on 2007-12-07
I'm stuck not knowing how to get to the "brown" desktop.
I turn on computer.....it tests and loads the kernel....
then the last "ok" just sits there. when I hit space bar, it then prompts me for my user name and password.
which gets me into the shell with my system, and I can run my commands like -ls  cd ../.. etc.......

Am I totally off base here? I went though all the download and install correctly, ran MD5 Checksum on the download, verified the disk after burning. I thought the GUI was supposed to come up automatically and then you could run Shell windows so you have the best of both worlds?

is there no GUI with the server version?
I will be eventually using this system to replace my hosting companies service. (But Not Yet THO :)
thank a ton
Jason

---

### Post by Kingsley on 2007-12-07
AFAIK, there's no GUI for the server edition. You can easily install one though. Just type this in.
```
sudo apt-get install gnome-core x-window-system-core gdm
```

---

### Post by hoist1138 on 2007-12-07
THANKS KINGSLEY! 
I really appreciate it!

---

### Post by ahmedfahaad on 2008-06-25
Hi,

i am getting this error after following your instruction to install gnome on my server edition v8.04....

Error states that:

Reading Package list.. Done
Building Dependecy tree.. Done
Reading State Information.. Done
[COLOR="Red"]E: could'nt find package gnome-core[/COLOR]

how could i provide this package.... do i need any ubuntu desktop edition cd to install gnome?

Thanks in advance,
Ahmed Fahad

---

