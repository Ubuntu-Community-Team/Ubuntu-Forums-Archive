---
title: "where/how do i find the file for  'sound' of 'system settings'"
date: 2014-02-28
forum: General Help
---

### Post by deaton25 on 2014-02-28
hi

i need to find the file for 'sound' of 'systems settings' 
i need to know that files command
and use that command to make a separate line for 'sound' in the 'sound and video' section of 'main menu'

i use gnome in ubuntu 12.04 lts

thanks

---

### Post by tgalati4 on 2014-03-01
System sounds are located in /usr/share/sounds.  If you are looking for the sound control such as *pavucontrol*, those are located in /usr/bin.

Some reading on editing menus:  [https://help.ubuntu.com/community/Applications#Using_and_Editing_the_menu](https://help.ubuntu.com/community/Applications#Using_and_Editing_the_menu)

---

### Post by 3rdalbum on 2014-03-01
```
gnome-control-center sound
```

I'll explain to you how I found it out:

I first opened the Gnome Control Center and clicked on "Sound" so it opened on my screen. I went to the terminal and typed:

```
ps aux | grep "sound"
```

The "ps aux" bit returns a list of programs currently running. The | character says "put the output of the first command as an input into the next command". The "grep" command searches the input data for the word "sound" and then displays the lines of the input data that have the word "sound" in them. There was only one, and that was gnome-control-center sound.

I also could have used "ps aux" on its own and then manually scrolled through the list to find what I was looking for.

---

