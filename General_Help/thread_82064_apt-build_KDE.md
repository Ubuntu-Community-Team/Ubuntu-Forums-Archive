---
title: "apt-build KDE?"
date: 2005-10-25
forum: General Help
---

### Post by Xentex on 2005-10-25
Morning All,

  I currently run KDE 3.4.0, on Hoary, and was wondering if anyone's had any success completely removing KDE, and doing an:

$apt-build install kde

Why would I do such a suicidal thing? 
I've config apt-build for "Strong" optimisation, and "Athlon-XP" proc.

If so, got any pointers? Would it be wiser (and easier) to rebuild kdelibs4 or something similar (i.e. very high dependancy on most KDE applications)

Any input appreciated :-)

---

### Post by mlomker on 2005-10-25
I'd be surprised if that works.  They do have [build script for KDE]("http://developer.kde.org/build/").  I haven't tried it, but I did read through the docs one afternoon.

---

### Post by Xentex on 2005-10-25
I think I'll pass then, lol

When I was running Gentoo, KDE was build from source - but emerge is very different to apt-get (in terms of power for compiling).

Thanks anyway :-)

---

### Post by lerrup on 2005-11-08
You'll get better performance upgrading your version of KDE to be honest.  have you tried 3.4.2/3 or even if you're feeling lucky, 3.5 beta?

---

### Post by asimon on 2005-11-08
I don't want to discuss the usefullness or the absense of it of those strong compiler flags, but all (KDE) packages should be buildable with apt-build, otherwise it's a bug in the package which should be reportet in bugzilla.

But kde is only a metapackage, which depends on the actual packages like kdegraphics, kdebase, etc. I am not familiar (not yet) with apt-build, will 'apt-build kde' build all missing dependencies too? 'Would be nice.

---

### Post by asimon on 2005-11-08
[QUOTE=mlomker]They do have [build script for KDE]("http://developer.kde.org/build/").  I haven't tried it, but I did read through the docs one afternoon.[/QUOTE]
These build scripts build KDE from source, but they don't build debian packages or apply the various Kubuntu patches, you'll get the prestine upstream version. apt-build on the other hand creates debian packages with all Kubuntu specific patches applied.

---

### Post by mlomker on 2005-11-08
>  apt-build on the other hand creates debian packages with all Kubuntu specific patches applied.

I'm aware of that.  It is also an option that I am confident will work. The philosophy of these boards is that we consider it better to offer someone a pointer to a workable option rather than leave questions entirely unanswered.

If you could have answered the apt-build question then that would have been welcome.  That's how I learn on here as well.

---

### Post by asimon on 2005-11-08
I just tested it, 'apt-build install kde' just builds and installs the kde meta package. Thus you have to build each kde package seperately, i.e. apt-build install kdelibs, apt-build install kdebase, etc.

---

### Post by asimon on 2005-11-08
> **mlomker]I'm aware of that.[/quote] But you didn't wrote this  said:**
> It is also an option that I am confident will work. The philosophy of these boards is that we consider it better to offer someone a pointer to a workable option rather than leave questions entirely unanswered. Don't be angry when someone adds more information to one of your answers. It's considered to be of help, you know.  :-)

---

### Post by mlomker on 2005-11-08
[QUOTE=asimon]Circumventing the distro's package managment is something you should point out explicidly. 
[/quote]

The link that I provided was to a webpage that would have made that evident.  I think it is reasonable to assume that the OP was fairly advanced since they were asking about rebuilding an existing package.

>  Don't be angry when someone adds more information to one of your answers. It's considered to be of help, you know.  :-)

You're going to make me quote myself?

> 
That's how I learn on here as well.


---

