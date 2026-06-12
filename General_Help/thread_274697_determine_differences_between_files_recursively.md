---
title: "determine differences between files recursively?"
date: 2006-10-10
forum: General Help
---

### Post by harty83 on 2006-10-10
How would you most effectively and easily determine differences between files in two directories with the same structure?

I have a new release for a web program that I've edited but I can't remember what files I've changed.  I would hate to have to go through each file (over a hundred) and diff each one.

Thanks!

---

### Post by epennings on 2006-10-10
Maybe xxdiff can do the job.

```

[COLOR="RoyalBlue"]a graphical file and directories comparison[/COLOR] and merge tool
A powerful tool for viewing the differences between two or three files,
or two directories, and can be used to produce a merged version. The
texts of the two or three files are presented side by side with their
differences highlighted with colors for easy identification. Among its
features are:
   * Comparing two files, three files, or two directories (shallow
     and [COLOR="RoyalBlue"]recursive[/COLOR]);
   * Horizontal diffs highlighting;
   * Files can be merged interactively and resulting output visualized
     and saved;
   * Has features to assist in performing merge reviews/policing;
   * Can unmerge CVS conflicts in automatically merged file and display
     them as two files, to help resolve conflicts;
   * Fully customizable with a resource file;
   * Look-and-feel similar to Rudy Wortel's/SGI xdiff, it is desktop
     agnostic (i.e. will work equally well with KDE or Gnome).
```

---

### Post by harty83 on 2006-10-10
Thanks. I'll look into it, but it looks like it will determine differences between what is in the directories (list file names) not between the files themselves (list differences between contents of files within directories).

---

