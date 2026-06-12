---
title: "How to make X11 Mouse icons work on 12.04-13.10"
date: 2014-02-03
forum: General Help
---

### Post by Steel Reign on 2014-02-03
I am not sure if this method of making mouse icons work is known. I have seached the web and a multitude of different methods, but none like that. None of the methods worked 100% for me. Only making half the icons work depending what tasks you are performing. 

This is how I got my mouse icons to work 100% across all tasks.

- First save the theme you want to add to yoru Desktop.

- In terminal 
         #cd /usr/share/icons/default

- Then either you can delete or rename the *index.themes* file. I used *index.theme.old*
         #sudo mv index.themes indexs.themes.old
         #cd ..

- Do the same thing you did for the default folder for the contents of the DMZ-White folder.
         #cd DMZ-White
         #sudo mv cursors/ cursors.themes index.themes cursors.old cursors.themes.old index.themes.old

- Go back the Desktop and copy the contens of your new themes to both the default folder and the DMZ-White folder. If you don't copy both the icon set will not work completely.
         #cd /home/*UsesName*/Desktop/*IconSetFolder*
         #sudo cp cursors/ index.themes default DMZ-White

- Then reboot to make changed take effect.
         #sudo reboot

Hopefully this helps out people out there. I know I had a crappy time trying to figure this.

Good Luck...

Steel

---

