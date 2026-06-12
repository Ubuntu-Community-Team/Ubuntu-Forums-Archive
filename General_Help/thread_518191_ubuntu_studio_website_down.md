---
title: "ubuntu studio website down?"
date: 2007-08-05
forum: General Help
---

### Post by limberlegs on 2007-08-05
Hi, all.

I just recently learned about ubuntu studio, and it got me very excited!  I have been trying to access the website (ubuntustudio.org) and it doesn't seem to be loading.  It has been this way for the last couple of days.  Any word on when it'll be back up and running?

Thanks!

---

### Post by apswartz on 2007-08-05
Yes, it does seem to be down.

Until it is back up you can check out these pages...
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)
[https://wiki.ubuntu.com/UbuntuStudio](https://wiki.ubuntu.com/UbuntuStudio)

---

### Post by por100pre1 on 2007-08-05
Yep, the page is down, but the repositories seem to be up. You can try install Ubuntu Studio packages over an existing **Feisty** installation. Try this:

```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Then install what you want with Synaptic. If you want to, you can start with this:

```
sudo apt-get install ubuntustudio-desktop linux-lowlatency
```

Worked fine to me, hope it works fine to you too. :guitar:

---

### Post by limberlegs on 2007-08-05
Hmm... it returned the following in my terminal window:

```
~$ sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop

```

I guess the repositories are down now as well?

---

### Post by por100pre1 on 2007-08-05
> **limberlegs said:**
> Hmm... it returned the following in my terminal window:

```
~$ sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntustudio-desktop

```

I guess the repositories are down now as well?

I just checked by downloading the package and it works... The repo is up.

---

### Post by por100pre1 on 2007-08-05
Do this: 

```
sudo apt-get update && sudo apt-get upgrade
```

and try again...

---

### Post by limberlegs on 2007-08-05
Weird, I'm getting the same problems.  I guess I'll just install what I need from synaptic anyway.

---

### Post by swj on 2007-08-07
Google text only cache.
[http://209.85.165.104/search?q=cache:T4A-TeqrVXAJ:ubuntustudio.org/downloads+ubuntu+studio&hl=en&gl=us&strip=1](http://209.85.165.104/search?q=cache:T4A-TeqrVXAJ:ubuntustudio.org/downloads+ubuntu+studio&hl=en&gl=us&strip=1)

Download mirrors for Ubuntu Studio.

:)

---

### Post by Sunflower1970 on 2007-08-27
(Edited message) 
Yay! It's back :)

---

