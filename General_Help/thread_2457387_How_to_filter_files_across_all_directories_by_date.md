---
title: "How to filter files across all directories by date, 16.04"
date: 2021-02-01
forum: General Help
---

### Post by aneblanc on 2021-02-01
On my netbook I have a 64GB SD card mass storage. I recently bought a 64GB USB drive to duplicate all my files from the SD card in case of a failure.
I have copied all my files from the SD to the USB. Now I would like to periodically add the newly created files and replace the modified files to keep the USB at the same state as the SD card.
How can I sort all my files on the SD card across all directories by date to select the most recent for copying? Thank you in advance.

---

### Post by ActionParsnip on 2021-02-01
are they in lots of sub directories or is it one flat folder full of everything?

---

### Post by Holger_Gehrke on 2021-02-01
You could probably get what you *ask* for with 'find' with one of the options '-mmin', '-mtime' or '-mnewer'. But for what you need - keeping two groups of files in sync either locally or across the network - you should use 'rsync' which will check what has changed and what hasn't and can even in a lot of cases write only the changes of a larger file.

Holger

---

