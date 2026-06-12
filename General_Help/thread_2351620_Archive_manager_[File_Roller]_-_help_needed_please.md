---
title: "Archive manager [File Roller] - help needed please."
date: 2017-02-05
forum: General Help
---

### Post by pat4 on 2017-02-05
Ubuntu 16.04, 64 bit. I'm running the default Archive Manager [File Roller] and Nautilus.   My problem revolves around extraction of files from both single and multi-part compressed archives with particular regard to the right-click context menu "extract here" option in Nautilus.

I deal with a large number of archives containing files of mixed formats. I invariably want to extract the files to the same directory as the archive and for this the "Extract here" option in the context menu is useful. This also allows me to select a number of archives and then execute the "Extract here" command for bulk extraction.... However, whenever I use this option the extracted files are placed within a sub-directory within the working directory.

I find that if I click a single compressed file, allow Archive Manager to open then choose "Extract", the files are extracted directly into the working directory. 

To extract a large number of archives this way is time consuming so I would like to know of any way to enable the "extract here" context menu command to extract directly to the working directory.

I have unchecked the option to "keep directory structure" and this makes no difference.  

If this function isn't possible within Archive Manager does anyone know of a suitable command-line script that will act as a "catch-all" extractor for compressed archives (of all formats). I now I can use the "unzip" command with a wildcard [ unzip "*.zip" ] but this only works with zip files and not *.rar or multi-part archives.

Any and all help appreciated.

Regards,  Pat.

---

### Post by ajgreeny on 2017-02-05
I think the behaviour will depend on the archive itself and the manner in which files and folders are contained within the archive.

If you have an archive with a single folder in it, in which are many files and folders, the "extract here" will extract that single folder the archive contained into the working directory or folder which held the archive.
If, however, the archive has multiple folders and files in it, the "extract here" option will simply extract all of those into the working ditectory which held the archive, for example, Downloads, which could make them very difficult, if not impossible to keep track of after extraction.

---

### Post by pat4 on 2017-02-05
Ajgreeny,
Thanks for the response..

Yes - in some archives he files are contained within a separate folder and I expect the folder to be extracted but I find the behaviour occurs even when the files are listed separately. Strange though, that the "problem" only manifests itself when using the "extract here" option from the context menu.

Kind regards,  Pat.

---

