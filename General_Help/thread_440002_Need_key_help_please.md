---
title: "Need key help please"
date: 2007-05-11
forum: General Help
---

### Post by DougieFresh4U on 2007-05-11
I have been searching threads for almost an hour, and can not find  keys for the following:

[B][COLOR="Red"]Reading package lists... Done
W: GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) feisty-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 580E2519969F3F57
W: GPG error: [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 576856718434D43A
W: You may want to run apt-get update to correct these problems[/COLOR][/B]



Could some one please guide me? Thanks

---

### Post by EndPerform on 2007-05-11
For the [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) repository, there's instructions on the front page on how to get the key imported:

```
wget http://debian.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```

As for the other repository, you might want to check their site and see if they have their key posted as well

---

### Post by DougieFresh4U on 2007-05-11
> **EndPerform said:**
> For the [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) repository, there's instructions on the front page on how to get the key imported:

```
wget http://debian.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```


Thank you:)

---

