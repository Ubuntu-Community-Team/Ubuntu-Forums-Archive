---
title: "Update error - not able to download/see the updates"
date: 2008-03-29
forum: General Help
---

### Post by petaloid on 2008-03-29
I've recently installed Ubuntu and I recently finished one crop of updates. that was done yesterday and now today when i try to update I get this error when i try to use the Update manager - i starts checking for downloads and then starts downloading them but after that i get this error:

[IMG]http://img.photobucket.com/albums/v202/teslaclaw/updaterror.png[/IMG]

followed by that this pops up

[IMG]http://img.photobucket.com/albums/v202/teslaclaw/updaterror2.png[/IMG]

What does this all mean?

EDIT: I tried to edit software sources in administration, to download from the main server [like so]("http://img.photobucket.com/albums/v202/teslaclaw/changethatimade.png")

But I run into the same errors when I run the update manager: [Error1]("http://img.photobucket.com/albums/v202/teslaclaw/updaterrorafterchange.png") , [Error2]("http://img.photobucket.com/albums/v202/teslaclaw/updaterrorafterchange2.png")

---

### Post by bwhite82 on 2008-03-29
Try removing the signing keys and re-updating.

---

### Post by petaloid on 2008-03-29
how do i do that?

---

### Post by bwhite82 on 2008-03-29
> **petaloid said:**
> how do i do that?

Click on System>Administration>Software Sources.

On the window that opens, click on the 'Authentication' tab highlight each key and click 'Remove'.

---

### Post by dcstar on 2008-03-29
> **petaloid said:**
> I've recently installed Ubuntu and I recently finished one crop of updates. that was done yesterday and now today when i try to update I get this error when i try to use the Update manager - i starts checking for downloads and then starts downloading them but after that i get this error:
........

When updates are in the process of being rolled out to all the repositories this sort of thing occurs as the files are not yet synced with the index lists.

Wait a day and then you should find that everything should work.

---

