---
title: "Own hosted website images not showing."
date: 2013-04-01
forum: General Help
---

### Post by zero2xiii on 2013-04-01
Hay all,

I am puzzled by this. I have created a very basic website, with a few images on the main page.
However loading the webpage from a browser on a remote server, the images simply do not load. Localy the site works perfectly.

All images are located in the "./images" folder:

```
.
&#9500;&#9472;&#9472; construction.html
&#9500;&#9472;&#9472; contact.html
&#9500;&#9472;&#9472; images
&#9474;   &#9500;&#9472;&#9472; bak
&#9474;   &#9474;   &#9500;&#9472;&#9472; pic1.jpg.bak
&#9474;   &#9474;   &#9500;&#9472;&#9472; pic2.jpg.bak
&#9474;   &#9474;   &#9500;&#9472;&#9472; pic3.jpg.bak
&#9474;   &#9474;   &#9492;&#9472;&#9472; pic4.jpg.bak
&#9474;   &#9500;&#9472;&#9472; img01.gif
&#9474;   &#9500;&#9472;&#9472; img02.gif
&#9474;   &#9500;&#9472;&#9472; pic1.jpg
&#9474;   &#9500;&#9472;&#9472; pic2.jpg
&#9474;   &#9500;&#9472;&#9472; pic3.jpg
&#9474;   &#9492;&#9472;&#9472; pic4.jpg
&#9500;&#9472;&#9472; index.html
&#9500;&#9472;&#9472; Site.zip
&#9492;&#9472;&#9472; style.css

```

The graphics are loaded in the two following manners. (the full adress way is only for debugging purposes.)
```
<div id="splash"> <img src="http://www.invisibleforceproductions.co.za/images/pic1.jpg" alt="" height="295"
          width="1180"> </div
```

```
<li class="first"> <img class="alignleft"
                  src="images/pic2.jpg" alt="" height="60" width="60"> <span>We

                  base all business we do on:</span></li>
```

Neither the full, nor the relative path produces the graphics.
The folder permissions are 0644
The file permissions are 0644
This is true for all the graphics and main files. I do not understand what might be the cause of this.

Please advise.

---

### Post by mcduck on 2013-04-01
All the images on the site seem to be working fine for me, so I assume you have already fixed the problem?

---

### Post by zero2xiii on 2013-04-01
Hay,

Some what. I dropped all the images in the root folder, and changed the paths to look only in the current directory.

I will upload a "test" page that will be coded as it is suppose to work.

The test page can be found here:
[www.invisibleforceproductions.co.za/test.html]("http://www.invisibleforceproductions.co.za/test.html")

Cheers

EDIT:
Seems like I found the problem. Seemingly the "execute" permission should also be set for the images to load.
Changing the folder permissions to 0755 allowed the pictures to be loaded. Is this correct, and secure? I thought read permissions are the only ones needed?
Also now the entire ./images/ directory can be listed, which I definitely do not want...

EDIT 2:
Seems like I have solved the issue. Had to turn off the public indexing. Still not sure why the executable flag allows the images to load. But it is working now. Marking the thread as solved... Need to sharpen my apache knowledge it seems... Along with it's file permissions....

---

### Post by mcduck on 2013-04-01
oh, that's a good point, you need to have execute permission on directories to be able to access their contents. You shouldn't need execute permission on the images though.

(permissions on directories are slightly different from the ones used on files, the "execute" is often called "search permission" as it's required to access the inode information of files and subdirectories. For example read permission allows you to list a directory's contents, but to cd into it or access the files using many tools you also need the execute bit to be set. And it also needs to be set for all the parent directories as well...)

---

### Post by zero2xiii on 2013-04-02
Oh I see,

Well now I have it working. Many thanks :)

Philip

---

