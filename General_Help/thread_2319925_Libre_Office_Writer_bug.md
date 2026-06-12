---
title: "Libre Office Writer bug"
date: 2016-04-08
forum: General Help
---

### Post by logie on 2016-04-08
I'm running Ubuntu 14.04 64-bit on a NUCi3 with an Intel Core i3.
 In Libre Office Writer I tried to alter my Default style, but when I tried to save the new style, it reverted to the old version.  I looked at Help, and it showed me the following message:


            D'oh you found a bug (text/shared/00/000000401.xhp#dokuspei not found)

 
Can anyone explain?

---

### Post by bapoumba on 2016-04-11
May be these ?
[https://bugs.documentfoundation.org/show_bug.cgi?id=82981](https://bugs.documentfoundation.org/show_bug.cgi?id=82981)
[https://bugs.documentfoundation.org/show_bug.cgi?id=71039](https://bugs.documentfoundation.org/show_bug.cgi?id=71039)

---

### Post by logie on 2016-04-12
Thanks for this.  It looks like the first of the two.  Unfortunately, I have not got a clue as to what the message means.  I am quite seriously ignorant , and would welcome some very simple instructons.  Thanks in anticipation.

---

### Post by bapoumba on 2016-04-12
From what I understand, templates for help menus have changed places, but this has not been reflected on all other items that use them (i may be wrong here :)). First bug link has been marked as duplicate of second bug link which is the one to follow or to comment in should you wish to do so. 

Which LO version do you use ? I use custom templates and styles for documents, but have never run into this. May be because I leave the Default alone and use mine to open docs from. Most of the time, when looking for something, I use the online help and not the one built in.

Edit : and the first bug link relates to a French localization. Are you using a custom localization ? If so, do you still see it when reverting to English for ex ?

---

### Post by logie on 2016-04-17
Thanks for your help.  I have decided to leave things be.  I can get by with the settings I've got, and life is too short ...

---

### Post by bapoumba on 2016-04-18
OK :)
One thing I forgot to mention as to why I leave all the default alone and create my own settings. One day, I did something on a default style that I could not reverse . Either I ran into some awkward bug or most probably I messed things up quite badly. And I was stuck as it was some index table style. So I now keep all the defaults and create my own stuff. At least, if I mess up something, I aways have the default to revert to.

---

