---
title: "How do you get GREP to skip &quot;./proc/sysrq-trigger&quot;?"
date: 2013-08-15
forum: General Help
---

### Post by nhtrader on 2013-08-15
ubuntu 12.0.4.2 LTS (x86_64)
grep v2.10


I'm trying to scan my entire HDD, but grep keeps getting stuck on some sort of process.

This is what I've tried but it gets stuck on ./sysrq-trigger

I started with this:
grep --exclude-dir=./{dev,tmp,proc,lost+found,sys,media}/* -rI -i --color "content" .

then I tried this:
grep --exclude-dir=./proc/sysrq-trigger --exclude-dir=./{dev,tmp,lost+found,sys}/* -rI -i --color "content" .

and this:
grep --exclude-dir=./sysrq-trigger --exclude-dir=./{dev,tmp,lost+found,sys,media}/* -rI -i --color -E "content" .

But I can't get past this /proc/sysrq-trigger

Can anyone hep me scan my HDD for only text files for three words "content", "music", and "video"?

---

### Post by DarkAmbient on 2013-08-15
Not sure if this works but:

```
grep --exclude=sysrq-trigger --exclude-dir=./{dev,tmp,lost+found,sys,media}/* -rI -i --color -E "video|content|music" . | grep 'music\|video\|content'
```

---

### Post by steeldriver on 2013-08-15
Another option that may work for you is to use 'find' to descend the filesystem and pass the results to a non-recursive grep  - then you can use the '-prune' option to exclude unwanted branches e.g.

```
find / \( -path /dev -o -path /proc -o -path /sys -o -path /tmp \) -prune -o -type f -exec grep -HIi 'content\|video\|media' {} +
```


You can add the '-xdev' option to exclude other mounted filesystems (which should take care of anything in /media without explicitly pruning it)

```
find / -xdev \( -path /dev -o -path /proc -o -path /sys -o -path /tmp \)  -prune -o -type f -exec grep -HIi 'content\|video\|media' {} +
```

Depending what you are looking for, you might want to add -w to the grep to limit it to whole words (else it will match strings like im**media**tely)

---

### Post by nhtrader on 2013-08-15
I tried your command. I suppose it worked b/c I didn't see sysrq-trigger, but I still got stuck. It now hangs without any clue as to why it is stuck. So thanks, it definitely got me past sysrq-trigger.

---

### Post by nhtrader on 2013-08-15
Well, I tried your first command (no xdev) and it worked. Thanks. What's interesting is that I had tried a variation of this earlier today but my syntax wasn't correct. Thanks for showing the correct systax. This command did not hang and I was able to find all occurrences of what I was looking for.

---

