---
title: "Broken dependencies error message when trying to download emerald-themes"
date: 2013-09-04
forum: General Help
---

### Post by marinecomm on 2013-09-04
I was downloading themes last night on Synaptic and came across a package called emerald-themes. Every time I try to download it, Synaptic flags it as having broken dependencies. When I check the 'Dependencies' tab it says it needs emerald (>=0.9.5). I did a search in Synaptic for emerald and I have version 0.9.5. So why am I getting this message?

---

### Post by ibjsb4 on 2013-09-04
Your running 12.04?  I do not see emerald-themes in synaptic.  Where are you finding it?

---

### Post by marinecomm on 2013-09-04
Ok, I see where it's coming from. It's in a PPA I got off launchpad. Guess I need to go over there to find out the answer to my question huh?

---

### Post by ibjsb4 on 2013-09-04
Don't see it there either.

[https://launchpad.net/ubuntu/+source/emerald-themes](https://launchpad.net/ubuntu/+source/emerald-themes)

---

### Post by marinecomm on 2013-09-04
[https://launchpad.net/~guido-iodice/+archive/precise-updates]("https://launchpad.net/~guido-iodice/+archive/precise-updates")

---

### Post by ibjsb4 on 2013-09-04
Are you running compiz?  This is what I am finding.

[http://www.webupd8.org/2013/05/how-to-install-emerald-in-ubuntu-1304.html](http://www.webupd8.org/2013/05/how-to-install-emerald-in-ubuntu-1304.html)

---

### Post by marinecomm on 2013-09-04
Yes, I have compiz and I already have the PPA that the article talks about installed in my repositories.

---

### Post by ibjsb4 on 2013-09-04
Try:

```
sudo dpkg --configure -a
```

and

```
sudo apt-get -f install
```

---

### Post by marinecomm on 2013-09-04
Neither or those worked

---

### Post by ian-weisser on 2013-09-04
The exact error messages would be very helpful.
Better yet, a paste of the entire package management session.
Those messages contain a lot of useful information.

Did you disable all PPAs before running those commands?

---

### Post by marinecomm on 2013-09-04
Here's the error message:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 emerald-themes : Depends: emerald (>= 0.9.5) but 0.9.5-0~webupd8~precise2 is to be installed
E: Unable to correct problems, you have held broken packages.

I didn't know I was supposed to disable all my PPAs before using those commands. I'll do that and see what happens.

---

### Post by ian-weisser on 2013-09-04
Here is one way I would try to solve it:

1) Disable all PPAs *except* the one containing emerald and emerald-themes

2) Uninstall the packages with [B]sudo apt-get autoremove emerald

[/B]If they won't uninstall, then remove them manually with **sudo dpkg --remove emerald** and **sudo dpkg --remove emerald-themes**

3) Clean out the offending packages from the cache with **sudo apt-get clean emerald emerald-themes**

4) Reload and reinstall the packages with **sudo apt-get install emerald emerald-themes** 

If they still won't install due to a dependency issue, then contact the PPA maintainer directly. They need to fix at least one package.

---

