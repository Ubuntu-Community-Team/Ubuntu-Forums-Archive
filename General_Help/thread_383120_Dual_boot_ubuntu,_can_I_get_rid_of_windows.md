---
title: "Dual boot ubuntu, can I get rid of windows?"
date: 2007-03-12
forum: General Help
---

### Post by wildzer0 on 2007-03-12
I recently installed Ubuntu on my laptop, I like it a lot and have managed to replace all my favorite windows applications with open source alternatives. So I don't really need windows anymore, but right now it's taking up 56 gigs of my 60 gb hard drive. Is there a way to just make ubuntu swallow my windows partition?

---

### Post by Kateikyoushi on 2007-03-12
Yes there is, I recommend to do it with gparted, it is easy to use and has a gui, you can use it to  delete the windows partition and resize the ubuntu, or you can make a /home partition in the free space. 
You can not work on partitions while mounted so unmount windows first, in case you decide to resize the ubuntu partition you can do it from the live disc.
Howto move to /home partition. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by natetheinfamous on 2007-03-13
I too am planning to Uninstall windows in the near future (my windows partition crashed... go figure) so I thought I would chime in on this thread, I hope that's alright. Just a quick question about GRUB: after removing the windows partition as mentioned above, is there any necessary configuration that has to be done to turn off the boot menu in grub and refresh it's OS list?

---

### Post by bryonak on 2007-03-18
> **natetheinfamous said:**
> I too am planning to Uninstall windows in the near future (my windows partition crashed... go figure) so I thought I would chime in on this thread, I hope that's alright. Just a quick question about GRUB: after removing the windows partition as mentioned above, is there any necessary configuration that has to be done to turn off the boot menu in grub and refresh it's OS list?


1. Open /boot/grub/menu.lst with root access (like 'sudo nano /boot/grub/menu.lst'). Around line 20 you'll see this entry:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```

2. Uncomment the 'hiddenmenu' line:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

3. enjoy!


There might be ways to "refresh" the boot menu, but I'd recommend editing it by hand. It's at the bottom of the /boot/grub/menu.lst file. Just look at the entries (1 entry consisting of 5 lines for Ubuntu and ~7 lines for Windows) and delete the ones you don't like ;)

---

