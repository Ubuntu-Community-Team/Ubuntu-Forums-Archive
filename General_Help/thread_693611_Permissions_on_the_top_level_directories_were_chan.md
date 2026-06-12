---
title: "Permissions on the top level directories were changed.  What should these be?"
date: 2008-02-11
forum: General Help
---

### Post by none-letmebe on 2008-02-11
One of my scripts went nutty (user error) and the for i in loop went and set the permissions on all the directories under / as 700.  

I changed these to 755 ( cd / ; chmod 755 * ) and then set /tmp (chmod 777 /tmp ; chmod +t /tmp ).

My question is what are the correct permissions for Ubuntu for these top level files.

Regards,
Silly-User.

---

### Post by none-letmebe on 2008-02-11
I think everything ought to be 755 except for /tmp as noted above and:

lost+found  700
proc        555

---

### Post by zvacet on 2008-02-11
If they had 700 permissions give them that permissions back.You changed permissions to root dir and that is not smart thing to do.

---

### Post by Ptero-4 on 2008-02-11
I think the OP meant that his script set the permissions to 700 because of an error made by him, which would mean that the permissions were originally something else.

---

### Post by none-letmebe on 2008-02-12
> **zvacet said:**
> If they had 700 permissions give them that permissions back.You changed permissions to root dir and that is not smart thing to do.

Indeed, dear child. This is not the type of judgemental response that I had expected.  Your answer is unhelpful and serves no purpose.


@Ptero-4 :  You are correct and I have corrected the permissions back to what these ought to have been.

Thank-you to all those on this forum who offer help.

---

### Post by zvacet on 2008-02-12
> This is not the type of judgemental response that I had expected.

There was nothing judgemental in my post.I just try to tell you that changing root dir permissions can lead you to unexpected problems.Probably my broken english is source of missunderstanding.

---

### Post by none-letmebe on 2008-02-12
> **zvacet said:**
> There was nothing judgemental in my post.I just try to tell you that changing root dir permissions can lead you to unexpected problems.Probably my broken english is source of missunderstanding.

Ok. Its a misunderstanding.  Of course, this was why I wanted to set the permissions back to the correct ones in the first place :)

---

### Post by chrisccoulson on 2008-02-12
As long as you don't recursively chmod everything, then you should be ok. Just to point out, I think the permissions on lost+found should be 700. Also, /tmp should have the sticky bit set.
```
sudo chmod 1777 /tmp
```

---

### Post by none-letmebe on 2008-02-12
Yup. you are right.  I forgot lost+found and I set the stickly bit with chmod +t /tmp .
Cheers.

---

