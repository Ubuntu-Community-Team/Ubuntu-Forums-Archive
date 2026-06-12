---
title: "bash /etc/profile Access Denied"
date: 2008-04-25
forum: General Help
---

### Post by cometa2k7 on 2008-04-25
My computer has gone horribly wrong.

The "sudo" command wasn't working, so I rebooted, thinking that this would help, but it didn't.

When I boot now, it crashes and says that "/etc/profile Access Denied".

I have checked the ownership of the files on my harddrive, but they are all owned by numbers (i.e. 1000, and 1001) These refer to the user.


Another problem which is incorporated into this, is that when I boot, and it fails to do so properly, it asks me to login, I do so, but it fails, and logs me into another account, which is a secondary to my own. 

I can't "sudo", and I can't boot.

**[SIZE="4"]Please help!!![/SIZE]**

Also, I currently don't have an Ubuntu installation disk, I lent it to my mate. I could make one if necessary, or get the disk back, because he is installing it this weekend.

---

### Post by Roukoun on 2008-04-25
What happens if you try to launch the Root Terminal (Applications > System Tools > Root Terminal) ?
If it doesn't work there is one more thing you can do but you don't have many possibilities:

Open the Terminal (Applications > Accessories > Terminal) and type:
    $ sudo nautilus
  ...give your password
Then you are logged in as root and you can handle your filesystem from the window that was appeared....  


I'm so curious to find out what happened!!!!!!!!!!!

---

### Post by cometa2k7 on 2008-04-26
> **Roukoun said:**
> What happens if you try to launch the Root Terminal (Applications > System Tools > Root Terminal) ?
If it doesn't work there is one more thing you can do but you don't have many possibilities:

Open the Terminal (Applications > Accessories > Terminal) and type:
    $ sudo nautilus
  ...give your password
Then you are logged in as root and you can handle your filesystem from the window that was appeared....  


I'm so curious to find out what happened!!!!!!!!!!!

I can't get a graphical display, because I can't actually log in. When I log in, it's terminal only, and in the wrong account, which doesn't have "sudo" privileges. I can't log in as root, because I don't know the password.

I have used three different live CDs to change the ownership of the files, but it keeps reverting to 1000, or 1001.

---

### Post by cometa2k7 on 2008-04-26
I just checked the /etc/profile against another from a live CD, they are exactly the same, so I'll assume that they are correct.

The number problem was just because Ubuntu decided to save the names as the user's number, not the name, which isn't a problem, it should recognise it in my system when I boot.

But I still can't boot. I need help.

---

