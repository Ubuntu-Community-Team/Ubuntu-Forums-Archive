---
title: "wpasupplicant won't install"
date: 2007-01-15
forum: General Help
---

### Post by meanmrmustard on 2007-01-15
I've recently done a clean instlal of Edgy from DVD and added repositories for Beryl from this howto:
 [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

along with enabling repositories for multiverse.

Now apt-get upgrade tells me:

Reading state information... Done
E: The package wpasupplicant needs to be reinstalled, but I can't find an archive for it.

After enabling trevino's repos, updating and upgrading, I get:
 
Unpacking replacement wpasupplicant ...
dpkg: warning - old post-removal script returned error exit status 10
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 10
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 10
Preparing to replace libgtop2-common 2.14.4-0ubuntu1 (using .../libgtop2-common_2.14.4-0ubuntu1.1_all.deb) ...
Unpacking replacement libgtop2-common ...
Preparing to replace libgtop2-7 2.14.4-0ubuntu1 (using .../libgtop2-7_2.14.4-0ubuntu1.1_i386.deb) ...
Unpacking replacement libgtop2-7 ...
Errors were encountered while processing:
 /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


If I try using synaptic, I get:

E: /var/cache/apt/archives/wpasupplicant_0.5.7+3v1ubuntu3_i386.deb: subprocess new post-removal script returned error exit status 10

Can someone tell me where the problem is here?

---

### Post by sdide on 2007-01-15
have you tried dpkg with the --force option, to make sure it purges
the old wpa_supplicant completely?

---

### Post by meanmrmustard on 2007-01-15
No I haven't.

Would that be :
"dpkg --force -r wpasuppplicant" ?

Then just apt-get install wpasupplicant?

---

### Post by meanmrmustard on 2007-01-16
Thanks Smolko!

---

### Post by anaspeople on 2007-01-16
What would the exact commands look like? Thanks

---

### Post by meanmrmustard on 2007-01-16
The solution was posted by Smolko, here:

[http://www.ubuntuforums.org/showthread.php?p=2020462#post2020462](http://www.ubuntuforums.org/showthread.php?p=2020462#post2020462)

Sorry I didn't post that in the first place.

:)

---

### Post by anaspeople on 2007-01-17
Thanks meanmrmustard! Everythings works properly again :D

---

