---
title: "Adding Apt sources"
date: 2007-03-14
forum: General Help
---

### Post by AnthonyJK@gmail.com on 2007-03-14
Hi, I just got Ubuntu installed and in the installation guide I'm using it says to:

[B]Head over to this site: [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)

Add his apt sources, then do a search for his macbook packages and install them, ex:

apt-cache search macbook

Then install the ones you see fit, the kernel modules gets your sound.

[/B]
I was wondering how I go about doing this I've been trying to figure it out for an hour with no luck :(. Thanks!

---

### Post by llamakc on 2007-03-14
The sources.list file is in the filesystem at /etc/apt

/etc/apt/sources.list

So if you want to use the ones recommended, first back up your current one:

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

```

Next, cp the one he has over your old one. However, I don't see where that link has a sources.list or link to one.

---

### Post by AnthonyJK@gmail.com on 2007-03-14
I don't see where either Im not sure what to do :(

---

### Post by llamakc on 2007-03-14
Email the person and ask what their sources.list looks like?

---

### Post by Kateikyoushi on 2007-03-14
Or check his other page. [LINK]("http://desrt.mcmaster.ca/dapper.xhtml")

---

