---
title: "Ubuntu 16.04 - How To Add Picture To Folder Thumbnail"
date: 2017-02-22
forum: General Help
---

### Post by AngelOfNorath on 2017-02-22
I have been searching for days how to add picture to my folders. And I am not referring only to the Ubuntu folder. Even that my external HHD has thumbnails in all of it's folders, when I connect him to the Ubuntu, none of them appears. 

If I haven't been clear enough, this a picture of what I want to achieve ( [https://i.stack.imgur.com/P60Cz.jpg](https://i.stack.imgur.com/P60Cz.jpg) ) 

Obviously this image is taken from Windows OS, but can it be done in Ubuntu? 

Thank you

---

### Post by howefield on 2017-02-22
Check the settings in Files > Preferences > Search and Preview tab > thumbnails.. anything in there ?

---

### Post by AngelOfNorath on 2017-02-22
I found the: Edit->Preferences-->Preview Tab. It has a option to Show thumbnails for files (depending on the size) but nothing for folders. Even when I messed around with the options, nothing changed. Neither to the ubuntu folders or the external driver folders.

---

### Post by howefield on 2017-02-22
To be honest, rereading your post again, I think I have misunderstood what you wanted.

You want the actual folder to show a preview image of what's inside ?

---

### Post by AngelOfNorath on 2017-02-22
As I wrote to my first post, this is what I want: [COLOR=#000000] [/COLOR][https://i.stack.imgur.com/P60Cz.jpg](https://i.stack.imgur.com/P60Cz.jpg)[COLOR=#000000]  . 
You know when you are in Windows OS and inside a folder you put a picture with the name "Folder"? And then the Folder's thumbnail has this picture? I want this for my Ubuntu. The thing is that all my folders of my external HDDs have this, and now in Ubuntu I see none of them, making it hard to choose the folder I want. (Now I have to read the name, when I was used to just look @ the image).[/COLOR]

---

### Post by howefield on 2017-02-22
> **AngelOfNorath said:**
> You know when you are in Windows OS and inside a folder you put a picture with the name "Folder"?

No, I'll take your word for it.

Would something like the attached image be of any use, showing two folders inside ~/Pictures as image icons ?

[ATTACH=CONFIG]273838[/ATTACH]

---

### Post by AngelOfNorath on 2017-02-22
Kind of... Could I use only one image for that you send? If yes, it could be a nice alternative. If I asked for a similar icon to that of the Windows, would it be much?

---

### Post by #&amp;thj^% on 2017-02-22
Sorry for passing through here... but maybe something like this?

---

### Post by AngelOfNorath on 2017-02-22
Oh, this looks like a Windows theme. Take for example this picture to understand exactly what I mean. 

Lets take for example this picture of Liszt. Lets suppose that inside that folder I have his music.  

[ATTACH=CONFIG]273853[/ATTACH]

If I put this picture inside that folder and renamed it to "Folder",
[ATTACH=CONFIG]273854[/ATTACH]

then the folder automatically would look like this:
[ATTACH=CONFIG]273855[/ATTACH]


That's what I am looking for. Or at least something similar.

---

### Post by #&amp;thj^% on 2017-02-22
Ahh! understood now....That is doable but you yourself would have to customize each folder you wanted to appear that way.
in other words...there is no automatic way to show what you are after...well that I know of anyway.
Some Tips For customizing your Folders: [http://askubuntu.com/questions/419969/any-way-to-change-the-default-folder-icon](http://askubuntu.com/questions/419969/any-way-to-change-the-default-folder-icon)

---

### Post by AngelOfNorath on 2017-02-22
&#927;h! Yes, I found it, it works. It literally replaces the folder icon with the picture you choose. (And that is kind of a problem... &#921; mean, the combination of picture/folder would make things easier... But I guess I am asking for too many things.) Any idea if another File Manager can do such a thing automatically? (Doing it for hundreds of folder it more of a punishment than organizing...)

---

### Post by #&amp;thj^% on 2017-02-22
> (Doing it for hundreds of folder it more of a punishment than organizing...)
Amen to that my friend :lol:. I know what you mean! It is a huge time consumer to be sure.
None of the file managers that I am aware of do this automatically on Linux....yet. (11 Year linux user)
Kind Regards

---

### Post by AngelOfNorath on 2017-02-22
Too bad... pfff until I have an answer now. This thing bugged my mind for days! I couldn't find a solution. Anyway, thanks for you time! I appreciate your help!

---

### Post by howefield on 2017-02-23
> **AngelOfNorath said:**
>  (Doing it for hundreds of folder it more of a punishment than organizing...)

The effect I showed in post number 6 was from a script called Cover Thumbnailer, it works with Music and Pictures folder, not sure about Video folder. It automatically takes a "selection" of images from your images and creates a folder icon from them, apparently there are extensive preferences that can be tweaked but I didn't explore them.
> 
**Cover Thumbnailer** is a small Python script which displays music album's covers and a preview of pictures which are in a folder in **nautilus**, the GNOME's file browser. Cover Thumbnailer generate the folder's thumbnail automatically, like any other thumbnailer ; you don't have to generate thumbnails manually.

Cover Thumbnailer is customizable (the is a lot of options). For configuring it, just launch its preferences GUI::

It seems quite old but does still work although perhaps not as elegantly as the images in your posts.

---

### Post by #&amp;thj^% on 2017-02-23
> **howefield said:**
> The effect I showed in post number 6 was from a script called Cover Thumbnailer, it works with Music and Pictures folder, not sure about Video folder. It automatically takes a "selection" of images from your images and creates a folder icon from them, apparently there are extensive preferences that can be tweaked but I didn't explore them.


It seems quite old but does still work although perhaps not as elegantly as the images in your posts.
+1 Nice find howefield :KS
Also if you are not comfortable with the script...There is a PPA you can add that has current builds from Ubuntu 9.04 to Ubuntu 16.10...seems to have some newer activity going on there.
[https://launchpad.net/~flozz/+archive/ubuntu/flozz](https://launchpad.net/~flozz/+archive/ubuntu/flozz)
Example:cover-thumbnailer     0.8.3-1~ppa1     Fabien LOISON **(2016-11-27) **
I had to log out and back in again to get it to function...but it works well and a bit more options than I would have thought
Just adding my findings is all.
Best Regards

---

### Post by howefield on 2017-02-23
Thanks 1fallen, only found the the script for 0.8.3 version but it did install very easily. A deb package is much preferable though :)

Extract the .tar.gz and from the extracted folder 

```
sudo install.sh --install
```

it quickly checks for installed dependencies and installs the script. You're are correct, a log out and log back in is required.

---

### Post by AngelOfNorath on 2017-03-10
Well, the Cover Thumbnailer is the best thing I can do. But it has it's problems. For example, the 1/3 of my whole music stills has that orange folder icon, while the other 2/3 changed and the selected imaged shows as it should. The weird thing is that when I copied the music folder to the desktop, the folder picture appeared as it should. My whole music is in an external driver and this leads me to the second problem. Even when I fixed some the folders without the right appearance, after unmounting  the driver and restarting my Ubuntu, all my changes were lost.

---

