---
title: "The following signatures couldn't be verified because the public key is not available"
date: 2013-12-01
forum: General Help
---

### Post by sam_baker2 on 2013-12-01
Hi,

I am trying to update my xubuntu 32 bit computer but I keep getting an error.
Specifically, when I do a sudo apt-get update, I see a lot of "get" attempts like these
examples as the terminal runs:

```

Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]                                 
Get:2 http://mu.archive.ubuntu.com precise-backports Release.gpg [198 B] 
Get:3 http://mu.archive.ubuntu.com precise-backports Release [49.6 kB]  
```

Then, at the end, I get this:

```

W: GPG error: http://ppa.launchpad.net precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EB563F93142986CE

```

Anybody know what is causing this?
I have xubuntu, 32 bit, 3.2.0-56-generic-pae.
I am running  xfce 4.8 desktop, but I am planning to add the ppa
repository later and upgrade to 4.10 latter.

Thanks for any help.

---

### Post by Bashing-om on 2013-12-01
sam_baker2; Hi !

You have lost the signing key - or never got it - for launchpad.
To authenticate launchpad, as it is a trusted site, do;
Terminal code:
```

Code:sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com EB563F93142986CE

```
Then see if you are able to update/upgrade.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by sam_baker2 on 2013-12-01
It's strange, I keep getting a keyserver timeout.
Will keep trying.

---

### Post by Bashing-om on 2013-12-01
sam_baker2; Well,

Try our server and see if it holds the key:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com EB563F93142986CE

```

[INDENT][INDENT]more than one way to 
[/INDENT][/INDENT]

---

### Post by sam_baker2 on 2013-12-01
Isn't that the same one?

---

### Post by claracc on 2013-12-02
You can try the "second approach" addressed in this link [http://opensourceforgeeks.blogspot.in/2013/04/w-gpg-error-httpppalaunchpadnet-precise.html](http://opensourceforgeeks.blogspot.in/2013/04/w-gpg-error-httpppalaunchpadnet-precise.html) in order to get the public key of repository you want. Note that in your case the key is EB563F93142986CE and as the link says you have to look for it beginning with 0x

---

### Post by oldos2er on 2013-12-02
This server seems to work better: ```
sudo apt-key adv --keyserver hkp://subkeys.pgp.net --recv-keys EB563F93142986CE
```

---

### Post by sam_baker2 on 2013-12-02
Thnks guys,
I went to the ubuntu keyserver and downloaded the key and manually installed it,
per the link claracc gave. Everything worked ok.
I can't figure out why I lost the key in the first place, although the computer is
rarely used and only updated once a week.

---

### Post by Bashing-om on 2013-12-02
sam_baker2; Outstanding !

You do good work ! Glad ya got it sorted out.

[INDENT]take care and
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by claracc on 2013-12-03
You are welcome. Glad you got fixed your problem.

---

