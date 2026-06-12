---
title: "Network manager (nm-applet) wont workap properly on my desktop!"
date: 2007-05-29
forum: General Help
---

### Post by loathsome on 2007-05-29
Hi there,

There's some kind of strange problem going on with my nm-applet (The GNOME network manager). It shows all the wireless networks, but whenever I try to connect to one, it just goes like «enter WEP-key» &#8594; loading &#8594; loading &#8594; «enter WEP-key» forever. (Yeah, I'm 100% the key is correct, it's not that). Everything works flawlessly if I connect manually via «iwconfig» in bash. nm-applet can't connect to a wired network either. This is a fresh feisty install (even happens in the LiveCD). I'm using a Linksys WMP54G wifi card, if that matters. On my laptop (that's running an Intel IPW3945), everything works just fine.

Appreciate your answers! Thanks a lot.

---

### Post by r343l on 2007-05-31
I have exactly the same issue (also using ipw3945). I have to setup fully my WEP network config in /etc/network/interfaces. If I try to use the gnome network manager it just never connects (lots of wpa_supplicant messages). It's always been that way for me (been on feisty since jan/feb). I've been planning on doing a fresh install to see if that would fix it, but it sounds like it won't.

---

### Post by r343l on 2007-05-31
And I should read more carefully -- you have it *working* with the ipw3945 driver. Hmmm...

---

### Post by chili555 on 2007-06-02
Do you really need Network Manager on your desktop? Don't you really just want to boot and automatically connect to your home router or access point?

I suggest removing NM and setting your ESSID and encryption in /etc/network/interfaces and be done.

---

### Post by zanglang on 2007-06-02
Not sure if this is the same problem, but it's the same for us Linksys G650+ users. In my case, NetworkManager doesn't play WEP/WPA well with my chipset (ACX111), so the rotating green thingy rotates for a long time until it gives up. Solution: I had to replace the driver with ndiswrapper.

My suggestion is check the Tutorials & Tips subforum and see if there are any guides specifically for setting up your wireless card to use NetworkManager.

---

