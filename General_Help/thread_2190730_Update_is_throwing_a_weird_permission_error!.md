---
title: "Update is throwing a weird permission error!"
date: 2013-11-28
forum: General Help
---

### Post by vdeepakkumar on 2013-11-28
Can some one help out with this weird Konsole error which appears after clicking 'Run Now' button?

[ATTACH=CONFIG]248177[/ATTACH]

---

### Post by Bucky Ball on 2013-11-29
Try:

```
sudo apt-get install flashplugin-installer
```

Not sure what you've done or what you're doing but presuming you're using Kubuntu. Could you be more specific? 'When I click Run Now' ... does that mean run update now?

Anyway, give error, if any, after you run the command I have given. You might also need to run, in this order, these two commands:

```
sudo apt-get update
sudo apt-get upgrade

```

... then try the install command for flash-plugin installer again.

---

### Post by vdeepakkumar on 2013-11-29
Basically, I presume my Kubuntu is automatically checking for any updates from the vendor. But this particular update keeps failing to download and gets locked down with this message. 

I would give a try of your sudo apt-get command sets tonight and keep you posted.

---

### Post by Bucky Ball on 2013-11-29
Sorry, should be:

```
sudo apt-get install flashplugin-installer
```

It's in Software Centre also.

---

### Post by J_Me on 2013-11-29
> Can some one help out with this weird Konsole error which appears after clicking 'Run Now' button? I get that same error, had it for a while now > sudo apt-get install flashplugin-installer Could I ask, I thought firefox/chromium were not using flash-plugins any more. Which are the programs that need it. Thanks

---

