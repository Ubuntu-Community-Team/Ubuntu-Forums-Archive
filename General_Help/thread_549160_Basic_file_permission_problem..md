---
title: "Basic file permission problem."
date: 2007-09-12
forum: General Help
---

### Post by randomusername on 2007-09-12
OK, so this is probably really simple but googling has gotten me nowhere. :)

If I wanted to grant user "x" write permission to directory "y" without changing the owner of the directory or giving the user any additional rights how would I do so?

---

### Post by aot2002 on 2007-09-12
>>If I wanted to grant user "x" write permission to directory "y" without changing the owner of the directory or giving the user any additional rights how would I do so?

just allow everyone to write to that directory silly
chmod 666 /tmp

replace tmp with your directory name/path
this would not change the user additional rights but would allow any other user to also write to that directory

---

### Post by logos34 on 2007-09-12
> **aot2002 said:**
> chmod 777 /tmp

wouldn't

**sudo chmod a+w /path/to/dir**    (or 'g+w' if the other user belongs to group)

be more specific and in line with what the OP asked for--i.e. 'not giving the other user any additional rights' (like execute)?

---

### Post by anaconda on 2007-09-12
yep, Or you could make a new group, and then grant that group access to that directory.. Then you can add anyone you want to that group...

and to do that in command line you would need to do:
```
sudo addgroup nameOfTheGroup
sudo adduser usernameYouWantToAddToTheGroup nameOfTheGroup
sudo chown yourUserName:nameOfTheGroup /path/to/dir
sudo chmod 770 /path/to/dir
```
First create the group
then add the user to that group
then make you and the group, owners of that directory
then give rwx (or whatever you want) rights to that directory to all the members of the group and you (the owner of that directory..) notice that yo can have different rights than the group members if you want..

Hmm.. looks complicated, and I am sure there are easier ways to do the same graphically..

and if you want to remove the rights from some user you can remove him from the group by:
sudo deluser userNameYouWantToRemoveFromTheGroup nameOfTheGroup

more info of the workings of chmod:
[http://supportweb.cs.bham.ac.uk/linux/files.php](http://supportweb.cs.bham.ac.uk/linux/files.php)

---

### Post by aot2002 on 2007-09-12
> **logos34 said:**
> wouldn't

**sudo chmod a+w /path/to/dir**    (or 'g+w' if the other user belongs to group)

be more specific and in line with what the OP asked for--i.e. 'not giving the other user any additional rights' (like execute)?


sudo chmod 666 file &#8211; read and write access to the owner, the group, and all others.
(change the permissions of the file file to read and write for all.)

Logos34:***
Screw off

---

