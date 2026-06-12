---
title: "Installing Oracle Jinitiator in Ubuntu"
date: 2006-07-19
forum: General Help
---

### Post by RedBowers on 2006-07-19
I am trying to figure out how to install the oracle Jinitiator that we use at our company to connect to our oracle database. I have read through metalink hoping to be able to find some type of clue and have come up with nothing. Our apps are on version 10.7NCA. Right now this is the only thing keeping me from pushing microsoft out the door.

Any help would be greatly appreciated. Thanks Y'all
Red

---

### Post by Ferri on 2006-08-29
I'm also stuck here. Anyone?

---

### Post by mpsii on 2006-09-11
JInitiator is a Windows-only application. You can try a Wine/IE/JInitiator combination. YMMV

---

### Post by RedBowers on 2006-09-12
I actually got around the problem by installing a windows 2003 server inside of a vmware server and used a seamless rdp hook to that. Does a fantastic job. Thank you for your input however.

---

### Post by frediE on 2007-01-12
OK, This is the point where give back to that of which I have taken.

Jinitiator is boarder line the D.  If there is any piece of code that my linux box can do without is that POS.

However, I give hope...  How can I run this wonderful applications they call Oracle on my linux box.

By using the built in JAVA.

1. install java
2. make sure the java plugin works in your Firefox
3. give thanks to A. Vallark

Below are instructions for How to use Oracle applications with Linux and Firefox!!!!
[https://ptweb.op.ph.ic.ac.uk/%7Egraceej/help/howto/oracle-java-linux/]("https://ptweb.op.ph.ic.ac.uk/%7Egraceej/help/howto/oracle-java-linux/")

---

### Post by troach on 2007-01-26
> **RedBowers said:**
> I am trying to figure out how to install the oracle Jinitiator that we use at our company to connect to our oracle database. I have read through metalink hoping to be able to find some type of clue and have come up with nothing. Our apps are on version 10.7NCA. Right now this is the only thing keeping me from pushing microsoft out the door.

Any help would be greatly appreciated. Thanks Y'all
Red

I would go visit [www.dizwell.com](www.dizwell.com) for some assistance. There are things you have to do in Ubuntu such as create symbolic links for AWK and SED. If you look at his Ubuntu/Oracle install guide, it might give you some ideas.

Good Luck!

---

