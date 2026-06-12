---
title: "Lost stability in Dapper"
date: 2006-11-16
forum: General Help
---

### Post by Mimsy on 2006-11-16
I have started to have a lot of problems wth my Dapper installation. I haven't done anything weird, that I know of - I haven't gone crazy trying to clean out orphaned packages, I haven't installed bizarre stuff from outside the repos, or edited files i don't know what they are. I've installed the updates the little orange glowy button wants to install, and that's about it.That I can remeber anyway.

My problem is that Dapper has become very unstable. Hibernate is working less and less often, which is bad in a laptop, and it is showing disturbing tendencies to freeze or crash in the middle of my doing something, like typing a paper or surfing the web. It's almost as bad as windows! ](*,) 

I've tried looking for solutions the past week, but it's a bit difficult to do forum searches without knowing what causes the crashes. 

I'd appreciate some help.

Thanks,
Mimsy

---

### Post by taurus on 2006-11-16
Just want to have a look at your /etc/apt/sources.list first then!

```
cat /etc/apt/sources.list
```

---

### Post by Mimsy on 2006-11-16
Certainly. Here you go:

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by David Corrales on 2006-11-16
I see a couple foreign repos: automatix and wine. Automatix probably only has the script (I don't use it so I don't know), but wine could be a problem -_-
Why don't you see which packages those repositories are installing in your system and roll back for a bit to see if you stop seeing the problems.

---

### Post by ububaba on 2006-12-21
Don't get excited **Mimsy**. Can't offer you any solution. I am sitting in the same boat. Did you
get anywhere with the solution?

---

### Post by Mimsy on 2006-12-21
I still don't have an official solution, but I have noticed that Dapper became a lot more stable again a couple of updates later, and now it is almost back to its normal self. Now it crashes only when I try to have too much open for the amount of RAM I have installed.

If I do find a more formal solution I'll post it here though.

/Mimsy

---

### Post by ububaba on 2006-12-23
> **Mimsy said:**
> I still don't have an official solution, but I have noticed that Dapper became a lot more stable again a couple of updates later, and now it is almost back to its normal self. Now it crashes only when I try to have too much open for the amount of RAM I have installed.

If I do find a more formal solution I'll post it here though.

/Mimsy

> title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hdb1 ro quiet splash noapic nolapic acpi=off
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot 

After the addition of **noapic nolapic acpi=off ** in [COLOR="Red"]menu.lst[/COLOR] I have obtained total stability.
You may try this.

---

### Post by az on 2006-12-23
> **Mimsy said:**
> I still don't have an official solution, but I have noticed that Dapper became a lot more stable again a couple of updates later, and now it is almost back to its normal self. Now it crashes only when I try to have too much open for the amount of RAM I have installed.


High uses of Ram and Hibernation both require a lot of swap space.

Did you take the default partitioning scheme when you installed?  Have you added more ram since then?

If you have more ram than swap, hibernation will usually fail.

---

### Post by Mimsy on 2006-12-24
> **azz said:**
> High uses of Ram and Hibernation both require a lot of swap space.

Did you take the default partitioning scheme when you installed?  Have you added more ram since then?

If you have more ram than swap, hibernation will usually fail.

Yes to the first question, and no to the second. That would be it then. Off to repartition! :)

/Mimsy

---

### Post by az on 2006-12-24
> **Mimsy said:**
> Yes to the first question, and no to the second. That would be it then. Off to repartition! :)

/Mimsy

Well, no.  The default partitioning scheme sets up your swap properly.  If you did not add ram, then you should be okay.


How much ram are you using?  Run:

free


and post the result.

---

### Post by Mimsy on 2006-12-26
I have no access to the laptop in question right now, but I know I have one 256 module in there. 

So if the default partitioning scheme sets up everythig properly, then the swap size isn't what's causing the laptop to fail to hibernate. In other words, there's something all else going on that messes things up. I'd have preferred if it was a simple matter of resizing partitions...


/Mimsy

---

### Post by Mimsy on 2006-12-27
Alright, back with the laptop. Here we are:

> mimsy@Falcon:~$ free
             total       used       free     shared    buffers     cached
Mem:        256116     139724     116392          0       4512      45284
-/+ buffers/cache:      89928     166188
Swap:       746980     100976     646004


What else do you need?

/Mimsy

---

