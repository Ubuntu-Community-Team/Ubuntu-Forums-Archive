---
title: "how to change icons?"
date: 2008-04-23
forum: General Help
---

### Post by thunderwolf333 on 2008-04-23
i have no idea how to change icons for anything.. lol
help?
i want to change the folder icons and on AWN change the trash icon and change my firefox launch icon.
i downloaded icons from gnome-look.

---

### Post by lostlinuxkiwi on 2008-04-24
Open your home directory and set it to show hidden files. You can do this by selecting it from the view menu, or just by pressing Ctrl+H. Then you want to look for a folder called .icons if you open that folder you will see all the themes you have installed. Then you just go into the folder for the icon theme you are using at the moment, and replace the icons to the ones you want to use. the firefox icon is probably in the scalable/apps folder.

If you haven't installed a new icon theme and are just using one of the icon themes that came with ubuntu then this way wont work because the default theme icons are somewhere else (i dont know where as Ive never bothered looking). if you want to install a new icon theme like the kind you get from gnome look then its really easy to do. Go to system > preferences > appearance. when the appearance preferences window appears click install and point it to the tar.gz file you downloaded and it will install it. you dont even need to unpack it.

---

### Post by Cannaregio on 2008-04-24
However, to change the icon of a [COLOR="Blue"]single application[/COLOR], just rightclick on its actual icon, select [COLOR="#0000ff"]properties[/COLOR] click on its actual icon (inside the properties panel) and just navigate to the new icon.

---

### Post by nlee1201 on 2008-04-24
Hey guys,

I've tried copying the extract from the tar.gz files into home/username/.icons and it still doesn't show up in system>preference>appearance in the customization window. I also tried installing it and it still doesn't work. Any ideas?

---

### Post by thunderwolf333 on 2008-04-24
thanks for the help guys! it worked.
to nlee1201 im not getting that problem but i hope you can solve it. 
but heres my input:
did you put the icons themselves, or the whole folder?
all you need to do is take the extracted folder and put it there.

---

### Post by BatsotO on 2008-04-24
you can put the whole ectracted folder in /usr/share/icons and change the owner and permission, make it same as all the other folder in there.

---

