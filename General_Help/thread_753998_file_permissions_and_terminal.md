---
title: "file permissions and terminal"
date: 2008-04-13
forum: General Help
---

### Post by searayman on 2008-04-13
i have a folder in ubuntu that has two icons over it. One looks liek a lock and the other is a box with an x in it. I have a bunch of pictures in this folder i need to get out. At the moment i can not even view the contents of the folder. So how can i unlock it?

thanks

---

### Post by sekinto on 2008-04-13
You can edit ownerships and file/folder privileges using the "chown" and "chmod" commands. You can Google those commands to find out the different things you can do with them (or you can use the "man chown" or "man chmod" commands to see all the options you have and how to use the commands).

If you just want to extract these pictures this one time though you should be able to do "gksudo nautilus" and then navigate to the directory and drag'n'drop the files you want.

---

### Post by aysiu on 2008-04-13
What folder is this? If it's outside of /home/*username*, then you should not change ownership or permissions on the folder, but there are other ways to modify it.

More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

