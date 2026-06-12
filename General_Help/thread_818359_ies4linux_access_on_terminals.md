---
title: "ies4linux access on terminals"
date: 2008-06-04
forum: General Help
---

### Post by casey.mynott on 2008-06-04
Hello all,

I am trying to setup a Edubuntu lab at my school and need access to internet explorer for some web sites that are IE only. I have ies4linux installed on the server but it is not accessible on the clients. Does anyone have an idea of how to do this or where I would find some info. I have searched and searched but no luck. Thanks for any help or a point in the right direction anyone can provide.

Casey

---

### Post by bingoUV on 2008-06-04
What kind of client and servers are they? How do the clients connect to the servers?

---

### Post by casey.mynott on 2008-06-04
> **bingoUV said:**
> What kind of client and servers are they? How do the clients connect to the servers?

The Clients are old P2's with 256MB of ram. The server is a newer Dell with 1.5 GB of ram. I just tried WINE and Notepad on the client and it works great. Now, I must be able to move some files around so IE works??? Suggestions????

---

### Post by bingoUV on 2008-06-04
How do the clients connect to the servers? SSH? VNC?

If you installed ies4linux on the server, why do you expect it to be accessible on the clients? For example, if you have rain in Texas, do you expect roads in Florida to be wet?

---

### Post by casey.mynott on 2008-06-04
> **bingoUV said:**
> How do the clients connect to the servers? SSH? VNC?

If you installed ies4linux on the server, why do you expect it to be accessible on the clients? For example, if you have rain in Texas, do you expect roads in Florida to be wet?

Okay, I am running a default edubuntu LTSP server setup. I don't really get your point. I have installed other programs and they show up on the client. Wine for example. Ies4linux does not. I am guessing that the script that builds the files doesn't put them into the right place in regards to the client folder? Thanks for the info thus far.

---

### Post by bingoUV on 2008-06-04
This LTSP bit was not clear to me. Now some LTSP expert might look into your problem.

---

### Post by casey.mynott on 2008-06-04
SOLVED! I just ran the ies4linux script on the client. I have done this before but it didn't work several times. For what ever reason it worked! ;)

---

