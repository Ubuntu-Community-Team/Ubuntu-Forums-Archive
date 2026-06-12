---
title: "Newbie, Kinda overwhelmed, Help!"
date: 2008-07-07
forum: General Help
---

### Post by minorm73 on 2008-07-07
i am new to ubuntu and linux i have some real basic questions
1st:  how do i access the command Line?
2nd:  how do I mount my hard drive formatted in ntfs?
3rd:  how can i execute exe apps?
4th:  how can i execute linux apps?
please be patient with me i am new and I am really a quick learner.
Thanks and God Bless you all and God Bless Linux!

---

### Post by Cap'n Skyler on 2008-07-07
hey !! 
welcome to the forums !! :)
command line:
applications-accessories-terminal(linux calls it a shell/terminal)
linux cant execute the exe like windows does--but there are executables that you can do.
  it depends on what you have downloaded or want to do.i can say if you cant make it execute,right click-then properties the file and make sure to give yourself permission to write view and execute the file.i learned that the hard way LOL

welcome to teh ubuntu!!
the best and easiest of the regular people linux!!:guitar:

---

### Post by iaculallad on 2008-07-07
> **minorm73 said:**
> i am to ubuntu and linux i have some real basic questions
1st:  how do i access the command Line?

Method 1: Navigate to Applications->Accessories->Terminal.
Method 2: Press Alt+F2, and input "gnome-terminal" (w/o double quotes) and press enter.

> **minorm73 said:**
> 2nd:  how do I mount my hard drive formatted in ntfs?

By using the mount command:

i.e:

```
mount -t ntfs /dev/hda5 /media/mountpoint
```

> **minorm73 said:**
> 3rd:  how can execute exe apps?

Either by using WinE, Cedega, or CrossOver

> **minorm73 said:**
> 4th:  how can i execute linux apps?

Either by entering the application name on the terminal or selecting it from the Applications menu.

Note that some applications needs sudo, gksudo, gksu command to execute properly.

---

### Post by Cap'n Skyler on 2008-07-07
hmmm
to execute linux apps...usually click or double click them if you can find it
your applications,places or system menus.and please do explore the synaptic package manager--it has a lot of cool stuff for you to do all sorts of things.:popcorn:

---

### Post by falcon61102 on 2008-07-07
Welcome.

Also, if you are going to be using that NTFS partition quite regularly and don't want to constantly mount it manually, check out this HOW-TO by Victormd... work's great:

[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

---

### Post by Victormd on 2008-07-08
> **minorm73 said:**
> 2nd:  how do I mount my hard drive formatted in ntfs?

Check the link on my signature... :)

> **minorm73 said:**
> 3rd: how can i execute exe apps?
To execute EXE apps you will need to install a package called Wine (note that not all apps will work as exe apps are windows standard). You can find more about it at winehq.org and to install, open a terminal and type:
```
sudo apt-get install wine
```
Before doing this, I would suggest you look up [how to manage repositories]("https://help.ubuntu.com/community/Repositories/Ubuntu") (database of linux apps that you can install directly using the "sudo apt-get install" command)

> **minorm73 said:**
> 4th: how can i execute linux apps?
Depends on the apps you're trying to execute. Do you want to install apps? If so, then refer to the repositories again... :) Otherwise, they should be listed under the Applications menu.

Hope this helps.

---

### Post by Victormd on 2008-07-08
> **falcon61102 said:**
> Welcome.

Also, if you are going to be using that NTFS partition quite regularly and don't want to constantly mount it manually, check out this HOW-TO by Victormd... work's great:

[http://ubuntuforums.org/showthread.php?t=802699](http://ubuntuforums.org/showthread.php?t=802699)

Thanks, glad to know it helped! :guitar:

---

### Post by falcon61102 on 2008-07-08
Yeah, worked like a charm... thank you.

---

