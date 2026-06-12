---
title: "Is my Folding at Home working?"
date: 2006-11-09
forum: General Help
---

### Post by sgstarling on 2006-11-09
I think I got it installed correctly. I 'started' it this morning. Tonight I checked the FAHlog.txt:

Here's the tail end of it, that shows my concern:

> [13:32:26] Assembly optimizations on if available.
[13:32:26] Entering M.D.
[13:33:06] Protein: p1809_Collagen_POG10new_refolding
[13:33:06] 
[13:33:06] Completed 0 out of 500000 steps  (0%)
[13:52:56] Writing checkpoint files
[14:12:49] Writing checkpoint files
[14:32:02] Writing checkpoint files
[14:50:06] Writing checkpoint files
[15:08:51] Writing checkpoint files
[15:26:09] Writing checkpoint files
[15:42:27] Writing checkpoint files
[16:01:59] Writing checkpoint files
[16:20:27] Writing checkpoint files
[16:38:36] Writing checkpoint files
[16:56:53] Writing checkpoint files
[17:15:08] Writing checkpoint files
[17:33:40] Writing checkpoint files
[17:51:50] Writing checkpoint files
[18:10:26] Writing checkpoint files
[18:28:44] Writing checkpoint files
[18:47:21] Writing checkpoint files
[19:05:36] Writing checkpoint files
[19:24:06] Writing checkpoint files
[19:42:24] Writing checkpoint files
[20:00:52] Writing checkpoint files
[20:18:59] Writing checkpoint files
[20:37:38] Writing checkpoint files
[20:55:54] Writing checkpoint files
[21:14:17] Writing checkpoint files
[21:32:31] Writing checkpoint files
[21:51:00] Writing checkpoint files
[22:09:10] Writing checkpoint files
[22:27:39] Writing checkpoint files
[22:45:42] Writing checkpoint files
[23:04:12] Writing checkpoint files
[23:22:24] Writing checkpoint files
[23:41:00] Writing checkpoint files
[23:59:15] Writing checkpoint files
[00:17:48] Writing checkpoint files
[00:36:12] Writing checkpoint files
[00:54:45] Writing checkpoint files
[01:12:59] Writing checkpoint files

So is this normal behavior? Will it ever tell me when I go from 0% to 1%? Can I really not have hit 1% yet? (My system is a 2 year old dell w/ celeron processor Um, it's over 1 gigahertz, but I forget the exact speed. And 1 gig of RAM.)

Are those "Writing checkpoint files" lines normal?

Thanks!

---

### Post by kthakore on 2006-11-09
I had folding at home running for weeks on my old compy and the fartest it got was 25%. This is because folding at home is throttled, meaning if you use anything on your compy folding at home diminishes CPU usage. So if you are using the compy reuglarly, I wouldn't be suprised that you have only hit 1%. Also open up system manager and view all processes, and see if folding at home is running.

---

### Post by sgstarling on 2006-11-09
Ok, I found that it IS running, but at only about 3%. It seems that nautilus was using 90+%. What's odd is that I had no nautilus open! Nautilus is the file manager, isn't it? Well I ended up killing nautilus, and then my folding ramped right up to 90+%! Yay! And I checked later, and it's up to 2% finished! WooHoo!

Just odd about that nautilus though...

---

