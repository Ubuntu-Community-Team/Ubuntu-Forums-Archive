---
title: "How do I restore a single file from Backup?"
date: 2016-04-04
forum: General Help
---

### Post by paul-hazelden on 2016-04-04
Running Ubuntu 15.10

I have done several searches and the answer seems to be 'restore from the Files menu in Nautilus'.  But I have 'Files', not Nautilus, and the Restore option is not available.

---

### Post by sudodus on 2016-04-04
Welcome to the Ubuntu Forums :-)

The file browser is called ***'Files'*** in standard Ubuntu. The name of that tool (under the hood) is ***nautilus***.

What kind of backup have you got? Which tool did you use to create the backup?

---

### Post by howefield on 2016-04-04
Seems to be working here in 15.10 but try right clicking inside the relevant folder rather than selecting from the Files menu.

---

### Post by paul-hazelden on 2016-04-04
I'm using the 'Backups' utility which comes with Ubuntu.  It is accessed from the System Settings.  The backup files it creates all start with 'duplicity-full'.

Do you need any other information?

---

### Post by paul-hazelden on 2016-04-04
Ah!  The screenshot from howefield shows the files viewed as icons.  When I switch my view from list to icon, I get the 'Restore missing files ...' option.  Thank you.

I always use the list view, never thought to change it.

Is this a bug?

---

### Post by howefield on 2016-04-04
> **paul-hazelden said:**
> Is this a bug?

Hmm, doubt it is a bug, should work in either list or icon view as long as you are right clicking on an empty space within a folder that has a "missing" file to restore. Seems to be working on this install as intended.

---

### Post by paul-hazelden on 2016-04-04
On further examination, when I right click in the space below the files in a directory with only a few files, then I get the prompt.

But I had been trying in directories which filled the window.  I can't find any empty space to right click in.  With the icon view, there is space between the icons to click, but I can't find any space when the list of files takes up the whole window.

---

### Post by paul-hazelden on 2016-04-04
So I can't restore files in list view to any directory with more than 28 files or subdirectories.

---

### Post by howefield on 2016-04-04
> **paul-hazelden said:**
> So I can't restore files in list view to any directory with more than 28 files or subdirectories.

Well, not exactly the case.. navigate to the folder with the "missing" files(s) to be restored and press Ctrl+Shift+F10 keys which bring up the correct context menu with the restore option.

Not saying that is ideal but easy enough.

If you feel like it, you can file a bug against Files if there isn't one already that you can "affects me too"

---

### Post by RobGoss on 2016-04-04
> **howefield said:**
> Hmm, doubt it is a bug, should work in either list or icon view as long as you are right clicking on an empty space within a folder that has a "missing" file to restore. Seems to be working on this install as intended.


You are correct I can also see this feature when I right click on a empty space in that folder...

---

### Post by paul-hazelden on 2016-04-04
> **howefield said:**
> Well, not exactly the case.. navigate to the folder with the "missing" files(s) to be restored and press Ctrl+Shift+F10 keys which bring up the correct context menu with the restore option.

Not saying that is ideal but easy enough.

If you feel like it, you can file a bug against Files if there isn't one already that you can "affects me too"

Ctrl+Shift+F10 ... why didn't I think of that?

Okay, it works.  Looks like a documentation issue rather than a bug.  Many thanks.

---

### Post by howefield on 2016-04-05
Cool, glad you got it.

For info and if you were really stuck, there is also the command line option to launch the restore files option.

```
deja-dup --restore-missing pathtorestore
```

Benefit being that the commands are the same irrespective of desktop environment.

There aren't many options but see...

```
man deja-dup
```

---

### Post by paul-hazelden on 2016-04-05
That is really helpful.  Thank you.

---

