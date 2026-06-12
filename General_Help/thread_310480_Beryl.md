---
title: "Beryl"
date: 2006-12-01
forum: General Help
---

### Post by guitarmaster on 2006-12-01
Hi All,

Anyone have any idea what's going on with the beryl repositories?

I'm trying to install beryl as a demo for my Boss on how great Ubuntu is (I run beryl on edgy at home like a dream) but whilst trying to install, I get:

```
Failed to fetch http://compiz-mirror.lupine.me.uk/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
W: GPG error: http://ubuntu.lupine.me.uk edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

When doing apt-get update

And then:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl

```

When doing apt-get install beryl

I checked out the beryl home page and found this:

"Server hard drive disk failed on Sunday, and we're currently trying to rescue it even though it does not look good at all. Apologies."

on [www.beryl-project.org](www.beryl-project.org)

Does anyone know when this is likely to be available....?

Or alternatively, you could save my bacon and point me in the direction of an alternative repository for beryl.... if such a thing exists?

Thanks in advance for your infinite wisdom which is so regularly showered down upon us mere mortals...

Guitarmaster

---

### Post by BarfBag on 2006-12-01
I'm having the exact same problem, so I'll help you out and bump your topic.

---

### Post by hanzomon4 on 2006-12-01
Here's the link to the new forums [http://forum.beryl-project.org/]("http://forum.beryl-project.org/"). I'll try to find you an amd64 repo, be right back....

EDIT: Back try this one.........
[quote="Mnemonicman"]There are packages of 0.1.2 for AMD64 at [http://beryl-mirror.lupine.me.uk/](http://beryl-mirror.lupine.me.uk/)

deb [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy main
deb-src [http://beryl-mirror.lupine.me.uk](http://beryl-mirror.lupine.me.uk) edgy main

wget [http://beryl-mirror.lupine.me.uk/1609B551.gpg](http://beryl-mirror.lupine.me.uk/1609B551.gpg) -O- | sudo apt-key add -[/quote]

---

### Post by Village on 2006-12-01
Sorry would that Repo work for intel's?

---

### Post by hanzomon4 on 2006-12-01
Do you mean an x86 cpu? If so then no use this one ```
deb http://ubuntu2.lupine.me.uk/ edgy main
```  and run this to get the key thing.. err whatever its called. ```
wget http://ubuntu2.lupine.me.uk/1609B551.gpg -O- | sudo apt-key add -
```

---

### Post by ner0tic on 2006-12-01
> **Village said:**
> Sorry would that Repo work for intel's?

the one listed above is for amd, scan the beryl forum for the x86 package for use with intel chips

---

### Post by Village on 2006-12-01
yeah I was talking the x86. Thanks for the help, I've been wanting to try out Beryl for a while. 

Village

---

### Post by guitarmaster on 2006-12-01
Hanzomon4,

You are a god....

I went to the compiz-mirror and was adding each of the debs one at a time. My next step would have been to try the repo you suggested, which is advertised on the front page there, so you saved me some time.... and hopefully anyone else who reads this thread...

Seriously, thank you very much for a lightning fast and accurate response.

Beryl is now working... and she is beautiful!

Guitarmaster

---

### Post by hanzomon4 on 2006-12-01
No problem, and quiet with the God thing. I don't wanna get struck by lightning or something

---

