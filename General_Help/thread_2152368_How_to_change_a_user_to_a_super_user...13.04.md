---
title: "How to change a user to a super user...13.04"
date: 2013-06-07
forum: General Help
---

### Post by PIE09gbLmgG6 on 2013-06-07
Ubuntu Team,

I've been at trying to add another user to the admin level...is there a trick to this?

Clicking on the user and changing the Account Type from Standard to Admin isn't offered...how do I set my second user as an admin as well?

Appreciate the help...

Mike-

---

### Post by matt_symes on 2013-06-07
Hi

We're not the Ubuntu Team. We're just Ubuntu users like you :)

The easiest way to do what you want is from the terminal.

Log into your normal user (the one with admin rights).

Open a terminal (type terminal in the dash) and type

```
sudo usermod -aG sudo <user_name>
```

Ubuntu is case sensitive so that needs to be a capital G in the command above.

Change <user_name> to the name of the user you want to give admin rights to.

Enter your password. It will not be echoed to the screen. This is normal.

Log into the new user and they should have admin rights.

To check your new user when you have logged in, open a terminal and type

```
groups
```

You're looking for the word sudo returned. For your reference, here are mine...

```
matthew-S206:/home/matthew % groups 
matthew adm cdrom **sudo** dip plugdev lpadmin sambashare
matthew-S206:/home/matthew % 

```

If that does not work then repeat the above steps but switch sudo for admin and re-run the above commands.

Belonging to the sudo group bistows admin rights in newer version of ubuntu, but belonging to the admin group does in older versions.

I am not running Unity are the moment (trying something different for a little while), so i cannot show you how to do it using the GUI.

Maybe someone else will.

Kind regards

---

### Post by Frogs Hair on 2013-06-07
Search "edit sudoers file" or "add user to sudoers file". I have not done this before, but found different instructions . Be very certain of the method before proceeding.

---

### Post by deadflowr on 2013-06-07
```
[COLOR=#000000]I am not running Unity are the moment (trying something different for a little while), so i cannot show you how to do it using the GUI.[/COLOR]
```

The gui in unity is simple.
Open the system settings, and go to user accounts.
Click the unlock button at the top and enter you current admin user's password.
Then click on the plus sign under the listing of current users.
The fill out the needed info, and make sure the dropdown box is set for administrator and not standard.
Make up a password, and enter it twice for confiramtion.
Then click create, or okay, or whatever it says.

---

### Post by PIE09gbLmgG6 on 2013-06-07
Ms,

Appreciated the help. Worked like a charm...once I did that the login boxes changed and everything had more items to choose from...it works!

Mike-

---

