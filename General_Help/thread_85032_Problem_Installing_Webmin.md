---
title: "Problem Installing Webmin"
date: 2005-11-01
forum: General Help
---

### Post by igb on 2005-11-01
I have just set up a new box with Breezy. When I apt-get install webmin I get the following errors:

```
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  webmin: Depends: perl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not going to be installed
          Depends: libnet-ssleay-perl but it is not going to be installed
E: Broken packages
```

I have installed webmin several times before on Breezy with no problems, so what's gone wrong this time?

Ian.

---

### Post by igb on 2005-11-04
Just in case anyone else has this problem, it seems that there was something with my repositories in sources.list. When I copied sources.list from a computer where I had installed webmin, the problem went away.

---

### Post by senzacionale on 2005-11-04
i don't have root users so what is now user and passwd for webmin?

---

### Post by dutler on 2005-11-05
The webmin users and passwds are suppose to be differnt than the systems. My installation of webmin said it created an account. root and copied the pass form some file.

but i can't log in... presumilly i do not have the correct user/pass...

---

