---
title: "Changing username for installing software"
date: 2014-07-22
forum: General Help
---

### Post by PaulAJohnston on 2014-07-22
Hi
New to ubuntu and I've installed a machine which I need to pass over to someone else.
When they try and add software it prompts them for the username which was entered when installing the system (mine).
The new user is in the sudoers and can add software vi the apt-get command but wants to be able to so this from the GUI.
Any thoughts on where the default username for the gui method of adding software (Software Centre) is stored and how to change it.
Cheers Paul

---

### Post by slickymaster on 2014-07-22
I would recommend not attempting to change a user's name. This is generally wrought with problems when the user's name is statically referenced in configuration files in the form of the user's home directory, **/home/<username>**. These are almost never written in a generic way so it's usually best to just create a new username and then migrate the user's files and data over to the new account.

---

### Post by deadflowr on 2014-07-22
Make the changes through the gui app "user accounts".
Make the new user admin, and change the original user to standard.

Then test it out.
Then when, or if, all is good, simply remove the old user.

And also, what exactly is "in sudoers" mean?
Typically a user only needs to be in an admin(sudo) group, which in turn is reflected in the sudoers file.

---

### Post by PaulAJohnston on 2014-07-22
Sorry if I didn't make myself clear.
All I want is when user 2 logs on and they want to add software with Software Centre that the default username is their username not that of the person who installed the machine.

---

### Post by deadflowr on 2014-07-22
> **PaulAJohnston said:**
> Sorry if I didn't make myself clear.
All I want is when user 2 logs on and they want to add software with Software Centre that the default username is their username not that of the person who installed the machine.

Will the original user be doing anything with the machine?
If not, my method is the one to do.

---

