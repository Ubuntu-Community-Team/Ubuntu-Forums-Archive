---
title: "ata 1.01 : exception Emask status { DRDY }"
date: 2008-05-14
forum: General Help
---

### Post by flokky on 2008-05-14
On my (terminal) login screen, I'm getting some errors which might be related to the hard drives inside the system. I don't know however why they keep occuring or how to prevent them. I've tested them using S.M.A.R.T. and the pass the test

I'm running Ubuntu 8.04 LTS desktop edition.

The error I'm getting looks a bit like this and if I'm waiting long enough the error is repeated and outputted to the screen. I cannot find it in my logs anywhere.

[PHP][2282.965897] ata 1.01 : exception Emask 0x0 SAct 0x0 SErr 0x0 frozen
[2282.965949] ata 1.01 : cmd e3/00:1e:00:00:00/00:00:00:00:00/50 tag 0
[2282.965976] ata 1.01 : status : { DRDY }[/PHP]

Thanks for any help!

---

### Post by pedro_orange on 2008-05-14
Eeek! that doesn't look good. Pretty fubar'd if you ask me.

Might be helpful to print the kernel ring buffer:

```
dmesg
```

You want you might want to stick it into a file; it's quite long.

```
dmesg > bootup.messages
```

Or summit.

---

### Post by zhuqing789 on 2008-05-14
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by flokky on 2008-06-03
Hi Pedro_orange: Didn't know it was that bad.

Anyhow, I placed the [output of the dmesg to a file]("http://www.browse2.be/logs/bootup.messages") which might enlighten you, but to me it doesn't contain any valuable information.

I would like to understand why this keeps happening and what I can do to fix this. Thanks for the help!

---

### Post by caezar1 on 2009-01-30
Hello, I have a similar problem:

In other O.S. the solve is the surface format or similar, This encapsulates the bad sectors.

Exist any program in ubuntu linux to repair this HDD?

---

### Post by dcstar on 2009-01-30
> **caezar1 said:**
> Hello, I have a similar problem:

In other O.S. the solve is the surface format or similar, This encapsulates the bad sectors.

Exist any program in ubuntu linux to repair this HDD?

This might be of use:

```
man badblocks
```

---

