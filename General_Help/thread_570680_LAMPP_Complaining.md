---
title: "LAMPP Complaining"
date: 2007-10-08
forum: General Help
---

### Post by Naatan on 2007-10-08
Arg, I've installed LAMPP a million times on ubuntu, and now on a fresh install of Ubuntu 7.10 im getting 403 errors, wtf!

I followed the steps on the XAMPP site, I added a subdirectory to **/opt/lampp/htdocs** and directed my browser to it..
I get the following error:

**You don't have permission to access /DCMS on this server.**

even with chmod set to 777, I tried chmodding to my local user or as root, no changes..

This is so annoying..
anyone know what this might be?

Edit:

Oh, and Im getting this error a few times when starting LAMPP, though that's nothing new, I've had it before and it worked despite..

**/opt/lampp/lampp: line 74: arch: command not found**

---

### Post by Naatan on 2007-10-08
Problem still stands

---

### Post by posterboy on 2007-10-08
Hmm, what happens if there's an index.html IN /opt/lampp/htdocs. I'm running the same lampp stack here, xampp, and have been for years, both on Fedoras and now on FF and I don't see that locally. Be happy to compare httpd.confs, if we need to,

---

### Post by Naatan on 2007-10-08
There's an index file yea..

the only thing I changed from the default .conf is that I added an alias:

```

Alias /divia "/home/nathan/.svn/DCMS/trunk"

<Directory "/home/nathan/.svn/DCMS/trunk">
    Options Indexes FollowSymLinks Includes ExecCGI
    AllowOverride All
    Order allow,deny
    Allow from all
</Directory>

```

same code I've always used..

so weird

---

### Post by posterboy on 2007-10-08
Well, here's another hmmm. Mess around a little at [www.raymondjones.net](www.raymondjones.net) and let me see your site, I'll do the same.

---

### Post by Naatan on 2007-10-08
It's a local server, for development only.. so I can't really show you, nor would it help as all you would see would be a 403 error ;)

I wouldnt know how that site could help me

---

### Post by posterboy on 2007-10-08
Well, me either, the xampp people maintain a pretty useful wiki, and there's a mailing list, I don't know where (or if) they hang out on irc. Maybe try some of those resources.

---

### Post by Naatan on 2007-10-08
I think the issue is related to Ubuntu though, as I said the configuration is exactly the same as before, and it worked fine..

it has to be a permission problem.. or perhaps it has to do with the latest kernel version gutsy uses..

---

### Post by Naatan on 2007-10-08
Solved it, changed the path of the homedir, even though I tried that a dozen times before it just started working all of the sudden..

Only thing I can think of is that I just updated some packages through the update manager.. guess that did it..

weird

---

### Post by posterboy on 2007-10-08
Sheesh! That may need to remain a mystery, these computer things should never, ever, shed ALL of their mystery!

---

### Post by Naatan on 2007-10-08
Problems back, apperantly it worked cause I had placed my directory inside the /opt/lampp/htdocs directory

When I put an alias on a directory in my homedir (/home/nathan) it returns an 403, even when I do a wget with root on the address..

this if very odd.

and just to make it more ****** up, when I change the Documentroot directory to "/home/nathan/public_html" even that returns a 403!

Im thinking about just installing the whole nine yards manually, xampp is supposed to make things easier, not harder

---

### Post by posterboy on 2007-10-08
Indeed, weird, for sure. All this stuff follows aliases without any issues.

---

### Post by Naatan on 2007-10-08
Installing the whole LAMP (linux+apache+mysql+php) package from scratch as we speaks

*sigh of relief*

I can just feel the control flowing back into my hands, xampp is usefull if you want it quick and dirty but dare not screw around

---

### Post by SreckoMicic on 2007-10-22
> **Naatan said:**
> 

Oh, and Im getting this error a few times when starting LAMPP, though that's nothing new, I've had it before and it worked despite..

**/opt/lampp/lampp: line 74: arch: command not found**

I think that this is/was your main problem, try to in lampp file replace word 'arch' (no quotes) on line 74 with 'uname -m' (without quotes too).

---

