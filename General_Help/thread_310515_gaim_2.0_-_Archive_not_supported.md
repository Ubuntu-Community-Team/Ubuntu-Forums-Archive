---
title: "gaim 2.0 - Archive not supported"
date: 2006-12-01
forum: General Help
---

### Post by smithveg on 2006-12-01
hi,

I had downloaded 'gaim-2.0.0-0.beta5.src.rpm'. But i do not know how to install in Desktop. It prompt me the error says 'Archive type not supported'

Someone know how can i un archieve this packages?

Thanks.

---

### Post by reclusivemonkey on 2006-12-01
> **smithveg said:**
> hi,

I had downloaded 'gaim-2.0.0-0.beta5.src.rpm'. But i do not know how to install in Desktop. It prompt me the error says 'Archive type not supported'

Someone know how can i un archieve this packages?

Thanks.

You are trying to install an RPM which is native to Red Hat and Red Hat based distros. Use apt-get to install gaim;

```

sudo apt-get install gaim

```

or download a DEB and double click it. Isn't gaim already installed on your machine?

---

### Post by smithveg on 2006-12-01
Thank your reply,

Ya, gaim come with the ubuntu default installation. But it's version 1.5. Now i want to update to 2.0.

Do you mind to tell me, where can i get the deb package?
I downloaded the RPM package from, [http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444](http://sourceforge.net/project/showfiles.php?group_id=235&package_id=253&release_id=462444)

---

### Post by reclusivemonkey on 2006-12-01
Erm, not sure I use Edgy myself. Does Automatix give you Gaim 2.0 Beta???

---

### Post by smithveg on 2006-12-01
What's Automix?

Ok, after i install a RPM from Synaptic, i seems to be able to open the file. But i do not know how to make the installation.

Is there any other package that use for ubuntu? Instead of RMP that is Red Hat archive.

---

### Post by reclusivemonkey on 2006-12-01
> **smithveg said:**
> What's Automix?

Ok, after i install a RPM from Synaptic, i seems to be able to open the file. But i do not know how to make the installation.

Is there any other package that use for ubuntu? Instead of RMP that is Red Hat archive.

The site is down at the moment; its a program which lets you easily install all sorts of things for Ubuntu;

[http://www.getautomatix.com/](http://www.getautomatix.com/)

In the mean time, you can get Gaim 2.0 for Dapper here;

[http://repository.debuntu.org/#availablepackages](http://repository.debuntu.org/#availablepackages)

---

### Post by arnieboy on 2006-12-01
Everything except the Automatix home page is up.
The forums, wiki and repositories are up and working. Our home page has had some database related issues and our host is looking into it. This however has not affected Automatix operations.

---

### Post by smithveg on 2006-12-02
Hi reclusivemonkey,

I follow the instruction here, [http://repository.debuntu.org/#availablepackages](http://repository.debuntu.org/#availablepackages)

But i can not trace out the gaim 2.0 package name. Can you show me the way to pick the package name. Thanks.

---

### Post by xabbott on 2006-12-02
> **smithveg said:**
> Hi reclusivemonkey,

I follow the instruction here, [http://repository.debuntu.org/#availablepackages](http://repository.debuntu.org/#availablepackages)

But i can not trace out the gaim 2.0 package name. Can you show me the way to pick the package name. Thanks.

Go to your Terminal (Applications> Accessories)
Type 
```
 sudo gedit /etc/apt/apt/sources.list
```
Go to the bottom of the file and paste in the following
```

deb  [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) edgy multiverse

```
Now save and exit. Once you are back at the command line paste:
```

wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt) && sudo apt-key add GPG-Key-chantra.txt && rm GPG-Key-chantra.txt
```
Then type
```
apt-get update
```

Now you should be able to get the newest version. You can use Synaptic or apt-get.

---

### Post by smithveg on 2006-12-02
Hi, xabbott,

You getting me confusing. I follow your instruction, the run, sudo apt-get update. Then i restart gaim. Nothing is update. The gaim version is still 1.5.1.

From the guide here, [http://repository.debuntu.org/#authentificate](http://repository.debuntu.org/#authentificate)
I had just stuck in a part.

$sudo apt-get update (dont)
$sudo apt-get install **packagename** (I can not get the correct package name)

Help !!!

---

### Post by xabbott on 2006-12-02
> **smithveg said:**
> Hi, xabbott,

You getting me confusing. I follow your instruction, the run, sudo apt-get update. Then i restart gaim. Nothing is update. The gaim version is still 1.5.1.

From the guide here, [http://repository.debuntu.org/#authentificate](http://repository.debuntu.org/#authentificate)
I had just stuck in a part.

$sudo apt-get update (dont)
$sudo apt-get install **packagename** (I can not get the correct package name)

Help !!!

It should be 
```
sudo apt-get install gaim
```

---

### Post by raist78 on 2006-12-02
Hi, hope you can help me with an issue with Gaim 2.0 beta5 in Edgy. It keeps crashing saying Segmentation fault (core dumped) ....the same thing was happening in beta3 (default edgy version). Looking for an answer in internet gave me no results. Can it be an issue of the deb packages...maybe i have to compile it myself?

---

### Post by smithveg on 2006-12-02
Hi, raist78,

I do not sure what you had faced, it may be i'm not facing this problems or i'm not using edgy. Anyway, you can try to give some details on what error you see. Then i might trying to helps out.

Smithveg

---

