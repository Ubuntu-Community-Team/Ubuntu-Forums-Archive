---
title: "Big Screensaver problem"
date: 2008-06-03
forum: General Help
---

### Post by Leo the Lion on 2008-06-03
I'm running Gutsy on a HP Pavilion dv2000 with an Intel Mobile GM965/GL960 graphics card. Every time I try to access the screensaver window through System>Preferences>Screensaver, my system reboots. The screensaver window comes up and the system immediately reboots. I've read that maybe the driver for the graphics card I'm using isn't compatible with screensavers on Gutsy. Does anybody have an idea of what might be happening? 

If not, how do I disable screensaver altogether without going through Preferences?

Thanks for the help.

---

### Post by Leo the Lion on 2008-06-03
Anybody??

---

### Post by Leo the Lion on 2008-06-04
bump

---

### Post by Leo the Lion on 2008-06-09
Any ideas?

---

### Post by Victormd on 2008-07-03
E aí Leozão,
Já resolveu o problema do screensaver?
entre no terminal e digite:
```
gconf-editor
```
depois vá em:
> /apps/gnome-screensaver
e desmarque
> idle_activation_enabled
Isso vai desativar o screensaver. Se vc quiser dar uma olhada no arquivo de configuração dele, vá em:
```
sudo gedit /etc/X11/app-defaults/XScreenSaver
```
E dê uma olhada pra ver se tem alguma coisa relacionada co open-gl. Acho q o seu problema pode estar relacionado com isso.

Uma outra coisa q pode estar afetando (se vc usou) é o **noapic** no menu.lst. Se vc teve q adicionar isso à sua linha do kernel, pode estar avacalhando com vc...

---

### Post by bfuzze on 2008-07-14
I'm having the same problem, can anyone translate the above instructions (to english)?

Thanks.

---

### Post by Victormd on 2008-07-17
> **bfuzze said:**
> I'm having the same problem, can anyone translate the above instructions (to english)?

Thanks.

Open the terminal and type:
```
gconf-editor
```

Then go to:
> /apps/gnome-screensaver
and uncheck
> idle_activation_enabled
This will disable the screensaver

If you want to get the screensaver working, you can take a look at the screensaver configuration file:
```
sudo gedit /etc/X11/app-defaults/XScreenSaver
```
and check to see if there's anything open-gl related. I think the problem might be related to your open-gl rendering. Another thing that can affect the screensaver behavior is the "noapic" instruction in your menu.lst. If you had to add this to the kernel line, that can be the problem as well.

---

