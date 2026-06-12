---
title: "launch rsync question"
date: 2008-06-11
forum: General Help
---

### Post by savsav on 2008-06-11
I would like to place a link or icon on my xubuntu desktop and double-click it to lauch terminal AND automatically run something like this:

rsync -av /home/abc/Desktop/Folder1/ /Folder2/


Okay?

I just want to automate my backups a little bit.

Is that possible.

---

### Post by HalPomeranz on 2008-06-11
Why make it something you have to click?  Why not run your command automatically out of cron at a particular time?

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by savsav on 2008-06-11
No , cron is not what i am looking for.

I want to be able to start the sync whenever I want.

So , is it possible to lauch terminal with the rsync command already typed in?

---

### Post by HalPomeranz on 2008-06-11
> **savsav said:**
> So , is it possible to lauch terminal with the rsync command already typed in?

Yeah, you can do something like:

```

gnome-terminal -e 'rsync -av /home/abc/Desktop/Folder1/ /Folder2/'

```

Though I warn you that the terminal window is going to disappear as soon as the rsync command exits.  There will have to be some additional cleverness if you want to keep the output around to study once the command is finished.

---

