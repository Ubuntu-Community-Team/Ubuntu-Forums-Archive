---
title: "secure webdav?"
date: 2008-04-24
forum: General Help
---

### Post by mdmolier on 2008-04-24
I just installed ubuntu 8.0.4. Under Places... Connect to server I can't connect to a secure webdav? I could do this in ubuntu 7. ANyoune knows the trick?

---

### Post by innuendosoft on 2008-04-29
hi mdmolier, you should go to Places->Connect to Server...
Then select "Custom location" and enter davs://hostname  where "hostname" is the URL of your dav server (without https if it has it).
You'll be prompted to enter user and pass, proceed and enjoy.

Good luck

---

### Post by ymp on 2008-04-29
I tried this, received no id & pw dialog and instead received an error message stating I could not connect,

---

### Post by siouzi on 2008-04-30
Secure webdav (davs, https) does not work in Ubuntu Hardy - prove me wrong :) Unsecure webdav (dav, http) may work, webdav with Kubuntu Konqueror or Gutsy may work... no thanks.

Using Nautilus I get repeatedly prompted for password and eventually it fails with some authorization error. After installing davfs2 and trying to mount webdav it fails with 401 authorization required or something like that. *Sigh*...

**Edit:** I take the first statement back! Secure webdav works, at least with **davfs2** and some Windows webdav server :popcorn: 

**Novell NetStorage** webdav is a problem, see e.g. this first Google result: [davfs with Novel Netstorage](http://www.smashedstack.net/webdav/).

However, using Nautilus I get

- Error: HTTP Error: Unauthorized. Please select another viewer and try again. (some Windows webdav server)
- repeatedly asked for password, fails (Novell NetStorage server)

:/

---

### Post by Conjacq on 2008-06-13
This is bug [#222532]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/222532").

---

