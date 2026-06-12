---
title: "Feisty Fawn with Gutsy repositories"
date: 2007-12-09
forum: General Help
---

### Post by Virgofenix on 2007-12-09
Can I use Gutsy repositories for my Feisty Fawn install?

---

### Post by skymera on 2007-12-09
i think that will do an effective upgrade..
unsafe in my eyes.

if you wanna use gutsy repos..upgrade?

---

### Post by Virgofenix on 2007-12-10
^I'm not comfortable with Gutsy, for various reasons. I just want to update my programs. What would make the packages in Gutsy break my Feisty install?

---

### Post by PmDematagoda on 2007-12-10
If you want to upgrade please follow this [guide.]("http://www.ubuntu.com/getubuntu/upgrading")

---

### Post by Virgofenix on 2007-12-10
I do not want to upgrade. I just want to know if I can use the packages in the Gutsy repo.

---

### Post by skymera on 2007-12-10
just use the feisty repo, since your using the feisty version.

theres no other way.

---

### Post by Soarer on 2007-12-10
If you are using the Gutsy repos, then you are using Gutsy. The packages in the repos ARE your system.

I guess you could use LILO to retain the current kernel, and then using Gutsy repos wlil update your kernel but LILO won't boot the new kernel unless you tell it to. But why bother?

If you have a problem with Gutsy, that problem is with the Gutsy repos, as that is where all the Gutsy code is.

Sorry if I misunderstood your question :)

---

### Post by Virgofenix on 2007-12-10
> 

If you have a problem with Gutsy, that problem is with the Gutsy repos, as that is where all the Gutsy code is.

So all the Ubuntu code is on the packages ie Ubuntu is a Debian install with Ubuntu modified packages? 

I used to have Gutsy installed, but I was uncomfortable with it. I reinstalled Feisty hoping to just add the Gutsy repos for updated programs. Ie, I want some parts of Gutsy, but not all of it, and certainly not a lot of what comes with the CD installer. Ex. I'd like to use the Exaile, EoG, and WINE, on the Gutsy repos but still keep this install as Feisty. Will I encounter problems other than dependencies?

I'm fairly new; so please bear.

---

### Post by PmDematagoda on 2007-12-10
You would experience more than just simple problems if you use the Gutsy repos, trust me, I have done this before and the OS did not become pretty.

In other words, stick to the Feisty repos as much as possible, if you don't like them, then get the compatible debs for the applications from their websites or compile them from the source.

---

### Post by Soarer on 2007-12-10
I'm a relative noob too (1 year) so no worries :)

The problem, as I understand it, is dependency. If you install a Gutsy package, likely it depends on some Gutsy libraries. Perhaps, those libraries, for some packages, depend on the Gutsy kernel. So you have at best a mix of Feisty & Gutsy libraries, and maybe a conflict with the kernel. AS I say I'm a noob so this could be wrong.

There may be some packages in the Feisty backports which are the same version as the Gutsy ones, but using Feisty libs. It depends on what you want to install. But if you enable the Gutsy repos, at some point you will have more Gutsy than Feisty, and maybe some problems in the transitional phase.

Would you like to share what it was about Gutsy that made you uncomfortable? I have been running it since before the beta, and I think it's better in every way than Feisty.

Of course, YMMV :)

---

### Post by Virgofenix on 2007-12-10
> **PmDematagoda said:**
> You would experience more than just simple problems if you use the Gutsy repos, trust me, I have done this before and the OS did not become pretty.

In other words, stick to the Feisty repos as much as possible, if you don't like them, then get the compatible debs for the applications from their websites or compile them from the source.

What specific problems did you encounter; and were you able to solve them?

---

### Post by PmDematagoda on 2007-12-10
I broke the Perl packages and many more besides it, another thing is that the Package Managers start to malfunction and it takes a lot of time to do anything, but in most cases the Package Manager just stops responding altogether.

In other words, using incompatible repositories is a very inefficient and a very risky thing to do.

---

### Post by rsambuca on 2007-12-10
What you want to do won't work.  How many times do you need to hear it?

You may have limited success with specific packages just going to [Ubuntu Packages]("http://packages.ubuntu.com/") and downloading the specific packages and dependencies separately.  If any of the programs you want require the new gnome dependencies, though, then you are hooped.

---

### Post by PmDematagoda on 2007-12-10
> **Virgofenix said:**
>  and were you able to solve them?

I did not answer this, sorry. 

Yes, I was able to solve it, but this meant that I had to replace the broken packages with the proper ones matching the Ubuntu version, and this just reverses the entire process by taking you back to square 1 where Ubuntu 7.04 contains only packages for Ubuntu 7.04(And beware, the square 1 may be in a little bit of a worse state than the time you left it;)).

This means that what you are doing is also a waste of time.

---

### Post by Virgofenix on 2007-12-10
> **rsambuca said:**
> What you want to do won't work.  How many times do you need to hear it?


Once - but I'd be dumb if I didn't ask why; and they don't seem to mind.

I don't think making the Gutsy packages compatible with Feisty is worth the effort so I'll just compile from source. Thanks to Dem and Soarer.

---

### Post by rsambuca on 2007-12-10
> **Virgofenix said:**
> Once - but I'd be dumb if I didn't ask why; and they don't seem to mind.

I don't think making the Gutsy packages compatible with Feisty is worth the effort so I'll just compile from source. Thanks to Dem and Soarer.

Compiling from source won't help in most cases, because you will still need the dependencies.

---

