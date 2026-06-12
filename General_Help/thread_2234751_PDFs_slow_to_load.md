---
title: "PDFs slow to load"
date: 2014-07-16
forum: General Help
---

### Post by humanracer on 2014-07-16
Hi
I downloaded some books from google but when I load the file after downloaded it takes a good minute before each page loads (most also have pictures). I don't have a lot of RAM. Does that have something to do with it?

Is there anyway I can go through the pages seamlessly?

---

### Post by grahammechanical on 2014-07-16
Not a lot of RAM? Yes, that most certainly has something to do with it. Another thing that will cause this is if the PDF document is made of scanned images. I have a couple of PDFs of old books where every page is a scanned image and with only 1GB of RAM they do take a time to load. I am guessing that the pages are loaded in and out of RAM as I move through the book.

Regards.

---

### Post by humanracer on 2014-07-16
Thanks for the reply Graham

Yes they are all scanned books. I have under 4gb of ram so I think it probably means I just have to be patent when moving through the pages.

---

### Post by Impavidus on 2014-07-16
If under 4GB means about 3GB your specs are still quite decent. You could try other PDF readers if you wish. It might improve things somewhat, but don't expect miracles.

---

### Post by at_first_light on 2014-07-17
You mentioned not having much ram, but if the pdf isn't too big you should be able to spare enough to create a ramfs. You can then dump the pdf file into the ramfs and open it from there. As other's have suggested you might want to install a different PDF viewing application too; I would recommend qpdfview which is pretty lightweight. 

[SIZE=4]_**Steps:**_[/SIZE]

_Create A Ramfs:_
1. Make a folder to mount in your ram. The command below will create a folder called ramdrive in your current user's home directory.
```
mkdir ~/ramdrive
```

2. Create the ramfs. The command below will give 50MiB to ramfs you will need to adjust this depending on how big your pdf file is.
```
sudo mount -t ramfs -o size=50m ramfs ~/ramdrive
```

3. Change the owner of the folder from root to your user. You will need to substitute "username" for your user's name.
```
sudo chown -R username:username ~/ramdrive
```

_Get Rid Of The Ramfs:_
1. Unmount the ramfs. Any files in it will be deleted.
```
sudo umount ~/ramdrive
```

2. Delete the folder. It must currently be empty.
```
rmdir ~/ramdrive
```

---

### Post by humanracer on 2014-07-21
Thanks I will try the ramfs and the alternative PDF viewers. I noticed when I turned off thumbnails, it seemed to speed it up a bit.

---

