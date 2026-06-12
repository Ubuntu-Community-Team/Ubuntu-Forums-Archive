---
title: "Error while deleting in Nautilus (works fine through the shell though)"
date: 2008-04-27
forum: General Help
---

### Post by digitalchaos on 2008-04-27
when I try to delete a folder through Nautilus (delete, not move to trash) It will give me the following error:
[b]Error while deleting
Error removing file: Not a directory[/b]

I am forced to delete all the contents of the folder first, and then it will let me delete the folder. This is a pain when dealing with large trees.

Alternately, when I use the shell and do a 'rm -rf' on that directory I do not get an error (being run as the same user as when deleting via Nautilus).  Is there a way I can fix Nautilus to do the deletes with the -rf option or something? I am not really sure what is going on here.

---

### Post by rubicon on 2008-04-27
> **digitalchaos said:**
> when I try to delete a folder through Nautilus (delete, not move to trash) It will give me the following error:
[b]Error while deleting
Error removing file: Not a directory[/b]

I am forced to delete all the contents of the folder first, and then it will let me delete the folder. This is a pain when dealing with large trees.

Alternately, when I use the shell and do a 'rm -rf' on that directory I do not get an error (being run as the same user as when deleting via Nautilus).  Is there a way I can fix Nautilus to do the deletes with the -rf option or something? I am not really sure what is going on here.
Try 'nautilus-actions' package. It adds actions in context menu, and you could add 'rm -rf' command to folders. 

This is workaround, though. I guess this is a bug in gvfs and you should search a bugreport on launchpad or file your own if there is no such.

---

### Post by digitalchaos on 2008-04-27
> **rubicon said:**
> Try 'nautilus-actions' package. It adds actions in context menu, and you could add 'rm -rf' command to folders. 

This is workaround, though. I guess this is a bug in gvfs and you should search a bugreport on launchpad or file your own if there is no such.

Thanks! nautilus-actions package will do the trick for now but I will leave this open for a bit longer just in case someone else has any ideas.

Alternately, what are some decent nautilus replacements that you would recommend to get around this issue?

---

### Post by rubicon on 2008-04-28
Thunar and Dolphin :) Former for Xfce, latter for KDE. Thunar works fine under GNOME because it uses GTK+ (as nautilus), but it is a bit simplier than Nautilus and Dolphin. And Dolphin is a bit unusual but cool :) Try it yourself!

These are the most popular file managers...

---

