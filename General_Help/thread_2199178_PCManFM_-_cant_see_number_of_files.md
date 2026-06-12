---
title: "PCManFM - cant see number of files"
date: 2014-01-12
forum: General Help
---

### Post by matospalka on 2014-01-12
Hi everybody,

at first, sorry for my English.

I installled Lubuntu, its pretty fine, but when I use PCManFM to explore files in my computer, sometimes i need to know, how much files is in some folder. So like in Windows, I right-click on the folder name, I can see some informations, but there is not shown number of files in the folder... Can I change somewhere settings to see it, or I need to go inside the folder and select everything to see how much files is there (this is not comfortable...)

Thanks a lot!

---

### Post by Dennis N on 2014-01-12
When you open a folder, the status bar at the bottom of the file manager window indicates how many items are there.

---

### Post by matospalka on 2014-01-12
> **Dennis N said:**
> When you open a folder, the status bar at the bottom of the file manager window indicates how many items are there.

Yes, but without subfolders... :(

---

### Post by Dave_L on 2014-01-12
You could install another file manager, such as Thunar or Nautilus. They both have the feature you want.

---

### Post by matospalka on 2014-01-12
> **Dave_L said:**
> You could install another file manager, such as Thunar or Nautilus. They both have the feature you want.

I know I can do that, but I was thinking, that such a simple feature has to be in PCManFM, so it looks that its missing... :(

So if i will install other file manager, and uninstall PCManFM, there will be no problem in Lubuntu?

And which alternative is the best ?

Thanks a lot for your help...

---

### Post by Dave_L on 2014-01-12
Maybe there's a way of configuring or extending PCManFM to obtain that feature, but I lack that knowledge.

You don't have to remove PCManFM. You can have multiple file managers. (This is not Windows :))

I would try Thunar first, since it's "lighter" than Nautilus.

Using synaptic or another package manager, install the package "thunar". If you see that it requires a lot of additonal packages to be installed, or if any packages will be removed, then it might not be a good idea.

I'm using Ubuntu, not Lubuntu, so I don't know with certainty whether there would be any problems. You may want to wait for someone else to post here and confirm that it won't have any bad side-effects.

---

### Post by mörgæs on 2014-01-12
No problem in adding Thunar.
Which version of Lubuntu do you use?

---

### Post by Dennis N on 2014-01-12
Thunar (version 1.6.3)  is not going to exclude subdirectories of the current working directory from its "items" count, at least in the default configuration.

Here is the structure of an actual directory, and what is inside it, from my Xubuntu:

```
Directory A
--Directory B
----file 2
----file 3
--file 1
```

When I open Directory A, Thunar's status bar reports "2 items" - counting Directory B and file 1. 

When I cd to the parent of A, right-click on A and choose "Properties", Thunar reports "5 items" (even though only 4 are "inside" A), now also including the two files in Directory B in the count, and apparently Directory A itself.

Edit: Looked for any settings to exclude directories from "items", but found none. Also, Nautilus (version 3.4.2) behaves like Thunar, execept when using the same directory structure as above, right-click on A from the parent of A and choose "Properties" Nautilus reports "4 items" instead of 5.

---

### Post by matospalka on 2014-01-15
Thank you for your help, so if I understand - I cant see number of files in my folder like in Ubuntu or Windows by right-click. The only solution is to install other file manager...

---

