---
title: "kde icon help - change icon and icon size -"
date: 2007-02-22
forum: General Help
---

### Post by alfo_uy on 2007-02-22
hello you there. hope you can help me.

i've 2 issues refered to icons that i can't solve. 

1st i want to have different icon sizes for my desktop icons.    <-- different sizes for different icons. i.e.: a bigger home folder icon and a normal firefox icon.

2nd i can't change some icons. ej: i linked the media folder to my desktop. automatically gave me a folder icon, wich i do not like. but i can't change it. i do not have permission. not even as a root member not even primary group, not even secondary and not even putting my user under the root group. can't change the icon on my fat 32 secondary hdd.

and that remembered me another issue... inside my fat 32 secondary hdd there are some sub folders in wich i can create files. but in others i can not!
no modifications made to specific folders such as permission, besides, i am the owner.

i did not find anything around here to solve my issue but maybe you can help me; if so, link me! or teach me!

thx!


<-- edited.

---

### Post by ewankho on 2007-02-23
You can change desktop icon size in KDE in System Settings->Appearance->Icons->Advance

---

### Post by alfo_uy on 2007-02-23
but there i change all of them. i want to do it individually.
sorry if i did not say it.

thx!

---

### Post by alfo_uy on 2007-03-02
> **alfo_uy said:**
> 
...

2nd i can't change some icons. ej: i linked the media folder to my desktop. automatically gave me a folder icon, wich i do not like. but i can't change it. i do not have permission. not even as a root member not even primary group, not even secondary and not even putting my user under the root group. can't change the icon on my fat 32 secondary hdd.

...



solved.

solution: i noticed that the icon modified folders, like home an others have now inside a little hidden file called directory. wich inside includes the name of the icon to display.
but "/media" does not. i think becouse it has the default icon. so with sudo and nano i created the file, wrote almost what the others include, changing the name to the icon that i wantened and "presto" now my media folder looks as i want it to be.

still fighting the others issues...

---

