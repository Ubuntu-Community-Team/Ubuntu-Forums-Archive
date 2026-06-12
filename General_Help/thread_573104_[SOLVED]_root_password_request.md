---
title: "[SOLVED] root password request"
date: 2007-10-11
forum: General Help
---

### Post by djbsteart1 on 2007-10-11
when i try to install java, the guide tells me to use the 'su' command which then prompts me for the root password. however i havent got a clue what the root password is and as i didnt set one when i installed i am slightly lost as to what i might me. so i was hoping that somebody here could either advise me on a different way of installing java or where my root password might be or how to set one, or what it is.
thanks in advance for this trouble to you, donald.

---

### Post by netztier on 2007-10-11
> **djbsteart1 said:**
> when i try to install java, the guide tells me to use the 'su' command which then prompts me for the root password. however i havent got a clue what the root password is and as i didnt set one when i installed i am slightly lost as to what i might me. so i was hoping that somebody here could either advise me on a different way of installing java or where my root password might be or how to set one, or what it is.
thanks in advance for this trouble to you, donald.

Which Java would that be? Do you install it from the ubuntu repositories with apt-get/aptitude/synaptic, or did you download some other package directly from java.sun.com? The package name in the Ubuntu repositories is **sun-java5-bin** or **sun-java6-bin**. Using the version from the repos is preferrable ove a 3rd party source, because system integration has been properly tested and verified.

In ubuntu, the root account is disabled, hence you cannot "become root" with su.

Any app that requires root priviledges must be started with **sudo <application name>**. If your currently-used user account is a member of the "admin" group  you get prompted not for the root pw, but *your own*. So if you need a root shell, all you do is **sudo bash** on a command line, give *your* password when prompted to... and voilà - you "are" root.

Alternative: use the "Main Menu" configuration tool in System -> Preferences. In the "Application Menu", there is a sub-group called "System Tools". Within that group, activate the checkbox next to "Root Terminal". 

Now you can navigate from the Gnome Panel -> Applications -> System Tools -> Root Terminal. After clicking, you are prompted for *your* password, and then you get a root shell.

best regards

Marc

*Edit: here's what the Ubuntu Community Documentation has to say about sudo, root and su: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)*

---

### Post by thirddeep on 2007-10-11
Run the installer with sudo, as in :
```
sudo JAVA_INSTALL
```
This will now ask for your password.

Or if you really want a root password :
```
sudo passwd root
```

Thd.

---

### Post by Joeb454 on 2007-10-11
when you're installing something, usually in Ubuntu it's sudo, from my experience anyway, or gksudo for graphical things.

And the root password is the password you put in when you installed ubuntu and created the first user account (which I'm guessing is yours)

e.g. If I create a user called Alf with password noggin at system install, then the root password is noggin

---

### Post by djbsteart1 on 2007-10-11
thanks a lot for the quick reply, they have helped a lot with the trouble. althoguh being very new to ubuntu and still ery lost i would be grateful if someone could tell me where the apt repos are? or am i being really stupid and there right infront of me?
thanks again, donald

---

### Post by taurus on 2007-10-11
You mean /etc/apt/sources.list!

```
cat /etc/apt/sources.list
```

---

