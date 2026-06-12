---
title: "Image Management under LINUX"
date: 2006-08-17
forum: General Help
---

### Post by bluntu on 2006-08-17
Wow, it took me about 2 weeks to know my way around Ubuntu. I can now set things up on my own now with the help of this forum so it's time to get back to work and to really use Ubuntu.

Being someone who works with images I find it very difficult to use LINUX for image management. One software that I missed most is PicaView, it's an awsome little utility that whenever you right click on an image you will see a small thumbnail preview. By clicking on it, it will brings you a bigger version of it and it's very useful when you're cleaning up images. I'm wondering if there's such tool for LINUX.

One thing that slows me down is the inability to create a Folder on the right panel of the File browser. I am forced to right click on the parent folder and then create a new folder.

Overall, image management under Ubuntu is a little slow.

[edit]
**Future Ubuntu should have "View as Thumbnails", right now there are only "View as List" and "View as Icons" in the File Browser.**

---

### Post by IYY on 2006-08-17
**Picasa** is a powerful image manager from Google that's been recently ported to Linux.

You can get it here: [http://picasa.google.com/linux/thanks-deb.html](http://picasa.google.com/linux/thanks-deb.html)

---

### Post by bluntu on 2006-08-18
Ok so I didn't give up and continued to explore Ubuntu's built-in Image Viewers and I am amazed!!

The answer to "PicaView (Window)" is... "GQview (Linux)". You can configurate GQview and remove everything and leave back just a Window. You can make this Window on top (a big plus!) and move them around if you like. You can select X images and it will only view those X images in one window. You can flip through your selected images (What picaview is all about).

Here's how it works in Windows:
You right click an image and you will see a small thumbnail. Then you click on that Thumbnail to view a larger version.

In Ubuntu:
You right-click (No thumbnail) then "Open With" ---> GQview.

The different between GQview and PicaView is that GQview doesn't have a thumbnail when you right click on it, other than that GQview is better than PicaView in my opinion.

Don't forget to play with the PREFERENCE.

---

### Post by orb9220 on 2006-08-18
"One thing that slows me down is the inability to create a Folder on the right panel of the File browser."

Are you talking nautilus? I can right click in right pane and create folder fine. Are you sure you are running in home if not you need to run a gdsudo nautilus.

---

### Post by kpkeerthi on 2006-08-18
> **IYY said:**
> **Picasa** is a powerful image manager from Google that's been recently ported to Linux.

Thanks for the update. I didn't know it has been "ported" to linux. The last time when I checked I learnt that it was just "wined". So never bothered to check it out.
And yes.. there is repo for ubuntu:
```

Add the following rule to e.g. /etc/apt/sources.list:

    # Google Picasa for Linux repository
    deb http://dl.google.com/linux/deb/ stable non-free

then use your package manager as usual, e.g.

    sudo apt-get update
    sudo apt-get install picasa 

```

**EDIT:** Just found that it still runs on wine. I'm not going to use it. Sorry guys.

---

### Post by MetalMusicAddict on 2006-08-18
Good to hear you gettin around. With some effort at the beginning it pays off big. :)

Im TOTALLY supprised to see nobody mention [F-Spot]("http://f-spot.org/Main_Page") (its in the repos). For managing large photo colections I see nothing better. I love it. You can even upload directly to a Flikr account if you have one.

Also, last I knew Picasa was "WINED" also.

---

### Post by Martin-Herrmann on 2006-10-04
Hi,

for all of you who are not just focused on a shiny surface ;) , but on a stable solution using standards (like IPTC) there is also Mapivi [http://mapivi.de.vu]("http://mapivi.de.vu").

Here are some hints how to install Mapivi for Ubuntu: [http://ubuntuforums.org/showthread.php?t=130912&highlight=mapivi]("http://ubuntuforums.org/showthread.php?t=130912&highlight=mapivi"), see posting #3 and #4.

Just my two cents. 

Regards,  Martin

---

