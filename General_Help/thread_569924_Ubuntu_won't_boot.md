---
title: "Ubuntu won't boot"
date: 2007-10-07
forum: General Help
---

### Post by Naatan on 2007-10-07
I can't boot ubuntu anymore  When I boot in safe mode to debug and try to vim something I get the following error:

symbol lookup error /us/lib/gtk-x11-2.0.so.0 undefined symbol g_hash_table_ref

I can't do anything right now as without vim I can't change any settings.. same goes for most other applications.

The only thing I can think of that might have caused this was the installation of xserver-xgl but I removed it again and it still gives the error.

I've tried reinstalling all packages with xgl in the name but this didnt work.

"gtk-x11-2.0.so.0" is a symlink to another file in the same folder with the same name only with an additional nummeric extension

Can anyone please help?

---

### Post by abduliounited on 2007-10-07
Hey there!!
how do you boot up in save mode?? I have a dual boot system xp and ubuntu. from today ubuntu doesn't boot properly. After the ubuntu window instead to get the login screen i get a dark screen where i can see only the cursor

thanks 
:)

---

### Post by Naatan on 2007-10-07
When your system boots you normally get the choice to press ESC to enter the GRUB menu, once in this menu you pick the second option, Im not sure if its actually called safe mode, but its boots you up in a terminal session

---

### Post by ryanVickers on 2007-10-07
Could you try to reconfigure the X server?

Also, would nano work (like vim, but lass features and way easier ;))

---

### Post by abduliounited on 2007-10-07
I have dual boot. I should still press esc??

---

### Post by Naatan on 2007-10-07
ryan, yes nano works, im gonna try reconfiguring X now, but it looks like the problem resides in the file being symlinked.

abd, yes just press esc to enter grub, it won't kill you ;)

---

### Post by Naatan on 2007-10-07
reconfiguring X didnt work, looking back it was a silly thing to try since the error appears in a terminal session

---

### Post by ryanVickers on 2007-10-07
could you check for where the symlink points to and remove the link, or put the file it *should* be finding in /lib?

---

### Post by Naatan on 2007-10-07
when i remove the link it doesn't work either cause a certain file isn't found, and there is no other file with a similair name in the /lib folder

---

### Post by hollerith on 2007-10-07
My 2c:

Confusion abounds here.  'Safe mode' is something MSWindows >spits< has - it starts with just basic drivers just in case its one of these that is preventing that OS startup.  Ubuntu doesn't have an option like that - most drivers are built in the kernel, some loaded as modules (that list of stuff happening when you choose a boot option).  That library is not required to 'boot Ubuntu' as you say.  You get a grub menu?  Select an option - the defaul -t which will try and start X?  If it fails it will say why your Xsession failed.  The window manager is not starting, that's all.  If you do Ctrl-F1 you should get a character-based console to login with.  From here you can use nano to edit files, or vi if you have.  You can `cat /etc/X11/xorg.conf` to read how to rebuild that file or tail /var/log/messages, .xsession-errors are in your /home.  Your problem sounds like a link to a library is broken somehow.  There could be lots of stuff trashed to do with your X window manager- only you know what you were doing when this happened.  Its probably no coincidence that you mention xserver-xorg?  You may need to reinstall X with apt-get - or return to your last working backup.  Check your sources list is still pointing at the correct repositories.

---

### Post by ryanVickers on 2007-10-07
> **Naatan said:**
> when i remove the link it doesn't work either cause a certain file isn't found, and there is no other file with a similar name in the /lib folder

well then, in theory, there's no reason for the problem to exist!  Is there something called a "g hash table reference"?:p

---

### Post by Naatan on 2007-10-07
hollerith:

if you would've read all the posts you would've known that I was only calling it safe mode because I couldn't recall the actual name, I am already in a terminal session.
As said reconfiguring X didnt work, reinstalling doesnt work either.

ryan:

that makes no sence, when the file exists the error says that the file has an illegal symbol of some sorts, when the file is removed/renamed the code breaks all together cause its looking for a file that doesnt exist.

So in theory, the problem still exists, and removing the file doesn't indicate anything other than that the file is vital

---

### Post by Naatan on 2007-10-08
Resorted to reinstall =\

---

