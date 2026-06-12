---
title: "trying to sort out Dega Dup backup failing...."
date: 2016-03-28
forum: General Help
---

### Post by pjstock on 2016-03-28
My Deja Dup backup is failing on an error: No space left in &#8216;/&#8217;

Someone on the deja dup forum helpfully suggested an answer:  [http://askubuntu.com/questions/67397/why-does-d%C3%A9j%C3%A0-dup-](http://askubuntu.com/questions/67397/why-does-d%C3%A9j%C3%A0-dup-)
say-there-is-no-space-left

But I cannot make the suggested fix work (and that Ask Ubuntu is intimidating. I was about  to ask for some scarification but got a warning "Wait! Some of your past questions have not been well-received, and you're in danger of being blocked from asking any more."

The suggested fix was to /tmp and to do that using these commands:
```

mkdir /othervolume/.deja-dup-cache
mv ~/.cache/deja-dup/* /othervolume/.deja-dup-cache/
rmdir ~/.cache/deja-dup
ln -sf /othervolume/.deja-dup-cache ~/.cache/deja-dup

```

I presume I substitute on of my own volumes for "othervolume"
but I have one labelled "New Volume" but that is causing the command to fail.

When I try:
```
mkdir /new volume/.deja-dup-cache
mkdir: cannot create directory &#8216;/new&#8217;: Permission denied
mkdir: cannot create directory &#8216;volume/.deja-dup-cache&#8217;: No such file or directory

```

is that name "new volume" not suitable?

or what am I doing wrong?

---

