---
title: "Build-essential a broken package?"
date: 2007-09-24
forum: General Help
---

### Post by AxAeo on 2007-09-24
So I tried to install build-essential on my desktop today...

```
axaaeo@axaaeo-desktop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages
```

This doesn't make any sense to me at all, seeing as I installed it on my Ubuntu laptop, which was installed from the same LiveCD as my desktop, and they've both downloaded the same updates and such. I tried sudo apt-get update, which didn't help... Any suggestions?

---

### Post by por100pre1 on 2007-09-24
Try this:

```
sudo apt-get install -f
```

```
sudo aptitude install libc6-dev g++
```

---

### Post by AxAeo on 2007-09-24
Thanks... It seems that the second command downgraded libc6-dev...

```
Downgrade the following packages:
libc6 [2.5-11 (now) -> 2.5-0ubuntu14 (feisty)]

Score is -40
```

I don't know the implications of that, but I don't have a problem with it, as long as build-essential gets installed, which it did.

What does the score mean?

---

### Post by por100pre1 on 2007-09-24
For each broken dependency in Aptitude the negative score increases. A score of -40 is usually not bad, something can be broken; but again, a score of -40 is usually not bad.

EDIT: BTW, Aptitude is a lot more strict handling dependencies than apt-get. It should not be something to worry about. :)

---

### Post by AxAeo on 2007-09-24
Ah I see... So basically it's a rating of how much crash potential my broken packages give me.

---

### Post by por100pre1 on 2007-09-24
> **AxAeo said:**
> Ah I see... So basically it's a rating of how much crash potential my broken packages give me.

Yes, basically that's what it is. The score is very low. :)

---

### Post by AxAeo on 2007-09-24
> **por100pre1 said:**
> Yes, basically that's what it is. The score is very low. :)
Ah I see.. Curiously, at what score should I begin to worry?

---

### Post by por100pre1 on 2007-09-24
I'm not an expert on those numbers. Usually when a solution describes to remove or replace packages then it is something to carefully consider. A good way to check for serious breakage is to use this command:

```
sudo apt-get install -f
```

As you can see it uses apt-get instead of aptitude, aptitude would try to resolve too many dependencies that doesn't represent serious breakage.

---

