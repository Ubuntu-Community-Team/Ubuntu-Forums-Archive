---
title: "Installing Dazuko in Gutsy"
date: 2008-04-22
forum: General Help
---

### Post by tommyhakinen on 2008-04-22
Hi,

I followed the instruction on this thread to install Dazuko :

> 
[http://ubuntuforums.org/showthread.php?t=589911](http://ubuntuforums.org/showthread.php?t=589911)


After the installation, I deleted of the tar.gz and the extracted folder on step 2

> 
2. Extract the tarred gunzip archive to a folder.


when I tried to empty the trash, I received an error message saying I have no permission. I force to delete it using 

> 
sudo rm -r


I would like to know, will this affect my Dazuko installation?
Thank you very much.

Regards,

tommy

---

### Post by ibuclaw on 2008-04-22
enter the extracted folder in the Trash in the terminal.
```
cd ~/.local/share/Trash/files/dazuko*
```
And type in:
```
ls -lA
```

If there are any hidden files/folders that aren't owned to you. Then try to remove it.
```
sudo rm -rf **.hidden**
```

Then try to empty the trash folder.

Regards
Iain

---

