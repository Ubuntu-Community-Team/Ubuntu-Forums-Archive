---
title: "i can't get a .sh file executed please help."
date: 2016-04-05
forum: General Help
---

### Post by zap199x on 2016-04-05
[IMG]http://i1362.photobucket.com/albums/r682/zap9x/Screenshot%20from%202016-04-05%20171114_zpsslun1rqg.png[/IMG]
it keeps running in that gedit thing and it would stuck there for hours i had to use terminal to manually run the file .... and it worked but i don't wanna see this problem again.
is it a one time thing or if there's something wrong please help , i've only used ubuntu for one day and all the guides only stop at double clicking the file.

---

### Post by lisati on 2016-04-05
Is the .sh file marked executable? If not, you should be able to change that from the "permissions" tab on the dialog you are seeing.

---

### Post by yetimon_64 on 2016-04-05
> **zap199x said:**
> ...
it keeps running in that gedit thing and it would stuck there for hours i had to use terminal to manually run the file .... and it worked but i don't wanna see this problem again.
is it a one time thing or if there's something wrong please help , i've only used ubuntu for one day and all the guides only stop at double clicking the file.

To do that (double click and execute the file) open any nautilus window ("files" browser window), go to the "Edit" menu > "Preferences" > "Behaviour" tab and select "Run executable text files when they are opened" (or an even safer option is to set as "Ask each time", for a prompt to either view or execute as needed.) 

At the moment it sounds as if the "View executable text files when they are opened" option is selected in which case the default application, gedit as per your screenshot, will be automatically used. 

As lisati noted, the sh file will need to be set as executable in the permissions tab for it to work successfully. 

Regards, yeti.

---

### Post by zap199x on 2016-04-05
ty both for answering , i changed the setting in behavior tab and it worked

---

### Post by yetimon_64 on 2016-04-05
It is good that it worked :). Could you please mark the thread as SOLVED ? [[COLOR=#0000ff]--Here--[/COLOR]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") is a guide for how to do so, if needed. Thanks, yeti.

---

