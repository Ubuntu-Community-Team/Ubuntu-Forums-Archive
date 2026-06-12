---
title: "Installation of OpenOffice.org Database"
date: 2015-09-04
forum: General Help
---

### Post by GirishSharma on 2015-09-04
I am using Ubuntu 10.04 LTS 32 bit on Virtual Machine.  When I try to install OpenOffice.org Database Version 3.2 by Ubuntu Software Centre I gets :

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.

And in the Details section this is there :
default-jre default-jre-headless java-common libhsqldb-java ttf-dejavu-extra

OK.  I tried to get the solution even but I am still not able to install the above software :
$ sudo -i
# apt-get clean
# cd /var/lib/apt
# rm -rf lists.old     ---- I added this line
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update

I don't know what more steps I need to follow.  Kindly help me.

Thanks and Regards
Girish Sharma

---

### Post by GirishSharma on 2015-09-07
Any update please.

---

### Post by howefield on 2015-09-07
You aren't likely to attract much in the way of replies running such an old, and unsupported version of Ubuntu not to mention such an old version of OpenOffice, which incidentally is also now not supported.

Perhaps it is time to bring it up to date. :)

---

### Post by GirishSharma on 2015-09-07
Thanks for reply.  Being an Old version should not be ever a technical reason.  What if I am happy with old version and Old is Gold... :)

Can you please focus on technical reason for not being able to install above OpenOffice.org database.

---

### Post by howefield on 2015-09-07
> **GirishSharma said:**
> Being an Old version should not be ever a technical reason.

Well actually, that's wrong.

> What if I am happy with old version and Old is Gold... :)

I am not saying don't use it, it's your machine and your choice.

> Can you please focus on technical reason for not being able to install above OpenOffice.org database.

No, I don't waste time on such long since unsupported software, I am merely explaining why you might not be attracting the answer that you would prefer to see.

Good luck.

---

### Post by GirishSharma on 2015-09-07
I am not attracting to newer version just because existing other software are working fine, so why I should just "upgrade" for only one software ?  Thing is why I am not able to install the older version software on older version OS ?  What is that technical reason is restricting me.

---

### Post by brian-mccumber on 2015-09-07
Technically, there is no more support for that OS or the software for it.

But you may find this article helpful - [http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

---

### Post by GirishSharma on 2015-09-07
It is unsupported.  Agreed.
It is older version.  Agreed.

So, can I say, no one on the earth can install OpenOffice.org database version 3.2 on Ubuntu 10.04 OS ?

---

### Post by brian-mccumber on 2015-09-07
If you go read that article at that link I provided and pay attention to the answer that is checked green there are ways to enable updates and get packages for your Ubuntu version. If that fails for you or you can't understand the answer then google how to install software on old and unsupported version of Ubuntu which is what I did when I found that article.

---

