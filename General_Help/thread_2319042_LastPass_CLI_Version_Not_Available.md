---
title: "LastPass CLI Version Not Available"
date: 2016-03-31
forum: General Help
---

### Post by Jason_Hunter on 2016-03-31
I can't get lpass to work right and it's because of a bug in 0.5.0:

[https://github.com/lastpass/lastpass-cli/issues/88](https://github.com/lastpass/lastpass-cli/issues/88)

It's fixed in 0.5.1, but that's not available: 

[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=lastpass&searchon=names](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=lastpass&searchon=names)

I see we got 0.7.0 available for Xenial, but I'm on Wily.

Why has not 0.5.0 been upgraded when it's pretty useless without 0.5.1? I mean, 16.04 isnt' really out yet. 

However, looking here: 

[http://packages.ubuntu.com/xenial/lastpass-cli](http://packages.ubuntu.com/xenial/lastpass-cli)


Isnt' there supposed to be a deb file there? I only see src files.

---

### Post by howefield on 2016-03-31
> **Jason_Hunter said:**
> Isnt' there supposed to be a deb file there? I only see src files.

Look a bit harder then, both the 64 and 32 bit .deb packages are available from the link that you provided.

---

### Post by slickymaster on 2016-03-31
> **Jason_Hunter said:**
> I can't get lpass to work right and it's because of a bug in 0.5.0:

[https://github.com/lastpass/lastpass-cli/issues/88](https://github.com/lastpass/lastpass-cli/issues/88)

It's fixed in 0.5.1, but that's not available: 

[http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=lastpass&searchon=names](http://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=lastpass&searchon=names)

I see we got 0.7.0 available for Xenial, but I'm on Wily.

Why has not 0.5.0 been upgraded when it's pretty useless without 0.5.1? I mean, 16.04 isnt' really out yet. 

However, looking here: 

[http://packages.ubuntu.com/xenial/lastpass-cli](http://packages.ubuntu.com/xenial/lastpass-cli)


Isnt' there supposed to be a deb file there? I only see src files.

Just click on the architecture of your system on that page, and you'll get a deb file to download
[ATTACH=CONFIG]268082[/ATTACH]

---

### Post by Jason_Hunter on 2016-03-31
Right, got it;) Thanks. 

Ok, but is this package supposed to work, even though it's not available on 15.10?

Is there any reason it's not available via apt in 15.10? Is there somewhere I can read a log or something, why it's not available? I mean, it's a supported OS and the actual LastPass is really not usable without it. 

I'm just generally curious?!

---

### Post by howefield on 2016-03-31
Packages are generally frozen at release and pretty much get security and  bug updates only, but not version updates. There maybe one or two exceptions to this rule.

[This page ]("https://help.ubuntu.com/community/UbuntuBackports")might explain better and then go on to explain what backports are.

---

