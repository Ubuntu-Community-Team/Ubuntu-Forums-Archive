---
title: "Mapping folders windows/Linux"
date: 2008-04-30
forum: General Help
---

### Post by Pat L.I. on 2008-04-30
Hello, 
I have my laptop dual booting hardy and windows xp. I have ntfs-config installed properly to share between partitions all is working great! Cheers to the ubuntu community.

can anyone point me towards a tutorial to map my Linux Places/Documents to my Windows My Documents folders and vice versa. So that I can just drop files into the folders and use them between Operating systems.
Perhaps my searches havent been good enough but i keep coming up with stuff for just regular ntfs sharing.
thanks in advance!
Pat

---

### Post by SlalomMan on 2008-04-30
Alright...this is what I do. I use my NTFS partition for most of my documents and pictures, etc. Because windows isn't too friendly to ext3 :(. But anyway...all I did was navigate to the User folder on the NTFS partition in Nautilus and then create links to Pictures, Documents, etc. (My pictures/Documents if you're on XP). Then I renamed the Links to pictures or whatever and moved them to my home folder, overwriting my existing folders.

Make sure you move your files out of your old folders before you do this, though.

---

### Post by Maratonda on 2008-05-01
Hi,
before you did this:
> **SlalomMan said:**
> all I did was navigate to the User folder on the NTFS partition in Nautilus
did you have to mount the partition? I guess you had.
Because in this case, I suppose that your links wouldn't work afterwards on your home ubuntu documents if the partition isn't mounted, right?

---

### Post by stijngysemans on 2008-05-01
I used to have an external hard disk set up to store my music, pictures and documents.
This is a work around.

---

### Post by Pat L.I. on 2008-05-01
SlalomMan - Thank you for the responses, I used your method and it worked fine. Nice and Simple!

Maratonda - yes I imagine the links would not work if the partition isnt mounted. but this should not be a problem unless windows or ubuntu crashes or does not shut down properly. then you would have to mount manually.

stijngysemans - I have an external drive connected to a different laptop that i access over ssh but the reason I wanted to share the directories between partitions is mainly because my girlfriend uses the laptop in windows so I want her to be able to upload/download pictures / music, documents etc as easily as possible using the methods that she is used to as well as allow me access to them in an organized fashion within ubuntu.

thanks for the help!

---

### Post by Nepherte on 2008-05-01
You could symlink to the corresponding directory in your windows partition. Say for example that you have all your music on your windows partition, you can create a symbolic link in your linux home directory that points to your windows music map.

open up a terminal and type:
```
ln -s <target directory> <symbolic link name>
```

---

