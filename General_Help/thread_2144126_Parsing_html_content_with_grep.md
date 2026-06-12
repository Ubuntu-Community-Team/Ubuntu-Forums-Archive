---
title: "Parsing html content with grep"
date: 2013-05-11
forum: General Help
---

### Post by Stonecold1995 on 2013-05-11
I have a html page things like this in it:
```
<a id="p1874298" href="index.php?page=post&amp;s=view&amp;id=1874298">
```

How do I use grep to output only the number (i.e. "1874298")?  So far this is what I have:
```
wget -O - example.com | grep -m 1 --only-matching --perl-regexp '<a id=\"[^<>]*'
```
But that doesn't fully work...

---

### Post by markbl on 2013-05-11
```

wget -O - example.com | sed s'/^.*id=\([0-9]*\).*$/\1/'

```

---

### Post by Stonecold1995 on 2013-05-11
So then, would this be the best way to do it?
```
wget -O - example.com | grep -m 1 --only-matching --perl-regexp '<a id=\"[^<>]*' | sed s'/^.*id=\([0-9]*\).*$/\1/'
```
Isn't there a better way do do this, rather than using grep and sed?  I'm sure it can be done with grep alone.

---

### Post by markbl on 2013-05-11
> **Stonecold1995 said:**
> So then, would this be the best way to do it?
```
wget -O - example.com | grep -m 1 --only-matching --perl-regexp '<a id=\"[^<>]*' | sed s'/^.*id=\([0-9]*\).*$/\1/'
```
Isn't there a better way do do this, rather than using grep and sed?  I'm sure it can be done with grep alone.
Why did you add that grep back into the command I posted? You only need sed.

---

### Post by markbl on 2013-05-11
I just realised you probably want to filter other lines out and just grab the number[s] from all the input. So you want something like:
```

wget -O - example.com | sed -n '/<a id=/s/^.*id=\([0-9]*\).*$/\1/p'

```

---

### Post by Stonecold1995 on 2013-05-11
So then if I wanted to only output the FIRST number, would it be best to pipe that to "head -1"?  Or does sed have a feature like grep's "-m 1"?

---

### Post by markbl on 2013-05-11
Yes, If I wanted only the first line of output then I would just add a "| head -1" on that sed line.

However, if you want a more robust solution to parse xml/html tagged data from the command line then I would look at using xmlstarlet. I have used xmlstarlet previously and it is excellent.

---

