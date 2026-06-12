---
title: "User Security"
date: 2007-06-11
forum: General Help
---

### Post by nami on 2007-06-11
In windows when I created user accounts, they were not able to view, read, execute another users files.  When I created a new account in ubuntu and give it "unprivileged" attributes, it was still able to view all my files and even open them...

How do I make my stuff private from other users?

---

### Post by taurus on 2007-06-11
You just change permissions of your $HOME account so nobody can view your stuff.

```
chmod 700 /home/**username**
```
Replace **username** with your actual login name.

---

### Post by nami on 2007-06-11
thanks, will try that tonight!

---

### Post by nami on 2007-06-15
> **taurus said:**
> You just change permissions of your $HOME account so nobody can view your stuff.

```
chmod 700 /home/**username**
```
Replace **username** with your actual login name.

i tried that and it locked me out completey.  i can no longer start any programs and it wont even let me login or log out of ubuntu.

it says:

could not load application
failed to change to directory /home/nami
permissio denied

i typed chmod 700 /home/nami

---

### Post by dannyboy79 on 2007-06-15
well is "nami" the owner of the /home/nami/ directory? if not, than yeah, you're screwed.
you can fix this by booting to the live cd, then you need to create a folder (sudo mkdir /media/install) where ever you want to when you're in the livecd, then mount whatever disc (say /dev/hda2) has your ubuntu OS on it. you can find out which disc to mount using this command
sudo fdisk -l
then it will return all your discs and their partitions
once you mounted the certain disc to that folder, which is done with this command
sudo mount /dev/hda2 /media/install
(note: install is the folder I created within the /media/ folder on the livecd)
then you just change the permissions back to what they are so at least you can boot into your system. that would be this command
sudo chmod 777 /media/install/home/nami
then just exit the live cd and reboot your computer.

for the record, I don't think you can make it so the group owner doesn't have read permissions which is what 700 did. it would need to be sudo chmod 770, and that would stop everyone else from reading the directory. Now that I think about it, I don't even think that would work!! Not sure how to help with the original question, only how to get you back into your system.

---

### Post by nami on 2007-06-15
thanks, i'll do that.

---

### Post by airtonix on 2007-06-15
strange.....all the versions of ubuntu since breezy have : 

+ allowed me to be first user on install (as expected) thusly becoming first sudo priviledged user.
+ created more users via the "system -> administration -> users and groups" gui.
  - users created are : 
    - given own home as a folder with a name thta matched their username, this folder exists under "/home/"
    - not allowed me to read the contents of other users homes.
    - can see those homes listed under "/home/" as individual folders named accordingly to the user owning the respective folder.
    - I as the first user cannot view nor edit the folder nor the contents of any other users home other than my own, and roots when impersonating via sudo.


[B]conclusion
[/B]I suspect that the checkbox for "privledged user" is related to wether or not the user is in the sudo list or not. meaning that they are able to peform superuser operations by prefixing thier commands with "sudo" or "gksudo".

**The solution**
firstly....windows is different to unix in its granulisation of its acl permission bits. (blah)so here is a caveat to my explanation : 
 + realise that you have a user account, its name is the one you choose.
 + this account has its own user group of the same name.(i call it the Your-UserName-Group in this post)
 + you use this Your-UserName-Group for sharing your stuff with other users by placing their username in the usergroup with a name matching your username. 
 + when controlling this aspect, you will use the second section for users in "Your-UserName-Group"
 + The third section is for those who are not You, or not inYour-UserName-Group.

 1. open nautilus (your filebrowser in gnome)
 2. right click on said folder. select properties.
 3. move to the permissions tab.
 4. move to the "Others" section where you will control access for people who are not  not in your Your-UserName-Group and change the "Folder-Access" drop-down-menu value to "None"
 5. move to the the "File-Access" drop-down-menu value to "None".

It may be possible that by doing the above, you will infact remove authorisation for system services to deal with certain config files present in your home. 


But i believe that these steps are not needed, for i have not pefromed these operations on any of my installs.....and i cannot see other users folder contents without using sudo.

and remember "privledged user" is most likley alluding to "add-this-user-to-the-sudo-list"....ala adding a windows user account to the administrator group. But better since the thing that annoys them when peforming admin operations will require a password....whereas the windowsBlista clone of this step will just keep requiring you to blindly click "OK?"....whats the point again?

---

