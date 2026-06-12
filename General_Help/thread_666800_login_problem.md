---
title: "login problem"
date: 2008-01-13
forum: General Help
---

### Post by aaronp on 2008-01-13
Hi all,

I installed Ubuntu 7.10 on my PC as dual boot with WinXP home a couple of days ago. (i686 installation, Gnome)

Everything has been gonig fine but all of a sudden I cannot log in. When I enter my credentials I get a long wait on the blank light brown screen then a quick flash to a black screen with a blue line then it simply returns to the login page again and again.
I know it is not the details I am supplying because I tried typing it in incorrectly and it came up immediately telling my username/password was invalid.

Any ideas?

Thanks in advance
Aaron

---

### Post by taurus on 2008-01-13
Press <Ctrl><Alt>F2 and login with your username and password.  Then, look at the disk space to make sure you haven't maxed it out to 100%.

```
df -h
```
And if you were, you can create some free space to at least allow you to run Gnome again so you can clean out some unused files on your machine.

```
sudo apt-get clean
df -h
```

---

### Post by aaronp on 2008-01-14
Thanks Taurus.

I will try that when I get home tonight but not sure that is the problem because I created a 10Gb primary partition + 2Gb swap and have only installed a handful of packages since installing Ubuntu.
I am able to login in if I choose 'Options' and then change the session to the restricted type (i.e. the one where the warning comes up to say no initiation scripts will be run) and once I have logged in this way it seems to work fine without any discernable difference to the normal login (when it was working)

Thanks again
Aaron

---

