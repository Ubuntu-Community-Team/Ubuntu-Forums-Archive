---
title: "Cannot create user"
date: 2007-03-26
forum: General Help
---

### Post by Seppl on 2007-03-26
Hi,

I installed Ubuntu Edgy last weekend and I'm really happy with it. But after playing around a little bit with Beryl, the session crashed and I was not able to log on with this user anymore. Since I didn't really do anything useful yet with this user, I simply deleted him. But now, I am not able to create another user with the name of the user I deleted. Some information seems to be still hanging in the system. Creating a new user with a different name works fine. Can anybody help me on this?

Thanks in advance!

Seppl

---

### Post by wj32 on 2007-03-26
Since you created a new user, I'm assuming you got a root terminal... When you're in the root terminal, type:

rm -r /home/[username]

---

### Post by zvacet on 2007-03-26
Go to the users&groups and create user.Try if it works with your username you deleted.Yo will give him old password too.Look in home directory if you still have folder with deleted user.I´m guessing that can be reason you can not create what you want,if you allready have folder with that user.Try with users&groups.

---

### Post by Seppl on 2007-03-26
Hi,

thanks for your quick help! I already deleted the home directory using 
sudo rm -rf /home/[username]. But I'm still not able to create the new user. What I found out now: Creating [username] doesn't produce an error and [username] is even shown in the user list of users&groups, but /home/[username] doesn't get created and when I log off and on again, the new user doesn't apperar in the list of users&groups anymore...

Regards, Seppl

---

### Post by gravz84 on 2007-03-26
I have a similar problem and I need help pls!!

what i wanted to do was give myself complete root privileges since nautilus shows a lot of folders as locked.. and i can't change the permissions cos it says only root has permission to do that?? 

So i did something with visudo and commented one of the lines.. i think its purpose was to enable the root account so I don't have to type in the pwd repeatedly!

Now I can't execute anything as root with sudo command!!!
when I type "sudo command" it doesn't prmpt for pwd but doesnt do anything either!!!
I can't even edit sudo now with visudo!! nor any program that requires root..eg synaptic!!

and also how does sudo work with nautilus or any other graphical browser?? i mean the locked folders? u might be able to access them in terminal with sudo but wat about thru nautilus!!!!

HELPPPP!!!!!!!!!
I am really getting frustrated with ubuntu now..

---

### Post by wj32 on 2007-03-26
Lemme see...

1. I create an user called "asdf". It creates /home/asdf.
2. I delete "asdf'. I see that /home/asdf is still there. I see that asdf missing in both /etc/passwd and /etc/shadow (good thing).
3. I delete /home/asdf.
4. I recreate an user called "asdf". /home/asdf is created again.

I don't see the problem... If you can spot any differences in my testing then that would be good.

---

### Post by wj32 on 2007-03-26
And... how exactly did you delete the user? Did you do it in System > Administration > Users and Groups?

---

### Post by zvacet on 2007-03-26
So you have user but don´t have directory.
```
sudo mkdir username
```

---

### Post by Seppl on 2007-03-26
@wj32: Yes, I used System > Administration > Users and Groups to delete and create the user.
@zvacet: No, I don't have the directory, no user in System > Administration > Users and Groups and no entry in /etc/passwd.

Can anybody tell where user informations are stored except from 
/etc/passwd and 
/home/[username]?

Thanks in advance,
Seppl

---

### Post by pppetter on 2007-03-26
gravz84---> if you want to use eg. nautilus with root privileges then run the following command:

gksudo nautilus

But I don't really see why you would want to do that, the folders and files are protected for a reason... Btw, this does not mean that you can open the files as a root user, if you want to be able to do that, see this thread [http://www.ubuntuforums.org/showthread.php?t=371412&highlight=nautilus+script+root]("http://www.ubuntuforums.org/showthread.php?t=371412&highlight=nautilus+script+root").

I honestly cant think of any reason for anyone to edit visudo, just as I cant see any reason for anyone to enable the root account(it's unsecure) - and if I remember everything right, you don't enable the root account by using visudo.

Anyways, to fix this, I would restart my computer and enter the GRUB menu and choose recovery mode (should be in the kernel list there) - then you'll be root, and then just type visudo and fix whatever you messed up.

---

### Post by wj32 on 2007-03-26
Wrong thread! Here it is: [http://ubuntuforums.org/showthread.php?p=2355210]("http://ubuntuforums.org/showthread.php?p=2355210")

---

### Post by octavianh on 2007-03-28
There is definitely a bug involved with the graphical "Users and Groups" applet.  Following steps reproduce the bug in the most current Feisty Fawn with all updates.

1.  Open "Users and Groups"
2.  Create user "test" with Administrator role
3.  Delete user "test" from the same applet
4.  Delete home directory using "sudo rm -Rf /home/test"
5.  Open "Users and Groups"
6.  Create user "test"
     - user shows up in the list in the applet
     - home directory not created
     - user added to /etc/group but NOT to /etc/passwd
7.  Log out and the user vanishes and no longer will appear in the "Users and Groups" applet

8.  commandline "adduser test" works correctly however.

This bug is confirmed by me on both i386 and PPC versions of Feisty with all the latest updates as of March 28th, 2007.  This leads me to believe that the graphical user management tool is storing either the old user name or the "administrator role" somewhere and this conflicts with the attempt to re-add the user after deletion.  At least it's fair to speculate that's what it might be.

---

### Post by octavianh on 2007-03-28
Filed as bug report so hopefully we'll get someone to look at this.

[https://launchpad.net/ubuntu/+bug/97527](https://launchpad.net/ubuntu/+bug/97527)

---

### Post by Seppl on 2007-03-29
Hi octavianh,

thank you for your reply! This looks exactly like the behaviour I got from the system. I will try to add the user using the "adduser" command as soon as I am back at my machine.

Thanks!
Seppl

---

### Post by zvacet on 2007-03-29
[https://help.ubuntu.com/community/AddUsersHowto]("https://help.ubuntu.com/community/AddUsersHowto")

read Command Line and last line is one you are looking for.Put your username and group is **admin**

---

### Post by iosh on 2008-02-09
the solution to this problem is really simple..
for ex:
i created the user john, in /home/john
then i delet john using rm -rf john
then i went to system, preferences, users and groups and i delete john account
after that i tried to create again john's account, but it didnt appeared..
to solve this problem after deleting john folder, and john account, go to system, preferences, users and groups and select "manage groups" and scroll down to the bottom of the list, were it still is john's name, then select it and delete it...after that you can create a new account with the same name :)

hope that this was useful, and sorry for the english mistakes:lolflag:

---

