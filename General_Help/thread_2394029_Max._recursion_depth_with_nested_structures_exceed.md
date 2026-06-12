---
title: "Max. recursion depth with nested structures exceeded at /usr/local/lib/perl/5.18.2/.."
date: 2018-06-11
forum: General Help
---

### Post by talishka on 2018-06-11
Suddenly im having issues with my apt upgrade

Excuting: apt-update & apt-upgrade -y I'm getting this error:

[B]Max. recursion depth with nested structures exceeded at /usr/local/lib/perl/5.18.2/Storable.pm line 278, at /usr/bin/apt-show-versions line 271.
E: Problem executing scripts APT :: Update :: Post-Invoke-Success 'test -x /usr/bin/apt-show-versions || exit 0 ; apt-show-versions -i'
E: Sub-process returned an error code[/B]

I reinstalled apt-show-versions
I upgraded CPAN modules

Ideas? Thanks!

---

### Post by howefield on 2018-06-11
Thread moved to the "*General Help*" forum for a better chance of help.

---

### Post by talishka on 2018-06-18
Nobody? :(

---

### Post by Yellow Pasque on 2018-06-18
Is there a reason you're using a local version of perl instead of the default version from Ubuntu repos? (Notice the error message points to /usr/local/lib)

---

### Post by revek on 2018-07-09
[COLOR=#111111][FONT=Ubuntu]Install cpanminus[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]apt-get install cpanminus[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]cpanm --uninstall Storage[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Fixed it for me.[/FONT][/COLOR]

---

