---
title: "[SOLVED] Gutsy + Pidgin"
date: 2007-11-09
forum: General Help
---

### Post by enneth on 2007-11-09
Ever since I upgraded to Gutsy Gibbon Pidgin has not been working properly. Sometimes it does not show fetch contact list and just shows a white and empty window, other times it is able to fetch the contact list, but then the window goes dark (when they don't respond or whatever) and it just stays dark making me unable to use Pidgin. It simply freezes. One out of 15 times it works.

I have tried removing and reinstalling it numerous times but that makes no difference whatsoever.

Is anyone else experiencing these problems? If so; found a solution?

---

### Post by djrobthaman on 2007-11-09
Are you using the version of pidgin included with the gutsy repos or one from a 3rd party that you had installed with feisty?

If it's the latter, your best bet is probably to uninstall pidgin completely, remove the third party repo and then install the version in the gutsy repos.

---

### Post by enneth on 2007-11-09
I am using the one from the Gutsy repos.

---

### Post by knutschr on 2007-11-09
Is it MSN you are trying to connect to?
It works for me after I asked it to listen to all ports 80 - 2048.

---

### Post by djrobthaman on 2007-11-09
I  no clue what could be wrong with pidgin (mine worked perfectly fine from the get go), but if it's freezing what you could do is start it from the terminal (I think the command is just "pidgin") and then just post whatever error messages you get from there.

---

### Post by enneth on 2007-11-09
Yes, it is MSN. How to make it listen on those ports? Without doing it in Pidgin (which I cannot because it freezes).

It says (in debug mode):
```

(19:56:30) proxy: Connected to 207.46.108.26:1863.
(19:56:32) proxy: Connecting to nexus.passport.com:443 with no proxy
(19:56:33) proxy: Connecting to login.live.com:443 with no proxy

```

Then it lists the contacts etc. till it gets to:
```

(19:57:13) msn: C: NS 000: BLP 10 BL
(19:57:13) connection: Activating keepalive.

```

... and then it does nothing.

**EDIT:** Figured out how to edit the port ranges (in prefs.xml, right?). However, it did not fix the problem.
I deleted my account from pidgin, ran it in debug mode and it showed me something with a plugin called 'currenttrack'. After disabling the plugin it started. Then I stopped Pidgin and startet it again, and now it seems to work.

Anyway, thanks for the (fast) help!

---

