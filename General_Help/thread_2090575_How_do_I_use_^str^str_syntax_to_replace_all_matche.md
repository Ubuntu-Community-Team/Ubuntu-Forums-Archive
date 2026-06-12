---
title: "How do I use ^str^str syntax to replace all matches?"
date: 2012-12-02
forum: General Help
---

### Post by sgy on 2012-12-02
Suppose I run the following command.
```

sgy@za-box:~$ cp -v .profile /data/ibook/sgy/misc/.profile-za-box

```Now, I would like to perform the same operation but with file .inputrc.  The following gets me close:
```

sgy@za-box:~$ ^.profile^.inputrc
cp -v .inputrc /data/ibook/sgy/misc/.profile-za-box 
`.inputrc' -> `/data/ibook/sgy/misc/.profile-za-box'

```But I would like to make the string substitution at all matches, not just the first.

How do I do that?  Where would I look for the answer?  Thanks.

---

### Post by steeldriver on 2012-12-02
couple of suggestions - by the magic of google...

[http://stackoverflow.com/questions/2149482/caret-search-and-replace-in-bash-shell](http://stackoverflow.com/questions/2149482/caret-search-and-replace-in-bash-shell)

---

