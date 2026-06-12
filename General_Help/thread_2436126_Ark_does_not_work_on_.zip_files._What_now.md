---
title: "Ark does not work on .zip files. What now?"
date: 2020-01-31
forum: General Help
---

### Post by semper-solus on 2020-01-31
Using Lubuntu 19.10. Ever since I upgraded, it seems Ark neither extracts nor compresses .zip files (with the sole exception of being able to extract single volume .zips)

As Ark is the default compression tool of Lubuntu, and this seems impossible to change through the user interface, what do I do to fix this?

Observations:
[LIST]
[*]Packages I have installed: zip, unzip, libzip5, libzzip-0-13, and libquazip5-1 
[*]I tried using PeaZip, but it wouldn't run because I was missing some qt library or other. I don't know. 
[*]If I open Ark, and open the drop-down box that picks the compression type, ZIP isn't even an option. 
[*]Going to LXQT Session Settings > Default Applications just lets me pick a terminal and browser, not a file compression thingy. 
[/LIST]

Help is greatly appreciated.

---

### Post by SeijiSensei on 2020-01-31
You can zip and unzip from the command prompt.

```
$ unzip /path/to/file.zip
```

Both programs have many options. See [man zip]("https://linux.die.net/man/1/zip") and [man unzip]("https://linux.die.net/man/1/unzip") for details.

---

### Post by Dennis N on 2020-01-31
> If I open Ark, and open the drop-down box that picks the compression type, ZIP isn't even an option.
Look again. It's at the bottom. (see screenshot)

In my quick test, it both compresses to .zip and extracts.

---

