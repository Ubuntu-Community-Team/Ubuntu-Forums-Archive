---
title: "Set file/folder permission per-user basis"
date: 2007-08-23
forum: General Help
---

### Post by invizibility on 2007-08-23
All,

I am working on a web server setup at home and just ran into this problem. Is there any way to allow the www-data (default Apache user) user to write to a specific folder without adding that user to my group. I don't want to give write permissions to any one apart from the owner.

Any clues are highly appreciated.

Thanks.

---

### Post by schallstrom on 2007-08-23
You have some directory belonging to your normal system user and your normal system user group. Now you want to give the user www-data, but not any other user, write access to this directory, right?

You either have to change the group ownership of the directory to some group www-data is member of (like the group www-data) or you have to add www-data to some group which has access to the directory (like your normal user group) and then add write permission for the group.

But what exactly do you want to do? A general tip: It's better to ask what you want to achieve in general then asking very specific questions (see [http://catb.org/~esr/faqs/smart-questions.html#goal](http://catb.org/~esr/faqs/smart-questions.html#goal)).

---

