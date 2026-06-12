---
title: "Documents Folder Moved"
date: 2018-07-08
forum: General Help
---

### Post by bionic3epl on 2018-07-08
[COLOR=#2C2C2C][FONT=&quot]Is the Documents Folder supposed to be under the Trash & SDXC folders, if not how do I move it back above them?[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2018-07-08
> **bionic3epl said:**
> [COLOR=#2C2C2C][FONT=&quot]Is the Documents Folder supposed to be under the Trash & SDXC folders, if not how do I move it back above them?[/FONT][/COLOR]

No its not>>Try this from the terminal:
```
trash-restore
```
EDIT I now see what you mean>>>just mouse click and hold the Documents folder in the left tree and move it up to where you want it to be.

---

### Post by bionic3epl on 2018-07-08
Tried that & it didn't work, Also my Trash Bin is empty.

---

### Post by #&amp;thj^% on 2018-07-08
See my edit.

---

### Post by bionic3epl on 2018-07-08
> **1fallen said:**
> No its not>>Try this from the terminal:
```
trash-restore
```
EDIT I now see what you mean>>>just mouse click and hold the Documents folder in the left tree and move it up to where you want it to be.

I tried moving it up & it won't let me move it up.

---

### Post by #&amp;thj^% on 2018-07-08
Now I know why I dislike nautilus so much. ;)
Thunar works just fine for me but I''m not recommending you use or install it.
If this is truly bothersome to you we can have look at this:
```
gedit ~/.config/gtk-3.0/bookmarks
```
paste that back here in code tags please.
Mine looks like this:
```
file:///home/me/Documents
file:///home/me/Downloads
file:///home/me/Music
file:///home/me/Pictures
file:///home/me/Videos
```
If not>> there is no real issue with where it is placed>>as long as it functions as expected. :)

---

### Post by bionic3epl on 2018-07-08
I tried that code & it opened a blank document, what am I supposed to put in the blank document?

---

### Post by deadflowr on 2018-07-08
Try 3.0 as in
```
gedit ~/.config/gtk-3.0/bookmarks
```

---

### Post by bionic3epl on 2018-07-08
file:///home/eddie/Documents
file:///home/eddie/Music
file:///home/eddie/Pictures
file:///home/eddie/Videos
file:///home/eddie/Downloads

---

### Post by #&amp;thj^% on 2018-07-08
Replace yours with the below:
```

file:///home/eddie/Documents
file:///home/eddie/Downloads 
file:///home/eddie/Music
file:///home/eddie/Pictures
file:///home/eddie/Videos
```
Logout and Back in again to see if the change helped.
Thanks deadflowr for the correct path ;)

---

### Post by bionic3epl on 2018-07-08
I happen to log out & logged back in b4 you posted w/ no change.

---

### Post by #&amp;thj^% on 2018-07-08
Well then use the dconf Editor as this just worked for me.
You may have to install it with:
```
sudo apt install dconf-editor
```
And open it after install, and navigate to>> **/ca/desrt/dconf-editor/boomarks**.
Now you will see the Use Default Value is on>> set to Off 
And you see a set of brackets like "[]" >> Inbetween those add this exactly as posted below:
```
['file:///home/eddie/Documents
file:///home/eddie/Downloads 
file:///home/eddie/Music
file:///home/eddie/Pictures
file:///home/eddie/Videos']
```
Now in the bottom right you will see a Check to apply>> hit that. 
Now if this dose not change things you will have to live with what you have.

---

