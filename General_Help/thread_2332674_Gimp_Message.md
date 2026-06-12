---
title: "Gimp Message"
date: 2016-08-02
forum: General Help
---

### Post by 4kh3RAm on 2016-08-02
Anytime I use Gimp, i get this window.

F> ailed to create thumbnail folder '/home/andy/.thumbnails/normal.

How do I stop that ?

---

### Post by howefield on 2016-08-03
An old thread but marked solved... [https://ubuntuforums.org/showthread.php?t=487369](https://ubuntuforums.org/showthread.php?t=487369)

It's not so hard to search before posting.

---

### Post by 4kh3RAm on 2016-08-03
That link is for a different question.

> Failed to open '/home/merrillj/.thumbnails/normal/gimp-thumb-3610-c672ef4f' for writing: Permission denied

And with the problems that chown has caused, I am very leerly of using chown.

---

### Post by vasa1 on 2016-08-03
> **4kh3RAm said:**
> ...
And with the problems that chown has caused, I am very leerly of using chown.

You should be leery of using sudo or root.

---

### Post by howefield on 2016-08-03
> **4kh3RAm said:**
> And with the problems that chown has caused, I am very leerly of using chown.

Not to side track this simple thread, but well, so you should be leery of using chown.

I wouldn't run commands on a production machine that I have no idea how to revert.

Imho, the main issue isn't so much using system commands, it is not having a way of reverting them when you mess up, exactly what that "way" means can take many forms, but as an example, it is easy enough to log the changes a chown command will do to a text file. That way, you have a record of what was changed and from what. 

Sorry for the sidetrack, but don't be leery of the chown command, be leery of the lack of backup strategy.

PS. The linked thread uses the chmod command, not chown  ;)

---

### Post by 4kh3RAm on 2016-08-03
Okey dokey.

So I could do chown blah blah >> Commands_Run.txt and then I would have a log to review  ??

---

### Post by howefield on 2016-08-03
Well, a simple example..

Create a few test folders in the /home folder with

```
mkdir -p ~/testing/{one,two,three}
```

and perhaps a test file with..

```
touch ~/testing/three/test
```

To change ownership of ~/testing/* from you to root, use 

```
chown -R root:root -v ~/testing > ~/Documents/chown.log
```

You should now have a chown.log file in your Documents folder which for me reads...

```
changed ownership of '/home/hugh/testing/three/test' from hugh:hugh to root:root
changed ownership of '/home/hugh/testing/three' from hugh:hugh to root:root
changed ownership of '/home/hugh/testing/two' from hugh:hugh to root:root
changed ownership of '/home/hugh/testing/one' from hugh:hugh to root:root
changed ownership of '/home/hugh/testing' from hugh:hugh to root:root
```

In this example, any folder and files already owned by root would be indicated with "ownership of '/home/hugh/testing/three' retained as root:root"

You would only use the double angle bracket if you wanted to append the output to an already existing file. Single angle bracket to create a new file.

You'll need to delete those folders/file with sudo or run the command again, only this changing back to you as user.

---

### Post by 4kh3RAm on 2016-08-03
O.K.

If I want to be able to access files on a separate drive without doing it as a superuser, how would I change ownership on that drive ?

---

