---
title: "[SOLVED] Changing status on Kopete to on-line"
date: 2007-12-05
forum: General Help
---

### Post by IanB2 on 2007-12-05
I've installed Kopete on my Gutsy Ubuntu desktop, as I'd like to use this with a webcam.

On the first install I was able to use Kopete and see all my MSN contacts ..... I was on-line with no problems.

On launching  the package subsequently, I can still see all my MSN contacts but CANNOT change my status to 'on-line'.

Any ideas?? :confused:

---

### Post by GSF1200S on 2007-12-05
> **IanB2 said:**
> I've installed Kopete on my Gutsy Ubuntu desktop, as I'd like to use this with a webcam.

On the first install I was able to use Kopete and see all my MSN contacts ..... I was on-line with no problems.

On launching  the package subsequently, I can still see all my MSN contacts but CANNOT change my status to 'on-line'.

Any ideas?? :confused:

wow.. thats weird. Ive used kopete for a long time and havent ever had a problem.

Your probably not going to want to do this, but I would delete the config folder located at:

/home/user/.kde/share/apps

and possibly even reinstall kopete just in case. How did you install it? Through Add/Remove, Synaptic, apt-get or aptitude in the terminal? If you used aptitude, just do a:

```
sudo aptitude remove kopete
```

and then reinstall using

```
sudo aptitude install kopete
```

If you did it any other way, type the following in a terminal:

```
sudo apt-get remove kopete
```

```
sudo apt-get autoremove
``` (this will delete all unused packages)

and then reinstall with
```

sudo apt-get install kopete
```

Make sure you delete the config folder first. Once installed, run kopete and set up your account again- you should be fine; this really seems like a fluke..

---

### Post by IanB2 on 2007-12-05
Thanks for the advise ..... I've followed the steps and have deleted the account, uninstalled and re-installed kopete on both of my PCs.

I'm still having exactly the same problem. On first launching, everything works fine.

After closing and relaunching,  I can see all my MSN contacts but cannot change my status to on-line. All my contacts appear 'offline' and I know at least one is currently on-line.

I get the same on both my PCs. :confused:

---

### Post by IanB2 on 2008-05-29
I've solved all the issues by switching to Skype which works nicely on both my windows XP and Ubuntu boxes.

---

