---
title: "Trouble with gtkpod &amp; rhythmbox when ipod is connected"
date: 2008-03-25
forum: General Help
---

### Post by DiggaUK on 2008-03-25
Thank you for reading my plee for help :-)

I have Ubuntu 7.10 and an iPod Nano 1st Generation 2Gb. Now I love Ubuntu, and have been using it for 3 months now with no problems at all. That is until I tried to connect my iPod!!!

I done my research first, and checked to see what was best for transferring music to it, and came to the conclusion that gtkpod was the way to go. So I installed it via add/remove applications, and started the program 1st time. I changed the mount point to 'mount/NANO/' (where automount puts my ipod), and restarted the program.

Now, whenever I connect my iPod, it's automatically mounted and gtkpod starts... then closes immediately, and this haopens every time. So I start gtkpod from terminal to see what error messages are reported. Here's what I get:

** (gtkpod:16022): CRITICAL **: ipod_parse_artwork_db: assertion `itdb' failed
Segmentation fault (core dumped)

So, I try the second option of using Rhythmbox instead to connect to my iPod, and guess what. This does exactly the same. Closes when I connect my ipod. The error message I get with this is:

** (rhythmbox:16029): CRITICAL **: ipod_parse_artwork_db: assertion `itdb' failed

(rhythmbox:16029): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

So there you have it! I haven't got a clue what to do or how to fix it. Have you?

I know I should get rid of my iPod, and buy a simple MP3 player, but it was a present from my wife, and I like the look and feel of it.

If I haven't posted enough info for a full diagnosis, I apologize in advance, and will give more details on request.

Thanks, DiggaUK

---

### Post by terto on 2008-03-25
I have had some odd stuff happen to me when I plug in my nano. I have never checked the error log though. What worked for me was going to the mount point, deleting everything (that does get rid of all your songs) then recreating the folders and DBs with gtkpod. that does the trick. I hope you have a backup of your songs so you can try this one.

Cheers.

---

### Post by meer_mortal on 2008-04-21
thanks for your help. worked perfect I just removed the itunes folder on my ipod and and start gtkpod up again. and sweet.

cheers

---

