---
title: "[SOLVED] stop unwanted updates"
date: 2008-05-09
forum: General Help
---

### Post by mandrill on 2008-05-09
I have software installed from internet downloads that is in the repos - same version - the downloaded stuff works better & easier - yet I constantly have the updater in my face telling me I have 2 updates - which I do not want or need. I have locked my versions in package manager, which did not work. 

I hope someone out there knows how to make this stop! (I know its probably a
3 word terminal command, but, I don't know what it is!)

Lots of looks, no takers?

---

### Post by mandrill on 2008-05-10
[QUOTE=mandrill;4923430]I have software installed from internet downloads that is in the repos - same version - the downloaded stuff works better & easier - yet I constantly have the updater in my face telling me I have 2 updates - which I do not want or need. I have locked my versions in package manager, which did not work. 

I hope someone out there knows how to make this stop! (I know its probably a
3 word terminal command, but, I don't know what it is!)

Bump.......

---

### Post by Xiong Chiamiov on 2008-05-10
I believe
```

sudo aptitude hold [packagename]

```
is what you're looking for?

You don't like to have up-to-date software?

---

### Post by zvacet on 2008-05-10
@** Xiong Chiamiov**


> You don't like to have up-to-date software?

Maybe he don´t use that packages and in that case there is no ponit to update it.I locked compiz because I have bad video card and I can not use it.

---

### Post by soldersplash on 2008-05-10
Thanks for the info Xiong :), I have similar issue to 'mandrill'.
I used a patched version of 'nspluginwrapper' to get round a problem with AdobeFlash stuff on the internet, now the package manager keeps telling me I haven't got the latest version. Of course I haven't 'cos it wasn't working for me! I think mandrill meant he had the same situation where latest version of something in repo doesn't work properly for him.

Could you tell us how to undo this 'hold' ?

I guess at some point when the official repo versions of what we are 'holding' are fixed both mandrill and I will probably want to let the package manager update us. :)

---

### Post by mandrill on 2008-05-10
> **Xiong Chiamiov said:**
> I believe
```

sudo aptitude hold [packagename]

```
is what you're looking for?

You don't like to have up-to-date software?

First, thank you - (I was right, 3 word command in terminal)....second,
I love updated software - but when the method of installation (repos) results in exactly the same version of software, only harder to access
and update, AND configures itself in a different location, making your email
inaccessible, causing further workarounds, then no, I don't want it. Sounds
a little Windows-like, don't you think?

---

### Post by spydon on 2008-05-10
> Sounds
a little Windows-like, don't you think? 

Hehe only that if it would have been windows you wouldnt have been able to do anything about it... ;)

---

### Post by mandrill on 2008-05-10
By the way.....sudo aptitude hold [packagename] did not work.

---

### Post by mandrill on 2008-05-10
> **spydon said:**
> Hehe only that if it would have been windows you wouldnt have been able to do anything about it... ;)

Still can't do anything about it. Or the whole samba bug; they just decided to stop mid-project and leave it broken. Only way to use is to edit /etc/smb./conf. There is a lengthy discussion in launchpad.

---

### Post by zvacet on 2008-05-11
@ **soldersplash**

```
sudo aptitude unhold
```

@ **mandrill**

```
sudo aptitude forbid-version packagename
```

---

