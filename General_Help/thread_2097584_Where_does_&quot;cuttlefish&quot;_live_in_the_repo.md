---
title: "Where does &quot;cuttlefish&quot; live in the repos"
date: 2012-12-23
forum: General Help
---

### Post by hwttdz on 2012-12-23
**EDIT: It appears to not be available for 12.10, but the 12.04 package should work [https://answers.launchpad.net/cuttlefish/+question/213205](https://answers.launchpad.net/cuttlefish/+question/213205)**

I'm looking for a program named cuttlefish ([http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish](http://www.omgubuntu.co.uk/2012/09/automate-ubuntu-with-cuttlefish)), according to a couple of sources it should be in the repository, but I can't find it via synaptic or apt-get or what-have-you.

Does anyone know what repository it should be in? Am I missing something from my sources.list?

```
## security
deb http://security.ubuntu.com/ubuntu quantal-security main restricted
deb http://security.ubuntu.com/ubuntu quantal-security multiverse
deb http://security.ubuntu.com/ubuntu quantal-security universe

## main
deb http://us.archive.ubuntu.com/ubuntu/ quantal main restricted
deb http://us.archive.ubuntu.com/ubuntu/ quantal multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal universe

## updates
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
deb http://us.archive.ubuntu.com/ubuntu/ quantal-updates universe
```

---

### Post by Paddy Landau on 2012-12-24
Thanks for posting this and the solution.

I had not come across Cuttlefish before, so I am going to try it!

---

