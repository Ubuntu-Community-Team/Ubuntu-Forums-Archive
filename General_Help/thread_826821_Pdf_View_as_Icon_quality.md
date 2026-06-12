---
title: "Pdf View as Icon quality"
date: 2008-06-12
forum: General Help
---

### Post by Robbyx on 2008-06-12
Is it possible to increase the pixel count of the icon that shows the pdf content in nautilus?

NB
It is possible to see the contents of the pdf if the view as icon is chosen. Unfortunately it has a very low definition. Idealy I would like to be able to expand up the icon so that I could read it.

---

### Post by ibuclaw on 2008-06-12
You can open the file with the app "Document Viewer", you know.
This is usually the set default, so you just double-click on the file.

Or if you prefer Adobe Reader, you can install it from the medibuntu repository.

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
Then run
```
sudo apt-get update && sudo apt-get install acroread
```

Regards
Iain

---

### Post by Robbyx on 2008-06-12
> **tinivole said:**
> You can open the file with the app "Document Viewer", you know.
This is usually the set default, so you just double-click on the file.

Or if you prefer Adobe Reader, you can install it from the medibuntu repository.

```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -

```
Then run
```
sudo apt-get update && sudo apt-get install acroread
```

Regards
Iain
 
Thank you for that helpful response.

I am trying to avoid having to rename each scanned document by being filing into appropriate folders and clearly viewing the contents of a pdf from the small incon that appears next to the listing in Nautilus. That is why I asked if the icon pixel count could be increased so that it would be easier to read when enlarged.

I am sure somewhere there is a setting that increases the pixel size of an icon.

I am sure a lot of people using their computers as a filing system would lke to be able to read the icon without opening the file.

---

### Post by ibuclaw on 2008-06-12
Ah, OK. Well I'm not too sure on that then.

I know there is a zoom in feature, but it won't help you if you want to read actually text from the file. Although, you can recognise book covers easier (see caption).

Regards
Iain
[[IMG]http://img136.imageshack.us/img136/2418/screenshotcfilebrowserel9.th.png[/IMG]](http://img136.imageshack.us/my.php?image=screenshotcfilebrowserel9.png)

---

### Post by Vivaldi Gloria on 2008-06-12
> **Robbyx said:**
> Is it possible to increase the pixel count of the icon that shows the pdf content in nautilus?

Start gconf-editor. Goto

> desktop > gnome > thumbnailers > application@pdf

In the command

```
evince-thumbnailer -s %s %u %o
```

put the size you want after -s. That should do it. See also

```
man evince-thumbnailer
```

If this doesn't work then it means that the setting

> apps > nautilus > icon_view > thumbnail_size

in gconf-editor overrides the evince-thumbnailer settings and I don't know what to do then.

---

### Post by Robbyx on 2008-06-12
Thank you. That might be what I want. At the moment I am not clear how to make the alteration. I tried a change and that stopped the ability to read any pdf thumbnails. I put in the following:

evince-thumbnailer -s900 %s %u %o

I would like to be able to scale the thumbnail upto a full page. Is that possible? Could you correct the syntax for me? I have been using Ctrl-Wheel to scale up the thumbnail.

Robin

---

### Post by Vivaldi Gloria on 2008-06-12
> **Robbyx said:**
> Thank you. That might be what I want. At the moment I am not clear how to make the alteration. I tried a change and that stopped the ability to read any pdf thumbnails. I put in the following:

evince-thumbnailer -s900 %s %u %o

I would like to be able to scale the thumbnail upto a full page. Is that possible? Could you correct the syntax for me? I have been using Ctrl-Wheel to scale up the thumbnail.

Robin

Try 


```
evince-thumbnailer -s 128 %s %u %o
```

first. I have never used this and I have completely shut-off pdf thumbnail generation so I cannot try it myself. You'll have to try it yourself. I am not sure about the correct syntax either. It could be -s n or -s nxm. The man page is not very helpful. I suggest you google for something like "evince-thumbnailer size".

Also keep in mind that changed settings only apply to those files whose icon doesn't already exist in your 

```
/home/your_user_name/.thumbnails
```

folder. But it is safe to delete the icons in that folder.

---

### Post by Robbyx on 2008-06-12
If you come across an application that will selectively enlarge the thumbnail when viewing please let me know. The evince thumbnail setting only allows limited expansion in practice. Setting it to 400 is better than the default, but Within nautilus ctl wheel enlarges all the thumbnails not just the one being viewed.

---

