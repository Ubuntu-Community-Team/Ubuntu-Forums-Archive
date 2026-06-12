---
title: "Update error"
date: 2013-01-10
forum: General Help
---

### Post by FrankJC on 2013-01-10
Hello all,

When my Update Manager shows that I have updates and I try to install them I get this error message:

Requires installation of untrusted packages.

apport-hooks-medibuntu libavcodec-extra-53 libavutil-extra-51

The updates don't install and I get the same message the next time I log in.

I look forward to your response.

Thank you
Frank :confused:

---

### Post by dino99 on 2013-01-11
you need to sign that medibuntu repo

sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

note: copy&past the whole command above into a terminal (one shot)

---

### Post by ibjsb4 on 2013-01-11
Hi Frank, welcome to the forums  :)

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

And please post using code tags.

[ATTACH]229889[/ATTACH]

Also

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Requires+installation+of+untrusted+packages.&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Requires+installation+of+untrusted+packages.&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by FrankJC on 2013-01-11
Thank you Dino99.  That did the trick.

---

### Post by FrankJC on 2013-01-11
Thanks for the help ibjsb4.  Where do I get these "Tags".  I assume they help categorize the questions or something.  I'm kinda new at  using forums.

---

### Post by ibjsb4 on 2013-01-11
> **FrankJC said:**
> Thanks for the help ibjsb4.  Where do I get these "Tags".  I assume they help categorize the questions or something.  I'm kinda new at  using forums.

The hash (#) mark in the pic.

And welcome to the forums  :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

