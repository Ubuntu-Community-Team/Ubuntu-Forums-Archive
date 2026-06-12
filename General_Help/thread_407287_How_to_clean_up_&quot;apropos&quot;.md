---
title: "How to clean up &quot;apropos&quot;"
date: 2007-04-12
forum: General Help
---

### Post by Phrawm48 on 2007-04-12
Can anyone please tell me how to clean "junk" out of information returned by the *apropos* command?  Specifically "hits" for unnecessary *.fr* and *.fi* man pages that I've moved out of the man directory in anticipation of permanently deleting those files?

I used the *apropos* command to get some information about *aptitude*.  When I did, I received results for *aptitude.fr* and *aptitude.fi* in addition to to information about my English language computer's *aptitude* program.

I first checked via Synaptic and Aptitude for *.fr* and *.fi* installation packages but couldn't find any.  (Note I may not have done the search right -- I'm still learning about these things...)

I next used *locate* to find all (known) instances of aptitude*.fi* or *.fr*.  The only results were ".[*fr* | *fi*]*.8.gz*" man pages.  Because I don't intentionally have French or Finnish programs on my system, I moved the *.fr* and *.fi* *.gz* files into a temp directory in anticipation of permanently deleting them.

Now I want to clean up the *apropos* cache(?) so that it will quit listing those now-unavailable files.  Can anyone please tell me how to do that?

Cheers & thanks,
Ric

---

### Post by Phrawm48 on 2007-04-13
Okay, I finally found out how to clean up the *index.db* database(s) used by the *man* and *apropos* commands.

First, if you have superfluous man pages (I had French and Finnish ones -- Lord knows why), use *locate* to find those files, then delete the files or move them to a pre-deletion directory if you're worried about breaking something.

Then use the following command line:

```
mandb --create

```This rebuilds the man databases, a.k.a *index.db*.  (I had three: */var/cache/man/index.db*, *.../man/local/index.db*, and *.../man/oldlocal/index.db*)

Voila!  My original problem -- extraneous *.fr* and *.fi* entries returned by apropos -- were removed.

Cheers & hope this helps,
Ric

---

