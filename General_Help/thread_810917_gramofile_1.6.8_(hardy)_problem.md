---
title: "gramofile 1.6.8 (hardy) problem"
date: 2008-05-28
forum: General Help
---

### Post by BasculeTheFule on 2008-05-28
Hi.

I have scoured the archives and googled till it hurts, but I am still stuck when it comes to deciphering this error message when I try to use gramofile to record:

/dev/dsp: Invalid argument

I have encountered the problem with both gutsy and hardy (32-bit) on various machines with differing sound cards.

'lsof | grep /dev/dsp' returns nothing and I am at a loss where to go next.

BTF

---

### Post by bwhite82 on 2008-05-28
Sounds like either an invalid argument in the program (a bug) or if you're running it from the CLI with an unknown option.

---

### Post by BasculeTheFule on 2008-05-28
Well, gramofile is run from the command line but takes no arguments from the the user, offering a menu from which options are chosen instead, so I am guessing it may be a bug. I cannot find anyway to configure it to use a different device either, but that's probably just me!

Thanks for the quick response.

---

### Post by BasculeTheFule on 2008-05-29
Added comments to [Bug #200181]("https://bugs.launchpad.net/ubuntu/+bug/200181"). Since this currently details two people encountering this issue I can't imagine it's going to get a lot of focus - indeed the issue has been present since 7.10 - so please update the bug with your comments if you have come across this post in search of an answer to a similar problem.

[Edit]
Also contacted the maintainers of the package.

---

### Post by BasculeTheFule on 2008-06-07
I have also asked a question here:

[https://answers.launchpad.net/ubuntu/+source/gramofile/+question/35551](https://answers.launchpad.net/ubuntu/+source/gramofile/+question/35551)

---

