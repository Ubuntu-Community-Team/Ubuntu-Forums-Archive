---
title: "How do I need to perform in order images to appear in Wallpapers dialog window?"
date: 2015-10-27
forum: General Help
---

### Post by abcuser on 2015-10-27
Hi,
using Ubuntu 14.04 I have downloaded plenty of wallpapers (jpg files) and saved them in /usr/share/background/ directory. I have set all files owner to root and permissions to 644 like other files in this directory. Then I have right clicked on desktop and selected Change Desktop Background. Appearance dialog opens up and in Look tab inside Wallpapers I expect to see this new images, but there are not available there. I have restarted computer with no effect on this Wallpappers drop down list.

I downloaded this files in order other users I have defined on computer can manually change the desktop wallpaper.

How do I need to perform in order images to appear in Wallpapers dialog window?
Thanks

---

### Post by tgalati4 on 2015-10-27
I am running MATE17 based on 14.04 and my backgrounds are stored in /usr/share/backgrounds/theme/*.jpg.

---

### Post by QDR06VV9 on 2015-10-27
For me Mint 17.2 and Mate 1.10.2 Stored in the same as tgalati4.
I know, picky picky!(lol)
Kind Regards

---

### Post by deadflowr on 2015-10-27
The image file names and locations need to be added to an .xml file in /usr/share/gnome-background-properties.
What I'd do, and have done, would be to simply open gedit and navigate to that folder, open the xml file for trusty wallpaper and edit it to.
Basically you need to change the fields for Name and filename.

Every entry will look something like this:
```
<wallpaper>
    <name>Backyard Mushrooms</name>
    <filename>/usr/share/backgrounds/Backyard_Mushrooms_by_Kurt_Zitzelman.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>
```
So only change the fields for name and filename.

***Optionally You can also change the options section, removing zoom and leaving it empty should give you all options like full and stretch.  
But you need to at least keep the <options></options> in there.
and you need to make sure not to remove any of the >, or </> parts.

It's rather tedious.

After you've made all your changes save it in your home folder, and then either copy it or move it into the gnome-background-properties folder using sudo.

Hope it helps, though it can seem rather convoluted sometimes.

---

### Post by abcuser on 2015-10-28
@tgalati4 and @runrickus, path /usr/share/backgrounds/theme/*.jpg does not exists in Ubuntu 14.04. Maybe this is MATE specific.

@deadflowr, your helps was extremely useful. Additional to your help I have figure it out that creating a new xml file in directory /usr/share/gnome-background-properties/ is also recognized by Wallpaper dialog. You know better adding a new file and having only my settings in it and leave original files intact.
So I did:
1. Copy trusty-wallpapers.xml file to my-wallpapers.xml
```
sudo cp trusty-wallpapers.xml my-wallpapers.xml
```
2. Opened newly created file and edited file according to your suggestion (deleting what was not needed).
```
gksudo gedit trusty-wallpapers.xml
```
3. Save the file.
4. Right click on desktop and select Change Desktop Background and there it is... new wallpapers appears in Wallpapers dialog.

Problem solved. Thanks a lot for help.

I am little bit surprised that adding wallpapers to Wallpapers dialog is so complicated.

---

