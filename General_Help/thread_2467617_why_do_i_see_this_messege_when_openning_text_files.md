---
title: "why do i see this messege when openning text files?"
date: 2021-10-02
forum: General Help
---

### Post by ronjjjg8885 on 2021-10-02
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289225&stc=1[/IMG]

---

### Post by deadflowr on 2021-10-02
It's a setting in Files Preferences, which your's is currently set to ask.
Options are open or view, execute or run, and ask.
I think the default is to open the file in a text editor.

---

### Post by The Cog on 2021-10-02
It seems a reasonable question to me. If you double-click an executable text file in a file manager, you might mean you want to open the file in an editor, or you may want to execute(run) it. So the answer to "why" is that they are marked as executable, so wanting to "open" them is ambiguous. 

It is not normal for text files to be marked as executable, unless they are scripts that are intended to be executed.
I suggest that you remove the executable flag from these text files, which will remove the ambiguity. You can remove the executable flag with the command
```
chmod -x <filename>
```
or if you have a directory full of them, you can use the * wild-card to remove the executable flag from all of them at once.

However, if the files are on a filesystem that doesn't support *nix permissions (e.g. NTFS, FAT, exfat) then you won't be able to remove the executable flag as it is emulated by the filesystem driver and not stored on disk. You may be able to change the mount options, but that's more long-winded and we would need to know how you are mounting the drive before we can advise on that.

---

### Post by ActionParsnip on 2021-10-02
Is the text file stored on NTFS?

---

### Post by ronjjjg8885 on 2021-10-03
no NTFS

i will look at the settings so that it gets opened immediately..

---

