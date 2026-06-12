---
title: "GAIM problems"
date: 2007-04-19
forum: General Help
---

### Post by dominicd on 2007-04-19
This is the error I get

```

Connection error from Notification server:
Reading error

```

I'm using Ubuntu Edgy and I had no problems with GAIM (2.0.0beta3.1) until now, I didn't do anything in particular before the problems arose.

In an attempt to fix it, I updated the system, reinstalled GAIM 2.0.0beta3.1 and upgraded to GAIM 2.0.0beta5 (I tried to get beta6 but no luck).

It's an MSN account btw and the login information is correct.

---

### Post by dominicd on 2007-04-19
I created an AIM account to test and it seems to work.. I'm not 100% sure since I don't have any AIM buddies but it doesn't give any connection errors so I guess it works.

Anyone got any idea how I can get my msn account working with GAIM again?

---

### Post by Gannin on 2007-04-19
I would first try installing something like amsn and logging in with that to make sure there isn't just some problem with your account or their servers.

---

### Post by dominicd on 2007-04-19
> **Gannin said:**
> I would first try installing something like amsn and logging in with that to make sure there isn't just some problem with your account or their servers.

Hmm...I'm trying to install it but I'm having some issues with the repos. maybe because of the new release?

One of the things I get is:
> 
W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available (...)


---

### Post by Gannin on 2007-04-20
Go here [http://amsn-project.net/linux-downloads.php](http://amsn-project.net/linux-downloads.php) and download and install the autopackage file.  It'll probably work better for you, and it'll be the latest version, too.

---

### Post by dominicd on 2007-04-20
> **Gannin said:**
> Go here [http://amsn-project.net/linux-downloads.php](http://amsn-project.net/linux-downloads.php) and download and install the autopackage file.  It'll probably work better for you, and it'll be the latest version, too.

Thanks I got aMSN installed and I can login there fine so it's definitely an issue with GAIM.

I'd really rather not use aMSN so any ideas are very welcome!

PS: I made a deb of aMSN (amsn_0.96-1.deb) I'd attach it but it's too big, if for some reason you want it just PM me I'll send it to you.

EDIT:
I'm just editing this post instead of replying so I won't bump the topic.

Optimalizing my DNS settings fixed the problem.

(See [http://ubuntuforums.org/showthread.php?p=2492151#post2492151](http://ubuntuforums.org/showthread.php?p=2492151#post2492151))

---

