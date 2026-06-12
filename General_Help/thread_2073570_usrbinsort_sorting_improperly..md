---
title: "/usr/bin/sort sorting improperly."
date: 2012-10-19
forum: General Help
---

### Post by Mozai on 2012-10-19
/usr/bin/sort has a weird quirk, and I am totally stumped as to why it's sorting strings in an unexpected order.

```
$ echo -e 'az\naa\n.a' |sort
.a
aa
az
```

This is what I expect.  '.' is 0x2E and 'a' is 0x61

```
$ echo -e 'aza\naaa\n.aa' |sort
.aa
aaa
aza
```

Still good so far.

```
$ echo -e 'azb\naab\n.ab' |sort
aab
.ab
azb
```

This, I have no idea why sort decided to put 0x2E between two lines each starting with 0x61

I've tried each of the sort options '-n' and '-g', and even '-b', '-d', '-f', '-i' and '-k1' just to wave some dead chicken bones. 

I've tried this with sort v7.4 (10.04.4 LTS) and with v8.13 (12.10), and I get the same screwy result.

Please tell me I'm overlooking something; I'm scared about filing a bug report for something in coreutils.

---

### Post by drmrgd on 2012-10-19
No idea of why, but maybe this is a clue?  If you run it with natural sort '-V' it works ok:

```
echo -e "azb\naab\n.ab" | sort -V
.ab
aab
azb

```

That also seems to work for you other test cases.  Again, I'm not sure I really understand the full functionality of the -V option, though.

---

### Post by Mozai on 2012-10-19
Just in case I was insane, I gave the same data to Perl's sort() function.
```
$ echo -e 'azb\naab\n.ab' |perl -ne 'push(@L,$_);END{@L=sort(@L);print join("",@L);}'
.ab
aab
azb
```

It's /usr/bin/sort that's the odd duck, but so much depends on this acting properly.  What am I overlooking?

---

### Post by Mozai on 2012-10-19
> **drmrgd said:**
> No idea of why, but maybe this is a clue?  If you run it with natural sort '-V' ...


`man sort` says:
```

       -V, --version-sort
              natural sort of (version) numbers within text

```

... does this mean the default for sort in Ubuntu is to parse lines as if they were version numbers?  Is that POSIX-compliant?

Are people using /usr/bin/sort expecting sort by byte-order or are we always aware of the always-on feature in Ubuntu's version of /usr/bin/sort to have "special sort of version numbers within text"

oh dear oh dear.

---

### Post by drmrgd on 2012-10-19
Yes, that's precisely why I'm confused about it.  To be honest, whenever I'm getting unexpected results from sort, I throw a -V at it, and it usually works.  It's definitely non-intuitive to me.  Then again, I'm no seasoned CLI pro :P

---

