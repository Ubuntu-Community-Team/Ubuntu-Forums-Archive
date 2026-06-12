---
title: "Problem when following Instructions for desktop video background"
date: 2008-05-20
forum: General Help
---

### Post by Nudgeworth on 2008-05-20
Hello guys :)

 I came across this post to have a video as your desktop background
[http://www.ubuntu-unleashed.com/2008/04/howto-loop-movie-or-video-as-desktop.html](http://www.ubuntu-unleashed.com/2008/04/howto-loop-movie-or-video-as-desktop.html)

 When following the instructions for installing xwinwrap.
 
 I got this answer when I entered the last command
"cp: cannot stat `xwinwrap': No such file or directory"

 Any ideas

---

### Post by bobjenkins on 2008-05-20
Which command are you getting the error on? Its probably a simple typo of file path

cd xwinwrap
make
sudo cp xwinwrap /usr/bin

That error is saying cannot copy because the folder is not found

Instead of
sudo cp xwinwrap /usr/bin

You can try copying it manually
If I am understanding it right (forgive me I am noob) you just made xwinwrap folder in your home folder, try and copy that to /usr/bin

Alternatively put newly created xwinwrap folder on your desktop then use this command in place of sudo cp xwinwrap /usr/bin

sudo cp /home/<yourusername>/Desktop/xwinwrap /usr/bin

enter username and don't forget the capitol "D"

goodluck

---

