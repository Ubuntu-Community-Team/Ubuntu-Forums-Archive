---
title: "malformed line 131 in source list"
date: 2013-10-31
forum: General Help
---

### Post by old_dog on 2013-10-31
As above the full error message is:
malformed line 131 in source list /etc/apt/source.list(dist parse)
couldn't read list of package sources

Line 131 says:
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner

Give me a clue, can I delete the line in question
Any advice please.

---

### Post by drmrgd on 2013-10-31
I think you're missing the distribution name in that line.  I think it's supposed to be something like (I'm running 12.04):

```

deb http://archive.canonical.com/ubuntu precise partner

```

Can you post the results of:
```

cat -n /etc/var/sources.list

```

If you want, you can comment out the offending line(s) by adding '#' in front them, and then running:
```

sudo apt-get update

```

The worst case scenario is that packages you've installed from the partner repos will not be upgraded when you upgrade packages.  Still, though, should be simple enough to fix the issue.

---

### Post by old_dog on 2013-10-31
Thanks.........
I added ubuntu saucy in front of partner

Jobs a good one.......... all sorted
cheers

---

