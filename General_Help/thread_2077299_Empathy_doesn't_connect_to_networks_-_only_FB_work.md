---
title: "Empathy doesn't connect to networks - only FB works"
date: 2012-10-28
forum: General Help
---

### Post by aigljd on 2012-10-28
Hi guys,

I have some issues making IM work and I need a little help :)

My empathy only connects to facebook via web auth and all my other networks do not work : gtalk, live, yahoo, jabber. Stating that there is a "network error" or that "it cannot connect". I don't understand why since jabber, gtalk, and fbtalk are all XMPP based they should all work together ? Am I missing something in the configuration ? Maybe the ports ?

Consequently, I installed pidgin as a backup multi-IM solution but same problem, I can't connect to any network.

Do you know what I can do to make them work ?

I'm on Ubuntu 12.10 w/ Gnome environment.

Thanks a lot for yout help :)

---

### Post by KFoder on 2012-10-28
I have exactly the same problem, after having updated to kubuntu 12.10 I cannot connect to any XMPP network, I have seen this on two different laptops one 32 and one 64 bit.

The problem exists in both Empathy and KDE IM.

Older Ububtu's and other os'es can connect without any problem.

Any ideas ?

EDIT: I have removed salut and reinstalled telepathy, but the problem persists.

Kim

---

### Post by aigljd on 2012-10-28
Oh that's quite annoying :/

Does an alternative IM soft would solve this problem ?

Thanks !

---

### Post by TheCosmicFrog on 2012-10-29
Same problem here. It's really irritating.

---

### Post by KFoder on 2012-10-29
I have solved the problem (well more or less)

I have tested with an alternative IM (Pidgin) and it works without any problem, but I'm not so fond of the interface.

So I decided to go all the way.

I removed Empathy and everything related to it, KDE IM and everything related to it, and everything related to telepathy.

After a reboot I made an install of Empathy, without any success, still same problem (can it be because I'm running KDE, that was  not a problem in 12.04).

So I removed Empathy and everything related to it, AGAIN, and installed KDE IM and that works without any problems.

I know this isn't quite your situation but maybe it can give you some ideas.

Kim

---

