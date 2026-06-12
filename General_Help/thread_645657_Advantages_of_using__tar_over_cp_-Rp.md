---
title: "Advantages of using  tar over cp -Rp ?"
date: 2007-12-20
forum: General Help
---

### Post by thelatinist on 2007-12-20
I want to copy multiple directories from one partition to another.  I've found two solutions, one using tar and one using cp -Rp.   Are there any advantages to using of these methods over the other?

The two commands I am considering are:

```
sudo cp -Rp [source] [target]
```

and

```
sudo tar cf - [source] | ( cd [target]; tar xfp - )
```

---

### Post by ~LoKe on 2007-12-20
> **thelatinist said:**
> I want to copy multiple directories from one partition to another.  I've found two solutions, one using tar and one using cp -Rp.   Are there any advantages to using of these methods over the other?

The two commands I am considering are:

```
sudo cp -Rp [source] [target]
```

and

```
sudo tar cf - [source] | ( cd [target]; tar xfp - )
```

I've never seen tar used that way...I can't see how there'd be a benefit.

---

### Post by kellemes on 2007-12-20
> **~LoKe said:**
> I've never seen tar used that way...I can't see how there'd be a benefit.

Same here..

cp is made for copying (tar for packing) so I'd use cp.
I can imagin there is a difference in speed at the most.

---

### Post by igknighted on 2007-12-20
> **~LoKe said:**
> I've never seen tar used that way...I can't see how there'd be a benefit.

I think the issue is if you don't trust the recursiveness of -R.  Perhaps it would preserve permissions and the like better then cp -R?  Not really sure.  It is clever though.

---

### Post by thelatinist on 2007-12-20
> **igknighted said:**
> I think the issue is if you don't trust the recursiveness of -R.  Perhaps it would preserve permissions and the like better then cp -R?  Not really sure.  It is clever though.

I believe the issue I read about somewhere was with preservation of permissions.  Is cp -p reliable when it comes to ownership and permissions?

---

### Post by igknighted on 2007-12-20
> **thelatinist said:**
> I believe the issue I read about somewhere was with preservation of permissions.  Is cp -p reliable when it comes to ownership and permissions?

[http://cmgm.stanford.edu/man2html/cp.1.html](http://cmgm.stanford.edu/man2html/cp.1.html)

according to this -p will preserve permissions and other attirbutes.  It seems that either command you listed initially should work equally well.

---

### Post by thelatinist on 2007-12-20
> **igknighted said:**
> [http://cmgm.stanford.edu/man2html/cp.1.html](http://cmgm.stanford.edu/man2html/cp.1.html)

according to this -p will preserve permissions and other attirbutes.  It seems that either command you listed initially should work equally well.

This link also seems to indicate that cp won't handle symbolic links properly.  It will copy the file the link points to, not the link.  I think this may be the reason for using tar, especially since I would like to keep my symlinks intact.

---

