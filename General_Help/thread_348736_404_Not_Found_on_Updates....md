---
title: "404 Not Found on Updates..."
date: 2007-01-29
forum: General Help
---

### Post by shields on 2007-01-29
I am a real novice here, so if you can help, imagine you're speaking to a third-grader.:D 

When I do a "sudo aptitude update" I get many "Hits" several "Igns" and a couple "Errs".  The Errors look like this:
> Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/free Packages
  404 Not Found
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) edgy/non-free Packages
  404 Not Found


Similar errors come up when I try to do a software update.  They look like this:
> [http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/free/binary-i386/Packages.gz:) 404 Not Found
[http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz:](http://packages.freecontrib.org/ubuntu/plf/dists/edgy/non-free/binary-i386/Packages.gz:) 404 Not Found

Any ideas what the problem is:confused: 

Thanks!:) 
Shields

---

### Post by taurus on 2007-01-29
I think that site, [http://packages.freecontrib.org](http://packages.freecontrib.org), is dead so you need to comment it out in /etc/apt/sources.list by placing a # in front of it.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and run these two commands again.

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by shields on 2007-01-29
Thanks for the quick reply.  Even my newbie mind could grasp it.

A follow-up question:
#ing that line out and running the update and upgrade made the error go away.  But if those sites are dead, where am I getting updates from?  How do I know my sources.list has the necessary sites in it?

---

### Post by taurus on 2007-01-29
That site is not an official site; it's a 3rd party repo so you are not missing anything at all.  

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by kpkeerthi on 2007-01-29
See [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by ruffneck on 2007-01-29
Thanks for the link to medibuntu kpkeerthi. It's really what I needed as I've had the PLF repos for the longest.

---

