---
title: "What type of passwords does keyring manager remember?"
date: 2012-12-25
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-25
What type of passwords does keyring manager remember? e.g., does it remember passwords from web login form? Hoes does it distinguish an input to be a password apart from other types of text entered?

---

### Post by dino99 on 2012-12-25
gnome-keyring is a daemon in the session, similar to ssh-agent,
and other applications can use it to store passwords and other
sensitive information.

The program can manage several keyrings, each with its own master
password, and there is also a session keyring which is never stored to
disk, but forgotten when the session ends.

meaning: related to session, not to apps inside that session.

---

### Post by Holmes.Sherlock on 2012-12-25
> **dino99 said:**
> gnome-keyring is a daemon in the session, similar to ssh-agent,
and other applications can use it to store passwords and other
sensitive information.

Does it mean that to make use of it, the other application have to be keyring-aware?

---

### Post by dino99 on 2012-12-25
all depend of the user choice inside each app security tab (or conf app's file)

---

### Post by Holmes.Sherlock on 2012-12-25
> **dino99 said:**
> all depend of the user choice inside each app security tab (or conf app's file)
Pardon, I couldn't follow you. Any further reference?

---

### Post by vasa1 on 2012-12-25
> **Holmes.Sherlock said:**
> What type of passwords does keyring manager remember? e.g., does it remember passwords from web login form? Hoes does it distinguish an input to be a password apart from other types of text entered?

I think the gnome keyring stuff only wants passwords to start apps, if at all. In the case of Chrome, for example, I used to get prompted for my login password (the one I enter when I start a Ubuntu session) when I was on 12.04 (with a mix of desktops). Subsequently, passwords entered or required in weblogin forms are handled by the browser itself and not by this keyring thing.

The whole keyring thing is largely a mystery to me and I try not to think of it because it doen't bother me nowadays.

---

### Post by Holmes.Sherlock on 2012-12-26
> **vasa1 said:**
> 
The whole keyring thing is largely a mystery to me and I try not to think of it because it doen't bother me nowadays.
I am trying to figure out how it can be used effectively.

---

