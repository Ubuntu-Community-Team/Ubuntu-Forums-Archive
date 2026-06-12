---
title: "[SOLVED] $home/.dmrc permissions?! Hiding my home folder..."
date: 2007-08-11
forum: General Help
---

### Post by Jawshie on 2007-08-11
Mkay I've read over some of the other forums and I dont feel they answer my questions very well. I like to consider myself a seasoned linux newb so be free to be technical but not outrageously so! :)

I noticed that other users on the installation could access my home folder and needless to say I didnt care too much for that. So I used the gui to set it to where people could not see my home folder. It worked yay! But then I got the often encountered (apparently..) $home/.dmrc file permissions error. I prompted to fix it by letting the users again see my folders... I think I understand whats going on! Some system user needs to access that file or something right?

I just want to set it to where normal users can not see my files in my home directory and not have this error.

---

### Post by aysiu on 2007-08-11
Well, just so you know: if someone has physical access to your computer and a little know-how, she can see and modify pretty much any file on your computer.

But to answer your question, you can deny people read access to your home folder by changing permissions on the folder (do *not* do a recursive permission change to all the subfolders and files--change permissions on only the top-level folder).

```
sudo chmod 750 /home/jawshie
``` should do it.

I repeat, though, **do not** do ```
sudo chmod -R 750 /home/jawshie
``` as that will give you the same .dmrc error.

---

### Post by Jawshie on 2007-08-12
Aye I do know... I hope one day Ubuntu will grace us with full disk encryption on installation. 

Ty very much it worked! I feel silly ^.^

---

