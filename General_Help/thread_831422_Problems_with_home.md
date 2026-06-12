---
title: "Problems with home"
date: 2008-06-16
forum: General Help
---

### Post by tatoniss on 2008-06-16
I have ubuntu 8.04 and i think I have lost privileges to access my home directory, When i log in i get this error(picture of error provided)
If anyone knows how to fix this it would be a great help and by the way I am new to ubuntu.

---

### Post by damis648 on 2008-06-16
try this in terminal:
```
sudo chmod 644 /home/user/.dmrc
```
replacing user with your user name and log out and back in and see if you still get the messages.

---

### Post by tatoniss on 2008-06-16
This did not work, is there anything else i could try?

---

### Post by damis648 on 2008-06-16
Just try making a simple text file in your home directory and see if it works.

---

### Post by tatoniss on 2008-06-16
I think that worked but it still says the error at login, I tried using root to change the permissions to the user but still has error

---

### Post by damis648 on 2008-06-16
No, you must make the file in YOUR home folder.. so try copying the file into 'tatoniss' and reply back if it worked.

---

### Post by tatoniss on 2008-06-16
yes it worked i copied it into tatoniss

---

### Post by damis648 on 2008-06-17
Hmm... it is interesting that all the permissions seeme to be ok. Try editing the properties of 'tatoniss' and check to make sure it is owned by you and only you can read and write to it.

---

