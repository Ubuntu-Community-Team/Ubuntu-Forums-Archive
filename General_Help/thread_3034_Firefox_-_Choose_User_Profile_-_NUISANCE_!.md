---
title: "Firefox - Choose User Profile - NUISANCE !"
date: 2004-11-02
forum: General Help
---

### Post by iminj on 2004-11-02
Whenever I open Firefox (a wonderful browser by the way), a box pops open reminding me to "Choose User Profile". It's a nuisance, because I can't figure out how to configure it to NOT pop open every time I open the browser.

Firefox shows a Default profile, and I have no problem being known as "default". I even clicked on the "Don't ask at startup" option .... but I can't get rid of this thing.

I use Firefox in Windows, and I don't have this shadow following me wherever I go.

Anyone have an answer ?

iminj

---

### Post by jdong on 2004-11-02
hmm, that's weird. Create a new profile and set it as default.

---

### Post by Loptr on 2004-11-02
Try issuing the following command, and make sure Firefox is closed when doing it:

```

find ~/.mozilla/ -type l -name lock -exec rm {} \;

```

---

### Post by mercurus on 2004-11-03
It sounds as though mozilla firefox is already open somewhere else, or as Loptr suggests, there's an old lockfile lying around your system telling firefox it is already running. I've only ever been offered the profile dialog when I'm opening multiple instances of firefox with multiple users.

If Loptr's solution doesn't fix the problem, try purging and re-installing the mozilla-firefox package.

Cheers
mercurus

---

### Post by jdong on 2004-11-03
[QUOTE=Loptr]Try issuing the following command, and make sure Firefox is closed when doing it:

```

find ~/.mozilla/ -type l -name lock -exec rm {} \;

```[/QUOTE]


OT and informational: use xargs; especially when find has a lot of matches, forking an 'rm' for every file is both hard on the system and inefficient. Use
```

find ~/.mozilla/ -type l -name lock | xargs rm -f

```

The first "l" is a lowercase L, while the second | is a pipe character.

---

### Post by iminj on 2004-11-03
I tried Loptr's "find ~/.  ..." suggestion; but ubuntu returned an error message:

file not found

So, I purged and re-installed Firefox ... Synaptic directed me to install it from my original ubuntu .iso CD. The 1st time I opened the browser, the user profile window popped open, but it's been stable since then.

Interesting, when I removed Firefox using Synaptic, it also removed a dependency called "ubuntu desktop". I don't think it was replaced when I re-installed Firefox.

What's ubuntu desktop? Anyone know? Do I need it?

iminj

---

### Post by mercurus on 2004-11-03
[QUOTE=iminj]I tried Loptr's "find ~/.  ..." suggestion; but ubuntu returned an error message:

file not found

So, I purged and re-installed Firefox ... Synaptic directed me to install it from my original ubuntu .iso CD. The 1st time I opened the browser, the user profile window popped open, but it's been stable since then.

Interesting, when I removed Firefox using Synaptic, it also removed a dependency called "ubuntu desktop". I don't think it was replaced when I re-installed Firefox.

What's ubuntu desktop? Anyone know? Do I need it?

iminj[/QUOTE]
 It's a pseudo-package that installs the basic packages required for the standard Ubuntu Desktop. The core of Ubuntu really, but removing it **doesn't** damage the installation - it just means you don't have the pseudo-package. The critical packages remain in place.

Cheers
mercurus

---

