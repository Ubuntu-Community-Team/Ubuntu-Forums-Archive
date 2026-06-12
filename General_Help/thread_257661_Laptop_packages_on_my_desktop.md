---
title: "Laptop packages on my desktop"
date: 2006-09-14
forum: General Help
---

### Post by misteral on 2006-09-14
I've been on Ubuntu for several months now. Going pretty good, even figured out installing a new hard drive.

Tonight I'm finally getting a chance to look around the system. Upgraded my kernel to 686, and thought i'd take a stroll through installed packages.

Right away, I see things like laptop; laptop-mode, toshset. Toshset is for Toshiba laptops. My first thought was "gone". I don't own a toshiba laptop, and I'm certainly not on a laptop on my PC. But when I selected it for removal it said it was going to remove some power management stuff, acpi-support, and gnome-session.

And it did this for just about any laptop related thing I saw. ](*,) 

My question is this... why? I know I can leave these things but it's annoying having software I don't want. I get upgrade notices to upgrade software I don't use, I'd like to take some control here.

Thoughts anyone?

Thanks!

---

### Post by aysiu on 2006-09-14
Why don't you just remove it and then reinstall the packages you want back?

---

### Post by misteral on 2006-09-14
I never thought of that, thanks! Seems to work!

---

### Post by Average Joe on 2006-09-15
> **aysiu said:**
> Why don't you just remove it and then reinstall the packages you want back?

Sure, but why are the packages removed in the first place?

I have been doing quite some reading on this forum recently, and I have learned a lot. But usually only the HOW's are explained, never the WHY's.

If you really want to learn more about your OS, blindly typing in commands that others suggest is not the right way. Unfortunately, in-depth answers are rarely given.

---

### Post by aysiu on 2006-09-15
Maybe the *why*s aren't given because people don't know why.

I don't have important packages removed when I try to remove Bluetooth--only the *ubuntu-desktop*, which isn't a real package, just a pointer to other packages.

But if someone else is experiencing that problem, this is a workaround I think is worth trying.

---

### Post by David Corrales on 2006-09-15
> **Average Joe said:**
> Sure, but why are the packages removed in the first place?

I have been doing quite some reading on this forum recently, and I have learned a lot. But usually only the HOW's are explained, never the WHY's.

If you really want to learn more about your OS, blindly typing in commands that others suggest is not the right way. Unfortunately, in-depth answers are rarely given.

I'll try to explain a bit about dependencies and meta-packages (really geeky term haha).

First of all, since Linux handles its programs and installed files in a different way than Windows, it's easy to feel confused when taking the leap. We've all been there :)
Linux is like a lego and Windows is more like an already built toy. Both have their pros and cons. For example, in Linux you reduce the redundancy of data (less copies of the same information floating around everywhere) while in Windows you might have several copies of the same library installed in different parts of the file system.

What makes the difference? It's a matter of design. You probably already heard the old tale that Unix based systems are about small programs that do one thing -but they do it right- and then get linked together in a chain (something like a production line). 
Well, the same happens with libraries. Linux likes (when possible) to have a unique library so that all programs link to it.
And guess what? the same happens with programs! They depend on each other, just like programs depend on libraries.

So when managing a Linux system you run into dependency problems a lot more often than you do in Windows. That's why package managing methods like apt or rpm were created. They handle all the ugly stuff so you can only select the program you want and they will (in the background) calculate the other packages you need (and the ones these need and so on...) and also install them.
When you open an application like Synaptic, you'll see a message that says something like "Calculating dependency tree". In that moment, the program is doing something like:
```

      A
     /  \
    B    C
   /     /  \
  D    G    H
 /  \
E    F

```
There's two ways to interpret this tree:
**Top to bottom**: A depends on B and C, B depends on D, D depends on E and F, C depends on G and H.
**Bottom to top**: E depends on D, D on B, B on A. The other packages F, G and H work the same way.
This difference is important because it determines the way the dependencies will be calculated and allows for the construction of meta-packages.

Let's tackle the couple of issues this post was all about, why does the remove and reinstall solution works and meta-packages.

**Remove and reinstall solution**: when you tried to remove the toshiba package, since it depends on power management and acpi packages, Synaptic in the end found that the best way to solve the dependencies was to remove them. Sometimes it does this because it sees that no one else needs them directly. It's almost guaranteed that said power management and acpi packages **DO NOT** depend on the toshiba ones. That's why you can reinstall them later on and leave the laptop package out of your system.

**Meta-packages**: let's use our artistic dependency tree to explain them. They're called **meta** because they're a package of packages, just that (as a side note, you might heard the term meta-information. It refers to information about the information).
Let's say that package A is *ubuntu-desktop*. You can easily see that installing *ubuntu-desktop* (if we're reading from top to bottom) will install B,C,D,E,F,G,H. This is really useful because we can then use these **meta-packages** to install a lot of programs at the same time without having to select them individually.
The key here is that B,C,D,E,F,G,H **DO NOT** depend on A. A is only used to group them for easier installing.
That's the reason why, if you uninstall F for example, A gets removed. One or more of A's dependencies are not met. Once you know the reason, it's not a problem because you understand that you're merely removing a **meta-package** but if that package happens to be called *ubuntu-desktop* I find it normal to freak out haha.
Finally it's good to remember that **meta-packages DO NOT** provide any services or programs *themselves*. They just install a lot of other packages. You can check if a package is a **meta-package** by reading it's description.

---

### Post by misteral on 2006-09-15
David
Thanks for that awsome explanation. Your node tree diagram's what did it for me (we use it as a question at work to find an algorithm to find first common parents)

I think the part you mention that it sees no one else using it so it figures why not remove it is probrably what was the most confusing, but it's all resolved now so I'm good

---

### Post by David Corrales on 2006-09-15
> **misteral said:**
> David
Thanks for that awsome explanation. Your node tree diagram's what did it for me (we use it as a question at work to find an algorithm to find first common parents)

I think the part you mention that it sees no one else using it so it figures why not remove it is probrably what was the most confusing, but it's all resolved now so I'm good

Woot! Glad to help :biggrin:

---

