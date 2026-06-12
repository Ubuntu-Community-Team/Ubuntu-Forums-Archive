---
title: "How do I create a Root Password?"
date: 2008-02-08
forum: General Help
---

### Post by Chappy7777 on 2008-02-08
I recently tried to use the Ubuntu Recovery that is one of the choices I now have on bootup since I have a dual boot, Feisty and XP.  When I clicked on the recovery choice it went thru my setup checking hardware, etc. At some point it stopped and asked me to enter my Root Password.
Since I have no Root Password, that ended that attempt at recovery. Just as well, since I found the answer to my problem yesterday when many others had the same problem when that system update messed up Flashplugin-nonfree in FFox. 

However, I'd still like to know how to create a Root Password in case I need it again. Someone told me how to do this a year or more ago, and having done it on Dapper, I then forgot how to do it.

So, can someone please help? Not the Admin PW needed to Login or to get to Synaptic, but the Root PW needed to get deeper.

---

### Post by bodhi.zazen on 2008-02-08
Ubuntu uses sudo, and there is no need to set a root password.

Use sudo <command> and enter your log-in pasword.

	[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

By default, the root account is locked. To set a root password, 

```
sudo passwd
```

To lock the account again,

```
 sudo passwd -l root
```

That is a small "L" and not a 1

---

