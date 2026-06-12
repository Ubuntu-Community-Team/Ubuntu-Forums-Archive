---
title: "Leafpad erases files over SMB"
date: 2016-01-30
forum: General Help
---

### Post by Mark_Bertolina on 2016-01-30
I just did a fresh install of lubuntu in a VM to verify this reproduces.
15.10
4.2.0-25-generic

Leafpad 0.8.18.1

Whenever you edit a text file on an SMB share, leafpad erases the entire file instead of saving your edits.  I mention this to the lubuntu group, since leafpad is the default program associated with file extensions such of .txt and thus very liekly to be where new users start editing such files.  But in fact, they will be silently erasing those files contents.  No other applications seem to have this problem over the SMB share, and I tested to 2 different smb shares, one a NAS4Free server running samba, the other a commerical NAS .

As a work around I uninstalled leafpad and installed mousepad, then associated files types with mousepad.  I encourage the lubuntu group to look into fixing this issue in Leafpad, or switching the default graphical text editor to something else.
sudo apt-get remove leafpad
sudo apt-get install mousepad


Leafpad doesn't seem to be under much development lately, though I have not contacted the author:
[http://tarot.freeshell.org/leafpad/](http://tarot.freeshell.org/leafpad/)


Others have noticed this problem with leafpad in general:

FS#44681 - [leafpad] wipest content of text files on smb when saving
[https://bugs.archlinux.org/task/44681](https://bugs.archlinux.org/task/44681)

Samba erases content of files when saving
[http://unix.stackexchange.com/questions/202848/samba-erases-content-of-files-when-saving](http://unix.stackexchange.com/questions/202848/samba-erases-content-of-files-when-saving)


I am happy to help test this problem further, just drop me a line.  If there is a better place for me to post this info / request let me know.
Mark Bertolina

---

### Post by mörgæs on 2016-01-31
Hi, welcome to the fora.

Unfortunately you are right: Leafpad and other applications which are currently packaged with Lubuntu are in a very slow development. 

If you are in touch with the Lubuntu developers you could suggest that Gedit is used in stead of Leafpad. It would benefit all if the same editor was used by all distros.

---

### Post by Mark_Bertolina on 2016-02-04
How do I best get this issue in front of the Lubuntu developers?  It is not strictly a lubuntu bug ... is it?

I think there is a reason not to use gedit in Lubuntu, because it is built on LXDE and they do not want the resource requirements of gnome just for something like gedit.

---

### Post by mörgæs on 2016-02-04
> **Mark_Bertolina said:**
> How do I best get this issue in front of the Lubuntu developers?  It is not strictly a lubuntu bug ... is it?


You could try the [mailing list]("https://lists.ubuntu.com/mailman/listinfo/lubuntu-users"). If not possible to change to Gedit then maybe Mousepad is an option.


> **Mark_Bertolina said:**
> 
I think there is a reason not to use gedit in Lubuntu, because it is built on LXDE and they do not want the resource requirements of gnome just for something like gedit.

The requirements for Gedit are so small that they are not worth considering. You could try to install and see what it drags along as dependencies, which is almost nothing. ```
sudo apt-get install gedit --no-install-recommends
```
is about 12 MB.


Still you could be right: Some people stop considering Gedit after reading the initial 'G', assuming without testing that it translates to 'dependencies' and 'slow'.

---

