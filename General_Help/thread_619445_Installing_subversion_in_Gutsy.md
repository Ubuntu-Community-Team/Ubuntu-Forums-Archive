---
title: "Installing subversion in Gutsy"
date: 2007-11-21
forum: General Help
---

### Post by Shardsofmetal on 2007-11-21
When I try to install subversion in gutsy using aptitude, I get the error "No candidate version found for subversion." I tried to install the package using apt-get and synaptic too. I tried updating the repositories using both synaptic and apt-get, and still no luck. Can anybody help me install subversion?

---

### Post by der_joachim on 2007-11-21
IIRC, svn is in either universe or multiverse. Make sure that you have enabled both repositories.

---

### Post by russyo on 2008-01-02
I'm having a similar problem.  /etc/apt/sources.list includes
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse

But subversion should be in main:
[http://packages.ubuntu.com/gutsy/devel/subversion]("http://packages.ubuntu.com/gutsy/devel/subversion")

I switched to a mirror (modified /etc/apt/sources.list, changing from [http://archive.ubuntu.com](http://archive.ubuntu.com) to [http://mirrors.xmission.com](http://mirrors.xmission.com)) and the problem has gone away, so there may be something wrong with archive.ubuntu.com.

sources.list:

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

deb [http://mirrors.xmission.com/ubuntu/](http://mirrors.xmission.com/ubuntu/) gutsy main

---

### Post by flbone on 2008-01-06
If I may add, I received this notice a few times and then after reading this thread discovered that main was not enabled in my repository list.  I enabled it and subversion appeared immediately and installed flawlessly.  I don't remember ever disabling main, so your problem may be that it simply wasn't enabled by default.

---

