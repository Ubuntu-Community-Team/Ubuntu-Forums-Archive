---
title: "capture messages"
date: 2014-05-12
forum: General Help
---

### Post by i57chevy on 2014-05-12
Hey guys.  I want to learn how to capture messages on my network at home.  Specifically, I want to be able to capture text messages that go across my router.

---

### Post by bapoumba on 2014-05-12
Text messages that you are sending from your phone or other type of messages such a text chat utilities on your computer ?

---

### Post by i57chevy on 2014-05-12
Can I do both?  I am trying to control and find out what is being sent and received on my network.

---

### Post by spynappels on 2014-05-12
Wireshark/tshark will allow you to see what is on the wire, assuming it's not encrypted.

---

### Post by i57chevy on 2014-05-12
do cell phones encrypt messages by default?

---

### Post by spynappels on 2014-05-13
If you are referring to SMS messages, these will not go across the IP network. SMS messages will use the GSM/CDMA network instead.

If you are referring to IM clients, some encrypt messages and some don't, you'll have to see.

I would just say that if you are intercepting messages going across the IP network, you probably should let any users of your network know that they may be subject to monitoring. Depending on your location, this may even be a legal requirement.

---

### Post by bapoumba on 2014-05-13
> **spynappels said:**
> 
I would just say that if you are intercepting messages going across the IP network, you probably should let any users of your network know that they may be subject to monitoring. Depending on your location, this may even be a legal requirement.
That was underneath my first question. Unless more info is given by the OP, I recommend no further help.

---

### Post by i57chevy on 2014-05-13
This is my home network.  Users are family members.  particularly minors.  I don't think that they have any legal requirements.

---

### Post by HiImTye on 2014-05-13
if your concern is minors on your network, you should look into a solution such as dansguardian. that's the extent of the assistance that I would be willing to give in these types of situations, as they carry legal as well as ethical issues.

---

### Post by i57chevy on 2014-05-13
ok, well thanks your your help.

---

