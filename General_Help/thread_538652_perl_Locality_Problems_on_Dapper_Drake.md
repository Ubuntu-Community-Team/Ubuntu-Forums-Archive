---
title: "perl Locality Problems on Dapper Drake"
date: 2007-08-30
forum: General Help
---

### Post by ivan09193 on 2007-08-30
Hey all,

I'm using Dapper Drake and am having some trouble with this weird program called perl.  Apparently it starts up every time I want to install something.

Anyhow, here's the error message:

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

I haven't actually seen any adverse effects because of this, but it doesn't look good.  Anyone know how to fix this?  Any help would be greatly appreciated.

---

### Post by ivan09193 on 2007-08-30
I have tried setting LC_ALL and exporting it as I saw on a website, but:

A.  It doesn't work (same error message as before in perl, just without an unset LC_ALL).

B.  It's a temporary fix anyway.

I think this may have something to do with my stupidity in installing Debian packages for the C library.  I "rolled back" the packages to an Ubuntu version in Synaptic, and ever since then I've had these problems with perl.

Still grateful for any help offered.

---

### Post by ivan09193 on 2007-08-31
Is the solution so obvious that anyone viewing this assumes that I have already solved the problem?  I haven't.  :)

---

### Post by ivan09193 on 2007-09-01
I can give more details on the problem if someone stepped up to answer my question.

---

### Post by tr333 on 2007-09-02
I'm not sure how to fix your problem, but I don't think there is a problem with perl reverting to the "C" locale instead of using the normal one.

FYI:  [Perl](http://en.wikipedia.org/wiki/Perl) is a scripting language like bash, and "perl" is the interpreter to run Perl code.

---

### Post by xihhox on 2007-09-14
hey ivan did you finally found out, how to solve this problem? would be helpful :D

---

