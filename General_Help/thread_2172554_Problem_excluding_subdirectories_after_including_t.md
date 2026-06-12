---
title: "Problem excluding subdirectories after including their parent in Duplicity"
date: 2013-09-05
forum: General Help
---

### Post by aeyoun on 2013-09-05
[COLOR=#333333][FONT=UbuntuRegular]I am backing up with something very similar to the below:
[/FONT][/COLOR]
```
/usr/bin/duplicity (irrelevant options) \
  --include /home/me \
  --exclude /home/me/example \
  ssh://remote/backupjar

```
[COLOR=#333333][FONT=UbuntuRegular]The problem I have is that the excluded example subdirectory is being included in my backups. Even after explicitly giving an option to exclude it. The output shows:[/FONT][/COLOR]
> A: /home/me
A: /home/me/otherstuff
A: /home/me/example
A: /hmoe/me/example/undesired-file

---

### Post by TheFu on 2013-09-05
I don't use duplic* ... but have you tried swapping the include/exclude order in the script?

---

### Post by aeyoun on 2013-09-05
Yes, I have tried rearranging the options. No effect.

---

### Post by TheFu on 2013-09-05
> **aeyoun said:**
> Yes, I have tried rearranging the options. No effect.

Does the man page have any precedent hints?

I looked at an online version ... seems you probably don't want the --include at all, just --exclude. Then the command just lists the directories to be included without the "--include" specifications.  The man page has exactly this example in the ... "Examples" section.

Something like:
```
/usr/bin/duplicity (irrelevant options) \
  --exclude /home/me/example \
  /home/me \
  ssh://remote/backupjar
```

---

