---
title: "[SOLVED] Help with find, grep, and rm"
date: 2008-03-27
forum: General Help
---

### Post by triphazard on 2008-03-27
Hi,

I have a collection of albums in one big "albums" folder and some of these album folders contain jpg files that i'd like to remove using find.  The thing is, I use the excellent Album Art software so each folder contains a "folder.jpg" that I want to keep.

So, the aim is to remove all jpg files recursively, except ones called folder.jpg

Now, I've tried some things...

Doing ```
find -iname "*.jpg" | grep -iv "folder.jpg" > output.txt
``` shows me that that syntax finds the exact files I want to remove.  It's just a case of getting them to go.

I've tried adding ```
-exec rm {} \;
``` but I suppose it doesn't like it after the grep or something (?)

I've also tried getting ```
rm -iR `find -iname "*.jpg"|grep -iv "folder.jpg"`
``` to work but it doesn't do the job either.

Is anyone able to help me out with this at all?

Sorry if this is in the wrong section...I couldn't find a better place to post it.

Thanks in advance.

---

### Post by croto on 2008-03-27
This will do the trick:
```

find -iname "*.jpg"   \! -iname "folder.jpg" -exec rm {} \;

```

There are two tests in that find line: -iname "*.jpg" and ! -iname "folder.jpg", the ! means "not" and it must be escaped for the shell not to interpret it as a special character. The two tests are combined in an "and" fashion (you can use the operator -and, see the manpage)

The option -exec belongs to the "find" command, you can't use it on grep. 

To see why  rm -iR `find -iname "*.jpg"|grep -iv "folder.jpg"` doesn't work. Try it like this:
```

ls `find -iname "*.jpg"|grep -iv "folder.jpg"`

```

You'll see that grep outputs the filepaths with spaces, and then ls or rm gets confused.

---

### Post by triphazard on 2008-03-27
> **croto said:**
> This will do the trick:
```

find -iname "*.jpg"   \! -iname "folder.jpg" -exec rm {} \;

```

There are two tests in that find line: -iname "*.jpg" and ! -iname "folder.jpg", the ! means "not" and it must be escaped for the shell not to interpret it as a special character. The two tests are combined in an "and" fashion (you can use the operator -and, see the manpage)

I'd been looking at how to do that for ages and had no idea that find could combine multiple rules.  I didn't actually know it had a "not" function either.  That's much better than throwing an inverse grep into the mix.

Thanks **very** much  :)

---

