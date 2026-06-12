---
title: "Locked photo files"
date: 2008-04-14
forum: General Help
---

### Post by tinkietruck on 2008-04-14
I just uploaded some pictures using gphoto2.  I see the files, but they are locked.  The owner is root.  I want to be the owner so I can see the photos.  The files are located /home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11.

Please help.  I have just solved the uploading problem.  

Thanks,
Brandy

---

### Post by Znort_Ubern00b on 2008-04-14
open terminal and type

sudo chown -R *username* /home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11
press enter and enter your password( i take it you are inadmin group)
user name is the user you want to own them.. i guess thats your username

---

### Post by tinkietruck on 2008-04-14
> **Znort_Ubern00b said:**
> open terminal and type

sudo chown -R *username* /home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11
press enter and enter your password( i take it you are inadmin group)
user name is the user you want to own them.. i guess thats your username

I tried.  Here is what happened.

```
 tinkietruck@tinkietruck:~/2008-4-11$ sudo chown -R tinkietruck /home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11
chown: cannot access `/home/tinkietruck/My': No such file or directory
chown: cannot access `Pictures/_2008': No such file or directory
chown: cannot access `Photos/_April': No such file or directory
chown: cannot access `2008/2008-4-11': No such file or directory
tinkietruck@tinkietruck:~/2008-4-11$ 

```

I copied and pasted the file location.  I am in the admin group because it's our personal home computer.

Thanks,
Brandy

---

### Post by Barrucadu on 2008-04-14
He forgot to escape the spaces... Here you go:

sudo chown -R username /home/tinkietruck/My\ Pictures/_2008\ Photos/_April\ 2008/2008-4-11

---

### Post by tinkietruck on 2008-04-14
Will try again, thanks.

---

### Post by tinkietruck on 2008-04-14
This is what I did.  Please help.


```
tinkietruck@tinkietruck:~$ sudo chown -R tinkietruck /home/tinkietruck/My\Pictures/_2008\Photos/_April\2008/2008-4-11
chown: cannot access `/home/tinkietruck/MyPictures/_2008Photos/_April2008/2008-4-11': No such file or directory
tinkietruck@tinkietruck:~$ sudo chown -R tinkietruck /home/tinkietruck/Desktop/link to My Pictures/_2008 Photos/_April 2008/2008-4-11
chown: cannot access `/home/tinkietruck/Desktop/link': No such file or directory
chown: cannot access `to': No such file or directory
chown: cannot access `My': No such file or directory
chown: cannot access `Pictures/_2008': No such file or directory
chown: cannot access `Photos/_April': No such file or directory
chown: cannot access `2008/2008-4-11': No such file or directory
tinkietruck@tinkietruck:~$ sudo chown-R tinkietruck/home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11
sudo: chown-R: command not found
tinkietruck@tinkietruck:~$  sudo chown -R tinkietruck/home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11
chown: `tinkietruck/home/tinkietruck/My': invalid user
tinkietruck@tinkietruck:~$ sudo chown -R tinkietruck /home/tinkietruck/My Pictures/_2008 Photos/_April 2008/2008-4-11
chown: cannot access `/home/tinkietruck/My': No such file or directory
chown: cannot access `Pictures/_2008': No such file or directory
chown: cannot access `Photos/_April': No such file or directory
chown: cannot access `2008/2008-4-11': No such file or directory
tinkietruck@tinkietruck:~$ 



```

---

### Post by tinkietruck on 2008-04-14
Thanks for all of the help on this.  The directions given have solved my problem.  I have access to the photos now.  I will remember to do this each time I upload pictures, unless there is some way that I can have access to every picture.  

I may have figured it all out.  Thanks again for all the help.


Brandy

---

