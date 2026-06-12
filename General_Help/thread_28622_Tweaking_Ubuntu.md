---
title: "Tweaking Ubuntu"
date: 2005-04-21
forum: General Help
---

### Post by defkewl on 2005-04-21
Excuse me,

I have few questions about tweaking Ubuntu
1. Does installing X server makes our Linux run much slower, assuming that X server takes memory resources and it would go even slower if we use a display manager such as Gnome?

2. Does our Graphic card has any relation with the speed? I have an on board VGA with 128 MB SDRAM and 32 MB VGA memory.


Yesterday I installed JBoss App Server in Ubuntu with X server and Gnome as the display manager. Then I access my JBoss from the sama machine from browser and it affect other applications performance. It's so difficult for me even to move the mouse cursor.

Anybody can give me some clue on this?

---

### Post by andvaranaut on 2005-04-21
Hi defkewl
[QUOTE=defkewl]Excuse me,

I have few questions about tweaking Ubuntu
1. Does installing X server makes our Linux run much slower, assuming that X server takes memory resources and it would go even slower if we use a display manager such as Gnome?
[/quote]

Installing per se does not, but running it does, of course. This is specially noticeable if your computer is quite old.

> 
2. Does our Graphic card has any relation with the speed? I have an on board VGA with 128 MB SDRAM and 32 MB VGA memory.


Not directly (unless you want to use 3D acceleration or something very fancy). However, if you are using shared memory for your VGA, the 32 Mb you use for it are substracted from the 128 Mb total memory of your computer, so that only 96 Mb are available for applications.

> 
Yesterday I installed JBoss App Server in Ubuntu with X server and Gnome as the display manager. Then I access my JBoss from the sama machine from browser and it affect other applications performance. It's so difficult for me even to move the mouse cursor.

Anybody can give me some clue on this?

I don't have much experience with jboss, but it's a complex application and is written in Java, which essentially means that it's probably a memory hog. 96 Mb is **very low** to run complex applications, so that running Gnome/KDE and jboss (and apache, I assume) at the same time would likely kill the performance of the machine.

Unless your computer is very old, the best advice I can give is updating to at least 256 Mb (more will not hurt, but you should see a very noticeable boost in performance). The slowing down of the computer is probably due to 'swapping', a process in which the system tries to get more free memory by storing unused memory parts in a special file on the HD. Needless to say, HD access is very slow compared to memory access. You probably see your HD light continuously during these slowdowns, don't you?

If you can't afford the memory, or your computer is too old to find modules for it, by all means reduce the amount of shared memory to 16Mb or 8Mb. You probably have an option on the BIOS to do that. Then, maybe you should look at using another window manager/desktop environment, such as icewm or xfce, in order to free more memory.

(BTW: I'm not implying that you have a old computer, it's that systems with only 128 Mb and shared memory are very rare these days ;))

good luck

---

### Post by yanik on 2005-04-21
If it's a 1Ghz or more, I'd say go with at least 512Mb.  get 1GB and stop worrying about the RAM thing for a while tho :)

---

