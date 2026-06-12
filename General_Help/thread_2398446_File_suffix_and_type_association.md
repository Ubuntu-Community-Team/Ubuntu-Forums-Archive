---
title: "File suffix and type association"
date: 2018-08-12
forum: General Help
---

### Post by corradoventu on 2018-08-12
SweetHome3D uses files with suffix .sh3d but having internally a Zip format.
On one partitions on my PC I have SweetHome3D installed via deb package, on a different partition I have the snap version of SweetHome3D. Both partitions are in Ubuntu Cosmic.
For the deb version the default application for .sh3d files is SweetHome3D while for the snap version the default is ArchiveManager.
If I select FileProperties-OpenWith for a .sh3d file 
on the 1st install (deb) I see:   Select an application to open "casa.sh3d" and other files of type 'Sweet Home 3D'
while on the 2nd install (snap) I see: Select an application to open "casa.sh3d" and other files of type 'Zip archives'
I understand that the type 'Zip archives' comes from the internal format of the file, but this is overridden some part to force type 'Sweet Home 3D'
Where is written that .sh3d is of type 'Sweet Home 3D' and not 'Zip archives'?

---

### Post by &amp;KyT$0P# on 2018-08-12
[FONT=Courier New]/usr/share/mime/packages/sweethome3d.xml[/FONT]

If you only need the change for one user, you can create a directory [FONT=Courier New]~/.local/share/mime/packages[/FONT] and put this file there.  If you need it system-wide it goes in [FONT=Courier New]/usr/share/mime/packages[/FONT] .

For the contents of this file to take effect, you'll need to run -
```
update-mime-database [COLOR="#FF0000"]<MIME directory you modified>[/COLOR]
```
where the "MIME directory" is the folder containing the [FONT=Courier New]packages[/FONT] folder, e.g. if you put the file in [FONT=Courier New]~/.local/share/mime/packages[/FONT] the MIME directory is [FONT=Courier New]~/.local/share/mime[/FONT]
Refer to [FONT=Courier New]man update-mime-database[/FONT] for more info

---

### Post by mc4man on 2018-08-12
I would think the snap has to provide that mime association (it doesn't..
So maybe take the .deb's .xml & put it in youe ~/snap/sweethome3d-homedesign/4/.local/share/mime/packages/ folder and see, 
If no good start an issue in snapcraft.io forum

---

### Post by corradoventu on 2018-08-13
copied the .deb's .xml to ~/.local/share/mime/packages and issued command:
corrado@corrado-HP-p5-cc-0731:~$ update-mime-database ~/.local/share/mime
... now it works. 
thanks a lot

opened an issue in snapcraft forum: [https://forum.snapcraft.io/t/sweethome3d-does-not-create-usr-share-mime/6839](https://forum.snapcraft.io/t/sweethome3d-does-not-create-usr-share-mime/6839)

---

### Post by corradoventu on 2018-08-13
copied to ~/snap/sweethome3d-homedesign/4/.local/share/mime
but update-mime-database results in:
corrado@corrado-HP-p6-cc-0801:~$ update-mime-database ~/snap/sweethome3d-homedesign/4/.local/share/mime
Note that '/home/corrado/snap/sweethome3d-homedesign/4/.local/share' is not in the search path
set by the XDG_DATA_HOME and XDG_DATA_DIRS
environment variables, so applications may not
be able to find it until you set them. The
directories currently searched are:

- /home/corrado/.local/share
- /usr/share/ubuntu
- /usr/local/share
- /usr/share
- /var/lib/snapd/desktop

corrado@corrado-HP-p6-cc-0801:~$

---

