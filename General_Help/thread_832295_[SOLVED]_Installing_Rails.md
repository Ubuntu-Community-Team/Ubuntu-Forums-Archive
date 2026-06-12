---
title: "[SOLVED] Installing Rails"
date: 2008-06-17
forum: General Help
---

### Post by lyceum on 2008-06-17
I had to re-install Ubuntu and I am trying to install Rails. The book states that /usr/local/bin/rails

But $which rails shows it in /usr/bin/rails.

I tried to drag it to the right spot, but it did not work and the rails I did is showing as an error. How do I move this?

-edit-

If there is a better spot for this in the forums, could this post be moved? I was not sure where to post this.

---

### Post by nhandler on 2008-06-18
I wouldn't actually move it. Instead, I would create a symbolic link from /usr/local/bin/rails to /usr/bin/rails. A symbolic link is similar to a shortcut on Windows. By doing this, you will be able to follow along with the book, and applications that use rails will still be able to access it in /usr/local/bin/rails. To create the symbolic link, enter the following code in a terminal:

```
ln -s /usr/bin/rails /usr/local/bin/rails
```

You should now be able to access rails through /usr/local/bin/rails and through /usr/bin/rails.

---

### Post by lyceum on 2008-06-19
> **Cheater said:**
> I wouldn't actually move it. Instead, I would create a symbolic link from /usr/local/bin/rails to /usr/bin/rails. A symbolic link is similar to a shortcut on Windows. By doing this, you will be able to follow along with the book, and applications that use rails will still be able to access it in /usr/local/bin/rails. To create the symbolic link, enter the following code in a terminal:

```
ln -s /usr/bin/rails /usr/local/bin/rails
```

You should now be able to access rails through /usr/local/bin/rails and through /usr/bin/rails.

Thanks, I actually got it fixed and was coming here to state that, I found 

[https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails)

and just re-installed.

---

