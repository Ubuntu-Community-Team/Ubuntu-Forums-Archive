---
title: "Installing something in my download folder"
date: 2019-02-28
forum: General Help
---

### Post by freddy58 on 2019-02-28
How would I use a Terminal to Install a Kdenlive, which is in my download folder.  I have been entering various terms in my Terminal and cannot get it to run
The Program that sits in my download folder if I Click on it, I get a message "Could not display "kdenlive-18012.1b-x86_64.appimage".   the under that it says 'There is no application installed for "Appimage application bundle" files  Then it says "Do you want to search for an application to open this file"
with Yes/no choice.    If I choose yes, a small black box appears on the top of my other screen (home screen) and if I click it opens a page that says nothing found.

I am running the latest LTS Ubuntu OS and i need hep here.

---

### Post by #&amp;thj^% on 2019-02-28
The preferred way to install any application in Ubuntu is to use Official Ubuntu repositories. 
To install you can run
```

sudo apt-get install kdenlive
```

This command will download about 200 MB of packages and will use about 450 MB disk space.

If you really need a bleeding-edge version of kdenlive you can choose AppImage or FlatPak. Here you'll pay with disk space.

   To install AppImage: 

 ```
wget https://files.kde.org/kdenlive/release/kdenlive-18.08.0-x86_64.AppImage
    chmod +x kdenlive-18.08.0-x86_64.AppImage
    ./kdenlive-18.08.0-x86_64.AppImage
```
You may have to change the VERSION numbering though.
   if you want to have the latest version, you'll need to add the PPA. Do this by typing
```

sudo apt-add-repository ppa:kdenlive/kdenlive-stable && sudo apt-get update
```

---

### Post by freddy58 on 2019-02-28
1 Fallen, I thank You
And Disk Space, no worries

---

