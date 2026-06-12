---
title: "bluetooth headset disconnecting"
date: 2007-03-18
forum: General Help
---

### Post by brynk on 2007-03-18
Hi,

I just got my new bluetooth headset (Plantronics Voyager 510) to work in Edgy. It works fine, but a short time after using it it gets disconnected, saying "RFCOMM channel lost". Obviously, this is not very convenient, since I'm using the headset primarily for calling (Ekiga). When I get a call the connection isn't fired up again, so I can't answer it. Is there anything I can do to keep the connection going?

---

### Post by brynk on 2007-03-19
I set the link mode option in my hcid.conf to master and that seems to do the trick:

```
lm master;
```

---

### Post by brynk on 2007-03-19
or not... :( 

I just lost it again, can someone please help me out on this?

---

### Post by fragos on 2007-03-19
/etc/bluetooth/hcid.conf try editing security user; to security auto; which I had to do to get my cell to pair with my Linux bluetooth dongle.  I haven't tried pairing with a headset and Linux although there are some howtos on that specific subject.

---

### Post by brynk on 2007-03-20
My security setting is already auto. The pairing isn't the problem, everything works great. It's just that the connection dies after a while.

---

### Post by fragos on 2007-03-20
I have no experience with a problem like this and haven't experimented with a bluetooth head set.  You might try the [www.linuxquestions.org](www.linuxquestions.org) which coveres many distributions.  They have a good Ubuntu forum and your problem may be shared with other distrobutions.  I recommend you look there as well.

---

### Post by PartisanEntity on 2007-04-08
> **brynk said:**
> Hi,

I just got my new bluetooth headset (Plantronics Voyager 510) to work in Edgy. It works fine, but a short time after using it it gets disconnected, saying "RFCOMM channel lost". Obviously, this is not very convenient, since I'm using the headset primarily for calling (Ekiga). When I get a call the connection isn't fired up again, so I can't answer it. Is there anything I can do to keep the connection going?

Hello, could you please tell me which How To or method you used to get the headset working? Thank you.

---

