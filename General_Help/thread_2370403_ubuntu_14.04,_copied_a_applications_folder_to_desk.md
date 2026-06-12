---
title: "ubuntu 14.04, copied a applications folder to desktop, oops! now what?"
date: 2017-09-02
forum: General Help
---

### Post by seekertom on 2017-09-02
I wanted to create a shortcut on desktop to easily get me to computer-usr-share-applications.

In share, I rt clicked applications folder, then copied to desktop. Now I have a folder on the desktop called applications, but the folder has a bunch of files most of which end in .desktop.
Was this not the correct way to get a shortcut to this folder onto the desktop? Can I delete the desktop folder or will I louse things up?

thanks, and hope you can help.
st :confused:

After reading the replies, my takeaway is this: I successfully copied the apps folder to the desktop, but when it landed there ubie changed the extensions to .desktop for system reasons. I now understand that what I'm seeing there will be ok to delete. Also, as I learn more about ubie, I see there are other ways of having my frequent shortcuts/apps available.
Thanks for the help, ever one!
st

---

### Post by ChuangTzu on 2017-09-02
make sure it is a copy and not cut/paste.  If it is a copy then its ok to delete from desktop and make a true shortcut or symlink.  
[https://www.howtogeek.com/287014/how-to-create-and-use-symbolic-links-aka-symlinks-on-linux/](https://www.howtogeek.com/287014/how-to-create-and-use-symbolic-links-aka-symlinks-on-linux/)

---

### Post by seekertom on 2017-09-03
its a copy because original applications folder is still there. what is unclear is the changed contents from obvious apps to files with dot desktop extensions.
thanks. st

---

### Post by Bucky Ball on 2017-09-03
If it's a copy, delete it as suggested. Not needed. Create a symlink or launcher instead, as suggested.

There is no need to copy the whole folder to your desktop (which is also a 'folder' and you are creating a redundant duplicate when the original can be linked to easily.)

---

### Post by again? on 2017-09-03
> **seekertom said:**
> its a copy because original applications folder is still there. what is unclear is the changed contents from obvious apps to files with dot desktop extensions.
thanks. st
The files in /usr/share/applications **are** .desktop files.
Run in terminal
```
ls -a /usr/share/applications
```

How they are displayed in the file manager depends on permissions.

If you change the permission for one of the copied files so as to be executable it will display
as an application launcher icon.
You can drag and drop .desktop files into gedit to view.

If you say why you wish to make a shortcut to this folder, you may get some better options.

---

### Post by mc4man on 2017-09-03
I would delete whatever you placed on your Desktop & do something like this

Create a file on your Desktop named applications1.desktop
Put this inside, save
```
[Desktop Entry]
Encoding=UTF-8
Name=Link to Applications
Type=Link
URL=file:///usr/share/applications
Icon=inode-directory

```

I probably wouldn't do in 16.04 unless using a patched nautilus to allow moving links on the Desktop, though not sure if the current 16.04 bug affects local links like it does web ones.. 
Your reported issue moving Desktop links in 14.04 Ubuntu makes no sense as 14.04 nautilus is fine in this regard.

---

