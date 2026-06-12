---
title: "Restore /usr/share/fonts on 10.04?"
date: 2013-10-24
forum: General Help
---

### Post by ChRaab on 2013-10-24
I did something extremely stupid.
I'm currently working on a 10.04 system (work-related), and since I was missing some fonts I decided to simply copy some over from my own, 12.10 system. I ran


```
cp -R <12.10 root>/usr/share/fonts/truetype/* /usr/share/fonts/truetype/

```

Immediately, terminal and window header fonts got completely messed up, although chromium still shows everything correctly, as does nautilus.
How can I restore this directory? Is there anything else I have do afterwards?


Thanks a bunch,
Chris


For grins and giggles, here's how it looks:
[http://i.imgur.com/8IbShgK.jpg](http://i.imgur.com/8IbShgK.jpg)

Someone told me to run ```
sudo fc-cache -fv
```, here's the output from that:
[http://pastebin.pw/y8r46n](http://pastebin.pw/y8r46n)

---

### Post by ChRaab on 2013-10-25
[COLOR=#333333][FONT=UbuntuRegular]Just want to add how this was resolved: Simply restarting X using[/FONT][/COLOR]
gnome-session-save --force-logout
[COLOR=#333333][FONT=UbuntuRegular](from an X terminal), next login everything was Ok again.[/FONT][/COLOR]

---

