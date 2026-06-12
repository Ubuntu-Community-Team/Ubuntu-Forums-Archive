---
title: "How to install K3b in Xubuntu 12.04"
date: 2013-01-31
forum: General Help
---

### Post by John Jason Jordan on 2013-01-31
I have a fresh install of Xubuntu 12.04, x86_64. Previously the computer had regular Ubuntu 10.04, and K3b was installed and worked fine. Now, when I try to install K3b I get massive unsurmountable interconnecting dependency errors. 

I realize K3b is a KDE application, but I don't want to install all of KDE just to run K3b. Although I used Gnome under 10.04 I was able to install K3b without installing KDE, although I'm sure it installed some parts of KDE.

How can I install K3b in Xubuntu 12.04?

Edit: And I just tried to install Ktorrent and got the same mess of dependencies that are "not going to be installed."

---

### Post by meteorrock on 2013-01-31
First, purge your other torrent app through the terminal. 

```
 sudo apt-get purge ktorrent* 
```

Then use the terminal to install the other app you want. For K3b just use these commands in the terminal

```
 sudo apt-get update
```
```
sudo apt-get install k3b
```

Its alot easier to let the apt-get install your packages for you, unless you are looking for a .deb file. In your case, looking over the K3b site, they do not have a .deb. 

):P

~~~~~~~~~~~~~~~~~~~~


Edit after solved: You did say you tried to install ktorrent in the last line of your thread before this problem begain. 

Let me quote it for you.

> I have a fresh install of Xubuntu 12.04, x86_64. Previously the computer had regular Ubuntu 10.04, and K3b was installed and worked fine. Now, when I try to install K3b I get massive unsurmountable interconnecting dependency errors. 

 I realize K3b is a KDE application, but I don't want to install all of KDE just to run K3b. Although I used Gnome under 10.04 I was able to install K3b without installing KDE, although I'm sure it installed some parts of KDE.

 How can I install K3b in Xubuntu 12.04?

 Edit: And I just tried to install Ktorrent and got the same mess of dependencies that are "not going to be installed."

> Edit: And I just tried to install Ktorrent and got the same mess of dependencies that are "not going to be installed."

> Edit: And I just tried to install Ktorrent

> Ktorrent

For the others in here trolling below, you are not helping the OP. I suggest to RTFM. Hate to be blunt, but discrediting advice on gender will get you nowhere. When you hap hazard install packages when problems begin, try to purge your last action and try over. That or word your questions more properly. :) That is why I said to purge ktorrent. 
 __________________

---

### Post by John Jason Jordan on 2013-02-01
> **meteorrock said:**
> First, purge your other torrent app through the terminal. 
```
 sudo apt-get purge ktorrent* 
```
Then use the terminal to install the other app you want. For K3b just use these commands in the terminal

Umm, ktorrent is not installed. So sudo apt-get purge ktorrent just returns "package ktorrent is not installed."

> **meteorrock said:**
> 
```
 sudo apt-get update
```
```
sudo apt-get install k3b
```

Its alot easier to let the apt-get install your packages for you, unless you are looking for a .deb file. In your case, looking over the K3b site, they do not have a .deb. 

I tried the command line first, and only tried Synaptic hoping that the GUI would make the error messages from the command line clearer to understand.

sudo apt-get update

Updates the repo list without error. But afterwards 

sudo apt-get install k3b

Results in a list of unmet dependencies that "are not going to be installed":

kde-runtime
libk3b6
libkcddb4
libkcmultils4
libkde3support4
libkdeui5
libkfile4
libkio5
libknotifyconfig4

If I try to install any of those dependencies separately each gives me a fresh list of unmet dependencies that "are not going to be installed." And if I try to install any of those dependencies I get yet another list of unmet dependencies that "are not going to be installed." This would probably continue until I had installed everything in the repositories, and there would likely still be unmet dependencies.

Ditto the above for Ktorrent.

There is something fundamentally wrong here, but I can't figure out what it is or how to fix it.

---

### Post by monkeybrain2012 on 2013-02-01
> **meteorrock said:**
> First, purge your other torrent app through the terminal. 

```
 sudo apt-get purge ktorrent* 
```

Then use the terminal to install the other app you want. For K3b just use these commands in the terminal

```
 sudo apt-get update
```
```
sudo apt-get install k3b
```

Its alot easier to let the apt-get install your packages for you, unless you are looking for a .deb file. In your case, looking over the K3b site, they do not have a .deb. 

):P

What does torrent have to do with k3b???

---

### Post by monkeybrain2012 on 2013-02-01
Did you add any ppa? It happens usually because some dependencies or dependencies of dependencoes have conflicting versions. It is hard to give general advice (at least for me) if that is the case. When that happens (only rarely) I would try to install the dependencies one by one and note the error and then try to install those unmet dependencies until I locate the culprit.

---

### Post by BBQdave on 2013-02-01
> **John Jason Jordan said:**
> How can I install K3b in **Xubuntu 12.04**?

If you are looking for a solid burn program, you already have it - **Xfburn** :D

The two most recommended are K3b and Xfburn. Xfburn is lighter, and pulls in less dependencies. Many Gnome folk prefer Xfburn over Brasero.

---

### Post by John Jason Jordan on 2013-02-01
> **monkeybrain2012 said:**
> What does torrent have to do with k3b???

They are bot KDE apps that I am trying to install on Xubuntu. A lot of the missing dependencies are the same for both apps, and appear to be KDE libraries and utilities.

When I had Ubuntu (Gnome) 10.04 I installed these apps and the dependencies just installed at the same time. Now that I am trying to install them on Xubuntu 12.04 I am in dependency hell.

The dependency error messages list the dependencies and then say they "are not going to be installed." Yet each one of the dependencies is in the repo. Why can't they be installed? Well, because each dependency has another long list of dependencies that 'are not going to be installed." 

That's why I say something is fundamentally wrong. These apps should just install, together with all their required dependencies. That's what apt-get is supposed to do. 

The suggestion to do apt-get update was a good one, because screwed up repo lists could cause this. Unfortunately, it didn't help. I'm still trying to figure out what is wrong.

---

### Post by monkeybrain2012 on 2013-02-01
> **John Jason Jordan said:**
> 
The dependency error messages list the dependencies and then say they "are not going to be installed." Yet each one of the dependencies is in the repo. Why can't they be installed? Well, because each dependency has another long list of dependencies that 'are not going to be installed." 



I understand, that is usually caused by the presence of conflicting versions in your sources somewhere down the dependency chain. It can be the result of 

a) packaging errors in the official repo, in that case it will be sorted probably in a few days hopefully. Nothing can be done on your end.

b) more likely you have some ppa's activated. 

so, let's say you want to install x, it depends on y but y is not going to be installed. You try to install y, it tells you it needs to install z but z is not going to be installed. You try to install z and find that it needs w but w is already installed. So you check in synaptic (choose w and right click, go to properties > versions) and find that there are two versions in your source. ver1 from official repo and ver2 with higher version number from ppa. ver2 is the installed version but you want ver1, so you need to either force version to ver1 or purge the ppa, for example.

---

### Post by John Jason Jordan on 2013-02-01
> **monkeybrain2012 said:**
> Did you add any ppa? It happens usually because some dependencies or dependencies of dependencoes have conflicting versions. It is hard to give general advice (at least for me) if that is the case. When that happens (only rarely) I would try to install the dependencies one by one and note the error and then try to install those unmet dependencies until I locate the culprit.

Yes, I have a ppa for caffeine. But I can't see how that could make any difference for KDE dependencies.

I think you are right about the version mismatch, but the computer is up to date, so everything should be on the same page.

I tried installing the dependencies one at a time, but each one brought up another long list of unmet dependencies that "are not going to be installed." For fun I copied down one of the lists and tried to install those dependencies. Yup, you guessed it, another long list of dependencies that "are not going to be installed."

---

### Post by John Jason Jordan on 2013-02-01
> **John Jason Jordan said:**
> I think you are right about the version mismatch, but the computer is up to date, so everything should be on the same page.

I tried installing the dependencies one at a time, but each one brought up another long list of unmet dependencies that "are not going to be installed." For fun I copied down one of the lists and tried to install those dependencies. Yup, you guessed it, another long list of dependencies that "are not going to be installed."

OK, problem solved.

Using Synaptic, I did a reload (even though I had already done sudo apt-get update), and nothing changed.

So, acting on a hunch, I changed the server from "server for the United States" to "Main." After it reloaded I tried again, and finally K3b installed with all its dependencies without issue. And so did Ktorrent.

I guess there are servers and then there are servers. :(

---

