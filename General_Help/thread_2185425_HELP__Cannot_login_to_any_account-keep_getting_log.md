---
title: "HELP:  Cannot login to any account-keep getting login screen"
date: 2013-11-02
forum: General Help
---

### Post by philnlaura on 2013-11-02
[COLOR=#333333][FONT=UbuntuRegular]I was using these commands in terminal:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo apt-get install gksu[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]gksu nautilus[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I needed to move some files from one account into another & then I wanted to rename some of the accounts. I got a failure message & my desktop wallpaper went black. I logged out & now I cannot log into ANY account at all. One account is my son's (with his school homework on it) & the other is mine (an admin). There is no password on my son's but I have one on mine. I cannot get into either account...I am brought back to the login screen. I can't even get to a terminal to make any changes. Any help would be appreciated![/FONT][/COLOR]

---

### Post by ginger3 on 2013-11-02
I am not sure if i can help. but can you clarify: did you successfully rename your accounts? do you get a log-in screen with the option to log-in with your new usernames? can you log in as guest?

---

### Post by philnlaura on 2013-11-02
I'm still new at terminology so I may not have described the situation correctly.  

When I set up Ubuntu 13.10 on my son's PC, I chose the name "Leslie02".  Once I had the admin established, I then added my son as a user in a terminal.  

Since I'm still learning what to type in the terminal for the command, I must have created a user (account?) named "username".  

So now I have 2 folders in the home folder:  Leslie02 and username.  And the Admin account is under "Leslie02" and my son is under "username" when I go to the User Account option in the System settings.  

When he saves any work, he has either a "Home" folder or a "Username" folder.  I don't want "Username" but I just want a "Home" folder.  

So I tried to merge the 2 together using the commands mentioned above (in Nautilus). That put his homework folder on MY desktop, too (which I don't need).  So I went in Nautilus (into the Home folder) & renamed the 2 folders inside.  I renamed "Leslie02" to "Admin" and "Username" to "User". 

In trying to copy the data from one folder into another, I created an "Untitled Folder" that copied all the data into there.  I then tried to move that data into the "Admin" folder & delete the "Untitled Folder" since I didn't mean to create it.  

When I did, I got several errors & my desktop wallpaper went to black and I logged out to see if logging back in would clear things up.  

I entered my correct password & the screen went black (which it does when it's logging me in) but it then brought up the login screen again.  

So I went to my son's account (who does not have a password) & tried to enter his account but the same thing happened...it brought up the login screen again.  So, now I can't get into any account & he has homework that needs to be turned in next week.

---

### Post by Elfy on 2013-11-02
I've edited your post to make it a bit more readable. Not everyone that comes here to help uses English as a first language.

This is the related AskUbuntu enquiry I assume - if not - you might want to read it

[http://askubuntu.com/questions/370089/help-im-locked-out-of-all-ubuntu-accounts](http://askubuntu.com/questions/370089/help-im-locked-out-of-all-ubuntu-accounts)

Posting that here so that information between times doesn't get jumbled.

---

### Post by steeldriver on 2013-11-02
First of all, don't panic - nothing is lost (yet ;) )

In Linux, the folder called /home is a system folder CONTAINING every user's actual "home" folders (which are named the same as the respective users, by default). When you log in using the GUI, the login process looks for a directory whose name matches the username, and tries to write stuff there (in particular, an Xauthority file that says who the GUI session belongs to). Since your /home/xxx directories now have the 'wrong' names (as far as the system is concerned - i.e. they are not the same as the users to which they belong) that write fails and the session can't start.

Exactly the best way to proceed is going to depend a little on what state everything is in right now. You should still be able to log in to a non-GUI session as 'Leslie02' by hitting key combination Ctrl-Alt-F1 (or Ctrl-Alt-F2, so on up to F6). If that works, type the following and post back with the results

```

ls -l /home

egrep ':[0-9]{4}:' /etc/passwd

```

If it doesn't work, you can boot into a recovery shell, or using a liveCD, and fix everything from there

---

### Post by philnlaura on 2013-11-02
Thanks for you help... the link you posted was actually by me relating to this issue.

I did what was suggested based on these posts:

"[COLOR=#444444][FONT=UbuntuRegular]I guess you have "rename(d) some of the accounts" by renaming the home folders. Is it right? If this is the case, then you can use a LiveCD to re-rename the folders back to their original names."   --I did try to rename the folders.  Then, I followed the info from this post:

"[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]If you hold [shift] during boot you will get a textmode menu.[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]Choose (recovery mode)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After boot you will be greeted by a colorful texmode screen choose root[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Make the system read/write[/FONT][/COLOR]
mount -o rw,remount /
[COLOR=#333333][FONT=UbuntuRegular]add a new user to your system:[/FONT][/COLOR]
adduser emergency
[COLOR=#333333][FONT=UbuntuRegular]give this sudo permission:[/FONT][/COLOR]
addgroup emergency sudo
[COLOR=#333333][FONT=UbuntuRegular]just reboot with reboot and login with your freshly made account.
If this all works out OK you can start repairing the things that went wrong."

I successfully created an "emergency" account & was able to access my data.  I got a couple of notices saying there were some things that are wrong but I could not report them...  However, I did rename the folders to their original names & rebooted.  Yet I am still unable to log into either the Admin or my son's account.  I can login successfully to the "emergency" account but the other 2 continue to bring me back to the login screen.[/FONT][/COLOR]

---

### Post by grahammechanical on 2013-11-02
Every installation of Ubuntu has a /home folder and in that folder are the folders of the users. In the case of someone like me who is a single user I have just one folder with my user name. If we create another user then that users gets a folder inside the home folder. So, far so good.

You started off with a /home folder that had a Leslie2 folder in it. That was your folder - you as administrator. Then you created a user for your son with the user name of "username." So, the /home folder now has 2 folders - Leslie2 and username. There was nothing wrong with this.

By renaming Leslie2 to Admin you hid your user configuration files from Ubuntu. That is why you are getting that black screen. You cannot login because Ubuntu cannot find the Leslie2 folder. There is a command line way to change passwords but I am not familiar with the commands. Also it may be fixed by renaming the Admin folder back to Leslie2. But how to get to a command line. I can tell you that much.

When you next boot, at the Grub menu select Advanced options for Ubuntu and select Recovery Mode. At the Recovery mode screen select Network. That will make a network connection and it will also put the file system into read/write mode which you need if you are going to edit system files. When you get back at the Recovery menu select Root and you will be at a command line prompt with root access to the file system. You now need to find that folder and rename it.

I am not so clever with Linux commands. Some I know of.

ls  = lists files and folders in current directory/folder. The current directory may be /home.

cd = change directories. cd /Admin will put you in the Admin directory/folder.

mv = move. Can be used to rename a file.

mv Admin Leslie2

I have not tested this, which I like to do before suggesting stuff.

Regards.

---

### Post by philnlaura on 2013-11-02
Okay.  I think I know where the problem is but how to correct it may be another story.  Here's what I got in terminal when I typed in your code:

emergency@leslie02-Aspire-M1100:~$ ls -l /home
total 12
drwxr-xr-x 14 emergency emergency 4096 Nov  2 16:03 emergency
drwxr-xr-x 23 leslie02  leslie02  4096 Nov  2 13:57 Leslie02
drwxr-xr-x 11 root      root      4096 Nov  2 13:54 username
emergency@leslie02-Aspire-M1100:~$ egrep ' [0-9]{4} ' /etc/passwd
emergency@leslie02-Aspire-M1100:~$ 

The problem is the account "username" was not intended to be called that...and it was created in the root, while the others were not in the root.  So my renaming the files in the GUI created the issue.

I then went into a terminal on my "emergency" account & deleted the 2 accounts that I cannot log into.  I created 2 new accounts in the terminal & saw that they were listed in the "User Accounts" that is in the System Settings within the GUI.  I then logged out of the "emergency" account & went to log onto the new accounts I just created & was still brought back to the login screen just like previous attempts.  So I am still facing the same issue & I've wasted 3 hours of my Saturday on this.

---

