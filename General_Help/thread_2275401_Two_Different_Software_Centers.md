---
title: "Two Different Software Centers??"
date: 2015-04-25
forum: General Help
---

### Post by gr8 on 2015-04-25
I just installed Ubuntu 15.04 on my desktop and laptop. I did the exact same thing for both installations.


  The software center on my desktop has the app xdotool and I installed  it with no problems. When I search for xdotool on my laptop it flat out  won't show up. I get the "no item match xdotool" error. It's the exact  same app on the same 15.04 on the same software center!


  Why won't xdotool show up on my laptop? I know I can install it with  the command line but it's lack of appearing is driving me bonkers. Where  is it?

---

### Post by plucky on 2015-04-26
> **gr8 said:**
> I just installed Ubuntu 15.04 on my desktop and laptop. I did the exact same thing for both installations.


  The software center on my desktop has the app xdotool and I installed  it with no problems. When I search for xdotool on my laptop it flat out  won't show up. I get the "no item match xdotool" error. It's the exact  same app on the same 15.04 on the same software center!


  Why won't xdotool show up on my laptop? I know I can install it with  the command line but it's lack of appearing is driving me bonkers. Where  is it?

Have you checked you Software Sources are the same on both machines?

You probably need to enable the Partner Repository in Software Sources.

Good Luck

---

### Post by mcduck on 2015-04-26
When you search for xdotool, take a look at the bottom left corner of the Software Center. There's a small text button labelled "*Show 1 technical item*". Click that, and the package will appear.

By default the Software Center will hide command-line applications, libraries and other packages that aren't graphical applications (unless you already have the package installed and search with it's exact name).

---

### Post by gr8 on 2015-04-29
Nice tip, I never noticed the "show technical items" before. Strangely enough the xdotool package randomly showed up on my laptop and I just went ahead and installed it.

---

