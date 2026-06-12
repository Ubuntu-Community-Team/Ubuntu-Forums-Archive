---
title: "LibreOffice complaining about lock permissions"
date: 2022-09-18
forum: General Help
---

### Post by Paddy Landau on 2022-09-18
**[SIZE=3]EDIT: Problem solved[/SIZE]**

I found the problem. I started setting my temporary folder ($TMPDIR) to a folder in RAM ($XDG_RUNTIME_DIR), and for whatever reason, LibreOffice doesn't like this.

It also affected trying to "print to file" from Evince, with the following error (the folder [FONT=courier new].tmp.OxN[/FONT] was, at the time, my temporary folder):
> Failed to create file “/run/user/1000/.tmp.OxN/gtkprint_75IHS1”
LibreOffice probably couldn't access the RAM disk because of Flatpak permissions (I haven't tested this). But as to why Evince couldn't access the RAM disk, I have no idea.

[SIZE=3]Summary[/SIZE]

Out of the blue, LibreOffice won't open any file, complaining about access permissions. I am not aware of having changed anything related to this issue.

I last used LibreOffice (successfully) one week ago.

[SIZE=3]Important information[/SIZE]

[LIST]
[*]Ubuntu 22.04
[*]LibreOffice 7.4.1.2
[*]LibreOffice installed through flatpak
[/LIST]
[SIZE=3]Details about the error[/SIZE]

LibreOffice opens OK, but when trying to open a document or spreadsheet, it gives the error:
> The lock file could not be created for exclusive access by LibreOffice, due to missing permission to create a lock file on that file location or lack of free disk space.

Select Notify to open read-only and get notified when the document becomes editable.
I get the choice of *Cancel* (which does as expected), *Open Read-Only* and *Notify*. If I select either of the latter two, it gives the error, "Write Error. The file could not be written."

Screenshots attached.

[SIZE=3]What I've checked and tried[/SIZE]

I definitely have enough space (home is on the same partition as root):
```
$ df --human /home
Filesystem                 Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu-root  465G  129G  313G  30% /
```
I uninstalled LibreOffice completely, including the configuration:
```
flatpak uninstall --delete-data org.libreoffice.LibreOffice
```
This correctly deleted the directory [FONT=courier new]~/.var/app/org.libreoffice.LibreOffice[/FONT].

I reinstalled LibreOffice:
```
flatpak install org.libreoffice.LibreOffice
```
I've checked that all files and directories within my home belong to me (both user and group), and that I have read-write access to all of them; both of the following commands return zero files.
```
find ~ -xdev ! '(' -group paddy -user paddy ')'
find ~ -xdev ! -perm /u+rwX
```
I even restarted the machine.

I've tried these several times.

I've been searching for an answer, but none of the proposed solutions that I've found seem to be relevant to me.

What can I do to diagnose and fix this, please?

---

