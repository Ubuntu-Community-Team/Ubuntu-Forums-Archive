---
title: "ANSI not properly supported in console"
date: 2015-05-09
forum: General Help
---

### Post by f-pete on 2015-05-09
Hi guys,

Running Ubuntu 15.04 with kernel 4.0 (kernel version isn't the issue as still having the problem booting into Vivid's 3.19.x kernel) Seems my consoles aren't not handling ANSI characters, mainly special symbols (which I use in my git enabled shell prompts) as well as basic lines in ANSI menus. The Ubuntu recovery mode menu is the best example, attached below. The inital Grub menus are all fine, but once I'm post-Plymouth something is getting in the way and "uglifying" my otherwise funky looking menu screens. Its only a big deal as its interfering with my usual devops tasks at work.
[INDENT][IMG]http://i.imgur.com/9ioDXSN.png[/IMG][/INDENT]

Any ideas? X terms are unaffected. System was newly built just a week ago on a fresh new drive. Hoping its something quick and easy before spending the time in the land of log files ;)

Muchly appreciated,
Pete

---

### Post by steeldriver on 2015-05-09
Your screenshot looks like an issue with the console encoding setting - maybe try

```

sudo dpkg-reconfigure console-setup

```

and trying UTF-8?

---

### Post by f-pete on 2015-05-09
> **steeldriver said:**
> Your screenshot looks like an issue with the console encoding setting - maybe try

```

sudo dpkg-reconfigure console-setup

```

and trying UTF-8?

absolute champion! that was it, set back to UTF-8 and sanity resumes...

---

