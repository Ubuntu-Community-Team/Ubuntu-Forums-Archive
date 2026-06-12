---
title: "ark and pass protected rar files?"
date: 2005-06-29
forum: General Help
---

### Post by Digitallysick on 2005-06-29
Where does it give me the option to put in a password?? *lost*

---

### Post by jeSah8ci on 2008-01-13
After two years this is still an issue.

I found [a possible answer]("http://www.kde-forum.org/artikel/17999/password-protected-archives-and-Ark.html") at the KDE Forum. You have to use the console.

Using something like:

> unrar e -pPASSWORD NameOfArchive.rar

Should do the trick to unrar the thing you want in the same directory.

However, I'm having trouble getting that to work, since the password for the archive is 'something.like.this'.

---

### Post by aparigraha on 2008-02-08
it works with

unrar e -p NameOfArchive.rar

and it will ask you for a pass twice afterwards. Just have it copied and paste it (twice).

---

### Post by LeDechaine on 2008-02-15
Man, this is really stupid, "un-rar-ing" a 700mb file takes a LONG time, and you have to unrar it third times? Ouch!

Poor guys who have X Gb passworded rar files to extract!
I wonder why this is still an issue.. Hmm.. Maybe because the closed-source Winrar people aren't cooperative? (Don't know)

Hell, rebooting my computer to unrar this file under Windows... This will take less time...
Note to myself: *Boycott RAR files*. ;)

---

### Post by scheffkocha on 2008-04-24
just want to advise you to [Unp]("https://help.ubuntu.com/community/Unp"), a really nice time saver when extracting!

---

