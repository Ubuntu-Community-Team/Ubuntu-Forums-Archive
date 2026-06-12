---
title: "Anyway to add the KDE or Debian menus to gnome"
date: 2004-10-30
forum: General Help
---

### Post by united on 2004-10-30
I install KDE for some of it's programs but use gnome. I would like to have the KDE or the Debian menus added to the gnome menu structure. How do I do this.

John

---

### Post by siacs on 2004-10-31
Here is a how-to that I have used before it was either with 2.4 or 2.6 or both.
I haven't tried with 2.8 but here it is

1) go to, "/usr/share/gnome/vfolders"

2) make a text file in that folder, name it "KDE.directory"

3) copy and paste, or type the below into it,

[Desktop Entry]
Name=KDE
Comment=KDE Applications
Icon=apple-red.png
Type=Directory

4) go to "/etc/gnome-vfs-2.0/vfolders"

5) open the file "applications-all-users.vfolder.info" in a text editor and add 
this ABOVE the last two lines

<!-- KDE-->
<Folder>
<Name>KDE</Name>
<Desktop>KDE.directory</Desktop>
<ParentLink>/opt/kde/share/applnk</ParentLink>
</Folder>

so in other words the bottom of the file will look like this below.

<!-- KDE-->
<Folder>
<Name>KDE</Name>
<Desktop>KDE.directory</Desktop>
<ParentLink>/opt/kde/share/applnk</ParentLink>
</Folder>

</Folder>
</VFolderInfo>


i DONT know what the two last lines are called. but i'm sure they are very 
important.


you logout and back in and find a red apple in the Applications menu with the 
kde menu inside.

of course you can use any icon and change the language. this is a just a 
starting point for you.

If it doesn't work with 2.8 maybe someone will know more and fix this how -to so everybody can benifit
Lets us know how it turns out>

---

### Post by rupert on 2004-10-31
you have to change /opt/kde into /usr/share/applnk
Open Office is twice now, but it doesnt matter.

In the new configs for 2.8 are no paths,
I have installed some universe apps that dont show up,
so i added a path to the games menu for example but it didnt helped.

---

### Post by united on 2004-10-31
Thanks for the code. It does work with /usr/share/ . . however there is only a few app links in that menu structure. 

This does point me in the correct direction and now I just need to find the mother load so to speak.

John

---

