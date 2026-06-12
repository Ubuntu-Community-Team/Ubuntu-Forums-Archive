---
title: "perl config problem"
date: 2007-06-16
forum: General Help
---

### Post by danmcb on 2007-06-16
Hi

I have an odd problem in the configuration of my ubuntu system that seems to stem from a perl configuration issue. It is kind of basic but I don't find any clues by google and so on.

When I try to run tools like debconf, I get :

Can't locate Debconf/Db.pm in @INC ... and the listing of @INC, which is all dirs under /usr/local/lib/perl5

By searching, I see that this module is there - it's under /usr/share/perl5

Now I do recall that a long while back, I built perl from scratch. I guess that I screwed some of the configuration up? How can I reinstall perl as ubuntu wants to see it, given that many of the syste admin tools seem to be screwed?

---

### Post by tr333 on 2007-06-17
just a guess, but possibly try "sudo apt-get install --reinstall perl".

if that doesnt work, then try removing the perl packages and reinstalling.

---

### Post by niteshifter on 2007-06-17
A quick fix to save un-installing / reinstalling:

Add the environment variable PERL5LIB to your profile, set it to /usr/share/perl5. See Perl's perlrun for more details.

Or, for when this happens and you don't want a permanet change to @INC: add this to the start of the script or module's code:

```
use lib 'path-to-directory';
```

Hope this helps...

---

