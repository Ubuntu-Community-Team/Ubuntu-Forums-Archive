---
title: "How compare content of directories and different files in kubuntu"
date: 2020-08-15
forum: General Help
---

### Post by petrogromovo on 2020-08-15
Hello,
Under my Kubuntu 18 using Krusader I can compare content of directories and different files are in green :
[https://prnt.sc/tziijt](https://prnt.sc/tziijt)

If there is a possibility to compare content of 2 files and different places?
Something like at left part 1 file and 2nd files at rigth part with different places selected?

Are there in kubuntu some other tools/apps for this?
Only in view mode...

Thanks!

---

### Post by sudodus on 2020-08-15
There are command line tools for this purpose. I use [FONT=Courier New]**diff**[/FONT].

Basic usage:

```

diff path1/file1 path2/file2

```

More advanced usage (in a very wide command line window to avoid line wrapping)

```

diff -y -W200 path1/file1 path2/file2

# or

diff -y -W200 path1/file1 path2/file2 | less

```

See [FONT=Courier New]**man diff**[/FONT] for more details.

---

### Post by dragonfly41 on 2020-08-15
Looking in my Krusader (in Ubuntu 18.04) I get this ..

[COLOR="#0000FF"]Hint: Krusader supports Kompare, KDiff3 and Xxdiff[/COLOR]

but also .. perhaps create a Useraction to take left and right panel locations
into Meld?

---

### Post by Dennis N on 2020-08-15
If comparing two text files, I use **meld**.

---

### Post by dragonfly41 on 2020-08-15
I have just tried creating a Krusader useraction leveraging meld command line and this works nicely direct from Krusader, launching Meld and comparing left with right content. I use Krusader for controlling a number of interactions with other apps. I have added Meld to this list.

---

### Post by petrogromovo on 2020-08-15
How did you set meld as option for Krusader ?

---

### Post by dragonfly41 on 2020-08-15
You can start by going to Krusader > Help > Krusader Handbook.

Refer to 6. Menu Commands > Useractions menu

Having read the above ...

In Krusader go to top menu bar > Useractions > Manage User Actions

Explore existing Useractions to get the idea of layout and variables to add to a new Useraction.

Click on first top button > Create new useraction .. opens template

Basic properties
Identifier: Krusader
Category: Meld
Title: &Meld actions
Tooltip: Meld
Description: Meld compares left with right
Command: meld %lCurrent% %rCurrent%


Note that in creating variables in Command field you can click on + sign to inject different variables into the command. Variables are bounded by % signs.

Of course you need to install meld and read its command line options.

When applying this new Useraction highlight a file in Krusader left panel, then highlight a file in Krusader right panel then (with both highlighted) go to Useractions > Meld .. and the Meld window should open comparing right and left files.

Footnote: Since you refer also to directory comparison you might need two Useractions

One to compare files
Another to compare directories.

---

### Post by TheFu on 2020-08-15
I would use **rsync** in dry-run mode.  From the rsync manpage:
```
        -n, --dry-run               perform a trial run with no changes made
```

---

