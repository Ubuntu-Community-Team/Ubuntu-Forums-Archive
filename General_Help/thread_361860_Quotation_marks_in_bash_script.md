---
title: "Quotation marks in bash script"
date: 2007-02-14
forum: General Help
---

### Post by CocoAUS on 2007-02-14
I would like one of my scripts to include the following code:

```
echo "for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo "gnome-open $uri" &
done" > $HOME/.gnome2/nautilus-scripts/Open\ as\ root
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

The problem is that the echo command recognizes the quotation marks as being the container for the echoed statement, so having quotation marks in the echoed content (the second line, reading: "gnome-open $uri") ends up messing up the command.

How do I place quotation marks in my echoed statement?

---

### Post by yabbadabbadont on 2007-02-14
You either need to escape the quotation marks with a backslash or alternate using double and single quotes.

Edit:  Try the following and see if either works.
```
echo "for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo 'gnome-open $uri' &
done" > $HOME/.gnome2/nautilus-scripts/Open\ as\ root
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```
or
```
echo "for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo \"gnome-open $uri\" &
done" > $HOME/.gnome2/nautilus-scripts/Open\ as\ root
chmod +x $HOME/.gnome2/nautilus-scripts/Open\ as\ root
```

Edit2: Just as a clarification
```
/home/bubba $ echo "this is a test"
this is a test
/home/bubba $ echo "this ""is"" a test"
this is a test
/home/bubba $ echo "this 'is' a test"
this 'is' a test
/home/bubba $ echo "this \"is\" a test"
this "is" a test
```

---

### Post by CocoAUS on 2007-02-14
Awesome, thanks.  I was under the impression that backslashes only worked for a specific set of characters.

Again, thanks much.

---

