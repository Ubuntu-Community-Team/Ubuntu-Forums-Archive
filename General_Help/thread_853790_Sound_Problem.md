---
title: "Sound Problem"
date: 2008-07-08
forum: General Help
---

### Post by Metallic_Silence on 2008-07-08
When I'm listening to music, it will cut out sometimes, then cut back in. I've used Banshee and Rhythmbox, and they both do the same thing. Also, I have a volume control wheel on my laptop and when I use it, nothing happens-I have to use the volume control on the tool bar, so could you help me? I'm using Hardy 8.04.

Thanks in advance :)

---

### Post by iaculallad on 2008-07-08
Does that happen when at the same time you're browsing web pages loaded with flash files?

---

### Post by Metallic_Silence on 2008-07-08
Ya it does. It will even when Im not surfing, but not as often.

---

### Post by iaculallad on 2008-07-08
Try installing the audio support wrapper for non-free Flash plugin if it could help resolve that problem:

```
sudo apt-get install libflashsupport
```

---

### Post by Metallic_Silence on 2008-07-08
> **iaculallad said:**
> Try installing the audio support wrapper for non-free Flash plugin if it could help resolve that problem:

```
sudo apt-get install libflashsupport
```

I've already tried that, and it got my sound working on firefox again, but my music still cuts out.

---

### Post by iaculallad on 2008-07-08
Does this holds true when using Totem/Mplayer?

---

### Post by Gonzalo_VC on 2008-07-08
[COLOR="Navy"]In my Acer 5043 laptop, sound was absent with (K)Ubuntu up to 7.10.
Now with 8.04 and Poseidon Linux 3.0 is working, but is not so good (not powerful).
:confused:
Any ideas?[/COLOR]

---

### Post by Metallic_Silence on 2008-07-08
> **iaculallad said:**
> Does this holds true when using Totem/Mplayer?

I haven't tried those, but Ill give them a shot and get back to you in a bit. Thanks.

---

### Post by Metallic_Silence on 2008-07-08
> **Gonzalo_VC said:**
> [COLOR="Navy"]In my Acer 5043 laptop, sound was absent with (K)Ubuntu up to 7.10.
Now with 8.04 and Poseidon Linux 3.0 is working, but is not so good (not powerful).
:confused:
Any ideas?[/COLOR]

Try ```
alsamixer
```
It worked for me. The volumes might just be on a low setting. Navigate with your arrows, and when your finished go back into terminal and type ```
sudo alsactl store
```

---

