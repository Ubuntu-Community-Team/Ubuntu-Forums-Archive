---
title: "Wine root in trash help"
date: 2007-12-13
forum: General Help
---

### Post by FoxHappy on 2007-12-13
I had deleted some wine files to reinstall wine (I know that's not a good way to do it, was learning, not the point)

Anyway, now I have this windows folder in my trash with a root folder in it that I can't delete. How do I delete it?

---

### Post by FoxHappy on 2007-12-14
Righto, well normally get a faster reply to my questions... I did however eventually find the answer, so anyone else if you have to delete a root or protected folder from your trash, do this.

***_WARNING_***
[I]Make bloody well sure you know what you're deleting when you do this, because you CAN screw up your OS if you delete something you shouldn't!
[/I]


Open a terminal and navigate to your trash can. It should be at:

```
/home/*username*/.Trash
```

If it's just a file you want to delete, use the code:

```
sudo rm *filename*
```

If you want to delete a directory, then use:

```
sudo rm -r *directoryname*
```

Remember, this will **permanently** delete *any* file or directory, so use carefully!

---

