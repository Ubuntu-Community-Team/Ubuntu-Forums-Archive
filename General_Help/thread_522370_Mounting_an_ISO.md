---
title: "Mounting an ISO"
date: 2007-08-10
forum: General Help
---

### Post by Harkainos on 2007-08-10
I am looking for the method to mounting an ISO.
I tried the man pages on it, but it is all greek to me.

Also is there a generic script for mounting/unmounting an iso when loading a game?

---

### Post by UK-Wobbie on 2007-08-10
> **Harkainos said:**
> I am looking for the method to mounting an ISO.
I tried the man pages on it, but it is all greek to me.

Also is there a generic script for mounting/unmounting an iso when loading a game?
Have a go on AcetoneISO2 [http://www.acetoneteam.org/download.html](http://www.acetoneteam.org/download.html) :)

---

### Post by capink on 2007-08-10
To mount iso:

```
sudo mount -o loop -t iso9660 /path/to/the/iso/file.iso /mnt
```

---

### Post by UK-Wobbie on 2007-08-10
> **capink said:**
> To mount iso:

```
sudo mount -o loop -t iso9660 /path/to/the/iso/file.iso /mnt
```

I did not no you can do things like that on Ubuntu lol :)

---

### Post by yellowband on 2007-08-10
you can mount tons of filesystems in linux, many natively i might add.

---

### Post by Harkainos on 2007-08-11
how would I put that in a script:

Basically

[Desktop Entry]
Encoding=UTF-8
Name=Game Name
Name[hr]=Game Name
Exec=sudo mount -o loop -t iso9660 /path/to/the/iso/file.iso /mnt
Exec=wine /path/to/the/executable.exe
Icon=/path/to/the/icon.ico
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false
ExeconExit=sudo unmount -o loop -t iso9660 /path/to/the/iso/file.iso /unmnt

Obviously this isn't exact, and probably not correct. Can a pro fix it? That way we can get a general script to do this.

---

### Post by capink on 2007-08-11
If I understand what you want correctly that would be the way to do it:


1. Create a mount point in wine tree

```
mkdir "~/.wine/drive_c/Program Files/game name"
```

2. Open an empty text file and create the following script, and rename it as you wish:

```

#!/bin/bash

gksudo mount -o loop -t iso9660 /path/to/the/isofile.iso "~/.wine/drive_c/Program Files/game name" &
wait
wine "c:\Program Files\game name\game_executable.exe"
```


3. Make the script executable using the following command:

```
chmod a+x /path/to/the/script
```

4. Create a launcher using you favorite text editor:

```
sudo gedit /usr/share/applications/game_name.desktop
```

and copy the following into the file:

```
[Desktop Entry]
Encoding=UTF-8
Name=Game Name
Name[hr]=Game Name
Exec=/path/to/the/script
Icon=/path/to/the/icon.ico
Terminal=false
Type=Application
Categories=Application;Game;
StartupNotify=false
```


I don't have experience with wine. And unfortunately I don't have any iso files right now to try this script out. So report back and I will try to help if I can.

---

### Post by Harkainos on 2007-08-12
I like it... I like it alot. 

I will try and tweek it and see where we come to.

If someone else has any other ideas, feel free to add.

---

