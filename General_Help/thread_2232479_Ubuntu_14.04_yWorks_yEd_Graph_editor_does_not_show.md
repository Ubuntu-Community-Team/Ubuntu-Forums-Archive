---
title: "Ubuntu 14.04: yWorks yEd Graph editor does not show"
date: 2014-07-02
forum: General Help
---

### Post by whashnez2 on 2014-07-02
Hello there!

I have a problem with the yEd graph editor on Ubuntu 14.04 64bit. I have it installed and after I launch it, the splash window appears loading, but after it's finished yEd does not come up. I can see the yEd icon on the left, but it never comes to the front. I have tried with both java 1.6 and java 1.7 OpenJDK or Oracle runtime environment, for both 32 and 64bit versions of yEd. When I try to launch it from the terminal it does not output any errors or debugging messages so that I can detect what's wrong. Could please help?

Thank you,
George

---

### Post by droetker on 2014-07-08
the yEd package for Linux seems to need a 32bit system, and  the OpenJDK seems to have problems with it.

---

### Post by eyalfir on 2014-09-28
Does anyone have a solution yet?

---

### Post by Steve_Hicks on 2015-03-31
It seems to be a problem with multple monitors and workspaces.

I needed to enable workspaces and then yEd opened in another workspace (and I then moved it to my main one).

See [http://askubuntu.com/questions/539930/yed-shows-no-windows](http://askubuntu.com/questions/539930/yed-shows-no-windows)

---

