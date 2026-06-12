---
title: "running natty server"
date: 2013-09-06
forum: General Help
---

### Post by anthony5 on 2013-09-06
hi all, first time here so thanks for reading this. i have a small company that uses the old natty lamp server and now we are starting to add retail to our php and running into problems, image that. i know it is beyond EOL, so no need to go there. my question is this.... what is the best and eayiest way to upgrade this server? I am not into all the verations on linux. natty is and ubuntu distro. we need php, mysql, apache to start with, thanks again. anthony

---

### Post by bluefrog on 2013-09-06
depending on the data you have on the server, it might as well be easier/quicker to backup that data and install a fresh recent ubuntu.
you can also upgrade of course.

---

### Post by anthony5 on 2013-09-06
yes i want to do a fresh install as a lamp type server, php mysql and apache. looking for the best server distro for inventory data maintaining and collection, and serving our php pages. simple. need to run a decent firewall and that about it.

---

### Post by sanderj on 2013-09-06
> **anthony5 said:**
> yes i want to do a fresh install as a lamp type server, php mysql and apache. looking for the best server distro for inventory data maintaining and collection, and serving our php pages. simple. need to run a decent firewall and that about it.

Can't you use Ubuntu 12.04? It's LTS and supported.

Or if you want an old version as *server*, you can use 10.04 (server only)

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

---

### Post by mörgæs on 2013-09-07
When you have a fresh install of 12.04.3 server version you can add the complete LAMP stack with one command:

```
sudo apt-get install lamp-server^
```

---

### Post by anthony5 on 2013-09-09
Thank you sir

---

### Post by mörgæs on 2013-09-09
You're welcome. 
If this solves your problem please mark the thread so. It will make it easier for others to find the answer.

---

