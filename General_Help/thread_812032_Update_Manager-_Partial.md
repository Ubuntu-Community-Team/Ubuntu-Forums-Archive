---
title: "Update Manager- Partial?"
date: 2008-05-29
forum: General Help
---

### Post by Exsecrabilus on 2008-05-29
Just a few minutes ago, I enabled the *hardy-proposed* repo just to check if the _Firefox 3 RC 1_ update was available.
(I only use *hardy-security* and *hardy-updates* repos 'cause I want to stay stable.)

As soon as I opened **Update Manager** to check, this window popped up:

[img]http://i212.photobucket.com/albums/cc134/Exsecrabilus/UpdateManager.png[/img]

I'm not exactly sure. I'm not asking you to repeat what it says and tell me "Oh, it means you can't install all the updates."
I'm requesting a clear explanation on what it means. THANKS SO MUCH!!!!! :D

---

### Post by forestpixie on 2008-05-29
It can happen because dependencies can't be fulfilled - you will have to wait a while.

Different servers are updated at different times - mine are ok now.

---

### Post by Exsecrabilus on 2008-05-29
Does the main server get updated first?

---

### Post by forestpixie on 2008-05-29
Not sure tbh - I'd of thought so, but I'm on main server and they weren't there earlier.

---

### Post by forestpixie on 2008-05-29
I thought that the rc update for firefox was in proposed.

---

### Post by Exsecrabilus on 2008-05-29
I know, that's what I said.

---

### Post by bapoumba on 2008-05-29
[http://ubuntuforums.org/showpost.php?p=5073060&postcount=173]("http://ubuntuforums.org/showpost.php?p=5073060&postcount=173")
May be this ? (unistall the beta ?).

---

### Post by Exsecrabilus on 2008-05-29
> **bapoumba said:**
> [http://ubuntuforums.org/showpost.php?p=5073060&postcount=173]("http://ubuntuforums.org/showpost.php?p=5073060&postcount=173")
May be this ? (unistall the beta ?).
I'm not saying it's a specific _Firefox_ thing, I'm just saying: when I opened **Update Manager**, that was the first thing that popped up.

Sorry for the confusion. ^_^

---

### Post by forestpixie on 2008-05-29
As it is in my little experience I don't think that I've had a partial update when not using proposed or backports. AFAIK it is as I said about dependencies not being availale to allow for the complete installation of a package.

As an aside the rc is just as slow at loading pages as it was before so I'll go back to opera for the time being.

---

### Post by bapoumba on 2008-05-29
> **Exsecrabilus said:**
> I'm not saying it's a specific _Firefox_ thing, I'm just saying: when I opened **Update Manager**, that was the first thing that popped up.

Sorry for the confusion. ^_^
Ah sorry :)
Do you have other repos, besides the regular ubuntu ones and -proposed ?

---

### Post by Exsecrabilus on 2008-05-29
I only have enabled *hardy-security* and *hardy-updates*.

I just enabled *hardy-proposed* to check if _Firefox 3 RC 1_ was available.

When I opened **Update Manager** to check, that window I posted a screenshot of popped up.

---

### Post by bapoumba on 2008-05-30
> **Exsecrabilus said:**
> I only have enabled *hardy-security* and *hardy-updates*.

I just enabled *hardy-proposed* to check if _Firefox 3 RC 1_ was available.

When I opened **Update Manager** to check, that window I posted a screenshot of popped up.
You probably want to have these to:

```
deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

```

Did you reload the file before running update-manager (**sudo apt-get update** or reload button)?

---

