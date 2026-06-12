---
title: "The NTFS tool don't work"
date: 2008-02-27
forum: General Help
---

### Post by the lemming on 2008-02-27
I have downloaded everything available in the adept manager that relates to NTFS.

Could somebody please tell me why nothing happens when I go into the K menu, choose System and select the NTFS configuration tool?

I have even uninstalled everything and reinstalled it all in the hope that the NTFS config tool works but nothing happened.

At the moment my laptop dual boots between kubuntu and XP and I want to have access to my XP partition.

Some people have kindly given me some script to put into a terminal but as I'm not that proficient in Linux I am not exactly sure what I am supposed to type or copy/paste.

Anybody know why the NTFS config tool does not work?

Cheers

---

### Post by ajeetraj on 2008-02-27
I don't know which version of ubuntu you are using but the best package to access your xp drives is called ntfs-3g. Once you have that then you will be able to configure or do anything you want. Actually it is available in the repo as well :) To get this just type this in your terminal: 
```
sudo apt-get install ntfs-3g l
```
to configure your ntfs-3g install this:
```
sudo apt-get install ntfs-config
```

It shouldn't ask you for other dependencies, but if it does then you can just download them too. 

After installing these two packages, just run in your terminal :
```
sudo ntfs-config
```

Then you will see a pop-up which will give you options on how to handle your drives. 

hope this helps!

---

