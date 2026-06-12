---
title: "BUG: Soft lockup detected on CPU#0!"
date: 2007-02-20
forum: General Help
---

### Post by Rallyus on 2007-02-20
Hi,


I need some help, a month ago I decided to give Linux a try, and installed Kubuntu Edgy in my new laptop (HP Pavillion dv9082eu).


I´m having some trouble getting a working DSL conection at home, so last saturday I went to my girlfriend´s and used her connection.

There was a huge ammount of upgrades to download (120!) and after installing them and trying to restart, I was left stranded in the middle of the booting.

The symptoms are:

At every first boot into Kubuntu with the new Kernel 2.6.17-11 Generic, it freezes in the middle of the boot, after shutting down and trying again I have no problems.

Booting into the old 2.6.17-10 Generic I have no problems.

I removed the bootsplash to check out what was wrong and it freezes during boot with the following message:

[17179603.972000] BUG: SOFT LOCKUP DETECTED ON CPU#0!


I'm a newbie and need some help please!

---

### Post by Rallyus on 2007-02-20
Ok, tried to investigate a litle further ...


My Laptop has a Intel 3945 a/b/g wireless card, and I have noticed that the soft lockup only happens when I have the wireless and bluetooth conection disabled on the switch.


:confused:

---

### Post by Cannaregio on 2007-03-28
Indeed.

Similar things happened to me, and the following could be useful for people with similar problems. Maybe. MAybe not. In fact I'm posting this on various threads that all deal with the same very annoying problem, and I see (now) that other fellow ubunters did find the same solution that I found. MAybe someone should pass this upstream, if it isn't already on the developers' table.

```
BUG: soft lockup detected on CPU#0!
```

Happens imho
[LIST]
[*]when you have a dual boot config
[*]when you TURNED YOUR WIRELESS OFF inLinux
[*]when you did reboot in windows after that
[*]when you now tried to reboot in linux with wireless still off
[/LIST]

Solution (worked for me)
[LIST]
[*]Reboot in windows
[*]Return wireless on
[*]shutdown windoze and reboot linux
[/LIST]

So the point is to RESET WIRELESS ON.
Why this kind of bug/error 
should be/could be/probably is 
related with wireless beats me.

(this rig was 2.6.17-11-generic, 3945 ABG Intel wireless, ubuntu edgy on a Siemens Amilo S that has an annoying flashing wireless light that you always like to turn off if there's no connection even if it is actually not necessary: let it flash and avoid the problem)

---

