---
title: "Two kernels?"
date: 2008-04-30
forum: General Help
---

### Post by EliBaskin on 2008-04-30
After installing Hardy (upgrading from 7.10), I've noticed that I have 3 options on startup - two Ubuntu kernels and Windows. One of the kernels end with 16 and the other with 14. How do I remove the older one?

---

### Post by Monicker on 2008-04-30
Use synaptic or apt-get to search for linux-image.  Removing the package for the older version should also remove the entry from the boot menu.

---

### Post by ibutho on 2008-04-30
Sometimes its a good idea to keep an extra kernel just in case something goes wrong with one of them, you can still boot into the system. If you are pretty sure you want to remove the older, kernel do as described above.

---

### Post by uconvert on 2008-04-30
I found a need for the 14 kernel. Since my fresh install to 8.04, I have been wrestling with Codeweavers Crossover Pro 6.0.0. I have three "Windows" Bible Study apps that I need use in Ubuntu and until Hardy, have had no problem running them. With the 16 Kernel, I can't install two of them, and the third installs, but does not run. 

On a hunch, I reverted to Gutsy, installed Crossover, then the one windows program I really need. I then did a upgrade to Hardy and booted first to the 16 kernel and the program would not function. I then booted to the 14 kernel and it works.

I think there is a conflict with the 16 kernel, wine is also showing errors (reminiscent of the days of DOS).

Codeweavers has a new release of Crossover Pro, but I am hesitant to buy if future kernel changes do not support it.

Any suggestions other than my remedy would be greatly appreciated.

---

### Post by forrestcupp on 2008-04-30
> **uconvert said:**
> I found a need for the 14 kernel. Since my fresh install to 8.04, I have been wrestling with Codeweavers Crossover Pro 6.0.0. I have three "Windows" Bible Study apps that I need use in Ubuntu and until Hardy, have had no problem running them. With the 16 Kernel, I can't install two of them, and the third installs, but does not run. 

On a hunch, I reverted to Gutsy, installed Crossover, then the one windows program I really need. I then did a upgrade to Hardy and booted first to the 16 kernel and the program would not function. I then booted to the 14 kernel and it works.

I think there is a conflict with the 16 kernel, wine is also showing errors (reminiscent of the days of DOS).

Codeweavers has a new release of Crossover Pro, but I am hesitant to buy if future kernel changes do not support it.

Any suggestions other than my remedy would be greatly appreciated.

GnomeSword is a great free native Linux Bible study software.  It's in the repos and it uses modules from The Sword Project.  Also, e-Sword is a great free Windows based Bible study software that has even more modules available (most free, but some commercial), and it works perfectly in Hardy with Wine.  If you want to try e-Sword, [here is a site](http://frankscorner.org/index.php?p=e-sword) with the tweaks to get it working in Wine.

---

### Post by uconvert on 2008-04-30
I am learning to use Gnomesword as well as e-Sword. 
I am a student of the Concordant method, and use Professional Bible Companion for the Concordant Literal Version. This program is based on the Seedmaster program and is the only program which has the entire text of this translation. E-Sword does have a Concordant module, but only for the New Testament.

---

### Post by doorknob60 on 2008-04-30
Two things to try:

1. Installing with Wine instead of Crossover
2. Reinstalling crossover in the new kernel

---

### Post by uconvert on 2008-04-30
This program doesn't work in Wine (I install it to a fat32 partition), and the new kernel is not as Crossover friendly as the previous.

---

### Post by forrestcupp on 2008-04-30
> **uconvert said:**
> I am learning to use Gnomesword as well as e-Sword. 
I am a student of the Concordant method, and use Professional Bible Companion for the Concordant Literal Version. This program is based on the Seedmaster program and is the only program which has the entire text of this translation. E-Sword does have a Concordant module, but only for the New Testament.

I understand what you're saying and the Concordant Literal Version seems like it would be useful, but you can get the same info and more with modules that *are* available for e-Sword.  I use the commercial module for the Complete Word Study Dictionary, which is a very extensive dictionary for every Hebrew & Greek word in the Bible referenced with Strong's numbers.  You can't beat studying the words yourself.

But I can understand why you would want to continue using what you already have.

---

### Post by sports fan Matt on 2008-04-30
I also have 2 kernels..Which one is the older one?

---

### Post by Monicker on 2008-05-01
> **sox fan Matt said:**
> I also have 2 kernels..Which one is the older one?

You should able to tell by the version numbers.  Newer kernels increment higher.


For example 2.6.12 would be older than 2.6.16.

---

### Post by uconvert on 2008-05-01
Of course I use both real books (I have about $1000 of reference books) as well as software (another $600 - Bibleworks 7, Biblesoft PC Study Bible, etc).

I just found a fix for the crossover problem, listed on the Codeweaver site forum [URL="http://www.codeweavers.com/support/wiki/FAQ/Ubuntu804_KnownBugs"].

It fixed my problem, so I am doing a fresh install and going to the 16 kernel.

Thanks and God bless :) :KS

---

