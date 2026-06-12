---
title: "X Window Not Starting"
date: 2005-07-06
forum: General Help
---

### Post by Jervous on 2005-07-06
First of all, I'd like to say hi to everyone, as I am new here. I am trying to boot Ubuntu from the Live CD so I can see how it is before I install it permanently. I am having a problem though.

After it loads, and it says everything is OK and running, it then says something like: "I cannot load the X Window." Can someone please tell me why? If it is important in any way, I had the SLAX Live CD running on this same machine yesterday.

Thank You,
Jervous

---

### Post by javiadip on 2005-07-07
Its prolly coz Ubuntu Live CD doesn't recognize your monitor, if u plan to install Ubuntu, you would have to manually configure your video card/monitor, its not that hard to do it manually. btw, what type of monitor/video card you using?

If you are using any other distro, I would suggest copy your xorg.conf if you are using Xorg or XF86Config is you are using xfree86. Sometimes it works, or you will have to make minor changes.

xorg.conf or XF86Config can be found in /etc/X11

---

