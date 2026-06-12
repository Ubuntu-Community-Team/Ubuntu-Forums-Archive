---
title: "Fiesty screwd everyting up, Ipod"
date: 2007-05-13
forum: General Help
---

### Post by bestial on 2007-05-13
So, I finally upgrade to fiesty in the belief that everything where gonna be so smooth. I have'nt hade anything else then trubble since I did. The most recent thing is that my ipod doesn't show up in neither nautilus, thunar or in banshee. This is driving me crazy. I have tried, sudo mount /dev/sdb2 /media/ipod, which worked in it's own kinda way, the ipod shows up in /media but not in banshee nor amarok.

So, anyone have any solution to this? It's kinda bizarre that something that used to work in the earlier versions of ubuntu suddenly doesn't.

But as always, it works for some, and don't for others, I guess.

---

### Post by takuhii on 2007-06-06
Amarok should detect your iPod automatically, if not go to tools > configure amarok > media devices (i think it's called that) and it'll list your iPod as /dev/sda2 (something like that), you then pick the plugin you want to use to handle the device and ipod should be one of them, think click OK.

Sometimes Amarok needs a push in the right direction, once it's found the iPod, click the devices tab on the left hand side you'll see a tools icon partially hidden by a >> symbol, click the >> and it'll give you some ipod related options, you now need to select the type of ipod you have (this ensures you get album artwork etc...

Good luck, I got my iPod working with amarok but the MP3s never played properly, so I'm still looking into other music managers...

---

