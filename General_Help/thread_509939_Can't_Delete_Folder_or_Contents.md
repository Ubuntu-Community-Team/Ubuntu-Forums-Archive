---
title: "Can't Delete Folder or Contents"
date: 2007-07-26
forum: General Help
---

### Post by adamd on 2007-07-26
I Just recently installed Ubuntu and then I installed Wine so I could play Steam and it didn't work so I followed every tutorial on how to delete Wine and I did (so I can reinstall it) but now I can't delete this folder or anything in it (Steam, Soldat, HotKeys, and Opera). Thanks a lot and here is an image of the folder if you need it.

The Folder is called Wine and you may need to zoom in on the image.

[http://s93.photobucket.com/albums/l63/adamd_2006/?action=view&current=Screenshot.png](http://s93.photobucket.com/albums/l63/adamd_2006/?action=view&current=Screenshot.png)

---

### Post by tbroderick on 2007-07-26
You are most likely looking for a .desktop entry. The might be in /usr/share/applications/.

You can use locate to find the files.

```
sudo updatedb
```

```

locate *.desktop
```

---

### Post by adamd on 2007-07-26
Thanks for the quick response, but there was nothing in /usr/share/applications/. Also, I am very new to this whole thing and don't really understand it that well, so could you tell me where to put in those codes? I think it's in the terminal but am not 100% sure. Also I don't think I am going to find them because I don't think they are actually there. Like when I click on them absolutely nothing happens. I think they got deleted but somehow the icons didn't get deleted. Thanks a lot.

---

### Post by tbroderick on 2007-07-26
Yeah, in a terminal. The obivious place is /usr/share/applications, but they could be in some variant, /usr/share/mimelnk/applications. It's easier to use locate, but first you have to update the database. Open a terminal and run the first command, it might take 30-40+ seconds to complete. Then use the second command to look for anything that matches. Also try other search strings like
```
locate wine
locate steam
```

---

