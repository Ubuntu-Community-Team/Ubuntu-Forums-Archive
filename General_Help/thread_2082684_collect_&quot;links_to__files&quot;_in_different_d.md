---
title: "collect &quot;links to  files&quot; in different directories and then copy"
date: 2012-11-10
forum: General Help
---

### Post by then_dude on 2012-11-10
hello everybody,  i would like to know if the next problem is possible to solve...  

a friend of mine asked me if i had any pictures of him, and yes i have, but they are all scattered over different directories.

 I would like to make a directory (or a file) where all his pictures are brought together. But i don't want to make hard copies of those files, which i would have twice on my harddisk.   When he comes around i would like to copy 1 file or 1 directory and all the files start to copy...   

So is there a way how i can tell ubuntu that there are a bunch of files scattered over the harddisk but there is reference to them in "my friends photo's" directory...  hope the problem is a bit clear. 

thanks

---

### Post by HiImTye on 2012-11-10
open *gedit* (text editor) and paste the following into it
```
#!/bin/bash
while read -r f; do
ln -s $f <destination folder>
done < <(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS")
exit
```replace *<destination folder>* with the path you want the links saved into

save it in *~/.gnome2/nautilus-scripts* (you may need to create the folder), naming it whatever you want it to appear as in your menu (for instance,* Link Pictures*). make sure you don't add a file extension (i.e. *.sh*), because the menu item is **exactly** what you name the file

to use it, when in nautilus (file manager), right click on a file, then choose *Scripts > Link Pictures* (or whatever you called it)

files will be linked in the folder you specified in the script

note: this will only work for local files. if you want it to work with networked files, then you need to change the script

---

### Post by then_dude on 2012-11-10
thanks a lot,

that's impressive. 

will it also work with directories  and not only files ?

thanks again

---

### Post by HiImTye on 2012-11-10
*ln* creates links to files and folders, just make sure you use the *-s* option or you will make a hard link, and if you delete a hard link, you also delete the original

edit: I just thought about it, and this script is really single purpose, you could make it a multi purpose script by doing this:
```
#!/bin/bash
F=$(zenity --file-selection --directory --filename=$HOME)
while read -r f; do
ln -s $f $F
done < <(echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS")
exit
```this will give you a folder selection dialog so that you can choose the folder to save the links in. you can change the folder by editing *--filename=$HOME* to the folder that you want

---

### Post by then_dude on 2012-11-10
thanks a lot,

took you 5 minutes, gonna take me a day to decipher it...
but then again, i must be earning my beans the hard way ;-)

thanks
kind regards

---

### Post by mcduck on 2012-11-10
Another option would be to simply have two file managers open (or use the dual-panel mode) and simply drag&drop the images to your "collection" location using middle mouse button, which will give you option to link the file.

---

### Post by then_dude on 2012-11-11
thanks guys,  i will try both,  the first as a great learning trick, the second as a very practic solution, i didn't know the middle mouse button was for that.   i got another question similar to these, but i'll make a new post for it  thanks again

---

