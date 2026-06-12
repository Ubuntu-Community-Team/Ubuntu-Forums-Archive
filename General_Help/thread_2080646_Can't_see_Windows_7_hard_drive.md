---
title: "Can't see Windows 7 hard drive"
date: 2012-11-04
forum: General Help
---

### Post by Spaceman9 on 2012-11-04
Yesterday I installed Ubuntu 12.04 LTS with Wubi on a drive running Windows 7. The file manager in Gnome can't find the part of the drive that has Windows on it. I used to have Kubuntu installed on a desktop and Krusader had no problems finding the Windows files in Windows 98SE.

What do I have to do to set up the file manager in Gnome so I can see files in Windows when I'm running Ubuntu? Thanks for any help.

---

### Post by jerome1232 on 2012-11-04
When using Wubi, you can find your Windows files under /host.

Just open Nautilus(that's the file manager), click File System in the left hand pane and double click on host. If you want you can press Ctrl+D to bookmark the location and it will show up in that left hand pane.

---

### Post by Spaceman9 on 2012-11-04
> **jerome1232 said:**
> When using Wubi, you can find your Windows files under /host.

Just open Nautilus(that's the file manager), click File System in the left hand pane and double click on host. If you want you can press Ctrl+D to bookmark the location and it will show up in that left hand pane.


Thanks veery much for the reply jerome1232;12337009. I tried it and I found the files in Windows. Is there anyway to Give Nautilus 2 panels like Krusader has? Or should I just use Krusader?

---

### Post by jerome1232 on 2012-11-04
> **Spaceman9 said:**
> Thanks veery much for the reply jerome1232;12337009. I tried it and I found the files in Windows. Is there anyway to Give Nautilus 2 panels like Krusader has? Or should I just use Krusader?

On my setup, 12.04 LTS using Unity, I can press F3 and get a second pane. Nautilus can also do tabs, which is what I use instead of panes.

---

### Post by Spaceman9 on 2012-11-04
> **jerome1232 said:**
> On my setup, 12.04 LTS using Unity, I can press F3 and get a second pane. Nautilus can also do tabs, which is what I use instead of panes.


Okay, thanks again. I'll do that then.

---

