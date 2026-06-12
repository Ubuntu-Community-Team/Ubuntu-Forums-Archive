---
title: "apt-get package not found problem (specifically php5-gd)"
date: 2007-04-26
forum: General Help
---

### Post by biofedora on 2007-04-26
Hi, 

I'm fairly new to Ubuntu. I have a LAMP server going via Ubuntu-server-6.10 but I need to get GD up and running. When I try:
      sudo apt-get install php5-gd
I get a package not found error. I have played extensively with my /etc/apt/sources.lst file and it currently consists of:

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

I have had this problem with other packages as well and so posted on this more general forum. Am I doing something wrong re apt-get configuration? I have spent a considerable amount of time trying to work this out. I also tried downloading the GD Ubuntu .deb package and installing but then I had to worry about unresolved dependencies and again saw the package not found message.

I appreciate any help anyone can give me. Thanks in advance.

---

### Post by Theimon on 2007-04-27
What if you use Synaptic to search for and install that package? Or try aptitude search php5-gd (or variations on that name).

---

### Post by az on 2007-04-27
You also need the dapper-security repos.

---

### Post by biofedora on 2007-04-27
Thanks for your input. The solution to this problem, embarassingly, lies with my carelessness. The apt-get repository list file is /etc/apt/sources.list NOT /etc/apt/sources.lst. Once I corrected that everything worked fine. I noticed that quite a few howtos and threads online used the .lst extension as well which only reinforced my use of it. 
Once again I appreciate your input and I will be more careful in the future.

---

