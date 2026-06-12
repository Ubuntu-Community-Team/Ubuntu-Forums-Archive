---
title: "No menu icons and other menu graffix missing in Ubuntu Studio 14.04!"
date: 2016-08-22
forum: General Help
---

### Post by Parsifal1 on 2016-08-22
I'm super confused on what's going on here. I've been really struggling with this one. A friend of mine gave me a laptop he had lying around and I was stoked because I thought it would make an awesome project linux comp! So far, this has been THE most frustrating linux install I've ever had. 

The laptop is an Acer Aspire 4830tg. It has an i5 2410M and an nvidia Geforce GT 540m.

First I tried to install nvidia drivers only to find that this particular GPU isn't supported in 14.04 (I couldn't even boot!!). So I installed the dummy drivers after lot of tinkering. Finally I could get back into Ubuntu Studio. Still however, I had no Icons in my menus. Not all of them, but most of them. I tried to screen shot it but it won't let me screenshot when the applications menu is open.

It's not just the applications menu, but other weird things. No minimize maximize icons. No Terminal icon. There's no Wallpapers!! When I click into "Extra Office Applications" the whole box is blank! It's really bizarre lol. I tried running "xfdesktop," and it didn't help. I tried using rm -R ~/.cache/sessions/* . Nothing. I've scoured le' Google to no avail and feeling like I've exhausted all the available resources I could find, so I'm finally coming for help. If anyone has some idea what might be going on, I'd love some insight. At this point I don't even know where to look anymore.

---

### Post by craftedvenom on 2016-08-23
Hmm.. Probably Missing system Files.. Did You Try To Reinstall? (Through Media)

---

### Post by Parsifal1 on 2016-08-23
Sorry for the tripple posts, the website was freezing and saying that my posts weren't going through and eventually it stopped loading all together. 
 
I finally gave up and reinstalled. The problem just kept getting worse. I eventually realized that it was image files in general that I couldn't view. I would open a Jpeg or something but it would just be a grey picture. I was reading all this stuff about how the nvidia geforce gt 540m was incompatible with Linux (which may be true) and that I needed to install Bumblebee. After installing and reinstalling Bumblebee and still the same problem persisting I gave up and just reinstalled. You are correct, it fixed the problem.

This was a new install and I think it happened after the first time I updated the system. My hypothesis is that my internet throttled and something one a download/install must have failed but I didn't catch it. No way to no for sure, I was never able to track the problem. This was definitely one of the weirder installs I've had with Linux. Either way, got things working now!

---

