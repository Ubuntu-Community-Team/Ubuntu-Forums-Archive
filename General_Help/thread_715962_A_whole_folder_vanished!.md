---
title: "A whole folder vanished!"
date: 2008-03-05
forum: General Help
---

### Post by cabbarosman on 2008-03-05
I left my laptop with Firefox and KGet running for a couple of hours. When I returned I found the kget with all the downloads stopped at 99% and the overall performance slowed down. So, as usual, i thought a reboot would refreshen up the performance. After the most of the black&white shutdown sequence was done, i had to shut down the computer manually by pushing the power botton.

When i booted again back to the ubuntu, i was greeted by a black background. After a little search I realized my whole pictures subfolder containing my photo album was vanished along the background image. As you can imagine, I am very frustrated right now. I was using this Dell 1420n for my main photo archive and I lost many of the photos I took! :mad:

This happened just now and I am sorry if this post isnt all very coherent but I am extremely frustrated right now. Do you now how I can get back my folder?

---

### Post by kellemes on 2008-03-05
You're using your filemanager (nautilus) to search your folder?
Check "Show Hidden Files" so  at least you know it's not a hidden folder..
Also you can search for a file you absolutely know existed in the folder, suppose it's name is "prettypicture.jpg" you can do the following from terminal.

```

sudo updatedb
sudo locate prettypicture.jpg

```

See if it turns up.

---

### Post by TheExplorer on 2008-03-05
I can confirm the magical Ubuntu feature of vanishing folders. Recently I was just surfing the net and listening to music... after some time a fired up Midnight Commander and found out that /opt has mysteriously left my HDD. What's that huh? Have any of you ever encountered such a thing?

---

### Post by kellemes on 2008-03-05
> **TheExplorer said:**
> I can confirm the magical Ubuntu feature of vanishing folders. Recently I was just surfing the net and listening to music... after some time a fired up Midnight Commander and found out that /opt has mysteriously left my HDD. What's that huh? Have any of you ever encountered such a thing?

No, I've playing with GNU/Linux for a long time and never saw folders mysteriously disappear.
But maybe I was lucky..;-)
I do actually assume I've been lucky and so I create backups every day, and sometimes even more often.

---

### Post by cabbarosman on 2008-03-05
Yes, I use nautilus as my default file manager.

The "Show Hidden Files" option was the first thing i tried and didn't help. I have just tried  to 'locate' files as you suggested but also couldn't find anything.

I'm sorry for not being very specific about my problem but as you can imagine from my first post I don't really know which running process caused the folder to disappear and I really didn't pay a lot of attention to specific details when I rebooted since I routinely reboot to improve performance.

---

