---
title: "Firefox = Too Slow"
date: 2007-10-01
forum: General Help
---

### Post by Grumpy Gus on 2007-10-01
Why is Firefox sooo friggin' slow?! Is there anything I can do to speed it up? :mad:

---

### Post by mcduck on 2007-10-01
Slow in what way? Slow to resolve addresses, slow to load pages or slow as in lagging user interface? Or slow to open when starting it the first time after boot?

---

### Post by Grumpy Gus on 2007-10-01
Slow to load pages. It takes forever! Swiftfox does it lickety split! But I can't get Swiftfox to work for some reason. :mad:

---

### Post by mindtrick on 2007-10-01
Try Fasterfox extension.

---

### Post by Grumpy Gus on 2007-10-01
I read that this could be due to something called Pango. What is it? And can I get rid of it? :mad:

---

### Post by rfruth on 2007-10-01
Too many themes / extensions (or a conflict) ?  I use Firefox (2.x) its no speed daemon but about = to Netscape, Opera etc

---

### Post by kerry_s on 2007-10-01
> **Grumpy Gus said:**
> I read that this could be due to something called Pango. What is it? And can I get rid of it? :mad:

sudo gedit /etc/firefox/firefoxrc

# which /dev/dsp wrapper to use
ICEWEASEL_DSP="aoss"
MOZ_DISABLE_PANGO=1
XLIB_SKIP_ARGB_VISUALS=1

---

### Post by kerry_s on 2007-10-01
> **Grumpy Gus said:**
> Why is Firefox sooo friggin' slow?! Is there anything I can do to speed it up? :mad:

here's my user.js, unpack it and put it in your .mozilla/firefox/funky-name, then just restart firefox.

---

### Post by strabes on 2007-10-01
If you don't use a lot of extensions (and even if you do) then epiphany should be a perfectly suitable replacement.

---

### Post by mcduck on 2007-10-01
> **Grumpy Gus said:**
> I read that this could be due to something called Pango. What is it? And can I get rid of it? :mad:

Pango doesn't affect the speed of loading pages, only the speed of rendering pages when they are loaded.

If the loading speed really is your problem there are several configurations that can be done in about:config, but I'd suggest getting the Fasterfox extension instead as it'll handle all those hacks for you.

---

### Post by hallowname on 2007-10-01
Swiftfox, Opera, or Konqueror... in that order... try to install swiftfox from a terminal with the swiftfox-installer

just chmod +x swiftfox-installer
then ./swiftfox-installer
and follow the instructions and type 'swiftfox' in the terminal or make a shortcut to the 'swiftfox' command

---

### Post by sstusick on 2007-10-01
Fasterfox has helped speed up Firefox for me :-D

---

