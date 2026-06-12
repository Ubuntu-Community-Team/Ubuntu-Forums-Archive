---
title: "How can I get the odd, individual app via Synaptic?"
date: 2005-06-13
forum: General Help
---

### Post by C.B. on 2005-06-13
Newbie Q: How do I install programs that I find on the net. I would prefer to use  Synaptic over CL interface. Please don't direct me to the "Unofficial Ubuntu 5.04 Starter Guide." It's all CL and I find it confusing. 

I have enabled the Comminty/Universe repository, but I find the selection of available programs is still limited. For example, I might like to download a recipe management program from SourceForge, but there appears to be no simple or straightforward way to do this. Can I somehow manually add SourceForge or, say, FreshMeat as repositories? Or can I somehow get specific apps, individually, thru Synaptic.

To those who may take the time to reply, thank you for your patient and long-suffering answers to newbie questions.

---

### Post by sethmahoney on 2005-06-13
If you want to install using Synaptic, you have to find a repository that has the program, but it is generally advised that you not add repositories that aren't Ubuntu-specific, because they can screw up your installation.  So...

The easiest way to install a program that isn't in the repositories is to download it as a .deb file and use

```
 dpkg -i filename.deb 
```

and replace filename.deb with the package name.  If you install a .deb file this way, it will show up in Synaptic, and (I think) if the program is ever added to Ubuntu repositories, it will be upgraded to the Ubuntu version at that time.

If there isn't a .deb available, the second easiest way, which doesn't always work, is to download the .rpm for the program and use alien to convert it to a .deb and then use dpkg to install it.  I'm not too familiar with alien, but I'm sure someone on the forum is.

You can also always request that a program be added to the repositories.

Hope that helps!

---

### Post by sethmahoney on 2005-06-13
Also, regarding the recipe-management program, there was some discussion about a particular one, with instructions on how to install it, elsewhere on this forum.  If you do a search for recipe management, you can find it pretty easily.  Also, it seems like, if you're inclined to try, you could use Tomboy to set up a recipe database fairly easily, even though that's not quite what it was intended for.

---

