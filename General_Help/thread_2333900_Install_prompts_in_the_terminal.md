---
title: "Install prompts in the terminal"
date: 2016-08-14
forum: General Help
---

### Post by mjruk on 2016-08-14
Hi All,

When I install some software via the terminal it prompts me to continue (yes or no) and others just install straight away without any prompt. Can someone explain why this is? I'm sure the answer is really straightforward :)

For example, when I install screenfetch I get prompted, when I install htop i don't:

[ATTACH=CONFIG]270690[/ATTACH]

---

### Post by howefield on 2016-08-14
You will get the prompt if you would install packages you didn't specifically specify or if packages will be removed as a result of the installation.

PS. The capital letter is the default, so if you see Y/n, then the Y is "active" and all you need do is press the enter key, ie, no need to type the Y key and then press the enter key. Always watch for packages which might be removed as a result of installing a package.

---

### Post by mjruk on 2016-08-14
Thanks howefield, much appreciated!

---

### Post by howefield on 2016-08-14
> **mjruk said:**
> Thanks howefield, much appreciated!

You are welcome, in your screenshot which is a little hard to read, you will see 4 packages which are required to be installed as part of installing the one(s) you specified, so the system is making you aware of that, and giving you the opportunity to back out.

There are ways around this if really wanted not to see the prompts, for instance using the -y option in most cases would install without the prompt but I'd not recommend using them until one is sure of the consequence.

---

