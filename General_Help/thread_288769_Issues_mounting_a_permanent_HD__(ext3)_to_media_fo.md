---
title: "Issues mounting a permanent HD  (ext3) to /media folder."
date: 2006-10-30
forum: General Help
---

### Post by marc_th on 2006-10-30
I'm having difficulty trying to mount a second 300GB hard drive so it appears as a device on the Desktop (and places) much like removable devices (iPod / flash drives) do.  I plan to use the drive to store music & video. Although the drive is usable, I can't get it to appear on the Desktop or under Places.

I'll outline the steps I took below--does anyone know what I'm missing or doing wrong?  Please bear in mind I switch to Linux/Ubuntu just this Friday...cold-turkey...so I have TONS to learn.

So, I installed the hd to the computer and, using gparted, partitioned & formatted the drive using the ext3 filesystem--Hello hdb1!

Then, I typed:

sudo mkdir /media/archive
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit/etc/fstab

and added the following line at the end of the file:

/dev/hdb1 /media/archive ext3 defaults 0 0

I saved the file and typed:

sudo mount -a
sudo chown -R username:username /media/archive
sudo chmod -R 755 /media/archive

And there you have it, the drive is up; I was able to copy 20GB of music on it (afterwhich, gparted tells me 20GB is bing used on the drive); however, for the life of me ](*,) , I can't get the drive to appear as an icon on the Desktop or under Places.  I've tried rebooting, typing other options in the fstab file, but after 4 hours of trying I got too frustrated.

Does anyone know what I'm missing?  Or mabye my strategy is wrong: I'm looking for a way to keep my music, videos and documents seperate from the OS, so I can format the OS drive without data-loss; I also want to be able to access it's contents quickly, so I can slap on some tunes, watch TV or find my resume without having to prgrams like iTunes/Rythmbox that manage your media for you.

Thanks in advance for any help!

---

### Post by marc_th on 2006-10-30
Bump. anyone have any ideas?

---

### Post by marc_th on 2006-10-30
I asked my mom but she had no idea by the drive mounted under /media wasn't appearing on the desktop; she told me to go play outside instead.  Can anyone offer me any suggestions?

---

### Post by marc_th on 2006-10-30
Is there anyone out there? I feel so cold and alone. ;)

---

### Post by steveneddy on 2006-10-30
Um - I'm not exactly the brightest one out here, but did you try looking under Places -->Computer -->Filesystem -->open the media folder then open the archive folder?

It looks like that is where you told it to create a new folder, so....create a new folder on your desktop if that's what you want, and link it to the folder you created.

Maybe that's too easy, and I may not be totally correct.

Maybe creating a new folder to store stuff in called:

/home/<username>/Desktop 

instead.

---

### Post by CatKiller on 2006-10-30
```
gconf-editor
```
apps/nautilus/desktop
check the volumes_visible box

---

### Post by marc_th on 2006-10-31
I don't believe it.  All I had to do was to reboot the machine, for the drive to appear.  Apparently, sudo mount -a and restarting Gnome doesn't cut it at this juncture in time.

---

### Post by CatKiller on 2006-10-31
Well, glad it's working for you now, anyway.

---

### Post by Sgurd on 2006-10-31
> **marc_th said:**
> 
sudo mount -a
sudo chown -R username:username /media/archive
sudo chmod -R 755 /media/archive


I'm doing something very similar.

I see the need for the first two lines.

What does the last line do?

---

### Post by steveneddy on 2006-11-01
> **Sgurd said:**
> I'm doing something very similar.

I see the need for the first two lines.

What does the last line do?

It gives you permission to read/write as a user without logging in as root or using the "sudo" command.

All users should be able to read/write to htis volume with this command.

---

### Post by LenzM on 2006-11-01
> **steveneddy said:**
> It gives you permission to read/write as a user without logging in as root or using the "sudo" command.

All users should be able to read/write to htis volume with this command.

755 only lets the owner of the file read and write, 775 would also let the group write and 777 would let any user write to it(not a good idea usually).

I don't think you want to do 
```

chmod 755 /media/drive
``` 
as this will make every file on the drive executable.  This isn't bad as far as I know, just unecessary.  
```

chmod u+w /media/drive
``` 
would let the owner of the file write to all of the files without making them executable.

---

### Post by Sgurd on 2006-11-01
I've aleady entered ```
chmod 755 /media/drive
```

Would it be advisable to enter ```
chmod u+w /media/drive
```?

Would I need to reverse the previous chmod?  Thanks - JD

---

### Post by LenzM on 2006-11-01
> **Sgurd said:**
> I've aleady entered ```
chmod 755 /media/drive
```

Would it be advisable to enter ```
chmod u+w /media/drive
```?

Would I need to reverse the previous chmod?  Thanks - JD

No `chmod u+w` wouldn't do anything now.  Undoing the `chmod 755` is possible but could get tedious and there's no real need.  It was more for future reference.

It's easier, imo, to use th `u+w` version, it literally adds write permissions for the user, `g+w` adds write permissions for the group, `o+x` for other users, and `a+x` does all 3 of those.  You can use - just like + to take away permissions, and you can also use 'r' for read permissions instead of/in addition to 'w', and 'x' for execute.

Just thought I'd let you know, it's one of those really useful command line things.

---

### Post by matthewstory on 2006-11-01
A note on the number system, for the inexperienced:

chmod 755 /files/or/directories/

The way this works is that each of the 3 numbers represents a different class of users . . . the first number represents the permissions of the owner, the second represents the permissions of the group that owns the file, and the third represents everyone else.  

Each number is the sum of all permissions given to that particular class of users where there are 3 different permissions each assigned a number:

Read Permission: gets a value of 4
Write Permission: gets a value of 2
Execute Permission: gets a value of 1

So a value of 7 in any column giver read/write/execute permissions to that class of users, a value of 5 gives read/execute priveleges to the class, a value of 6 gives read/write permissions to that class, a value of 4 gives read only permissions, a value of 2 gives write only permissions, and a value of 1 gives execute only permissions.

Common one's you might use:

a config file would generally get a value of 644, so that anyone can read it, but only the owner can edit it.  555 is what all your system stuff should be, kernel image, /proc folder etc.  755 is a pretty standard one for non-security risk files, 775 also pretty standard, and 777 if you just don't care who can do what.

enjoy!

---

### Post by iamhugeinjapan on 2006-11-01
In Nautilus, if you drag the folder you want to the bottom section of the left panel, it will be there permanently and be accessible from the Places menu.

---

### Post by matthewstory on 2006-11-01
some more useful permissions stuff for the CLI . . . 

You might at one point want to see what the permissions on a given file are, to do this use the ls -l command

ls -l

This will print a list of all files in your present working directory (PWD) with a lot more output that's usefull.  On the lefthand most side you will see somethign like this:

-rwxr-xr-x

the first space is for a special bit, the - indicates that it's just an average everyday file, but it could hold a d for directory, or an l for link.  The next 3 charecters represent the owner's permisions, the first spot is for read, the second spot for write, the third part for x.  The next 3 are for the group, and the last three are for everyone else.  If there is a dash then that class doesn't have that permission, if there is a letter, then that class has that permission.  The above example is 755, this is what 777 would look like:

-rwxrwxrwx

644

-rw-r--r--

775

-rwxrwxr-x

555

-r-xr-xr-x

This might come in handy.

---

### Post by Sgurd on 2006-11-03
A lot of good info; Thanks - JD

---

### Post by BLTicklemonster on 2006-11-03
Install pysdm from synaptic, run it (terminal as sudo pysdm, though it will appear in administration, I don't remember the name it's under, and it will show drives attached. you can mount from within it, they will appear on the desktop.

---

