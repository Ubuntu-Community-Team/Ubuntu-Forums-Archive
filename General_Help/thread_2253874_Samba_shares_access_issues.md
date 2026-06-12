---
title: "Samba shares access issues"
date: 2014-11-23
forum: General Help
---

### Post by khaled5 on 2014-11-23
Hello Everyone,

First of all apologies, i know that discussions about this have been all over the place and it's a subject widely talked about, however i am still missing my issue so i hope you guys will be able to help out.

I installed Ubuntu Server 14.04.1 LTS edition on a separate physical machine, installed OpenSSH and samba. I am easily able to access the server through SSH and all went well.

Next up was me setting up the shares, and here i am sure i messed up somehow but i can't figure out why. First of all, i had to auto-mount my hard drives, so i changed the  [FONT=Ubuntu Mono]/etc/fstab[/FONT]  file and it went something like this : 

```


#Boot and swap files
UUID=47b67722-d20a-4132-9117-2f9e1978ae54 /               ext4    errors=remount-ro 0       1
UUID=71477ffe-e2ab-4362-b64b-98bc558760f4 none            swap    sw              0       0

#My own shared folders

/dev/sdb1 /media/shareddrive ext4 defaults 0 1
/dev/sdc1 /media/storage ext4 defaults 0 1
/dev/sdf1 /media/games ext4 defaults 0 1


```

Note : I will eventually change the permissions but for now i need it accessible from anyone, regardless of users. 

With my folders mounted, i edited the /etc/samba/smb.conf file and added the following at the end : 


```


[Games]


   path = /media/games/Gaming Files
   browseable = yes
   read only = no
   guest ok = yes
   writeable = yes




[Shared Folder]


   path = /media/shareddrive/Shared Folder
   browseable = yes
   read only = no
   guest ok = yes
   writeable = yes


[Tutorials and Installation Files]


   path = /media/shareddrive/Tutorials and Other stuff
   browseable = yes
   read only = no
   guest ok = yes
   writeable = yes




[Clonezilla Images and backups]


   path= /media/storage /Ghost images
   browseable = yes
   read only = no
   guest ok = yes
   writeable = yes


[Family Movies]


   path = /media/movies/Movies
   browseable = yes
   read only = no
   guest ok = yes
   writeable = yes



```

Now i accessed this shared folder and all went well, i tried opening an Flv file and an mp4 file from different shared folders, all went well. 

Then i told my brother to access the service from his account on the same windows PC, he could see the shares, but couldn't access all folders, and those that he could access he couldn't open any files, the error he faced is the following : 

[COLOR=#333333][FONT=Helvetica Neue]You do not have permission to access  Contact your network administrator to request access.

I checked the smb file again and i tried creating a user with his username to re-create the same situation as my own user account that is facing no problems

He still cannot access, so can anyone notice the problem here that i'm missing ? 

Also, i am sorry if this is the wrong board or if i missed something important in my description, so please ask if you need more missing information

thank you in advance[/FONT][/COLOR]

---

### Post by Morbius1 on 2014-11-23
It doesn't sound like a samba issue but a Linux permissions issue. Samba share permissions can't override the permissions on the folder or file itself.

I don't know which folder in particular you are having issues with but list the permissions of the folder and it's contents and see if the guest user can actually access the folder. For example:
```
 ls -al "/media/shareddrive/Shared Folder"
```
Side notes:

[1] You really don't want to do this:
> #My own shared folders

/dev/sdb1 /media/shareddrive ext4 defaults 0 1
/dev/sdc1 /media/storage ext4 defaults 0 1
/dev/sdf1 /media/games ext4 defaults 0 1
Run the following command:
```
sudo blkid -c /dev/null
```
With the output change all those /dev/sdxy's to UUID=long-sting-of-numbers.

During boot what the system sees as sdb one time it may see as sdf another. UUID's solve that problem.

[2] This is just a recommendation but I would get out of the Windows habit of having spaces in names of files and folders. Linux can handle them but it's awkward since thing's have to have quotes around them or escapes like \040 or %20 depending on where you are specifying them.

Use camel back instead like SharedFolder instead of Shared Folder.

---

### Post by khaled5 on 2014-11-23
Thank you for your reply! 



Regarding the side notes:

> **Morbius1 said:**
> [1] You really don't want to do this:

Run the following command:
```
sudo blkid -c /dev/null
```
With the output change all those /dev/sdxy's to UUID=long-sting-of-numbers.

During boot what the system sees as sdb one time it may see as sdf another. UUID's solve that problem.
 

Done that, thank you!

> **Morbius1 said:**
> [2] This is just a recommendation but I would get out of the Windows habit of having spaces in names of files and folders. Linux can handle them but it's awkward since thing's have to have quotes around them or escapes like \040 or %20 depending on where you are specifying them.

Use camel back instead like SharedFolder instead of Shared Folder.

I thought about that, but i've already wrote small software on my pc that will be reading the directories and searching for these specific names so i'm going to go with adding \040 for the spaces, but thank you for the advice! I'll keep it in mind for my next builds. 


> **Morbius1 said:**
> It doesn't sound like a samba issue but a Linux permissions issue. Samba share permissions can't override the permissions on the folder or file itself.

I don't know which folder in particular you are having issues with but list the permissions of the folder and it's contents and see if the guest user can actually access the folder. For example:
```
 ls -al "/media/shareddrive/Shared Folder"
```    

I ran the command, i got the following output : 


```
drwxr-xr-x  8 root   root   4096 Nov 23 01:18 .
drwxr-xr-x 22 root   root   4096 Nov 23 00:20 ..
drwxrwxrwx  4 khaled khaled 4096 Oct 26 20:18 anime
drwxr-xr-x  2 root   root   4096 Nov 23 00:20 cdrom
drwxrwxrwx  4 khaled khaled 4096 Nov 23 01:45 games
drwxrwxrwx  3 khaled khaled 4096 Oct 28 00:02 movies
drwxrwxrwx  3 khaled khaled 4096 Oct 27 19:33 series
drwxrwxrwx  4 khaled khaled 4096 Oct 26 12:22 shareddrive

```

Doesn't " drwxrwxrwx " mean that it should be accessible by everyone and modifiable by everyone even guests? 
Please bare with me, i'm still learning here and the documentation is fairly confusing to me. 

Thank you in advance for the rest of your help :)

---

### Post by Morbius1 on 2014-11-23
That looks more like the output of "ls -al /media" but yes it does look like everyone has read and write access to say the /media/shareddrive folder. They may not have access to /media/shareddrive/Shared Folder but everyone should be able to read and add to the /media/shareddrive folder.

Does "khaled" himself have access to all these folders locally - on the server itself. If so why not make all your client users appear to be "khaled" for these guest shares. For example:
> [Shared Folder]
   path = /media/shareddrive/Shared Folder
   browseable = yes
   read only = no
   guest ok = yes
   [COLOR=#0000cd]**force user = khaled**[/COLOR]
   writeable = yes
As long as you restrict access only though samba and you do everything administratively as "khaled" on the server itself then all the samba users should have access to all these shares.

---

### Post by khaled5 on 2014-11-23
> **Morbius1 said:**
> That looks more like the output of "ls -al /media" but yes it does look like everyone has read and write access to say the /media/shareddrive folder. They may not have access to /media/shareddrive/Shared Folder but everyone should be able to read and add to the /media/shareddrive folder.

Does "khaled" himself have access to all these folders locally - on the server itself. If so why not make all your client users appear to be "khaled" for these guest shares. For example:

As long as you restrict access only though samba and you do everything administratively as "khaled" on the server itself then all the samba users should have access to all these shares.

Ok that worked, adding force user = khaled worked, however this implies that the problem is indeed public access restriction from the linux system itself, not samba. It is possible then that the sub-directories have restricting policies when the parent directory doesn't. And yes indeed as you stated the output of ls -al was indeed that of /media, i wanted to see if all the parent directory had the restriction. 

So now if you don't mind i have a question: 

My final goal will be to control who access what on the server, I will create 4 samba users, me as Khaled and one for my mother and brother and a "guest" one, with each different permissions and read/write rights, i know how to do most of that but using force user = khaled will make doing all this impossible, so i will have to go around this by just changing the permission for the whole /media directory, including sub-directories. However is there some command to do that all automatically? Or will i have to go into each individual folder in all the sub-directories to change them?  

Finally, thank you again for your help! I appreciate it so much :)

---

### Post by Morbius1 on 2014-11-23
If you want some users to have read access and others have write access to the same share then "force user" may not be the the ultimate solution to your issue. "Force user" can resolve a lot of issues but it limits what else you can do with the share. If you limit who has write access but use force user one negates the other. 

It depends on how complicated you want to make this.

[A] You could for example simply create two shares for the same folder. 
> [Shared Folder - Read Only]
path = /media/shareddrive/Shared Folder
browseable = yes
read only = yes
guest ok = yes
That will take care of the guest and everyone who only has read access to the share.

And then another one for all of those who you want to have write access:
> [Shared Folder]
path = /media/shareddrive/Shared Folder
browseable = yes
read only = no
guest ok = no
valid users = khaled, brother
force user = khalid
"valid users" will restrict who has access to the writeable share but after the credentials are accepted by samba both users will be converted to khaled.

[B] You could do this in one share but it comes with a price. You could do the following:

*** Change group permissions of the folder to plugdev ( doesn't have to be plugdev I just chose one that already exists )
```
sudo chown :plugdev "/media/shareddrive/Shared Folder"
```
*** Change permissions to add the sgid bit which will make every new file inherit the group ( plugdev in this case ) of the parent folder:
```
sudo chmod 2775 "/media/shareddrive/Shared Folder"
```
*** Then change your share definitions to this:
> [Shared Folder]
path = /media/shareddrive/Shared Folder
browseable = yes
read only = yes
guest ok = no
valid users = khaled, brother, mom, smbguest
write list = khalid, brother
create mask = 0664
force directory mode = 2775
force group = plugdev

- The "write list" overrides the "read only = yes" constraint.
- khaled and brother will have to be members of the plugdev group in order to be able to write to the share.
- The whole sgid/2775/force group stuff will make sure that every new file added will have the group = plugdev so that everyone on the write list will be able to edit all files.
- mom will be able to gain access but she's not on the write list so she can only read.

The only complication is this scenario is the "guest". In [A] anyone can freely gain read access to the read only share. But [B] requires that all users provide credentials so that samba can figure out who's on the write list and who is not. In this example you would have to create the "smbguest" user and add him to the samba password database:
```
sudo smbpasswd -a smbguest
```
And have that guest user provide a username and password. It doesn't have to be a secret password it can literally be "smbguestpw" but he/she will need to log in.

I think I did all that right - it's very late here so I might have missed a t or an i somewhere in all that but I think that will do it.

EDIT: already found and fixed a typo. I think I'll shut down for the day.;)

---

### Post by khaled5 on 2014-12-20
> **Morbius1 said:**
> If you want some users to have read access and others have write access to the same share then "force user" may not be the the ultimate solution to your issue. "Force user" can resolve a lot of issues but it limits what else you can do with the share. If you limit who has write access but use force user one negates the other. 

It depends on how complicated you want to make this.

[A] You could for example simply create two shares for the same folder. 

That will take care of the guest and everyone who only has read access to the share.

And then another one for all of those who you want to have write access:

"valid users" will restrict who has access to the writeable share but after the credentials are accepted by samba both users will be converted to khaled.

[B] You could do this in one share but it comes with a price. You could do the following:

*** Change group permissions of the folder to plugdev ( doesn't have to be plugdev I just chose one that already exists )
```
sudo chown :plugdev "/media/shareddrive/Shared Folder"
```
*** Change permissions to add the sgid bit which will make every new file inherit the group ( plugdev in this case ) of the parent folder:
```
sudo chmod 2775 "/media/shareddrive/Shared Folder"
```
*** Then change your share definitions to this:


- The "write list" overrides the "read only = yes" constraint.
- khaled and brother will have to be members of the plugdev group in order to be able to write to the share.
- The whole sgid/2775/force group stuff will make sure that every new file added will have the group = plugdev so that everyone on the write list will be able to edit all files.
- mom will be able to gain access but she's not on the write list so she can only read.

The only complication is this scenario is the "guest". In [A] anyone can freely gain read access to the read only share. But [B] requires that all users provide credentials so that samba can figure out who's on the write list and who is not. In this example you would have to create the "smbguest" user and add him to the samba password database:
```
sudo smbpasswd -a smbguest
```
And have that guest user provide a username and password. It doesn't have to be a secret password it can literally be "smbguestpw" but he/she will need to log in.

I think I did all that right - it's very late here so I might have missed a t or an i somewhere in all that but I think that will do it.

EDIT: already found and fixed a typo. I think I'll shut down for the day.;)


Thank you for your help, 
and sorry for the absurdly late reply, i had put the project on hold till i finish my finals.

Now that it's done, time to fight with this thing again :p

Honestly i think i messed it up last time i tried :P 

i wanted to ask, let's say i want to change the ownership and permissions of /media/certainfolder to khaled and have everyone able to write and edit and execute everything and anything 

i'd have to enter : 

```
sudo chown khaled "/media/certainfolder"
```

```
sudo chmod 777 "/media/certainfolder"
```

yes ? 

however what that does is change ownershipof only that folder and the permissions to only that folder, how can i change all the directories and sub directories inside the folder ? Also, one more issue, does having space bars in the directories affect these ? because under most of the folder in my storage, they were originally windows folders and they have space bars everywhere in the names, so will i have to rename them all ? 

thank you in advance for all the help you've given me, and i am sorry if the questions are quite lame and obvious, but i'm still learning linux in general

---

### Post by Morbius1 on 2014-12-20
> however what that does is change ownershipof only that folder and the  permissions to only that folder, how can i change all the directories  and sub directories inside the folder ?
You can do a "recursive" change. For example:
```
sudo chown -R khaled "/media/certainfolder"
```
And for a recursive chmod this:
```
sudo chmod -R a+rwX "/media/certainfolder"
```
You might be tempted to do this: [B]sudo chmod -R 777 "/media/certainfolder"
[/B]But what that will do is make every single file in that directory executable which is not recommended.

A chmod -R a+rwX will keep only those files already marked executable but leave the others un-executable.
> Also, one more issue, does having space bars in the directories affect these ?
Spaces in the name of things is a pain in Linux but you don't have to rename everything. Just make sure you place quotes ( as you have done in your post ) around the path.

---

### Post by khaled5 on 2014-12-30
> **Morbius1 said:**
> You can do a "recursive" change. For example:
```
sudo chown -R khaled "/media/certainfolder"
```
And for a recursive chmod this:
```
sudo chmod -R a+rwX "/media/certainfolder"
```
You might be tempted to do this: [B]sudo chmod -R 777 "/media/certainfolder"
[/B]But what that will do is make every single file in that directory executable which is not recommended.

A chmod -R a+rwX will keep only those files already marked executable but leave the others un-executable.

Spaces in the name of things is a pain in Linux but you don't have to rename everything. Just make sure you place quotes ( as you have done in your post ) around the path.


Ok will try, i just need to know what are the downsides of having all files executable? 

Also, i will have on server executables .exe files, will having the directory not executable forbid me from running them directly through a share ? meaning i will access the server through share on a windows system and run the exe file directly in opposed to copy it to the machine then run it

---

