---
title: "Editing from Bash"
date: 2007-10-29
forum: General Help
---

### Post by Sutur on 2007-10-29
Hi there.

I know there is a way to **add** a string of text to a given file (but I've forgotten).

Is there a way to locate a specific string of text in a file, remove & save it - all from a single bash command?

The reason I ask, is that I have a firefox extension called noscript. I don't fully trust myself to use it properly, even though it's likely I do. They don't give you an option to 'forget' all the sites I have trusted, so instead I have to sift through my prefs.jf file and remove entries beginning with "capability.policy.maonoscript.sites".

Any suggestions/workarounds?

---

### Post by stylishpants on 2007-10-29
> **Sutur said:**
> 
Hi there.

I know there is a way to **add** a string of text to a given file (but I've forgotten).

```

echo "this is a new line" >> file

```
> **Sutur said:**
> 

Is there a way to locate a specific string of text in a file, remove & save it - all from a single bash command?

The reason I ask, is that I have a firefox extension called noscript. I don't fully trust myself to use it properly, even though it's likely I do. They don't give you an option to 'forget' all the sites I have trusted, so instead I have to sift through my prefs.jf file and remove entries beginning with "capability.policy.maonoscript.sites".

Any suggestions/workarounds?


```

 perl -ni -e 'print unless /^user_pref\("capability\.policy\.maonoscript\.sites/' file

```

---

### Post by Sutur on 2007-10-30
Thanks man

---

