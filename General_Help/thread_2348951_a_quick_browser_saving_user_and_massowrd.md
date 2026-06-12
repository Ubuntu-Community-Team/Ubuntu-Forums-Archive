---
title: "a quick browser saving user and massowrd?"
date: 2017-01-09
forum: General Help
---

### Post by matteoraggi on 2017-01-09
Chromium can save user and password, but it is heavy in fronto of to other browsers. Midori for exampel is more quick, but it don't save the login forms data.
Suggestions?

---

### Post by DuckHook on 2017-01-09
It seems like you are looking for a password manager like KeePass2. It has a feature that will autotype your usernames and passwords into specific fields. However, its real use is to remember long and highly secure passwords for you for heightened security. You will only ever need to remember one password (make it a good long complex one), which then unlocks the rest. It can be installed with:```
sudo apt install keepass2
```It is also cross-platform and I believe that it has Windows, Mac, iOS and Android versions.

Another password manager is Password Gorilla:```
sudo apt install password-gorilla
```Password Gorilla cannot autotype into specific fields, nor is it as cross-platform, although I believe there is a version for Windows.

Both are open source.

There are many other password managers, both FOSS and closed source, that can be Googled.

A word of caution: apart from clearly meaningless websites, it is not a good idea to rely on the password memory features of web browsers because any scoundrel who can break your login passphrase has full access to your browser and can read your passwords off of your browser simply by asking for them. This is also true of *seahorse*, the keyring app that Chromium piggybacks onto to store passwords.

A better strategy is to *not* store your passwords in your OS keyrings (by always choosing "*NEVER* remember passwords for this site" when asked by your browser), and to use KeePass to remember them instead. However, make sure you use a *different* but equally robust passphrase for KeyPass. This way, even if a scumbag gains access to your computer, s/he may not necessarily gain access to your bank account.

If the above answers your question, please mark thread "solved" using thread tools at the top of this thread, so that others can benefit from your solution.

---

### Post by bearlake on 2017-01-09
There is a lot of good password manager programs out there.

Been using keepass2 for many years now across many OS.

If you go with keepass2 and want to auto-type usernames and passwords, you will need the package xdotool as well.

```
sudo apt install xdotool
```

---

### Post by vasa1 on 2017-01-10
Could it be that OP is looking for a browser "lighter" than Chromium but which can save passwords and "login forms data"? Apparently, Midori, while lighter, doesn't fit the bill.

---

### Post by DuckHook on 2017-01-10
> **vasa1 said:**
> Could it be that OP is looking for a browser "lighter" than Chromium but which can save passwords and "login forms data"? Apparently, Midori, while lighter, doesn't fit the bill.Good point.

I don't know the capabilities of all the browsers out there. Who could? There must be dozens of them. However, I would say that browsers mainly come in two types with little (if anything) in between. They are either:

[LIST=1]
[*]Powerful and feature-rich, but bloated, or
[*]Lean and fast, but feature-poor
[/LIST]
I haven't found anything that is both lean and feature-rich. That's why I suggested KeePass. It gives Midori (which is lean and fast) the one capability that OP requested (and a really nice bonus benefit as well).

I haven't tried browsers like Dolphin or Opera. They might work, but I doubt that they are lean and fast. Iceweasel is only marginally less bloated than FF, Chrome is even more bloated than Chromium and stuff like Links2 are at the completely featureless end of the continuum. Midori appears to be an excellent choice for the OP and it would appear that s/he only wants the one additional feature.

---

### Post by howefield on 2017-01-10
Epiphany-browser might do what you want, although being on the lean side means it is.. well, lean :)

It does have a password manager.

---

### Post by tea for one on 2017-01-10
> **matteoraggi said:**
> Chromium can save user and password, but it is heavy in fronto of to other browsers. Midori for exampel is more quick, but it don't save the login forms data.
Suggestions?

I've just logged in to this forum via Qupzilla

[http://www.qupzilla.com](http://www.qupzilla.com)

---

### Post by vasa1 on 2017-01-10
> **tea for one said:**
> I've just logged in to this forum via Qupzilla

[http://www.qupzilla.com](http://www.qupzilla.com)And it seems that there's a password manager GUI: [https://camo.githubusercontent.com/6689dfead80997ee9b5be53a2910cc23a424f615/687474703a2f2f692e696d6775722e636f6d2f65617a436850712e706e67](https://camo.githubusercontent.com/6689dfead80997ee9b5be53a2910cc23a424f615/687474703a2f2f692e696d6775722e636f6d2f65617a436850712e706e67)

Also: [https://github.com/QupZilla/qupzilla-plugins/wiki/PIM](https://github.com/QupZilla/qupzilla-plugins/wiki/PIM)

---

