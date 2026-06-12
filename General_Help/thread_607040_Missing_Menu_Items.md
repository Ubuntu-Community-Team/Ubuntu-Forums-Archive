---
title: "Missing Menu Items"
date: 2007-11-08
forum: General Help
---

### Post by jmeggers on 2007-11-08
I loaded 7.10 on a new drive on my Lenovo T60p widescreen but it looks like I don't have all the menu choices I should in the System menu. For example, I don't see a users and groups menu item under Administration.  There are others missing as well that seem like they might be associated with administrative control over the OS.  Any suggestions about how to get them to appear?  I have no data on the drive so I could reinstall, but getting the video working was something of a pain and if I don't have to do that I would rather not.  I'm having other issues related to admin rights (can't do system updates because it rejects my password) and in troubleshooting that issue I noticed this problem about the menus.

Thanks for any help

John

---

### Post by prodigalson666 on 2007-11-08
Did you right click on the menu bar or button? You'll get the option to edit menus, you can select or deselect just about anything on your menu through this.

---

### Post by jmeggers on 2007-11-09
I am able to bring up the menu editor.  The items that are missing appear in italics in the list (see attached screenshot), and I'm able to check the box for those items that are unchecked, but it doesn't when I close the window.  The item I checked does not appear in the menu, and when I go back into the menu editor, it is once again unchecked.  The help screen is of little help in terms of why it's behaving this way.  Once again, thanks for any assistance.

---

### Post by chrisccoulson on 2007-11-09
You probably aren't a member of the admin group, and therefore, cannot run adminstrative applications. Type the following in a terminal and pst the output:
```
id
```

---

### Post by jmeggers on 2007-11-09
Here's the output:

uid=1000(jmeggers) gid=1000(jmeggers) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),115(netdev),117(powerdev),1000(jmeggers)

---

### Post by chrisccoulson on 2007-11-10
You aren't a member of admin, so thats the problem. If there is another user on the system that you know is a member of the admin group and can use sudo, you can log in as them, open up the Users and Groups tool, and then add your username to the admin group. 

If there are no other users on the system in the admin group, you'll need to boot in recovery mode (select the recovery mode option from Grub) and add your username from the terminal. At the recovery console, type:

```
usermod -a -G admin <*your_user_name*>
```

That should add you to the admin group and give you sudo privileges

---

### Post by jmeggers on 2007-11-10
Thanks very much for the help.

John

---

