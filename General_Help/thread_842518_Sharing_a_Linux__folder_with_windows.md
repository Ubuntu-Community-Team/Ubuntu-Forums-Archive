---
title: "Sharing a Linux  folder with windows"
date: 2008-06-27
forum: General Help
---

### Post by Fatal Equinox on 2008-06-27
Hello,

How can i share/view my Ubuntu folders with windows.  I would like to be able to access my Ubuntu Linux folder in windows basically.  When i right-click and go though the properties>share tab,  i get an error 255 and it says i don't have permission and i need to do through administrator. How do i get around that because im on the only Ubuntu account.

Thank you

---

### Post by prshah on 2008-06-27
> **Fatal Equinox said:**
> 
How can i share/view my Ubuntu folders with windows.  I would like to be able to access my Ubuntu Linux folder in windows basically.


You need to install the ext2/3 IFS drivers in Windows; download them from [www.fs-driver.org/](www.fs-driver.org/)

I recommend that when asked during install, you enable read-only access to your ubuntu partitions. You can very easily destroy your ubuntu installation if you allow read/write access to your ubuntu partitions, and make a minor mistake.

---

### Post by Fatal Equinox on 2008-06-27
> **prshah said:**
> You need to install the ext2/3 IFS drivers in Windows; download them from [www.fs-driver.org/](www.fs-driver.org/)

I recommend that when asked during install, you enable read-only access to your ubuntu partitions. You can very easily destroy your ubuntu installation if you allow read/write access to your ubuntu partitions, and make a minor mistake.

This will work even for wubi? Seems this is for like if you have a partitioned harddrive,  wubi is just inside windows.   

Thank you

---

### Post by prshah on 2008-06-28
> **Fatal Equinox said:**
> This will work even for wubi?


No it won't work, you're right there. I missed the part about Wubi.

---

### Post by Fatal Equinox on 2008-06-28
> **prshah said:**
> No it won't work, you're right there. I missed the part about Wubi.

Thanks for the site the thought.... when i do a proper partition i will use it.  Yea wubi is why i posted on the wubi part of the forum , still i should have been more clear about my setup.



wubi 8.04 with hardy install obviously.   Anyone else have any ideas?

---

### Post by lisati on 2008-06-28
I was going to suggest one of the tutorials on Samba but then spotted the bit about Wubi......

---

### Post by minhmeoke on 2008-06-29
You can use Explore2FS [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) , just drag-and-drop the files into it, however you will only have read-only access.

You could also try some of the other solutions in this thread: [http://ubuntuforums.org/showthread.php?t=436923](http://ubuntuforums.org/showthread.php?t=436923)

---

