---
title: "mutt problems"
date: 2008-04-20
forum: General Help
---

### Post by spx3 on 2008-04-20
Hi,

I have a problem with mutt.
I've already read the faq and the docs and some other unofficial docs
on the net.
No solution I have found.
The problem is that in the folder browser I want to see how many new
messages I have.
I've seen in the FAQ this
 set folder_format="%2C %t %8s %d %f %N"
int the faq they also mention that this does not work for anything
other than IMAP
and I do not have IMAP.
ok now...what can I do to get a new message count for each folder ?
there was a C patch somewhere for this written by someone but that's
really ... I have to compile
all mutt all over etc...
I just want to be able to somehow hook on some mutt results and resend
them to mutt so that it can display
them but I don't know how.
has anybody else done this ?

---

### Post by andrew.46 on 2008-05-19
Hi,

 Looks like this cannot be done with the standard mutt but there is a patch that I note has been altered for the recent 1.5.18 release:

[http://www.lunar-linux.org/index.php?option=com_content&task=view&id=44](http://www.lunar-linux.org/index.php?option=com_content&task=view&id=44)

 Perhaps this is what you are after? I have not tried it myself. I note also that there is [a debian package]("http://packages.debian.org/sid/mutt-patched") incorporated into Ubuntu which contains this patch:

```
$ sudo apt-get install mutt-patched
```

which may be a little easier to use.

    Andrew

---

