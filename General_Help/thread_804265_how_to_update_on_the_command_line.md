---
title: "how to update on the command line?"
date: 2008-05-22
forum: General Help
---

### Post by ELMIT on 2008-05-22
I have now installed a Ubuntu server. I wonder how do I update the system whenever something is available? The server has no graphic, no icon to be informed, no clickable install now, ...

BTW, is there a way to get update information via email, messengers, so that I know that the server needs an update?

bye

R.

---

### Post by kerry_s on 2008-05-22
sudo apt-get update
sudo apt-get upgrade

---

### Post by pdwerryhouse on 2008-05-23
Or alternatively:

sudo aptitude update
sudo aptitude safe-upgrade

---

### Post by c4v3m4n on 2008-05-23
sudo apt-get update

sudo apt-get upgrade

that should do it

---

### Post by ELMIT on 2008-05-23
Maybe I said something wrong.

The server does not have a graphical interface, so it has also not the notification icon that updates are ready.

The quoted command sudo apt-get update, just updates the list of possible updates, but it does not show me any detail of updates available and it does not install any updates.

bye

R.

---

### Post by johnl on 2008-05-23
> **ELMIT said:**
> Maybe I said something wrong.

The server does not have a graphical interface, so it has also not the notification icon that updates are ready.

The quoted command sudo apt-get update, just updates the list of possible updates, but it does not show me any detail of updates available and it does not install any updates.

bye

R.

You're right, apt-get update just updates the list of software available in the repository.  You need to run 'sudo apt-get upgrade' afterwards in order to actually perform any upgrades.

---

### Post by ELMIT on 2008-05-23
Thanks!

I am just upgrading other machines, so I was confused about upgrade and distribution upgrade.
That worked now.

Is there a method I can use to get informed which of my servers have updates available? or just do these two commands daily?

bye

R.

---

### Post by angry_johnnie on 2008-05-23
Aptitude, maybe.

just
```
sudo aptitude
```
 without anything else, will bring forth a nice, nearly gui-ish, tool, much like a text-mode version of synaptic.

Look for **upgradable** in the list of categories.

---

### Post by kerry_s on 2008-05-23
> **ELMIT said:**
> Thanks!

I am just upgrading other machines, so I was confused about upgrade and distribution upgrade.
That worked now.

Is there a method I can use to get informed which of my servers have updates available? or just do these two commands daily?

bye

R.

i don't think so, but if your lazy like i am, you can use alias's to save you some typing, you just add them to the .bashrc
here's mine:

```
alias su='sudo -i'
alias update='sudo apt-get update;sudo apt-get -u dist-upgrade'
alias install='sudo apt-get install'
alias remove='sudo apt-get remove --purge'
alias search='apt-cache search'
alias show='apt-cache show'
alias clean='sudo apt-get clean'
alias fix='sudo apt-get -f install'

```

you might want to change the "dist-upgrade" to just "upgrade" i run debian so it's safe for me, wouldn't want you accidentally jumping up to a buggy release.

---

