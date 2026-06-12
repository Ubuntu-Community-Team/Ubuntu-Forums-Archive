---
title: "Plex not seeing content on second hard drive."
date: 2015-10-13
forum: General Help
---

### Post by GameGuru on 2015-10-13
I just switched from Windows again to Ubuntu 15.04 installed on my Samsung 250GB Evo SSD and had all my movies and television on my 2TB WD mechanical drive formatted as FAT32.  Installed Plex Media Server, it sees the 2TB drive but no folders or content.  Thinking it was because of the FAT32 I backed everything up and reformatted as Linux Journal, copied everything back but Plex still doesn't see anything on it.  What do I have to do to get Plex to see my media's on this drive?

---

### Post by ajgreeny on 2015-10-13
Several possible answers at [http://askubuntu.com/questions/395291/plex-media-server-wont-find-media-external-hard-drive](http://askubuntu.com/questions/395291/plex-media-server-wont-find-media-external-hard-drive) and I will be interested to hear if they work or not.

Keep trying and please report back any success.

---

### Post by GameGuru on 2015-10-16
Ok my second hard drive was mounting but it was not being seen by Plex so someone walked me through how to fix it but now the drive doesn't mount and I can't add anything to it.  Plex can still access everything on it and I can only see it if I click it's "Mounted at" link in disks.  What did I do to screw it up?  Here is information on the drive:

Here is what disks says:

[IMG]http://i60.tinypic.com/18g6qb.png[/IMG]

This is what nano shows:

[IMG]http://i58.tinypic.com/2r6dv2g.png[/IMG]

It's the 2TB drive I mounted with help from users so that Plex would see the drive.

This is what fdisk shows:

[IMG]http://i57.tinypic.com/2n9e4nk.png[/IMG]

What do I need to do so that this disk is auto mounted?  I am a newb when it comes to Ubuntu/Linux but I am trying to learn so please explain it like I am new.  Thanks in advance.

Oh an if I need to format the second hard drive fresh to fix this I am fine with that, I don't have much on it.  I just need it to auto mount so I can add to it and I need Plex to be able to see it.  Thanks again.

Oh and this is my blkid if you need it:

[IMG]http://i58.tinypic.com/107rpdv.png[/IMG]

Thanks again to anyone who can help!

Ok I am doing some more reading and tried to mount it but it says it is already mounted or busy:

[IMG]http://i58.tinypic.com/xqhxko.png[/IMG]

As you can see nothing is telling me it is mounted, isn't showing up in task bar, file viewer or desktop.  Not being skilled in Ubuntu this is killing me ha ha.

[IMG]http://i59.tinypic.com/168euq0.png[/IMG]

Ok I am doing some more reading and tried to mount it but it says it is already mounted or busy:

[IMG]http://i58.tinypic.com/xqhxko.png[/IMG]

As you can see nothing is telling me it is mounted, isn't showing up in task bar, file viewer or desktop.  Not being skilled in Ubuntu this is killing me ha ha.

[IMG]http://i59.tinypic.com/168euq0.png[/IMG]

Ok installing proprietary driver now, I will let you know how it goes.

That did it, thanks!

---

### Post by ajgreeny on 2015-10-16
Please do not add large images to your posts as you have done here.  Use thumbnails which you can add using the paperclip in the toolbar of the reply box, though not if you use the **Quick-reply** box; you need to use **Go advanced**.

Your plex problem, however, is most likely a permissions problem.  See the possible answers at:-
[http://askubuntu.com/questions/395291/plex-media-server-wont-find-media-external-hard-drive](http://askubuntu.com/questions/395291/plex-media-server-wont-find-media-external-hard-drive)
[http://askubuntu.com/questions/537154/plex-media-server-cannot-seem-to-find-data-on-my-disks](http://askubuntu.com/questions/537154/plex-media-server-cannot-seem-to-find-data-on-my-disks)
[http://ubuntuforums.org/showthread.php?t=2087341](http://ubuntuforums.org/showthread.php?t=2087341)

Good luck; I hope one of those helps.

---

### Post by GameGuru on 2015-10-16
Thanks for the reply ajgreeny.  Sorry about the images.  

Plex works fine, I am just not getting access to the second hard drive to add files to it.  It is not showing up as mounted in the file explorer or in the side bar.  I can access it through Disks by clicking the mount point but for READ ONLY, can't add anything to the drive.

Plex can play what is already on there, I just can't add anything as it (files, create folders nothing).    Disks sees it, when I try to manually mount it it says it is already mounted but I can't see it in file explorer or anything.

---

### Post by Bucky Ball on 2015-10-16
And Threads Merged.

These are pretty much about the same thing. All the info is already here so just keep going. If you don't get a response for 12 or so hours, simply post 'bump'.

---

