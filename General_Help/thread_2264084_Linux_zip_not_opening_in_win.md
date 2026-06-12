---
title: "Linux zip not opening in win"
date: 2015-02-05
forum: General Help
---

### Post by zeron00 on 2015-02-05
A small zip file created with GUI in Kubuntu and uploaded to a central server.  Downloading it into windows and trying to extract it is somewhat problematic: windows just says that it cannot open the "folder" (sic). Using some other program, like winrar or 7zip, opens the archive but the contents of the archive is shown as one file instead of the 10 that I packed into it. This inner file has the same name as the archive minus the zip-extension. To see the original content of the archive I have to open this inner file manually with some archiving program.  It looks like the gui utility in kubuntu is using tar utility on the original files before compressing them, which causes problems for windows (there's no difficulty downloading and opening the same file in linux).  It seems that I'm not the only one to experience this mystic behaviour. There is an older closed thread here that describes a similar situation: [http://ubuntuforums.org/showthread.php?t=1696447](http://ubuntuforums.org/showthread.php?t=1696447) . It is marked as "Solved" but I see no explanation of why this is happening.

---

### Post by Holger_Gehrke on 2015-02-05
Could you try an have a look at the file type of the archive using the 'file' command in the shell ? I suspect your archiver is not producing a zip file at all but a gzipped-tarfile. The output of ```
file archive.zip
``` should look like this```
archive.zip: Zip archive data, at least v2.0 to extract
``` while a tar.gz even if it's named as a zip will produce somehing like ```
archive.zip: gzip compressed data, from Unix, last modified: Fri Sep  5 17:18:03 2014, max compression
```

These archiver GUIs are usually just thin shells on top of either libraries or the actual command line archivers. If it's set to produce tar.gz files (which is the default for some of them), then even telling it to name the file whatever**.zip** won't actually make it produce zip-files.

---

### Post by zeron00 on 2015-02-09
Yes, you're right -- the file is a gzip-archive. The results of the file command:

```

$ file archive.zip
$ archive.zip: gzip compressed data, last modified: Mon Jan 19 20:16:02 2015, from Unix

```

Is there a way to force the GUI utility to create a zip-archive? Or, if not, how can I do it in commandline?

---

### Post by Holger_Gehrke on 2015-02-09
> **zeron00 said:**
> 
Is there a way to force the GUI utility to create a zip-archive? Or, if not, how can I do it in commandline?


Sorry,  but since I don't even know which of the GUI tools you use, I can't tell you how to make it produce zip files. fileroller - the one I use when I don't use the command line - offers an option in the dialog for file creation. 

On the command line there's various tools for the different formats: tar,zip and unzip, 7z and 7za(which is not an unpacker but a 7z without support for some additional formats), unrar (yes, a 'rar' exists, but it's closed source and you've got to pay for it), lha, zoo, ace ... All of them come with man pages.

To create a zip from the command line, you'd enter something like:
```

zip "Archive name" "list of files to archive split with spaces, wild card characters allowed"

```
and season to taste with some of the options from the man page.

---

### Post by mastablasta on 2015-02-09
never seen that or had problems opening files from Linux in windows. 

I assume you are using Ark. just set it to use zip instead of tar.gz.

[https://docs.kde.org/stable/en/kdeutils/ark/ark.pdf](https://docs.kde.org/stable/en/kdeutils/ark/ark.pdf)

---

