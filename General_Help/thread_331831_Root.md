---
title: "Root"
date: 2007-01-05
forum: General Help
---

### Post by fredster001 on 2007-01-05
Hi, 

I am trying to install compiz to try out...

I was following this guide, [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/) and it said i need to add 

[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

to my source list which if i'm correct it located in /etc/apt

However it will not let me change this file as it says the owner is 'Root'.
I am the only user on the laptop, and was the first one created when i installed ubuntu last week.
What do i need to do to give me access to do this, i'm guessing i need the rights of 'root' but how?

If it helps, when i open the terminal, the first line i get isL
freddie@freddie-home:~$ 


Thanks

fredster001

---

### Post by drascus on 2007-01-05
I am having a similar issue as I am trying to install a driver through ndis I wanted to place the driver in the root folder but the computer said that It was a protected folder I think there is a way to log in as a root user. I have been reading a bit about it and I thing that there is a way to access it through the terminal by using the sudo command but I am still a newbie myself. 
~Mike~

---

### Post by bikeboy on 2007-01-05
This page should explain it all

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

But if not, feel free to post again of course :)

---

### Post by fredster001 on 2007-01-05
thanks for the link,

however i'm still not sure what the command for adding a line to a file is,

the location of the file is:  /etc/apt\sources.list 
the line i wish to add is:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev

I am quite new to all this btw....

Thanks

---

### Post by finer recliner on 2007-01-05
> **fredster001 said:**
> thanks for the link,

however i'm still not sure what the command for adding a line to a file is,

the location of the file is:  /etc/apt\sources.list 
the line i wish to add is:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev

I am quite new to all this btw....

Thanks


```
gedit /etc/apt\sources.list & 
```

gedit is a basic text editor. once the file is open, just copy and paste the line where it needs to go. save and exit

the & will allow you to open gedit without temporarily disabling the terminal.

---

### Post by finer recliner on 2007-01-05
oh, and to open a root shell (shell where you are root user)

type "sudo -i" and then enter you password.

type "exit" when you are finished being root.

---

### Post by Dr0n3 on 2007-01-05
> **fredster001 said:**
> thanks for the link,

however i'm still not sure what the command for adding a line to a file is,

the location of the file is:  /etc/apt\sources.list 
the line i wish to add is:

deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) edgy dev

I am quite new to all this btw....

Thanks
..
Did you set a root password for the user root? If not go to System > Administration > Users and Groups. There you'll see the root account and you can set a password.

Then open a  terminal. The commands you need to enter are bolded.

**sudo nano /etc/apt/sources.list**

This opens the Nano editor so you can edit files.
Add the line(s) you wish to add.

Press control-x
answer yes
It shows file to write. Just keep answering yes.
Done.

ps.

more important is also that your user account is added to the sudoers file. You can find this file in the /etc folder. You can only edit this file by issuing the command **sudo visudo** as root.
By default the user root and all users of the admin group have sudo privilidges. You can check if your user account is added to the admin group by going to Users and Groups in the System > Administration menu.
This should do the trick.

Also when using the sudo command always enter your own user password when asked. Don't enter the root password, because the whole idea of sudo is that certain users are allowed to have temporary admin privilidges. You only need the root account for root only tasks. For example editing the sudoers file.

---

### Post by fredster001 on 2007-01-05
> **finer recliner said:**
> ```
gedit /etc/apt\sources.list & 
```

gedit is a basic text editor. once the file is open, just copy and paste the line where it needs to go. save and exit

the & will allow you to open gedit without temporarily disabling the terminal.

THanks i tried that, (i realised i put the wrong sort of slash in as well).
It opened the files, i added the lines put when i went to save it is says:

You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again.


Any ideas???

Thanks

---

### Post by fredster001 on 2007-01-05
Ah, Dr0n3

Your advice worked.

Solved that one.

Thanks

---

### Post by bikeboy on 2007-01-05
```
gedit /etc/apt\sources.list
```

Should be

```
sudo gedit /etc/apt/sources.list
```

Again, anytime you need root privalages, just put a sudo before the command, the password it asks for is your normal user password. You don't need to set a root password, your first user should be part of admin by default, and an earlier poster showed how oyu can add new ones.

---

