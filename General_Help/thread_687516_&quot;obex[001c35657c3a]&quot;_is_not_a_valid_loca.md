---
title: "&quot;obex://[00:1c:35:65:7c:3a]&quot; is not a valid location."
date: 2008-02-04
forum: General Help
---

### Post by ele_mugv on 2008-02-04
that's wat happens when i try to connect to my mobile phone using bluetooth...pls help

---

### Post by kjbuente on 2008-02-04
There is a OBEX package(s) that you need to install. I do not know the name of the top of my head. Type OBEX in synaptics and read the discriptions. It should say something about adding OBEX support. I think you can find it as well if you type in bluetooth instead. Thats how I found it.

Just a side note, make sure that your phone does support OBEX. I spent days trying to get it to work with my motorola V710, only to find out that it was not compatible.

---

### Post by Kevbert on 2008-02-05
I have a similar problem with Obex...not a valid location.
I'm using an Acer Travelmate 803lci laptop, with built in bluetooth, trying to talk to a Sony Ericsson T68i, which support Obex.  I've tried downloading a number of bluetooth programs from the repositories and had no luck transferring any files to or from the phone.
I'm able to pair the two devices and make each discoverable to the other.:confused:

---

### Post by steveneddy on 2008-02-05
**gnome-obex-server**

Put this in your start up file in System --> Preferences --> Sessions

so it starts when you start.

You also may want to try using [blueman]("http://blueman.tuxfamily.org/") as a means of controlling the bluetooth stuff. It is a great piece of software and, IMHO, better than the Gnome stuff.

You may have some of this installed.

Look under Applications --> Accessories --> Bluetooth File Sharing

that's gnome-obex-server

---

### Post by Kevbert on 2008-02-08
Sorry about the delay in replying. Thanks for the info.  I can now transfer files.  The fun bit will be to repeat this on an old Apple Mac!!!

---

### Post by HuBaghdadi on 2008-03-02
Hi.
I got the same error.
If I want to use blueman, should I disable (or something like) GNOME Bluethooth manager?

---

### Post by bvivek88 on 2008-03-02
Thanx for ur answer it worked for me:):

---

