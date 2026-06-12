---
title: "relative symbolic links"
date: 2008-07-06
forum: General Help
---

### Post by daz4126 on 2008-07-06
When I right click on a file, there is an option to 'make link'. This produces a file that is linked to the original file. The link target that gets created is an absolute path. Does anybody know how to make the link path relative?

thanks,

DAZ

---

### Post by sdennie on 2008-07-06
I'm not sure this makes sense.  If you make a link to a file using the relative path and then moved that link (which is only logical to do), the relative path would no longer be valid.

---

### Post by daz4126 on 2008-07-06
That is what I want to do!

I want to copy a load of relative links and copy them to another folder so that they link to another file by the same name instead.

It is for an icon theme.
Say I have an image called a.png and b.png, c.png and d.png all link to it.
In another folder, I also have an image called a.png, but it is a different size. I also want b, c and d to link to this image, so rather than create all these links again, I would like to just copy the links from the other folder into this folder. At the moment I can do this, but they stll link to a.png in the other folder, so they are the wrong size.

Does that make sense?

cheers,

DAZ

---

### Post by u-slayer on 2008-12-12
any progress on this? I too want to create a relative symbolic link.

I tried 

```
ln -s ./file3 file
```

but this created a broken link.

---

