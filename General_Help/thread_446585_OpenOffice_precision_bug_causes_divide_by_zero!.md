---
title: "OpenOffice precision bug causes divide by zero?!"
date: 2007-05-17
forum: General Help
---

### Post by davient on 2007-05-17
Hi there, I have posted a query about this on OpenOffice.org ([http://www.oooforum.org/forum/viewtopic.phtml?p=226056#226056](http://www.oooforum.org/forum/viewtopic.phtml?p=226056#226056)) the guys there have been very helpful but as yet have had no success.  We think this may be a ubuntu specific problem and hence I am posting here.

I will summarize my problem and the discussion here.  Thanks :)

If you create the following sheet: -


```

               A
1 =POWER(120000;-2)
2 =POWER(120000;-2)
3 =A1/A2
```

in 2.0.4-ubuntu5  you get: -

```
    A
1  0
2  0
3  #DIV/0!
```

Upgrading to OpenOffice.org 2.2.0 yields

```
    A
1  0
2  0
3  #VALUE!

```

when in fact =POWER(120000;-2)  should yield 6.94E-11
and therefore naturally a1/a2 should yield 1

In fact if you modify the formatting to Scientific  for cells A1 and A2 you get:
```
    A
1  6.94E-011
2  6.94E-011
3  1
```the correct result !?

It seems that the default formatting (and from playing around any numerical formatting) appears to pass on the loss of accuracy from the format to the cells requesting the data for formulas!

This is quite a major problem.


I running Open Office 2.2  under Ubuntu Edgy on an IBM T30.  trying the same under Fedora has no problems, and other users report no problems on other distros and also under windows.


Please redirect me if this is not the correct place to post.

cheers, and thanks in advance for your help.

Dave

---

