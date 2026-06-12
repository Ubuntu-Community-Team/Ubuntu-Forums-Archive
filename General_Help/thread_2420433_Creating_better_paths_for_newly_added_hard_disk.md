---
title: "Creating better paths for newly added hard disk"
date: 2019-06-05
forum: General Help
---

### Post by ubotbuddy on 2019-06-05
What is the best way to create mounted hard drives in such a way that they are easily accessible within the File window?


I have successfully added a couple of spinning hard disks to my Ubuntu 18.04 system (which is installed on a SSD).  Now I would like to figure out how to get the mounted drives with a single click rather than drilling into the file system.


Thanks


Buddy

---

### Post by SuperFreak on 2019-06-05
You could add links in your home directory and add them to the left menu in Nautilus[https://ubuntuhak.blogspot.com/2013/04/symbolic-links-in-ubuntu.html]("https://ubuntuhak.blogspot.com/2013/04/symbolic-links-in-ubuntu.html")(drag the link to the left Nautilus menu I believe is how it's done)

---

### Post by kpatz on 2019-06-05
Just go to the folder where your drive is mounted in nautilus and then drag it into the left bar, and it will be added to the list.

---

### Post by Dennis N on 2019-06-05
What I do is create several bookmarks for frequently used folders on my separate data disk. You have to navigate to those folders the first time, but once the bookmark is set, it's in the file manager side pane for direct access.

---

### Post by Impavidus on 2019-06-05
Put them in your [/etc/fstab](https://help.ubuntu.com/community/Fstab) to make them mount automatically when you boot Ubuntu. Then your filemanager won't even tell you it's a different device. They'll get integrated into your filesystem at whatever location you configured as mountpoint. Filemanagers support bookmarks for easy one-click access.

---

### Post by ubotbuddy on 2019-06-05
Thanks everyone.

Nautilus.  Hmmmm...from what I see I like what it looks like.  I'm currently setup with Nemo 4.0.6.  I did not see the ability to do Bookmarks within Nemo.  I did make a note of Nautilus though.  I'm trying to learn as I go so I had better not change too many things at once.

I do have my mounts setup in my /etc/fstab

Thanks

Buddy

---

### Post by kpatz on 2019-06-06
What version of Ubuntu are you running?  Nautilus is the default in 18.04.

---

### Post by Morbius1 on 2019-06-06
> I did not see the ability to do Bookmarks within Nemo. I did make a note of Nautilus though.

Are you sure you don't have that in reverse?

In Nemo: Nemo > Bookmarks > Add Bookmark

In Nautilus : Nautilus > Hamburger Icon Thingy on the right top side of Nautilus > Centre top icon thingy ( lordy, I hate what they've done to Nautilus )> Bookmark this location:
[ATTACH=CONFIG]283395[/ATTACH]

---

### Post by ubotbuddy on 2019-06-06
LOL  I know what you meant.

I'll check it out when I get home.

Buddy

---

### Post by ubotbuddy on 2019-06-07
Update:

After reading Morbius1 post that Nemo should have Bookmarks.  I went back to look in greater detail.  i was looking around for the hamburger icon and then it jumped out at me.  "Bookmarks" is actually on the menu bar to the left of Help.   DUH on me!  LOL

Nothing like being a noob.  lol

Buddy

---

### Post by deadflowr on 2019-06-07
If you've figured it out and the solution works for you,
please go ahead and [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

