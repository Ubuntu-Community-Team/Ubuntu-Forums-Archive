---
title: "need advice"
date: 2007-07-07
forum: General Help
---

### Post by bomb-24 on 2007-07-07
I was going to install Ubuntu 7.04 on my system. I currently am running windows xp now. Should I install the desktop or server edition? And should I go with version 6 or 7? And my final question, Is Ubuntu the best thing to install? Or should I use a different linux?

---

### Post by aysiu on 2007-07-07
Read this:
[http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by init1 on 2007-07-07
> **bomb-24 said:**
> I was going to install Ubuntu 7.04 on my system. I currently am running windows xp now. Should I install the desktop or server edition? And should I go with version 6 or 7? And my final question, Is Ubuntu the best thing to install? Or should I use a different linux?
Desktop
7
Yes
Ubuntu is one of the most stable and easy to use Linux distributions I have ever used. If it doesn't work, try something else. Vector Linux is nice.

---

### Post by bomb-24 on 2007-07-08
thank you everyone. already installed Ubuntu 7.04. Running good. I have another question. What does logging on as user "root" do?

---

### Post by aysiu on 2007-07-08
> **bomb-24 said:**
> thank you everyone. already installed Ubuntu 7.04. Running good. I have another question. What does logging on as user "root" do?
It isn't necessary. Everything that 99.99999999% of Ubuntu users need can be accomplished more easily with *sudo*

Read these two pages for more details:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bomb-24 on 2007-07-08
I want to set up this thing on my computer and the website that is instructing me on what to do is telling me to log on as user "root". And I have done some things on Ubuntu where I get a message saying that I dont have permission to change a file or create something or whatever. Do you know what thats all about?

---

### Post by aysiu on 2007-07-08
Well, *sudo* basically allows you to be root for a particular command, so here's the difference: 

**Log in as root**: ```
su
password:
apt-get update
apt-get install xnest
exit
exit
``` **Use *sudo***: ```
sudo apt-get update
password:
sudo apt-get install xnest
exit
``` If you have many commands in a row to run as root and don't feel like typing in *sudo* a million times, just use ```
sudo -i
``` That will give you the same effect as a root login.

For more details, read the two links I posted earlier.

---

### Post by bomb-24 on 2007-07-08
thank you! Did you read my speaker and remote error post in general help? If you feel up to it, read it and see what you think. If you want. You have helped enough. Thank you again.

---

