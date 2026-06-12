---
title: "Changing users home folder in gutsy"
date: 2007-10-20
forum: General Help
---

### Post by Chris_huh on 2007-10-20
I have just installed Gutsy dual boot with vista and had a go at changing the users folder (in ubuntu) to the same as the one in vista. This is on a separate hard drive so none of the files are shared with an OS. So now the user folder is /media/stb1. When i load up ubuntu it comes up with an error saying that the $HOME/.dmrc file has the wrong owner or permissions. When i look at the .dmrc file in /media/std1/.dmrc it is owned by root. 

How can i change this owner to be chris instead?

---

### Post by TheodoreWard on 2007-10-20
sudo chown user:group file

e.g. 

sudo chown -R chris:chris /home/chris
(-R changes all files in the subdirectory also)

---

### Post by thirddeep on 2007-10-20
So let me get this straight, you changed your /etc/passwd file to /media/std1/ for user chris ?

I would warn caution if that is a NTFS partition.  Further more, if you did the above, that means it's the entire partition for that one user.

Regardless, here is how you set the correct permissions:
```
sudo chown -R chris:chris /media/std1
```

Thd.

---

### Post by Chris_huh on 2007-10-20
It is NTFS but i haven't seen any problems with NTFS in gutsy. I am the only user on the computer. With vistas file system the videos/pictures/music/etc folders match up perfectly in ubuntu so i thought it would be great if i could get them to work together.

I changed it by going to System>Administration>Users and groups so i dont really know about /etc/passwd. Also i have no idea why i typed std1 as it is actually sdb1.

When i do sudo chown -R chris:chris /media/sdb1 the terminal just thinks for ages, then finally shows up chris@Chris:~$ again but nothing seems to have changed.

Since the entire parrtition is owned by root does it need to be changed in a different way?

---

### Post by thirddeep on 2007-10-20
You will learn that most *NIX utilities exit with nothing if all was good :-)

You can:
```
echo $?
```
but I am unsure if that will report "sudo" exit status or "chown" exit status.  If it reports "0" that is good.

Just do
```
ls -la /media/sdb1
```
and see if it's owned by chris.

You will also need to re-login probably.
Thd.

---

### Post by Chris_huh on 2007-10-20
I did ls -la /media/sdb1 but everything that comes up is still owned by root.

Would i need to unmount the volume then remount it again maybe, so that it is under my name?

---

### Post by Jaded Phoenix on 2007-10-22
Hi!
I'd suggest you try to edit the /etc/fstab manually.
launch the terminal window, and type in
```
sudo gedit /etc/fstab

```
if you're under GUI, or
```
sudo nano /etc/fstab

```
if you're under console.

Then, find the line for your /dev/sdb1 (actually, you should look at the comments above each line, as Ubuntu handles the hard drives by their uuid).
Find the options field (it will have something like 'defaults,utf8' in it).
Then, add
```
,uid=1000,gid=1000

```
to the field (I presume, your user id is 1000 and your group id is also 1000, you can check it in 'Administration/Users management')

Then, you'll have to reboot. Or, if you're under console, do
```
sudo umount /dev/sdb1
sudo mount -a

```
That's all, the whole NTFS partition will now belong to YOU! :-)

---

### Post by Chris_huh on 2007-10-22
Thanks, that got the partition under my name (and the .dmrc file too) but i still get an error saying that it doesnt have the right permissions.

It has Owner: Read and write, Group: Read and write, Others: none. How can i change this to be 644? When i try and change it from the .dmrc properties window the permissions just flip back to what they were.

---

