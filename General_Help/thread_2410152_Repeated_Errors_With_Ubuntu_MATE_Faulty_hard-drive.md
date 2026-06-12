---
title: "Repeated Errors With Ubuntu MATE: Faulty hard-drive root of problem?"
date: 2019-01-11
forum: General Help
---

### Post by retsek2 on 2019-01-11
I've had numerous problems with Ubuntu MATE which have prevented me from getting on to my OS. They have often been errors which required me to debug or reinstall certain directories or files. Is this is a problem with Ubuntu MATE or do I have a faulty hard-drive (it is quite old). If it is a problem with Ubuntu MATE, would this problems be solved by switching to a different distro, say, Kubuntu?

Thanks in advance

---

### Post by deadflowr on 2019-01-11
Look at the SMART data:
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")
Probably best to run SMART tools from a live session (the "Try" selection option from the installer media)
You can post the output if you're not sure what any of it means.

---

### Post by retsek2 on 2019-01-11
I think I've finished, but I don't understand any of what it has produced...

---

### Post by retsek2 on 2019-01-11
It has a list of about 6 errors that all occured on disk start up at hour 5698, but none before or after that? Would it be alright for me to dump the entire output either in this thread or in a pm to you and you can quickly inform me on whether there is anything to cause concern?

---

### Post by yetimon_64 on 2019-01-11
> **retsek2 said:**
> ...Would it be alright for me to dump the entire output either in this thread...
Post your output in the thread between [noparse]```

```[/noparse] tags.

Use the "Adv Reply" editor here and press the "#" button on the editor toolbar to get a set of code tags. Copy your output and insert your cursor between the code tags then paste the output there.

 Dealing with tech problems in PM is generally discouraged on the forum, doing so takes your problem into a private discussion which only 2 people can see. The more sets of eyes that are on your problem increases the chance of you getting a better outcome with your issues.

Generally if a hard drive is failing you will often see "Reallocated sector count" errors, there may also be other drive failure errors of concern so I'd suggest you post your output here in between the code tags as mentioned above.

**Edit:** if your output is too large to post to the editor you can also copy your output to an online "pastebin" link let us know if that is the case and someone will provide the url for that service. The online pastebin lets you store the information online and paste a link to it here.

Regards, yeti.

---

### Post by deadflowr on 2019-01-11
Post it here, no PMing please.
You can cut it down to the section marked as
```
SMART Attributes Data Structure revision number: ##
Vendor Specific SMART Attributes with Thresholds:
```
The important numbers are the raw values.

---

