---
title: "DVD quality"
date: 2005-05-08
forum: General Help
---

### Post by Neo1275 on 2005-05-08
Hey guys new Ubuntu user here. I must say that this was the easiest linux install I've ever had and I've used Mandrake, Red Hat, Suse, and Gentoo before. Anyway I have a question about dvd's, I'm currently using Xine and I'm wondering if it's possible to increase the quality. What I mean is if any of you have experience with Windoze and have used the ffdshow filter with a dvd player like zoom player it allows you to increase certain settings like resizing the video or increasing the sharpness etc. I'd like to know if there's anything like that for linux. Or perhaps there's a setting within Xine that I'm unaware of. Any help  is appreciated. Thanks

P.S. I just thought of another question related to Xine. Is there a way to "bookmark" my dvd's so that if I stop the playback or have to restart Xine I can resume from where I left off. Or is there another player that supports this function. Or is there a plugin or third party program for Xine that will do this. Thanks again

---

### Post by eivind on 2005-05-09
Kaffeine has some quality settings. This is a kde program, but you should be able to install it without adding all kde packages. Just do 

sudo apt-get install kaffeine

and play with the settings there.

Good luck!

Eivind

---

### Post by calt129 on 2005-11-14
If you're using Xine (or gxine, whatever) try switching the video driver from "auto" to "xshm", i.e. see Preferences->Video->(First tab), if you're not seeing this tab, switch to "Advanced" mode on the very first "gui"-tab.

For example, a few guys recommend "XV"-mode, but on my laptop, "xshm" gives the best results.

---

