---
title: "port 80"
date: 2007-08-14
forum: General Help
---

### Post by cssutto on 2007-08-14
I have just installed a Kyocera KR 1 router and noticed after a port scan that port 80 is open.

Previous to the router install, this port was closed.

What is the significance of this open port?

KR1 requires that all setups to the router be done by going to the KR1 web site and making all changes through it.  Is this the reason for port 80 being open?

CSSJR

---

### Post by Seisen on 2007-08-14
Port 80 is the port that the server "listens to" or expects to receive from a Web client, assuming that the default was taken when the server was configured or set up.

---

### Post by cssutto on 2007-08-14
My question was poorly framed.

The question is:  Is this open port a hazard?

Gibson says it is, but he is talking windoze.

If it is a hazard, is there a way to protect it?

I would think that closing it would shut down the router.  Is that correct?

I am new to routers and I admit that the connunications side of computers is the great mystery to me.

CSSJr

---

### Post by lloyd_b on 2007-08-14
> **cssutto said:**
> My question was poorly framed.

The question is:  Is this open port a hazard?

Gibson says it is, but he is talking windoze.

If it is a hazard, is there a way to protect it?

I would think that closing it would shut down the router.  Is that correct?

I am new to routers and I admit that the connunications side of computers is the great mystery to me.

CSSJr

Having this port open is probably *required* in order to access the router's configuration.  It isn't really a security risk, provided that the administrative functions are protected by a good password.  On the other hand, if there's no password or an easy to guess password, then it *is* a hazard.

Look through the configuration pages (the "KR1 web site") - there should be a place to set the password.

Lloyd B.

---

### Post by cssutto on 2007-08-14
Thanks.

I have set a password and 128 bit encription as well, but I had the question about port 80.

Thanks.

CSSJR

---

