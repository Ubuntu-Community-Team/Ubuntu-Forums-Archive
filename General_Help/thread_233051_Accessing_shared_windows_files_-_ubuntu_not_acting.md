---
title: "Accessing shared windows files - ubuntu not acting as normal"
date: 2006-08-09
forum: General Help
---

### Post by hafley on 2006-08-09
Hey guys, i've seen on here that a lot of you have access to a windows network within 5 min of a ubuntu install. Well not for me. I've got 2 laptops one winxp one ubuntu, wireless network, and i know the file sharing works. 

On ubunto i browse to Network Servers > Windows Network

But there is nothing there. For a moment abuot an hour ago i saw my workgroup "mshome" but now that's not even there.

This seams like it's not an issue for other unbuntu users, so whats makes me so special?

Thanks guys.

---

### Post by tronica on 2006-08-09
heres what i do to acces w2k3 server

first on the linux box

> cd /mnt
> sudo mkdir server
> sudo chmod 777 server
> sudo mount -t cifs //ipaddresshere/share /mnt/server -o user=usernamehere,pass=passhere

then just open /mnt/server folder you made and there you go. you should be able to stream music and video from you winbox as well.

---

### Post by Ramses de Norre on 2006-08-09
Check [this]("http://ubuntuforums.org/showpost.php?p=868493&postcount=14").
And reading the whole thread might interest you too.

---

### Post by hafley on 2006-08-09
I know i don't need samba because i do not plan to change my ubuntu files from windows

---

### Post by yopnono on 2006-08-09
> **hafley said:**
> Hey guys, i've seen on here that a lot of you have access to a windows network within 5 min of a ubuntu install. Well not for me. I've got 2 laptops one winxp one ubuntu, wireless network, and i know the file sharing works. 

On ubunto i browse to Network Servers > Windows Network

But there is nothing there. For a moment abuot an hour ago i saw my workgroup "mshome" but now that's not even there.

This seams like it's not an issue for other unbuntu users, so whats makes me so special?

Thanks guys.

Ok first if you like to use the network browse, you need to make sure that your computers are in the same "workgroup". 
To change in XP check network settings, In Dapper open "gconf-editor" and then go to "system / smb" change the value to the same as the XP.

After this you should be able to "see" the xp share (if you have shared a folder)

---

### Post by hafley on 2006-08-09
That seamed to work, thank you

---

### Post by clarkth on 2006-10-04
> **tronica said:**
> 
then just open /mnt/server folder you made and there you go. you should be able to stream music and video from you winbox as well.

This was just what I was looking for.  Thanks!

---

