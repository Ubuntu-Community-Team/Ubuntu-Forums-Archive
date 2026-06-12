---
title: "old user files"
date: 2008-05-29
forum: General Help
---

### Post by Tim0miT on 2008-05-29
i created a new ubuntu user and now i want rid of it

so i went users and groups and chose to delete

but the home folder for that user still exists and only contains the example folder

how would i go about deleting this??

---

### Post by zvacet on 2008-05-29
Type **cd /** to be on top of filesystem.After that** ls** to see all directories.Go to the home with 

```
cd home
```

and then **ls** again to see user folders.After that 

```
sudo rm -r usernamefolder
```
[B]
usernamefolder= user folder you want to delete[/B]

---

### Post by Tim0miT on 2008-05-29
didnt work :(
heres what i got


[PHP]tim@PC:~$ cd /
tim@PC:/$ cd home
tim@PC:/home$ sudo rm -r mac
[sudo] password for tim: 
rm: cannot remove `mac/.gvfs': Permission denied
tim@PC:/home$ 
[/PHP]

---

### Post by Oldsoldier2003 on 2008-05-29
> **Tim0miT said:**
> didnt work :(
heres what i got


[PHP]tim@PC:~$ cd /
tim@PC:/$ cd home
tim@PC:/home$ sudo rm -r mac
[sudo] password for tim: 
rm: cannot remove `mac/.gvfs': Permission denied
tim@PC:/home$ 
[/PHP]

this is what I would do

```
sudo useradd -m mac
sudo userdel -r mac
```

---

### Post by Tim0miT on 2008-05-29
ok so i did that

i manualy deleted the group named mac

and this is what i got from the code you gave me:)


```
tim@PC:~$ sudo useradd -m mac
useradd: user mac exists
tim@PC:~$ sudo userdel -r mac
userdel: error removing directory /home/mac
tim@PC:~$ 

```


thanks for trying to help lol

any more ideas

---

### Post by Oldsoldier2003 on 2008-05-29
> **Tim0miT said:**
> ok so i did that

i manualy deleted the group named mac

and this is what i got from the code you gave me:)


```
tim@PC:~$ sudo useradd -m mac
useradd: user mac exists
tim@PC:~$ sudo userdel -r mac
userdel: error removing directory /home/mac
tim@PC:~$ 

```


thanks for trying to help lol

any more ideas
No ideas ATM, because the commands I gave you should work perfectly fine, I'm not getting any problems whatsoever in creating and deleting users and there homes using those commands.

What version of Ubuntu are you running, and have you done any updates recently?

```
cat /etc/lsb-release
```will give you the release info

```
sudo apt-get update
sudo apt-get upgrade
```

then try recreating and removing the user again

---

