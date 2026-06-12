---
title: "Conky window displaying not at every session start"
date: 2017-01-24
forum: General Help
---

### Post by alain.roger on 2017-01-24
Hi,


my mom has Kubuntu 16.10 installed on her laptop.
I setup on her laptop, the same conky script as on mine.


While on my laptop the script start with desktop/session, on her laptop randomly it starts.
What i discovered (and from my point of view this is weird) it's that using ALT+TAB can switch and display the conky window on her desktop...but only if script is started because sometimes it does not start and i do not know why.


Any idea why it is needed to use ALT+TAB to display conky window while on my laptop conky windows is displayed normaly ?


thx

---

### Post by ajgreeny on 2017-01-24
Do you have any pause in the conky startup command in the "autostart applications" system on the problem machine.

Conky can not start properly if the DE is not fully up and running, so on my Xubuntu 16.04 the command used in my autostart settings is **conky -p 20**, ie giving a pause of 20 secs before the application starts.

It may also help to see the .conkyrc file (is that what you mean by conky script?) you are using.
Alt-Tab on my machine does not affect the conky display in any way, so maybe you have the window settings wrong; here are mine'
```
# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type desktop

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

---

### Post by alain.roger on 2017-01-24
yes the script that run conky script do a 60s pause before running it.
The script is EXACTLY THE SAME on my laptop and my mom laptop.
so why would it work correctly on my laptop and not on her ? it makes no sense :(

---

### Post by ajgreeny on 2017-01-24
In that case I have no idea why the difference in your conky uses.

I do not know Kubuntu, having not used it nor even tried it for about 7 years, so wonder if that might make any difference compared with Xubuntu, which I use.
I note from the info below your post that you say you are on 17.04 and your mother on 16.10; could that be the reason?

---

### Post by alain.roger on 2017-01-25
In fact the same script worked before on my mom's laptop. She uses Kubuntu 16.10 and nothing changed since except some updates linked to Ubuntu 16.10 (classical stuff)

---

