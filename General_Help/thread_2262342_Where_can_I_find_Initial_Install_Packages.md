---
title: "Where can I find Initial Install Packages?"
date: 2015-01-24
forum: General Help
---

### Post by Maleificus on 2015-01-24
Hello,

A few weeks ago I reinstalled Kubuntu on my system so that I could take advantage of having an encrypted home directory on a second partition. I initially used a network install from a USB flash disk, and though I thoroughly enjoyed the new options I was given, it didn't install properly and I had to use a full install ISO. 

Which brings me to my question. On that network install ISO there were some package suite options like publishing, video editing, sound editing, stuff like that; stuff that I didn't find in the full install ISO. So, my question is; where do I find all those packages?! I was very interested in checking out that software, and it seemed like it installed a lot of cool stuff when I checked out the kickoff menu.

---

### Post by oldfred on 2015-01-24
The server install uses this, is this what you saw?
 Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel


All the packages are available in Software Sources, synaptic or from command line.
With command line you do have to know package name which may not be identical to what the software is.

---

### Post by SeijiSensei on 2015-01-25
From the main menu, choose Applications > System > Software Center.  You'll see a variety of categories of software you can browse.  Some of the applications may have been installed already, but most probably reside in the online repositories.  You can install them with a few mouse clicks.

---

### Post by Maleificus on 2015-01-25
> **oldfred said:**
> The server install uses this, is this what you saw?
Used by Server install to choose what you want
sudo apt-get install tasksel
sudo tasksel


All the packages are available in Software Sources, synaptic or from command line.
With command line you do have to know package name which may not be identical to what the software is.

This is exactly what I was looking for, thanks!

---

### Post by flaymond on 2015-01-25
You can find the package to install before installing it in the terminal. Just type this to see packages available in the repos -

```
 apt-get cache search <example>
```

This will give you a wide of choice and also fast, but lack of desription and reviews.

---

