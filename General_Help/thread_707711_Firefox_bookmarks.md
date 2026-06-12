---
title: "Firefox bookmarks"
date: 2008-02-25
forum: General Help
---

### Post by kevindubrow on 2008-02-25
Hey, every time I restart Ubuntu, my bookmarks in Firefox are missing...anyone know why this is happening?

---

### Post by Arwen on 2008-02-25
When you say missing you mean deleted or they just don't appear on top?When you go Bookmarks->Manage bookmarks you can't find them in there?

---

### Post by kevindubrow on 2008-02-25
They are completely gone. They aren't in the manage bookmarks menu or anything.

---

### Post by Arwen on 2008-02-25
In your /home/username dir in a hidden folder named .mozilla: can you find a file named bookmarks.html and a folder named bookmarkbackups?Are they empty?
What about reinstalling firefox?

---

### Post by y-lee on 2008-02-25
Firefox keeps its bookmarks in a file called bookmarks.html in a hidden folder in your home directory. the path to this folder looks like:

**/home/username/.mozilla/firefox/xxx.default/**

where username is your username and the xxx will be some random looking stuff like in my case **57wj47mm.default**, If you have multiple profiles each profile will have bookmarks and the **default** part will be the profiles name. Open nautilus and set it to view hidden folders navigate there and see if you have any bookmarks, ie a file called **bookmarks.html**, you should also have a **bookmarks.bak **file. 

Also open firefox in a terminal and see if it generates any errors, use the code below and post errors here if any.

```
firefox
```

Edit: Arwen beat me to it. lol.

---

### Post by kevindubrow on 2008-02-25
Hah...is it weird that there is no "bookmarks" folder in the .mozilla folder? Should I just make one?

---

### Post by Arwen on 2008-02-25
I do this path to find that folder : /home/username/.mozilla/firefox/xxx.default/bookmarkbackups.
No,it should be made by firefox

y-lee I think typing firefox in terminal may show an error or sth,last time I heard about mysteriously gone bookmarks was because of spyware or a badly installed plugin(in XP,though)

---

### Post by y-lee on 2008-02-25
> **Arwen said:**
> y-lee I think typing firefox in terminal may show an error or sth,last time I heard about mysteriously gone bookmarks was because of spyware or a badly installed plugin(in XP,though)

Yep plugins can do it, if so try

```
firefox -P
```

create a new profile and try to save bookmarks in the new profile. Reboot and see if they are still there. Permission problems can also cause bookmarks to not be saved, that error would show up in the terminal. (don't ask how i know that :lolflag: )

---

