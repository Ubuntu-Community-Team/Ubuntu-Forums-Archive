---
title: "Conky unity theme."
date: 2013-01-05
forum: General Help
---

### Post by critanime on 2013-01-05
Is there a unity themed conky setup. I have been playing with Gotham theme but it seems to flicker when I click menu items.

I am using ubuntu 12.4.

---

### Post by Frogs Hair on 2013-01-05
I don't know of any themes specifically for Unity . The only thing you would want is a theme that the conky window doesn't interfere with the launcher. I also see in the .conkyrc that there are no buffers and the line is added to control flicker.```
no_buffers yes
```

This is what I find on the other conky themes I have used or modified. For some reason the author excluded this. 

```
double_buffer yes
```

---

### Post by critanime on 2013-01-06
I tried setting that and it still flickers. So I had a look through the wiki type site for conky and tried this. 

```
own_window yes
```This fixed it. Since I applied this it has stopped flickering all together when I do anything on the desktop. The only drawback is that I can't right click round the area that conky is running. 

This is how I have the window set-up.

```
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```This is how it looks

[IMG]http://i.imgur.com/BktTI.png[/IMG]

I saw plenty of cool and complex looking conky configs. However I prefer simplicity with a bit of style thrown in. So gotham suited me more.

---

