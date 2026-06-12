---
title: "SVN problems after update"
date: 2007-10-14
forum: General Help
---

### Post by drinkingbird on 2007-10-14
So, I jumped on the computer this morning, saw a message about software updates being available, and let that grab some updated packages.

Then I went to update a checked out copy of a project I'm working on, from a remote SVN repository, and I get the message:

```
svn: Unrecognized URL scheme for 'https://svn.example.com/trunk'
```

According to the SVN FAQ, this is something to do with SVN not being able to see plugin libraries that it uses for repository access, or some such problem. I haven't touched any of that, and just allowed an automatic update to run.

Is this a known problem? Is there an easy workaround?

Thanks

---

### Post by molo on 2007-10-14
I have this problem as well, so if you get it solved somehow please post the solution (I'll do the same, of course).

Regards,
molo

---

### Post by molo on 2007-10-15
It looks like today's SVN package update fixed this.

---

### Post by zasf on 2007-10-16
> **molo said:**
> It looks like today's SVN package update fixed this.

yes, problem solved!

---

