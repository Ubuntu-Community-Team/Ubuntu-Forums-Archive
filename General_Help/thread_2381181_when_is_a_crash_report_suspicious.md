---
title: "when is a crash report suspicious?"
date: 2017-12-27
forum: General Help
---

### Post by tshis on 2017-12-27
What are some keywords a neophyte might be on the look out for to warn of possible attacks on her neo-soul?   err...I mean laptop.

---

### Post by oldos2er on 2017-12-28
Post the crash logs on pastebin, post a link here, and let people look at it. Not sure what you mean by keywords in this context, and how they would relate to an "attack."

---

### Post by Habitual on 2017-12-29
"INFO", "ERROR", "WARNING" and "FATAL"

I generally discard "INFO entries when looking at/for trouble. :)

I think these may assist.
[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)
[https://wiki.ubuntu.com/DebuggingProgramCrash](https://wiki.ubuntu.com/DebuggingProgramCrash)
[https://wiki.ubuntu.com/Kernel/CrashdumpRecipe](https://wiki.ubuntu.com/Kernel/CrashdumpRecipe)

---

### Post by dragonfly41 on 2017-12-29
I have been exploring various tools to analyse log files.
Two which are quite useful are

petit and glogg

Install by

```
sudo apt-get install petit glogg
```
Read the petit docs here ...

[http://crunchtools.com/software/petit/](http://crunchtools.com/software/petit/)

But note reference to /var/log/messages should be
/var/log/syslog   (/var/log/messages seems not to be used in recent distros)

For example read the Word Count feature ...
[COLOR=#002d7a]
sudo petit [/COLOR][COLOR=#006fe0]--[/COLOR][COLOR=#002d7a]wordcount[/COLOR][COLOR=#006fe0] /[/COLOR][COLOR=#800080]var[/COLOR][COLOR=#006fe0]/[/COLOR][COLOR=#002d7a]log[/COLOR][COLOR=#006fe0]/syslog[/COLOR]

Then select keywords to define in glogg filters such as those given by @Habitual.

But from the word count there might be other keywords you wish to investigate.

---

