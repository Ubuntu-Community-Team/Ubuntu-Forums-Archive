---
title: "error in synaptic package manager.."
date: 2007-08-18
forum: General Help
---

### Post by shadows123 on 2007-08-18
when i had click reload i had this error :
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
any idea how to solve this??

Thanks :)

---

### Post by forestpixie on 2007-08-18
I assume you've added a wine repo to your sources.list - where did you get it from?

there was probably a line that added the key which perhaps you didn't do.

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/) - this address goes to a page which has a link to here
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb) - is that where you got it?

if so the code to add the key is

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

you might need to add the repo line from that page - not sure :( that would need this added from a termninal if you're running feisty

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```

which you need to enter into a terminal

Does that help at all - I've not needed to use wine so I'm just following the first link

---

### Post by shadows123 on 2007-08-18
yeah that does help me out :)
thanks a lot lol..
well wine is good because you don't find dreamweaver & etc.. and.. i really like dreamweaver hehe :p
Thanks a lot dude :)

---

### Post by forestpixie on 2007-08-18
cool glad I could help - you can help others by marking thread solved :)

---

