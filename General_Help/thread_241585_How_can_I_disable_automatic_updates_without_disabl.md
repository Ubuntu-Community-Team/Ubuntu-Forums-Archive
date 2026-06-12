---
title: "How can I disable automatic updates without disabling security updates?"
date: 2006-08-22
forum: General Help
---

### Post by yioan on 2006-08-22
Is there any way to disable all updates, except those that regard security updates?

---

### Post by yioan on 2006-08-25
hmmm...

"apt-get update" updates everything located in the /etc/apt/sources.list file. Is there any way to update selected sources or to pass a sources.list file as a parameter?

thanks.

---

### Post by peabody on 2006-08-25
> **yioan said:**
> Is there any way to disable all updates, except those that regard security updates?

Don't know of a way off-hand.  You could comment out all other repositories and leave the security one enabled, then perform an update, then go back an uncomment the other repositories.

---

### Post by yioan on 2006-08-25
I have thought of this but... it should be another way...

Another way is by replacing sources.list each time a security update script is executed... but I am looking for a more efficient way.

---

### Post by FSHero on 2007-12-23
I was wondering a something similar: I want "sudo apt-get upgrade" to not take packages from feisty-backports, only feisty's main, restricted, universe and multiverse. The only reason I added backports was to install Kompozer, which wasn't in feisty's distribution repository.

I think I shall use "pinning" as described on [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports). Does anyone else have any experience of this?

(Note: I'm running Kubuntu Feisty Fawn.)

---

