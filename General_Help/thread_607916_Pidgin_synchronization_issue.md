---
title: "Pidgin synchronization issue"
date: 2007-11-09
forum: General Help
---

### Post by Nonno Bassotto on 2007-11-09
I'm experiencing the following problem with Pidgin. Most times I connect, a dialog pops up for every person in my MSN buddy list, saying something like

```
"the local buddy list differs from the one on the server. Do you want to add xxxx to the server list?"
```

This is a known Pidgin bug, see for instance [this report]("http://developer.pidgin.im/ticket/3676"). It seems that it happens whenever you modify your buddy list from a different client or a different sopy of Pidgin.

Now the question is: since it doesn't happen with a fresh install of Pidgin, there must be some information stored somewhere, I guess in the .purple directory, that causes the problem. Do you know what I can do to solve this? I already tried deleting .purple/blist.xml and .purple/accounts.xml, but this didn't solve the problem.

I don't want to remove the whole .purple directory, since it also stores the logs, my settings for the plugins and so on.

---

### Post by Nonno Bassotto on 2007-11-10
:(

---

### Post by Nonno Bassotto on 2007-11-11
I removed the whole .purple directory, then copied logs and so on, but everything broke again after a few connections.I'm gonna break down and cry...

---

### Post by Depressed Man on 2007-11-11
Does it ask you this each time? I've encountered that myself (naturally going happen since I use Pidgin in 4 different OS environments..). But usually I tell it to not add it back onto the list and it's fine after that.

---

### Post by Nonno Bassotto on 2007-11-11
No, only say one time out of two. But if I say "no" the contact will not appear...

---

### Post by Nonno Bassotto on 2007-11-12
Help! PIdgin as it is now is close to unusable...
Every time I lose the contact icons, aliases and so on...

---

### Post by Nonno Bassotto on 2007-11-13
Really, any help? I'm losing every day all my settings, icons, aliases, last seen info and so on. I cannot use Pidgin like this. I don't know what to do: if I change IM application I will lose all my logs anyway.

---

### Post by Mr_Congeniality on 2007-12-26
I am having the exact same issue, and it happens every time I connect to my MSN account.  More than at least 100 to 200 pop up.  But my CPU is able to handle it, but it gets really tedious.

I would like to know a way to fix it as well, I'm looking into it further.  If I get anything I'll let you know.

---

### Post by viciouslime on 2007-12-26
I knwo you've already tried deleting the pidgin settings folder, but perhaps when you re-imported the settings that did something.

If I were you, i would back-up, then delete .purple again (same for .gaim if it exists) then restore ONLY your logfiles. I know this means setting up all your plugins again, but at least pidgin should be usable again...

---

### Post by Nonno Bassotto on 2007-12-26
This has not happened to me for a while, so I guess I'm leaving everything as is...

---

