---
title: "How to add 15.04 wallpapers to 14.04"
date: 2015-07-08
forum: General Help
---

### Post by geovino on 2015-07-08
How can you add Ubuntu 15.04 wallpapers to 14.04? I see old instructions went that was nautilus. Now its a different file manager (files). I have the images, I just want to get permission to add to usr/share/backgrounds.

---

### Post by dino99 on 2015-07-08
i suppose you can select wallpapers from feisty to vivid into synaptic; install what you wish, then go to System Settings > Appearance > background and apply after selecting the one you like

---

### Post by v3.xx on 2015-07-08
> Now its a different file manager (files).
Its still nautilus, just not as feature rich these days.
> I have the images, I just want to get permission to add to usr/share/backgrounds. 
Old school way
```
gksudo nautilus
```
New nautilus way
```
pkexec nautilus
```
Either way will give you the needed permissions.

---

### Post by geovino on 2015-07-08
> **v3.xx said:**
> Its still nautilus, just not as feature rich these days.

Old school way
```
gksudo nautilus
```
New nautilus way
```
pkexec nautilus
```
Either way will give you the needed permissions.

Thanks, but I get this error:

davek@OptiPlex-780:~$ pkexec nautilus
error: XDG_RUNTIME_DIR not set in the environment.

(nautilus:5608): Gtk-WARNING **: cannot open display: 
davek@OptiPlex-780:~$ sudo pkexec nautilus
[sudo] password for davek: 
error: XDG_RUNTIME_DIR not set in the environment.

(nautilus:5620): Gtk-WARNING **: cannot open display: 
davek@OptiPlex-780:~$

---

### Post by v3.xx on 2015-07-08
Ok, going to be a tough customer are you :)

Let just go to terminal.  I assume you have the background pics in your home folder.
```
sudo mv ~/name_of_folder_w/pics /usr/share/backgrounds/
```
I do not know whats going on with your file manager, should of worked.
Maybe start a thread on it.

---

### Post by geovino on 2015-07-08
Thanks did that, but now It still won't let me move pics out of the folder to add to the rest in the /usr/share/backgrounds folder.

I'll just pull from my pictures folder instead, too much trouble for something that's not important.

---

### Post by v3.xx on 2015-07-08
You can use the move command again.

```
sudo mv /usr/share/backgrounds/name_of_folder/name_of_pic /usr/share/backgrounds/new_folder_name/
```

---

### Post by v3.xx on 2015-07-08
> I'll just pull from my pictures folder instead, too much trouble for something that's not important. 						
Thats what I do.  I set up a ~/.mybackgrounds for the ease of it.

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by grahammechanical on 2015-07-08
gksudo has been depreciated. It started with Ubuntu 14.04. Not only is it not installed by default any more but it does not work so well either. I use

```
sudo -H nautilus
```

That will also show error messages but it does give us a Files/Nautilus window with root/administrator privileges. The simplest and easiest way to get images to select as background images is to put the images in the Pictures folder and then in the Appearance utility change the panel from Wallpapers to Pictures.

I think that you will find that you need to do more than simply move the Vivid background images into /usr/share/backgrounds. To get the images to show up in the panel that shows the background images you will need to edit an xml file.

Go to /usr/share/gnome-background-properties/ and you will see to xml files - ubuntu-wallpapers.xml and trusty-wallpaper.xml. Examine trusty-wallpapers.xml. The listing of the images in that file is what makes it possible for the background images to appear in the Appearance utility. A sample of the markup. It is from vivid-wallpapers.xml.
> 
 <wallpaper>
     <name>150305-cinqAA</name>
     <filename>/usr/share/backgrounds/150305-cinqAA_by_Pierre_Cante.jpg</filename>
     <options>zoom</options>
     <pcolor>#000000</pcolor>
     <scolor>#000000</scolor>
     <shade_type>solid</shade_type>
 </wallpaper>
 <wallpaper>
     <name>Cedar Wax Wing</name>
     <filename>/usr/share/backgrounds/Cedar_Wax_Wing_by_Raymond_Lavoie.jpg</filename>
     <options>zoom</options>
     <pcolor>#000000</pcolor>
     <scolor>#000000</scolor>
     <shade_type>solid</shade_type>
 </wallpaper>

The information for each image is enclosed in <wallpaper></wallpaper> code tags. You need to edit trusty-wallpapers.xml to contain references to the vivid background images.

To edit these system files I use

```
sudo -H gedit
```

But there is something to watch out for. Gedit will automatically create a backup file with the same name as the original but with the tilde character ( ~ ) pre-pended to the front of the file name. The tilde character makes the file a hidden file but it will still be read by the system and the existence  of these hidden files complicates the presentation of the background images by the Appearance utility.

I am using wily werewolf (15.10). It still has the 15.04 background images. If I was to copy all the 14.04 background images into /usr/share/backgrounds/ and then copy trusty-wallpapers.xml into /usr/share/gnome-backgrounds-properties/ I would do what you are trying to do but in reverse.

If I was to copy trusty.xml from /usr/share/backgrounds/contest/ into the contest folder of my present installation I would get two slide shows. The vivid and the trusty slide show.

Regards.

---

### Post by v3.xx on 2015-07-08
> sudo -H nautilus
Thats good to know, thanks.

---

