---
title: "(Ubuntu 14.04) Update Error Given"
date: 2015-09-21
forum: General Help
---

### Post by jooge on 2015-09-21
The last 2 times I updated using:

```
sudo apt-get update
```

I gotten a error it seems:

```
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFC71127F425E228
```

What is this and can I fix it? Thank guys :)

---

### Post by QDR06VV9 on 2015-09-21
This should work
```
[COLOR=#000000][FONT=Ubuntu Mono] sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EFC71127F425E228[/FONT][/COLOR]
```
Then run again
```
sudo apt-get update
```
And you should be able to resume with what you were doing.

---

### Post by jooge on 2015-09-21
Worked like a charm my friend. Thank you for your time.

---

### Post by QDR06VV9 on 2015-09-21
You are very welcome.

---

