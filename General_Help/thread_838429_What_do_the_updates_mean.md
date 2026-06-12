---
title: "What do the updates mean?"
date: 2008-06-23
forum: General Help
---

### Post by solwic on 2008-06-23
I noticed a bunch of updates today, Jun 23, for compiz, and I'm wondering where I can find out what those updates were for.  I've got compiz turned off so my ATI video card works semi-properly, but would love to turn it back on if they've fixed it.  

Is there a site somewhere?  A changelog or something?  

Thanks!

---

### Post by solwic on 2008-06-23
Anybody know?

---

### Post by Greyed on 2008-06-23
Google knows.

Search on "ubuntu compiz package", 2nd hit is the package details for compiz in dapper.  Replace "dapper" with "hardy" in the URL and get this page:

[http://packages.ubuntu.com/hardy/x11/compiz](http://packages.ubuntu.com/hardy/x11/compiz)

Sidebar, "Ubuntu changelog".

[http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.7.4-0ubuntu6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.7.4-0ubuntu6/changelog)

---

### Post by Vivaldi Gloria on 2008-06-23
> **jrock612 said:**
> I noticed a bunch of updates today, Jun 23, for compiz, and I'm wondering where I can find out what those updates were for.  

Make the lower pane of the update manager visible.

---

### Post by solwic on 2008-06-23
> **Greyed said:**
> Google knows.

Search on "ubuntu compiz package", 2nd hit is the package details for compiz in dapper.  Replace "dapper" with "hardy" in the URL and get this page:

[http://packages.ubuntu.com/hardy/x11/compiz](http://packages.ubuntu.com/hardy/x11/compiz)

Sidebar, "Ubuntu changelog".

[http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.7.4-0ubuntu6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.7.4-0ubuntu6/changelog)

Ahh a straight answer!  Thank you, sir (or ma'am, as it were)!

---

### Post by Vivaldi Gloria on 2008-06-23
Actually, the link Greyed wrote above does NOT show the latest update. Here is the latest one:

```
  * debian/patches/028_compiz_manager_blacklist:
    - blacklist i815 (LP: #221920)
  * debian/patches/030_fix_screensaver:
    - dropped, the xserver is fixed now so we do not need
      to work around it (LP: #160264)
    - this means, that this version can *not* be backported
      to gutsy (or any older version of ubuntu) unless the
      xserver there is patched too
```

See

[http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.7.4-0ubuntu7/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.7.4-0ubuntu7/changelog)

I repeat, enable the lower pane of the update manager to see the descriptions of the update.

---

### Post by Greyed on 2008-06-24
Huh.  Should not the link be updated with the latest changelogs since it is what is currently in Hardy?  If not, what is the appropriate link to direct people.  If so, where do we file a bug?

I know of other ways to get to the information (heck, look in /usr/share/doc/[package]) but directing them on the web seems simplest.

---

