---
title: "What is this and how can I fix it?"
date: 2008-06-28
forum: General Help
---

### Post by chroncile on 2008-06-28
I tried installing wine and firefox 3, but everytime I try to, I get these errors:

```

firefox-3.1:
  Depends: libcairo2 (>=1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
  Depends: libpango1.0-0 (>=1.20.1) but 1.18.3-0ubuntu1 is to be installed
 Depends: xulrunner-1.9.1 but it is not going to be installed


```

Please help me, I want to get rid of the errors. Thanks :)

---

### Post by steveneddy on 2008-06-28
You want to run the Windows version of Firefox 3 with wine?

As far as the packages go, go to Synaptic and search for the packages and install them.

libcairo2

libpango1.0-0

---

### Post by chroncile on 2008-06-28
No...there's a Firefox 3 setup in the synaptic package manager.

---

### Post by chroncile on 2008-06-28
Hello? Come on, please help a noob.

---

### Post by clw3388 on 2008-06-28
So... What's wrong with firefox in ubuntu?? I don't understand why you want to load wine and run firefox (windows version) in wine.... 
Maybe you can elaborate as to why.. People might have another work around... 

I suggest to just open a terminal and use sudo aptitude isntall firefox.. Nuthin wrong with the linux version of firefox..

---

### Post by Taxman415a on 2008-06-28
> **chroncile said:**
> No...there's a Firefox 3 setup in the synaptic package manager.

Yes, you're really not giving us much to go on to help you. What are you trying to do? Simply install the wine and firefox packages from synaptic? Don't you already have firefox? If you're not getting any wine errors telling us about that is just confusing the question.

What version of Ubuntu are you running? If you don't know, open up a terminal and give us the output of lsb_release -cr

---

### Post by chroncile on 2008-06-28
Omg, there's a firefox 3 for UBUNTU! Not windows, I'm not trying to use Wine to run it. I want to install firefox 3, but I keep getting that error. I need help fixing that error, look at that error and nothing else.

---

### Post by Taxman415a on 2008-06-28
Again, you're going to have to tell us more about what you are doing. What version are you running? (it looks like you are running 7.10 Gutsy). So what did you do to try to have Firefox 3 be available? It's not available by default to Gutsy. Asking questions with an approach that appears demanding without giving proper information isn't a generally successful method.

---

### Post by mc4man on 2008-06-29
Actually you can install it in gutsy from synaptic (Gran Paradiso ver.), it's listed under firefox. It does seem to appear the OP either has a borked hardy upgrade or is using hardy repo in gutsy

edit i never used it but there's no issue installing (in gutsy from gutsy repos)

---

### Post by chroncile on 2008-06-29
firefox-3.1:
  Depends: libcairo2 (>=1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
  Depends: libpango1.0-0 (>=1.20.1) but 1.18.3-0ubuntu1 is to be installed
 Depends: xulrunner-1.9.1 but it is not going to be inst

:|

---

### Post by steveneddy on 2008-06-29
> **chroncile said:**
> firefox-3.1:
  Depends: libcairo2 (>=1.6.0) but 1.4.10-1ubuntu4.4 is to be installed
  Depends: libpango1.0-0 (>=1.20.1) but 1.18.3-0ubuntu1 is to be installed
 Depends: xulrunner-1.9.1 but it is not going to be inst

:|

Are you running Gutsy?

FF3 won't install on Gutsy I don't think.

If you are on Hardy, the two packages:

libcairo2

libpango1.0-0 

Those are the installed versions of those packages on a fully updated Hardy install.

So, you must be running Gutsy, right?

Also - if you DL FF3 from Mozilla website, unpack it, then run the launcher from the folder, then you have it already.

I just don't understand the issue maybe, but you can get the updated packages from the internet easily. 

May look in 

packages.ubuntu.com

---

### Post by steveneddy on 2008-06-29
> **chroncile said:**
> 

Please help me, I want to get rid of the errors. Thanks :)

They aren't errors, it's telling you to install a newer version of those two software packages.

---

### Post by chroncile on 2008-07-01
Yes, I am running Gusty and I want to end these 'errors'.

---

### Post by txcrackers on 2008-07-02
So where did you get Firefox **3.1** from? Considering 3.0 has *just* been released...

---

### Post by daleus on 2008-07-05
sometimes

apt-get install -f

fixes it, I don't hold much hope, but try it.

---

