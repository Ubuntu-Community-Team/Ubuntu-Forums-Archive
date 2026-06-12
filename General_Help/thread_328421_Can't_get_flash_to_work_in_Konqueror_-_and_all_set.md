---
title: "Can't get flash to work in Konqueror - and all settings look to be right..."
date: 2006-12-30
forum: General Help
---

### Post by malacoda on 2006-12-30
Hi All,

I'm having one hell of a time trying to get flash to work in Konqueror - never had this much trouble getting to it work in Konq before and don't know what to try next...

As it is I have:

- Konq java path set to: /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

- have all the Firefox flashplugins scanned in and listed in Konq's config. settings

- have even switched from Blackdown Java to Sun Java and made sure that I removed the Blackdown plugin and installed the Sun plugin (and verified Firefox still worked after doing so...)

And yet still no flash in Konq...

Any thoughts or suggestions?

Malac

---

### Post by malacoda on 2007-01-01
Well, still no luck.  

Made sure konq-plugins and konqueror-nsplugins were installed and even uninstalled and reinstalled them along with Konqueror and still no luck...

I get the feeling this is going to be a bit of a long-term troubleshoot and quite a learning experience - if I can ever get it figured out...

Again,  any thoughts or ideas please send my way.

Malac

---

### Post by Mau on 2007-01-15
Hey,
I've been having the exact same problem.  I downloaded the flash 9 beta from the Adobe website, put it in .mozilla/plugins, and it still wouldn't work.

But!  I have finally found a solution!

You have to remove KDE's Flash interpreter.  For me, I think all I had to remove was konqueror-plugins-gnash.  This started making Flash work great, even with a 'Start' button (just what I wanted).

---

### Post by malacoda on 2007-01-15
Thanks Mau,  I'll try it out tonight when I get home from work.  Hopefully it'll do the trick as it's the last thing I need to get working in order to have my linux system set-up and running just the way I want it...

Regards,
Malac

---

