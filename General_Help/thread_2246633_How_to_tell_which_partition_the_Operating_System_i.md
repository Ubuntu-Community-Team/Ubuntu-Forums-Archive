---
title: "How to tell which partition the Operating System is on?"
date: 2014-10-02
forum: General Help
---

### Post by christon74 on 2014-10-02
Good afternoon fellow ubunters :)
I have two PCs and a laptop. 
This morning I have installed Linux Peppermint alongside Windows XP (not connected to the web) and Zorin on a slim PC (please do not ask which brand, I really do not know, I bought it from Amazon). Now the problem is that Zorin will not boot. I only get the 'Zorin welcome screen' so to speak and the white wheel keeps turning for ages! (sigh!)
I have tried the advanced options, recovery, try repairing broken packages, not to much avail.
XP will boot in two shakes of a lamb's tail though. 
And it seems Ubuntu 12.04 is still present on one of the partitions. So my idea was to delete this one partition, and this could perhaps help me boot Zorin again? 
Thank you in advance for help ;)

Chris.

---

### Post by christon74 on 2014-10-02
one thing I need add: When I try a normal boot after dpkg (repair broken packages) here is the message I get on the screen: Warning: Fake initctl called, doing nothing.

Uuuuh?

---

### Post by grahammechanical on 2014-10-02
Deleting one partition will not fix the loading problems of an OS on another partition. For all you know Zorin could be built upon Ubuntu 12.04 and deleting what you think is a 12.04 partition would actually be deleting Zorin. Try re-installing.

Regards.

---

### Post by christon74 on 2014-10-03
Good morning Grahame:)
Many thanks for this info. I think problem is solved. I have found how to load Zorin. It is a bit strange but it is listed under 'Ubuntu 12.04', but I can log on to Zorin OK. And I have just re-grown the /dev/sda7 partition I had shrunk to a mere 23 a wee while ago. So everything is back to normal.;)

---

