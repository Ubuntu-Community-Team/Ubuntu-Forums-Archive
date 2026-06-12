---
title: "Linux Mint Aurora Theme"
date: 2008-06-12
forum: General Help
---

### Post by dalinkwent on 2008-06-12
Hopefully this is in the right place, this is my first post here.

I've been using ubuntu for about 6 months or so, and I love it, but I haven't come across a theme I really liked until I installed Linux Mint on my girlfriends laptop.  I have to use ubuntu for 64 bit support on my computer (Folding@home), but I want her theme.  I've found a couple variations on the Aurora theme that comes with Elyssa, but none that are quite the same, and I really want it.  Does anybody know where I can get that exact theme, or how to copy it from her computer to mine?  I tried copying the .themes directory, but then I felt pretty stupid when I realized it was empty on both computers, so I came here for some help. Thanks

---

### Post by Xasz on 2008-06-12
[This?]("http://www.compiz-themes.org/content/show.php/LinuxMint-alpha?content=82713&PHPSESSID=3cd5213f9c1ed3b9abca5bddbd9959e1")
I just installed it 2 hours ago. It is indeed teh secksah

Actually, I think you may have meant [This]("http://www.linuxmint-art.org/content/show.php/+.aura+desktop?content=70099")

---

### Post by dalinkwent on 2008-06-13
Still not quite, it's a blue theme with transparency on the non-active title bars, I really dont think it's on gnome-look or even linuxmint-art, so I'm really looking for a way to transfer it from the laptop to my box.  I'm currently reinstalling everything on my computer because I screwed up my whole installation last night, but here's a screenshot if anybody has seen this theme out there anywhere.

---

### Post by dalinkwent on 2008-06-14
Come on, here on the ubuntu forums where you guys solve crazy technical problems all day long, nobody knows how to copy a theme from one computer to another?  I've made a little progress, I copied the /usr/share/icons, theme, and background folders over and I have the basic theme working now, but a lot of elements still don't work right. I lost the cool 3d buttons that the laptop has, along with the nice blue graphic in the background on tooltips and a few other minor things...what else am I missing?

---

### Post by Forlong on 2008-06-14
Do you know the name of the theme?

What's the output of ```
ls /usr/share/themes
``` on your Mint install?

---

### Post by dalinkwent on 2008-06-14
> ls /usr/share/themes
Aurora           Cassandra   Elyssa      Lightning     Murrine
Aurora-Midnight  Clearlooks  Emacs       Metabox       PepperMint
Barbara          Daryna      Gilouche    metacity-1    Raleigh
Carbon           Default     Human-Blue  Murrina-Blue  WildMint

The theme is called Aurora, and all the folders above (theme, icons, and backgrounds) without any errors, so I'm guessing everything is there.  I must be missing a folder, but since I can't find any info about copying themes I don't know what it is.

---

### Post by el_itur on 2008-06-14
Try copying those folders to ~/.themes and the matching /usr/share/icons/ folder to ~/.icons 

That should do the trick, you should have it available on the appearance app.

---

### Post by Forlong on 2008-06-15
> **dalinkwent said:**
> The theme is called Aurora
I see... well, I could have guessed that from the title #-o

Now do this on the Mint install:
```
dpkg -S /usr/share/themes/Aurora
```

---

