---
title: "Creating password protected but not invisible folders"
date: 2013-08-06
forum: General Help
---

### Post by ginger3 on 2013-08-06
I'm using Ubuntu 13.04. I'd like to password protect a directory without making it invisible and/or having to mount it. I'd just like to be asked for the password of the directory and then access it. Just changing permissions to make the directory root or giving it octal permission 700 and/or creating a . file is not sufficient for my needs.  I would also like to know how to remove the password protection if i need to. Truly, thank you, kindly.  

I've been searching the internet and everything I've found related to 13.04 seems to point to encfs: making your folder invisible and mounting it via fusermount.

---

### Post by GwL3eNC on 2013-08-06
Hi,

is cryptkeeper the right tool for your purpose?

[http://tuxtweaks.com/2009/03/create-an-encrypted-folder-in-ubuntu-with-cryptkeeper/](http://tuxtweaks.com/2009/03/create-an-encrypted-folder-in-ubuntu-with-cryptkeeper/)

---

### Post by slickymaster on 2013-08-06
You have [Cryptkeeper]("https://apps.ubuntu.com/cat/applications/precise/cryptkeeper/") in the repositories.

To install it just run in a terminal```
 sudo apt-get install cryptkeeper
```Then, after installing it, go to Applications -> System Tools -> Cryptkeeper and it will automatically attach itself to the top panel.
To create an encrypted protected folder, click on Cryptkeeper applet and select ‘New encrypted folder’, type the folder name and where to save the folder and click ‘Forward’, enter a password and click ‘Forward’ again and the folder will be created and ready to be used.

---

### Post by ginger3 on 2013-08-06
Thank you both for your speedy replies, but Cryptkeeper isn't what I'm looking for. Is there really no way to just create a password protected folder without also hiding it and having to mount it?

---

