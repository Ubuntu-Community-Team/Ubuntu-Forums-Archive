---
title: "[chmod -R 777] vs [chown -R] for external HDD"
date: 2017-01-11
forum: General Help
---

### Post by k7788mount2external0 on 2017-01-11
I know that [chown -R] makes me the owner while [chmod -R 777] simply allows me to read/write files without changing the owner.

Which should I use for an external HDD (ext4)? The end result seems to be the same for a desktop user.  I don't have any sensitive information in the drive, just photos / videos / music. 

1. Which is better if I only use the drives with my personal Ubuntu desktops (always UID=1000)?

2. Which is better if I might also use the drive with a Fedora desktop (which I assume has a different UID)?

3. What is the difference between 
[sudo chown -R user: /media/user/drive-name] 
[sudo chown -R user:user /media/user/drive-name] 
[sudo chown -R $user:$user /media/user/drive-name]

4. I read somewhere that I should never use [chmod -R 777]. Why is this and does it apply to my situation?
Should I use [chmod -R 666] instead?

---

### Post by TheFu on 2017-01-11
Depends on what you consider better.

IMHO, a mix of each would be best.  The normal practice is to provide the least authority required to the users/processes and ZERO access to others.  That means that YOU need to learn more about the basics of Unix file and directory permissions to implement what YOU think is best.  Letting the world have write access is crazy, IMHO. When your system gets hacked (not if), then all those files are at risk.  Plus the attacker has a huge area of free storage to load up whatever tools and programs and data he may want to use your system as a pivot point of C&C for thousands of other machines.

Fedora and Ubuntu and every Unix system made use file and directory permissions following the same rules.  Android, iOS too.

You can search for answers for why never to use 777. 

I wouldn't use 777 or 666 permissions anywhere, ever.  Those are the answers a someone ignorant about security uses.  Ignorance can be solved through learning.  Look for a unix/linux file and directory permissions tutorial.  Create a few accounts and groups. Mix and match the groups with different userids.  Open a few terminals and get to work on the tutorial. Try some things that don't make sense and see what happens. How can you get around those permissions?  For example, what does 066 do?  What does 060 do?  What does 540 do?  Try accessing using different userids in different (and the same) groups.  Spend 45 min on this and you will learn an unbelievable amount that will serve you well for the rest of you Unix life.  

Understanding these permissions are the core of all Unix system security.

---

### Post by oldfred on 2017-01-12
If it is personal data and ext4, I would use settings similar to /home.
       
 Ubuntu /home is permissive:
[https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access](https://wiki.ubuntu.com/SecurityTeam/Policies#Permissive%20Home%20Directory%20Access)
sudo chown -R $USER:$USER /home/$USER
sudo chmod -R a+rwX,o-w /home/$USER 
    
Never use -R on any system folder. That is recursion and will change system settings which are not the same in various folders.

 Seems like a better way as you have more control over what is executable. Isee post #8 & 10 by morbius1.
[http://ubuntuforums.org/showthread.php?t=1795369](http://ubuntuforums.org/showthread.php?t=1795369) 

 sudo chmod -R a+rwX,o-w /mnt/data
#is better than this:
sudo chmod -R 777  /mnt/data 
    
 [http://ubuntuforums.org/showthread.php?p=12181259](http://ubuntuforums.org/showthread.php?p=12181259)

---

### Post by Morbius1 on 2017-01-12
Run the following command:
```
getfacl /media/$USER
```
You should see something like this:
> tester@vub-16041:~$ getfacl /media/$USER
getfacl: Removing leading '/' from absolute path names
# file: media/tester
# owner: root
# group: root
user::rwx
user:tester:r-x
group::---
mask::r-x
other::---
The /media/tester ( in this example ) folder was created by the system not me and it was assigned special permissions ( via an ACL ) that limits access to whatever is past it to root and tester. This is by design.

Setting the /media/user/drive-name to 777 in the hopes that someone else will gain access on the same system will do you no good.  Setting it to 777 so that you can use it on another system will not do you much good either. THe other system user will be able to add something to it but when it returns to you it will have that user's name and UID so you won't be able to do much with it unless you so a recursive chown on it as root. It's the reason why you never see usb sticks formatted to a Linux filesystems at your local electronics retailer.

---

### Post by TheFu on 2017-01-12
Please **look up** and *understand* all the commands *and options* BEFORE running them.

---

