---
title: "highlight and repeating key not working"
date: 2007-04-24
forum: General Help
---

### Post by kalindriv on 2007-04-24
Hi guys,
I installed Feasty on my acer aspire 5672wlmi (with ATI Mobility Radeon X1400) in dual boot with windows.
I have some big problems because I need to work with editors:

1) I can't highlight text with my mouse

2) Sometimes and randomly, when I move along the text with the arrows, some 'p' character appears where the arrow has just shifted.

3) Moreover, when I press for long time any key, the repetition doesn't work. I mean, for example, holding for long the key 'a', it doesn't appear 'aaaaaaaaaaaaaaaa', but only 'a'. This is a big problem especially when using arrows!!!

4) The last problem, but I don't know if it is connected with the others, at the boot loading of the system, when the modules are loading, or the checks are preforming, instead of the "roating slash" (I mean, the sequence of characters \ | / - \ | / - \ |), I receive a sequence of ^@ symbols .... why?????????

I use the following video driver:
```

xxx@yyy:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)

```

I'm not sure it is a video driver problem, but I already tried to set in a different way the keyboard preferences, but, nothing new happens!!

Thank you very much for the help, I'm going mad for these problems, 'cause I can't work easily.

---

### Post by qhartman on 2007-05-24
I hope you've gotten these resolved, but in case you haven't...

I doubt very much that your problem is video driver related. I've seen things like this when keyboard layouts and locales and codepages and whatnot are set incorrectly. Double check that everything is set to "en-us". Searching for "changing locale" should provide some more concrete guidance.

---

