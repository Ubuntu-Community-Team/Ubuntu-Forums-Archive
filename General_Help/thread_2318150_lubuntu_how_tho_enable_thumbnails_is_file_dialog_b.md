---
title: "lubuntu how tho enable thumbnails is file dialog boxes"
date: 2016-03-23
forum: General Help
---

### Post by Chelidze on 2016-03-23
I want to enable thumbnails in file dialog boxes.

right now it only shows the file name and file type icon.

So how can i enable thumbnails ?

---

### Post by vasa1 on 2016-03-23
> **Chelidze said:**
> I want to enable thumbnails in file dialog boxes.

right now it only shows the file name and file type icon.

So how can i enable thumbnails ?What do you mean by "file dialog box"? Can you explain or post a screenshot?

---

### Post by QIII on 2016-03-23
Are you asking about displaying previews of image files in your GUI file manager?

---

### Post by Chelidze on 2016-03-23
I apologizing for not providing enough information.

This is what i am talking about 
[http://i.imgur.com/KJv5bDU.png](http://i.imgur.com/KJv5bDU.png)

as you can see there are icons but not thumbnails.

So can i have thumbnails in that menu.

---

### Post by vasa1 on 2016-03-23
What are your settings in File Manager > Preferences?

---

### Post by Chelidze on 2016-03-23
It shows the thumbnails in file explorer but doesn't in the open file menu, example

[ATTACH=CONFIG]267953[/ATTACH]

---

### Post by vasa1 on 2016-03-23
> **Chelidze said:**
> It shows the thumbnails in file explorer but doesn't in the open file menu, example
...
Yes, although the "open" dialogs of some applications offer individual previews in a pane on the right hand side. But not thumbnails.

---

### Post by Chelidze on 2016-03-23
That application is chrome but i have exactly same issue on firefox as well

---

### Post by QDR06VV9 on 2016-03-23
This is not the best solution but will get you what you want.
```
sudo apt-get install konqueror
```
  Yes this KDE package has many dependencies, but you will have what you want:

---

### Post by Chelidze on 2016-03-23
> **runrickus said:**
> This is not the best solution but will get you what you want.
```
sudo apt-get install konqueror
```
  Yes this KDE package has many dependencies, but you will have what you want:

Will not this just change the file explorer ? I have no problem with pcmanfm, i want thumbnails in chrome

---

### Post by Dennis N on 2016-03-23
I think the "Preview" pane in the open/save dialogs was provided to eliminate the need for thumbnails in the file list area of the dialog, so it is not going to be possible to have both. This kind of dialog you refer to (with preview pane) is only used from a graphics capable application like Gimp, GPicView or even Firefox when opening/saving an image file.

---

### Post by vasa1 on 2016-03-23
> **Chelidze said:**
> Will not this just change the file explorer ? I have no problem with pcmanfm, i want thumbnails in chromeDo you know of any other distro or DE that offers what you want because I suspect it doesn't have to do with individual apps.

---

### Post by Chelidze on 2016-03-23
> **vasa1 said:**
> Do you know of any other distro or DE that offers what you want because I suspect it doesn't have to do with individual apps.

I honestly never thought about it, it was just pointed out to my by a friend that asked me to help them with the PC, I installed light weight lubuntu instead of windows 8, there but now i am getting hammered buy such things :D, unity has the same menu in chrome and firefox. So i don't know should i give up on this ? I really don't want to install windows.

> **Dennis N said:**
> I think the "Preview" pane in the open/save  dialogs was provided to eliminate the need for thumbnails in the file  list area of the dialog, so it is not going to be possible to have both.  This kind of dialog you refer to (with preview pane) is only used from a  graphics capable application like Gimp, GPicView or even Firefox when  opening/saving an image file.

If there is a possibility to disable right side preview and have thumbnails it will be more than acceptable

---

### Post by vasa1 on 2016-03-23
If such a feature is really important, I see only two options: find an operating system that gives you everything you want or write the necessary code, compile software etc.

I find the preview system far more informative. Very often, telling two thumbnails apart isn't easy. I really don't care for them. I've turned them off in PCManFM and in LibreOffice as well.

---

### Post by mcduck on 2016-03-24
The file selection dialog doesn't grab it's settings from your file manager or anything like that, it only looks similar since it's based on the same toolkit. So changing between Nautilus, PCManFM, Thunar, Konqueror or something else has nothing to do with how the file selection window looks like in Chrome or Firefox.

The dialog window you see comes straight from GTK toolkit, and it supports preview, but it's up to each program's developers to turn it n or off. So if you don't get preview when selecting a file in Chrome, that's because Chrome's developers decided to not enable that option. The only thing you can do about it is to get source code for that program and edit it to enable the preview.

...most of the time programs only enable the preview if they only handle image files. So GIMP would display the preview since you can only select files where it makes sense, while your web browser doesn't since you are often selecting all kinds of files and the preview wouldn't work with most of them and would then just look odd and waste screen space. IN some programs it's of course possible to code in different settings based on what type of file youa re selecting, but when it comes to choosing files to upload something to a web service, for example, it's impossible for the browser to do that since it depends on the web page in question.

---

