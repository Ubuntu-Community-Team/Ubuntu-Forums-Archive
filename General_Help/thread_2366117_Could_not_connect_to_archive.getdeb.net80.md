---
title: "Could not connect to archive.getdeb.net:80"
date: 2017-07-14
forum: General Help
---

### Post by alain.roger on 2017-07-14
Hello,

It's been now few days that when i do a: sudo apt update && sudo apt upgrade, kubuntu 17.04 returns me the following error:
```
[FONT=monospace][COLOR=#000000]W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/zesty-getdeb/InRelease  Could not connect to archive.getdeb.net:80 (144.76.[/COLOR]
200.19), connection timed out
[/FONT]
```

Till now i had no issue and i did not add any ppa for a long time.

I tried several different servers like master, germany, france, uk, and so on.... nothing changed

I had a look at similar issues from the past on internet but nothing help so far.

Any idea what's happening with servers and how to fix this issue ?
thx

---

### Post by howefield on 2017-07-14
Looks like the getdeb servers are down again.

Not much you can do but disable the PPA until the servers are up, this will at least stop the error.

---

### Post by greatquux on 2017-07-14
Any indication that is the just temporary and the servers will be back?  I assumed if it was permanent there would be a goodbye message somewhere, but just want to make sure...

---

### Post by vasa1 on 2017-07-14
Monitor or post in [https://plus.google.com/+getdeb](https://plus.google.com/+getdeb) for news?

And here is a workaround from 2011: [https://askubuntu.com/a/51717](https://askubuntu.com/a/51717). Whether the same code works today is unclear :)

---

