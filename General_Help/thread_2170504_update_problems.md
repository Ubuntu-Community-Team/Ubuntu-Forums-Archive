---
title: "update problems"
date: 2013-08-26
forum: General Help
---

### Post by Buntu Bunny on 2013-08-26
The following has happened the last two times I tried to update. 

Me:
```

$ sudo apt-get update && sudo apt-get dist-upgrade
```

Terminal:

```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en  

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

I looked back through the output and found:

```
: Unable to parse package file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en.decomp (1)
```

Unfortunately, I don't know what this means. So I ran

```
sudo apt-get upgrade
```

and the system did indeed update the one package needing it.

Out of curiosity, I then asked Update Manager to check for updates. It returned the same "failed to fetch..." message. 

So I'm still able to update things, but there's obviously a problem. Please, what exactly is the problem and what do I need to do to fix it?

---

### Post by Bashing-om on 2013-08-26
Buntu Bunny; A fine afternoon to ya;

See if this helps:
```

sudo rm /var/lib/apt/lists/* -vf  ##will remove the damaged list 
sudo apt-get update ##will bring in new scripts that should not be broken and will replace it with a new list;

```
though possible might have to do something withe the "partial" directory, but let us do no more than needed.

[INDENT][INDENT]should workie great, last long time
[/INDENT][/INDENT]

---

### Post by Buntu Bunny on 2013-08-26
Bashing-om thank you for the quick response! Your help is always appreciated.

I ran the codes you gave, but am still getting the same error messages. :(

---

### Post by Bashing-om on 2013-08-26
Buntu Bunny; OK !

A bit more aggressive - dealing with that "partial" directory:
```

sudo apt-get clean
sudo cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update

```

[INDENT]if at first you don't succeed ?
[/INDENT]

---

### Post by Buntu Bunny on 2013-08-26
Success! Whew, thank you Bashing-om!

Wishing you a wonderful rest of the day. :P

---

### Post by Bashing-om on 2013-08-26
Buntu Bunny; Thank you .. my day will be.
I wish all your troubles to be this small.

[INDENT][INDENT]later
[/INDENT][/INDENT]

---

