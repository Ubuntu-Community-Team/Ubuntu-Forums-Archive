---
title: "Recovering files - permission denied..."
date: 2014-02-01
forum: General Help
---

### Post by Hvidemose on 2014-02-01
I&#8217;m trying to get some user files from a **Xubuntu **partition. More precisely I need to recover my mozilla files from my user folder. I&#8217;m using an live usb with **Lubuntu**, but when I try to drag and drop the folder, I get a message: *error opening directory *and *permission denied*.

How can I get this folder out before installing a new system?

---

### Post by Portaro on 2014-02-01
Maybe you can use 

sudo 

or sudo su

and then move the files for one folder to another,

and also you can do it with terminal -

sudo cp /

examples -> [http://www.cyberciti.biz/faq/copy-command/](http://www.cyberciti.biz/faq/copy-command/)

---

### Post by robin7 on 2014-02-01
The file manager in Lubuntu has an option to "Open Current File as Root," I think.  Under one of the tabs at the top of the pcmanfm window.  I used to open the "restricted" folder as root and have another instance of the file manager open to copy the files to or from.  If drag-and-drop doesn't work, use copy-and-paste.

---

### Post by PotatoHead007 on 2014-02-01
I am not sure what exactly Lubuntu is, but i am assuming its based on Ubuntu. So, what i would do(something similar was mentioned by Portaro) is this(in terminal):

sudo cp /media/yourHDDname/home/username/.mozilla

That should work, assuming its like Ubuntu. You might want to tinker around with the path a bit.

Here is another way, not sure if it works in LiveUSB though:


ALT+F2
A window should open, asking you what command you want to execute. Type: 

gksudo nautilus

This should open your root folder, then just navigate to where your .mozilla file is. 

Really hoped i helped, if it did not work, please post the output :)

---

### Post by varunendra on 2014-02-01
Be aware that all the methods suggested above will make the copied files be owned by root.

When copying them back to the newly installed system, you'll need to make them be owned by the User whose Home you'd be copying them to. To do so recursively on the folder and its contents -
```
sudo chown -R $USER:$USER /path/to/the/copied/folder
```

---

### Post by Hvidemose on 2014-02-01
> The file manager in Lubuntu has an option to "Open Current File as  Root," I think.  Under one of the tabs at the top of the pcmanfm window.   I used to open the "restricted" folder as root and have another  instance of the file manager open to copy the files to or from.  If  drag-and-drop doesn't work, use copy-and-paste. 				

Thanks mate!!! This worked!

---

### Post by robin7 on 2014-02-01
Cool!  Be sure to mark the thread [SOLVED] so that others with the same issue can spot it.

---

### Post by Portaro on 2014-02-01
Nice solved.

---

