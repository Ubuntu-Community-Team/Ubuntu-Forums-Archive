---
title: "Logout / Login Problems, PLEASE help!"
date: 2007-08-23
forum: General Help
---

### Post by andrew-gw on 2007-08-23
I'd like to start off by thanking this entire community because I've been able to find help so easily until now and I love using Ubuntu.  But I have a problem.

The first problem is major, and I really need help but I can't find the solution anywhere.  Ever since I've installed Feisty Fawn Ubuntu, whenever I log-out and then log back in later, any panes or windows or anything are just blank, and I can click but it's shooting in the dark and I'm wondering why there's nothing there. I've had to restart the computer every time... for whatever reason this only happens after I've logged-out and back in. ( Attached image )  Might I also add that I'm dual-booting with Windows XP SP2 and have had the problem BEFORE installing anything.

The other problem I've been having ( Other screenshot ) is with Avant Window Navigator.  Beryl might be the problem, I'm not sure, and I have AWN set to start-up on boot in the sessions manager.  The dock icons appear at the far left of my screen and take about ten seconds to finally slide-over onto the background.

Thanks SO much in advance!

---

### Post by dragomirov on 2007-08-24
Beryl as well as compiz are testing software so they can't assure you a perfect job (I wonder if perfection in software exists).
The only way is trying, so remove from your startup session beryl or just hit ALT+F2 and run "metacity --replace" to restore metacity as window manager. Then try the logout/login thing and see if there's a difference.

---

### Post by andrew-gw on 2007-08-24
The white window bug happened before installing Beryl, so I can almost assure you it's a Compiz problem, from the "Desktop Effects" option.  I've sinced fixed the problem, but unfortunately I have no idea how.

If anyone else out there has the same or a similar issue, I suggest you play around with your Sessions manager and the manager / rendering options in Beryl.

Thanks Dragomirov, your suggestion likely would have worked if I'd seen your reply first, lol.  As for the dock problem, it still lags for ten seconds before it looks right.  I don't really think it needs fixing, but it is fairly annoying.  I'm wondering if the session order has anything to do with this, but for now I've stopped using AWN until it's a little more stable.

Thanks all!

---

