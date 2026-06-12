---
title: "Remove theme :S"
date: 2007-05-11
forum: General Help
---

### Post by matty13 on 2007-05-11
I cant find remove button, i clicked customize and removed but it wont shift off the list and remove completley!

Please help!

Screen:
[img]http://i10.tinypic.com/53ortpw.png[/img]

---

### Post by Foxmike on 2007-05-11
Well, if you want to go back to the original theme, you can select "Human" in the list. 

If you absolutly don't want to see the theme again in your list, you first have to select another theme in the list. Then, open a terminal and enter this command:

```
ls ~/.theme/*wii*
```

The terminal will give back to you an answer that looks like 

```
/home/(your username here)/.theme/(something)
```

then, you write ```
rm (space)
```
and you select the entire line the terminal answered to you, and you click the middle button of your mouse.  THis will paste the selection after the rm command.  The theme will be removed.

---

