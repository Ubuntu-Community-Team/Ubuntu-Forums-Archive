---
title: "libgtk2-perl missing from new install"
date: 2014-07-29
forum: General Help
---

### Post by ykuzma1 on 2014-07-29
I have a deb package that I developed, and so far I had been testing it with Ubuntu 12.04. This worked totally fine. Software Center would use debconf to get user input during installation, not only for my application but some of the dependencies such as mysql-server and postfix. Now I'm testing in 14.04 and Software Center freezes up on me. In the terminal it says that Gnome could not be initialized with Software Center falling back to dialog. dialog never seems to appear - but that's a totally separate issue. This is solved by installing libgtk2-perl *before* installing the package. Both using `apt-get install libgtk2-perl` in `preinst` or setting libgtk2-perl as a `Pre-Depends` does not fix this issue.

So is Ubuntu 14.04 supposed to come installed with libgtk2-perl? I was going to submit a bug report but I wanted to make sure that it was legitimate problem first as I couldn't find much about this after some searching.

---

### Post by ykuzma1 on 2014-07-30
bump

---

### Post by mc4man on 2014-07-30
"So is Ubuntu 14.04 supposed to come installed with libgtk2-perl?"
No, it doesn't. ( even libgtk3-perl isn't part of the default install

---

### Post by ykuzma1 on 2014-07-30
I know it doesn't come installed. That why I asked is it *supposed* to.

To me, not including it seems to break a major part of Software Center (one of the most important features Ubuntu provides new comers who don't know about `apt-get` yet). For example, install MySQL Server on a 14.04 build. On my machine, it installs all the way through without a single input box. It's supposed to have one for the password for the root MySQL user. Instead it installs *without* a root password. Tell me that's not a huge security hole for newbies.

I guess a better question would be - is there something that was supposed to take the place of libgtk2-perl in 14.04? Once again, I am only asking to confirm that this is an issue with others and that it's not already being taken care of so that I can file a bug report. I couldn't seem to find any bug reports or forums on the internet talking about it so I wanted to double check.

libgtk3-perl is irrelevant to what I'm asking because no part of Software Center depends on it.

---

### Post by grahammechanical on 2014-07-30
I am on Ubuntu 14.04.1 and synaptic tells me that libgtk2-perl is installed. It is version 2:1.249-2. This installation is close to being default. I do have unity-system-compositor installed. My Utopic install also has libgtk2-perl installed.

Regards

---

### Post by ykuzma1 on 2014-07-30
I thought you were onto something there. Unfortunately, Ubuntu 14.04(.1) doesn't come installed with synaptic; synaptic also happens to depend on libgtk2-perl which is where you got it from. I just tried to install Utopic in a VirtualBox VM to test that, but it freezes when you enter in the password. I'll try to test Utopic in xen when I get home from work. Did you happen to also install synaptic in Utopic?

---

### Post by mc4man on 2014-07-30
> **ykuzma1 said:**
> I know it doesn't come installed. That why I asked is it *supposed* to.
.
To be more precise it's not supposed to.
So file a report on why it should be inc.
As far as your deb, have you tried making it a Pre-Depends: in the control file?

---

### Post by ykuzma1 on 2014-07-30
Do you have some reference to support that? I ask because it has been included in previous versions of Ubuntu (Ubuntu 12.04 for example). Not to mention, there are the other problems I've listed in this thread such as the potential security holes and the general lack of the user being able to configure new applications. This leads me to believe it's a problem with Ubuntu and not my package. (Even if it was, why would I file a report at that point? I'd happily just fix my package if I could.)

As far as my deb, please read my first post. I did.

---

### Post by ykuzma1 on 2014-07-30
Tested Ubuntu 14.10 in xen, still no libgtk2-perl, and Software Center still doesn't ask for user input.

---

### Post by grahammechanical on 2014-07-30
> [COLOR=#000000]synaptic also happens to depend on libgtk2-perl which is where you got it [/COLOR]

Ah! Sorry for the false hope.

---

### Post by ykuzma1 on 2014-07-31
> **grahammechanical said:**
> Ah! Sorry for the false hope.

No worries! I still appreciate the help.

---

