---
title: "software properties gtk crashed with not found error in execute child error 2"
date: 2016-10-19
forum: General Help
---

### Post by missmoondog on 2016-10-19
this is the error i get after lubuntu 16.04 starts and find while sending report. doesn't seem to hurt anything, but hate seeing errors!!

software properties gtk crashed with file not found error in execute child (error 2)

anybody have any ideas on how to fix?

thank you

edit:
edited to fill in 1 missing word from what my error message says EXACTLY and put parenthesis around error 2!

---

### Post by missmoondog on 2016-10-21
186 views and no one has any idea what this error is?

about to do the upgrade switch from Lubuntu 16.04 to Quelitu 16.04 from here, [http://wavesofthefuture.net/computers/downloada.shtml](http://wavesofthefuture.net/computers/downloada.shtml)

maybe that will fix this issue. was using Quelitu 14.04 previously and it worked perfectly.

---

### Post by howefield on 2016-10-22
> **missmoondog said:**
> 186 views and no one has any idea what this error is?

3 of whom are actual real live people (apart from you and I)

You could try purging software-properties and then putting it back.

```
sudo apt purge software-properties-common
```
```
sudo apt install software-properties-common
```

> about to do the upgrade switch from Lubuntu 16.04 to Quelitu 16.04 from here, [http://wavesofthefuture.net/computers/downloada.shtml](http://wavesofthefuture.net/computers/downloada.shtml)

Good luck.

---

### Post by missmoondog on 2016-10-22
thank you howefield,
i wasn't really paying attention when i did that upgrade switch and rebooted, but i think that error was gone. only got that error on 1 computer out of 6 that i have quelitu on. 

doing that switch is super easy and only takes like 5 minutes. don't know why those people over at wavesofthefuture.net didn't make their own 32bit iso for that OS, like they did for quelitu 14.04. they made their own iso for the 64bit version. with the 32bit version, you have to install lubuntu first, then do the upgrade/switch afterwards.

will keep a closer eye on that 1 computer next time i'm on it and see if i get that error and if so, will try your suggestion.

thank you

---

### Post by missmoondog on 2016-10-25
marking topic as solved as doing that switch thing from Lubuntu to Quelitu has fixed the issue! :)

---

