---
title: "What is the point of sharing a folder if users can't simply share it ?"
date: 2015-09-15
forum: General Help
---

### Post by AgentZ86 on 2015-09-15
I am confused about the permissions.

I seem to be running into a problem with sharing folders.
Typically I thought if I share a folder on the network that a user on the network could access that folder and files and read/write to them ? 

I am getting permission errors and the machine that is sharing the folder also has a lock icon on the folder.
I'm not sure what to do with this. I can't seem to restore from backup with ubuntu backup tool either.

The permissions of the folder and files seems to be user = nobody and group = nogroup.

What happened and why ? 
Please advise
Thanks

When I right click  and select permissions on a file it says permissions cannot be determined ?

---

### Post by brian-mccumber on 2015-09-15
I have noticed this also when using shared public folders on my two computers. Usually the lock isn't a problem I can still copy the file to the computer that is displaying the lock but sometimes I have to go back and put the file in the shared folder of the other computer using the computer the file is coming from instead of retrieving it from the shared folder of the computer the file is coming from, I guess it depends on the file type. It is more an annoyance than a problem I have never not been able to share a file. The permissions can't be determined because the owner of the file is nobody and the file belongs to group nobody.

---

### Post by AgentZ86 on 2015-09-15
> **brian-mccumber said:**
> I have noticed this also when using shared public folders on my two computers. Usually the lock isn't a problem I can still copy the file to the computer that is displaying the lock but sometimes I have to go back and put the file in the shared folder of the other computer using the computer the file is coming from instead of retrieving it from the shared folder of the computer the file is coming from, I guess it depends on the file type. It is more an annoyance than a problem I have never not been able to share a file. The permissions can't be determined because the owner of the file is nobody and the file belongs to group nobody.

So how are you suppose to use files on the shared folder for all users.

I mean I can read and open libre office docs. but can't edit them or use them.
It's read only files.

This seems to be only recently that it started doing this.
I have been using the shared folder for a long time without these pad lock icons on them.

How to fix this ?
Thanks

---

### Post by brian-mccumber on 2015-09-15
I have been making a copy of the file that is locked on the computer I want to transfer it to. Then I delete the locked copy.

---

### Post by bab1 on 2015-09-15
> **AgentZ86 said:**
> I am confused about the permissions.

I seem to be running into a problem with sharing folders.
Typically I thought if I share a folder on the network that a user on the network could access that folder and files and read/write to them ? 

I assume you are referring to usershares created via Nautilus (i.e. Samba usershares)
Not necessarily.  It depends upon what the share definition parameters are set.  It also is important as to how you access the *shared directory*.  By that I mean that if you share a directory and then access that directory via Samba (//Server_Name/public) you could have one set of ownership and permissions settings.  If you access that same directory locally (/home/<user>/Public) you will have the ownership and permissions of the logged in user.  > 

I am getting permission errors and the machine that is sharing the folder also has a lock icon on the folder.
I'm not sure what to do with this. I can't seem to restore from backup with ubuntu backup tool either.

The permissions of the folder and files seems to be user = nobody and group = nogroup.
These are not permissions.  They're the ownership parameters of the file or directory.  These are what you get when the Samba usershare is shared by the non root user and with guest access.
> When I right click and select permissions on a file it says permissions cannot be determined ? 
When you look at the permissions via the Samba share, those permissions are obscured to the local file manager.  In this case local is not really proximity, it's more network share vs local directory.
> So how are you suppose to use files on the shared folder for all users.

I mean I can read and open libre office docs. but can't edit them or use them.
It's read only files.

This seems to be only recently that it started doing this.
I have been using the shared folder for a long time without these pad lock icons on them.

How to fix this ?
If setup correctly network shares should act just like any other directory.  Most of the time usershares are best suited to a read only situation except for creator.  The use of guest only should be on a limited basis.  If you want to have network shares that act like any other directory you will have to create them in the /etc/smb.conf file as the root user (via sudo).

---

### Post by bab1 on 2015-09-15
> **brian-mccumber said:**
> I have noticed this also when using shared public folders on my two computers. Usually the lock isn't a problem I can still copy the file to the computer that is displaying the lock but sometimes I have to go back and put the file in the shared folder of the other computer using the computer the file is coming from instead of retrieving it from the shared folder of the computer the file is coming from, I guess it depends on the file type. 

No it has nothing to do with the file type.  it has to do with whether you are a local user or a network user (the client to the Samba server) 
> 
It is more an annoyance than a problem I have never not been able to share a file. The permissions can't be determined because the owner of the file is nobody and the file belongs to group nobody.
"*Share*" is is just a name.  What you are really doing is making a file available over the network via an application named Samba.  This can be read only or read and write.  There are 2 methods of creating a share. Either as a mortal user (a login account) or as root.  The root created share is more flexible, but more complex to setup.

The user nobody and group nogroup are legitimate and in no way inhibit the listing of ownership and permissions.  Network share permissions are not available through the file manager for any user.
> I have been making a copy of the file that is locked on the computer I want to transfer it to. Then I delete the locked copy. 
Make the share in the /etc/smb.conf file and use the shares as a full featured NAS.  Much easier in the long run.

---

### Post by AgentZ86 on 2015-09-16
Well crap.
So if I wanted a shared folder on the network that all users can read/write/delete etc. I would have to set this up in samba not just share the folder by right clicking etc.

Can this be done easily with a clickety method of some sort of samba gui etc ?

---

### Post by bab1 on 2015-09-16
> **AgentZ86 said:**
> Well crap.
So if I wanted a shared folder on the network that all users can read/write/delete etc. I would have to set this up in samba not just share the folder by right clicking etc.

Sharing a folder by via the GUI is using Samba.  The difference is not the interfaces you use, but whether or not the root user (via sudo) creates the share or not.  If you create the share you are limited to what you have already created.  If the share is a root created share you can create whatever you need.
> 
Can this be done easily with a clickety method of some sort of samba gui etc ?
Sort of.  I believe there is a GUI Samba admin app available.  I have never used it.  Editing a half dozen lines or so in a text file just hasn't seemed that hard to me.

---

### Post by AgentZ86 on 2015-09-16
> **bab1 said:**
> Sharing a folder by via the GUI is using Samba.  The difference is not the interfaces you use, but whether or not the root user (via sudo) creates the share or not.  If you create the share you are limited to what you have already created.  If the share is a root created share you can create whatever you need.

Sort of.  I believe there is a GUI Samba admin app available.  I have never used it.  Editing a half dozen lines or so in a text file just hasn't seemed that hard to me.

Ok so I don't really need any more gui tools then.

So let me ask this. When I right click a folder and select share(allow others) and share (Guest)  shouldn't anyone be able to copy/move/delete/edit and use the folder just like a folder on their local machine ?

I can't even create a share all the sudden for no reason that I can tell.

right click, share, (allow users) and click share produces error 255

The (guess) option is inactive (greyed out) 

I don't get it

---

### Post by bab1 on 2015-09-16
> **AgentZ86 said:**
> Ok so I don't really need any more gui tools then.

So let me ask this. When I right click a folder and select share(allow others) and share (Guest)  shouldn't anyone be able to copy/move/delete/edit and use the folder just like a folder on their local machine ?
You would think so, but that is only true if you access the folder via Samba.  If you access the shared folder as a local user, your local user ownership and permissions apply (<local_user>: <local-group>).  If you access the folder as a network share then the Samba user ownership and permissions apply (nobody:nogroup).  This is what you have been experiencing.  If you setup the share via the smb.conf file you can specify the users access.  If you have multiple users accessing the same share you can add them to a common group and manage the share access via that common group.

---

### Post by AgentZ86 on 2015-09-16
> **bab1 said:**
> You would think so, but that is only true if you access the folder via Samba.  If you access the shared folder as a local user, your local user ownership and permissions apply (<local_user>: <local-group>).  If you access the folder as a network share then the Samba user ownership and permissions apply (nobody:nogroup).  This is what you have been experiencing.  If you setup the share via the smb.conf file you can specify the users access.  If you have multiple users accessing the same share you can add them to a common group and manage the share access via that common group.

Ok, thanks

For some reason I lost the ability to even create a share on fresh install.
It give me the error but I select cancel instead of OK to overwrite etc.

So adding the user to the group should solve this problem even if the user access the files from either samba or locally ?

---

### Post by bab1 on 2015-09-16
> **AgentZ86 said:**
> So adding the user to the group should solve this problem even if the user access the files from either samba or locally ?
It's a little more complicated than just that.  You have to account for files that are created in the share by users as well as the already existing documents ownership and permissions.

All of my shared documents are in a file system that starts at /srv/share.  All users that access that share are in a common group.  All files and folders created in that share have have the same group ownership (<user>:common).   The permissions for the "common" group is always read/write for the files and read/write/eXecute for the folder.  I configure the file system to provide that, but you can do the same thing using Samba also.

I always prepare the file system for sharing, then add the users (Linux/Samba) to the system and only then do I create the share.

---

### Post by AgentZ86 on 2015-09-16
> **bab1 said:**
> It's a little more complicated than just that.  You have to account for files that are created in the share by users as well as the already existing documents ownership and permissions.

All of my shared documents are in a file system that starts at /srv/share.  All users that access that share are in a common group.  All files and folders created in that share have have the same group ownership (<user>:common).   The permissions for the "common" group is always read/write for the files and read/write/eXecute for the folder.  I configure the file system to provide that, but you can do the same thing using Samba also.

I always prepare the file system for sharing, then add the users (Linux/Samba) to the system and only then do I create the share.

Thanks, this makes sense.

One more question as I start reading the Samba documents please.

If I were to create a folder and right click the folder and share as (allow user) and (guest) 
Does this actually allow you to use the files as you wanted for any user and/or group as long as they access via samba and NOT through the file browser ? 

Or does the common group still need to be created for the users to have read/write for the folder ?

Thanks for the help

---

### Post by bab1 on 2015-09-16
> **AgentZ86 said:**
> Thanks, this makes sense.

One more question as I start reading the Samba documents please.

If I were to create a folder and right click the folder and share as (allow user) and (guest) 
Does this actually allow you to use the files as you wanted for any user and/or group as long as they access via samba and NOT through the file browser ? 

Or does the common group still need to be created for the users to have read/write for the folder ?

Thanks for the help
[/QUOTE]
It makes every user act as the user nobody.  That user has full rights to the data created in the folder.  This is because when you configure **guest=ok** Samba does not check the users ID and just automatically allows all operations as the user *_nobody_* in the group *_nogroup_*.
[QUOTE]

When you are done reading, come back and I will show you how to set up a share correctly.  The time spent reading will help.  Creating the share and seeing it work will help too.   Think about who (what users) you want to have access and how much access you want to allow (e.g. read or read and write).

Post back here and I we can start then.  I'm gone for a couple of hours now.

---

### Post by AgentZ86 on 2015-09-16
What will happen to the files I already have saved and all the permissions,user/group that seems to be giving me trouble ? Will setting up samba correctly be able to handle this and correct this subject for me once I setup samba shares correctly ?

Please advise

---

### Post by bab1 on 2015-09-16
> **AgentZ86 said:**
> What will happen to the files I already have saved and all the permissions,user/group that seems to be giving me trouble ? Will setting up samba correctly be able to handle this and correct this subject for me once I setup samba shares correctly ?

Please advise
All of that can be corrected to whatever user:group we use.  The root user can alter just about anything on the system, including things that would destroy the system.  If you are a member of the *sudo* group you can use sudo (**[SIZE=3]S[/SIZE]**witch **[SIZE=3]U[/SIZE]**ser and**[SIZE=3] Do[/SIZE]** to switch to the root user to correct the permissions (chmod) or the user (chown).  Everything is reconfigurable by the root user.  If you installed Ubuntu then your user account is a member of the *sudo* group by default.

Do you have any experience with using the terminal or using terminal commands?  You will be more in control of the system if you learn how the terminal works and some simple terminal commands.

For more information can read about the command here: [**[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)**]("https://help.ubuntu.com/community/RootSudo")

---

### Post by AgentZ86 on 2015-09-16
Great thanks,

And yes I have some beginner level command terminal experience.

For a Samba user, can this user be the same user as the ubuntu users ? Or should the samba users be different ? 
I'm just reading the Samba documentation and wondered if these samba users should be samba exclusive or does it matter ?

---

### Post by bab1 on 2015-09-16
> **AgentZ86 said:**
> Great thanks,

And yes I have some beginner level command terminal experience.

For a Samba user, can this user be the same user as the ubuntu users ? Or should the samba users be different ? 
I'm just reading the Samba documentation and wondered if these samba users should be samba exclusive or does it matter ?Any mortal user (human) that needs access to the Samba shared data on a Ubuntu host should have a Linux account (adduser) and a Samba user account (smbpasswd -a).  You need both accounts per person.  This provides the security separation you might need in the future.

---

### Post by AgentZ86 on 2015-09-17
> **bab1 said:**
> Any mortal user (human) that needs access to the Samba shared data on a Ubuntu host should have a Linux account (adduser) and a Samba user account (smbpasswd -a).  You need both accounts per person.  This provides the security separation you might need in the future.

Got it thanks,

So so I'm reading the docs, smbpasswd -a myusers
And this appears to require the user to already exist on the linux account as well. At least that is the error message I get when trying to use the samba command for a user that does not exist.

I added the user but did not notice any changes to the samba folder. I was expecting to see a smbuser file or something.

So I guess my last question would be (does the samba user have to exist on the linux user as well)

It seems so but I'm having trouble confirming this.
Thanks for all the help

---

### Post by bab1 on 2015-09-17
> **AgentZ86 said:**
> Got it thanks,

So so I'm reading the docs, smbpasswd -a myusers
And this appears to require the user to already exist on the linux account as well. At least that is the error message I get when trying to use the samba command for a user that does not exist.

I added the user but did not notice any changes to the samba folder. I was expecting to see a smbuser file or something.

...So I guess my last question would be (does the samba user have to exist on the linux user as well)

It seems so but I'm having trouble confirming this.
Thanks for all the help 


The Samba user listing gets some of it's information from the Linux user account data.  You need to have Linux user before you can successfully add a user to the Samba user database.  The Samba users databases are at /var/lib/samba.  You can't read them directly however.  They are not text files.  To look at the contents of the database you use this terminal command ```

sudo pdbedit -L

```
This should list all the Samba users.  Please post the output of the command back here.

To post the text output you should place the text between [noparse]```
 
```[/noparse] blocks.  This preserves the text formatting making it easier to read.  The simplest method is to click on the [SIZE=5]**#**[/SIZE] icon at the top of the "Advanced Editor" that you are using to reply with.  Then you paste the text in between the code blocks.

---

### Post by AgentZ86 on 2015-09-18
Thanks this is been helpful.

I'll post some output later this evening after I read a little more.

---

### Post by bab1 on 2015-09-18
> **AgentZ86 said:**
> Thanks this is been helpful.

I'll post some output later this evening after I read a little more.
Whenever you are ready I will show you what to do to set up Samba correctly.

---

### Post by AgentZ86 on 2015-09-18
so far the user command just shows my single user

user1:1000:user1

strange that I have been sharing a folder on a ubuntu 14.04 machine for over a year easily and users can read/write all over the place simply by sharing the folder and allowing guest.

Now all the sudden I can't share a folder without having any files locked that go into the folder from another computer.
I don't mind learning samba but with all the point and click of the OS you would think there is a simple right click share method that would simply allow a user of one pc to have read/write access to a folder on another pc.

I don't know why I did this so easily before but not it seems so complicated and theoretically it shouldn't have even worked considering what you posted.

Reading for a few days now and no closer to sharing a folder. I thought I understood what I've read but it appears that I don't because the folders just will not share.

I have a user on this machine just for testing, a folder, workgroup not much else, I added another samba server from another machines and created 2 users and shares.

I can see the netbios name in the network but can't access them. 
I can even access a folder I created and asks for user and pass which appears to login. However, cannot ad a single file to it.

I have created smb.conf from files examples I found on the web that are suppose to be simple share solutions even full access examples with passwordless use.
None have produced any sharing ability.

The only thing that seems to get close is right click share, guest etc. However, this doesn't allow me to share the way I want with read/write access without restrictions for the users of that folder.
Here is one example of a simple share

```
###### Default stuff from samba original files ########

[global]
workgroup = WORKGROUP
netbios name = MYTESTFILES
server string = %h server (Samba, Ubuntu)
dns proxy = no
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
server role = standalone server
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

############ Misc ############

usershare allow guests = yes

#======================= Share Definitions =======================

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

[mytestfiles]
path = /home/mytestfiles
available = yes
browsable = yes
public = yes
read only = no
writable = yes
valid users = user1
```

---

### Post by bab1 on 2015-09-19
You seem to be all over the map on this.  When you are ready to start fresh I will help you configure a Samba server that shares files to all users.  You do not need to reinstall Samba, but you should start with the one machine that you want to be the server for the network and have the default smb.conf file available.  Have some idea on what users are to be able to use the file share.

I'm ready when you're ready.

---

### Post by AgentZ86 on 2015-09-19
I am ready. 

I am in irc samba chat and people there seem helpful. However, after posting my code not much progress.
[https://bpaste.net/show/c81bf903d353](https://bpaste.net/show/c81bf903d353)

I can see my netbios and share but when I click the folder says: Failed to mount windows share, no such directory.
This is killing me.

I'm going to read the entire Samba book all the way through if I can't understand it then I'm going to have to get some video instructions.

I'm usually pretty good with reading tech docs. I learned python online pretty easy and made some gui apps etc. 
I learned mql and some sqlite3, then started learning django for kicks. 

I'm missing something simple here that is holding me back with samba

starting with the first chapter of samba 1.7 smbstatus or sudo smbstatus

I create users, restart smbd, restart nmbd; 
I get nothing, no users shown.

ok making some progress, 
chapter 1.9 says netbios names can only be 15 characters and characters only; and those few other symbols lists.

I was using _underscore in my netbios name and this underscore appears not to be allowed. We lets from what I can tell so far.
Anyhow reading on.

Thanks for any help. I'll be online reading most of the day today. And will likely be in irc samba chat too Agent86 same name on samba chat
Just FYI

---

### Post by bab1 on 2015-09-19
> **AgentZ86 said:**
> ok making some progress, 
chapter 1.9 says netbios names can only be 15 characters and characters only; and those few other symbols lists.

I was using _underscore in my netbios name and this underscore appears not to be allowed. We lets from what I can tell so far.
Anyhow reading on.

Thanks for any help. I'll be online reading most of the day today. And will likely be in irc samba chat too Agent86 same name on samba chat
Just FYI
What "book" are you reading?

I think it would be best for me to wait until you are done experimenting and then spamming your own thread here with any and all thoughts.  It becomes painful to correct all the incorrect side issues such as the one above.

When you are finally done I'll help.  It rather not go through unnecessary mistakes however.  I'm not interested in chat (irc or otherwise).  From my perspective Samba is a 10 minute setup.  The Samba install expects that the infrastructure (file system, etc.) are correctly set up.  I suggest that in your case it is not.

---

### Post by AgentZ86 on 2015-09-19
[https://www.samba.org/samba/docs/using_samba/ch01.html](https://www.samba.org/samba/docs/using_samba/ch01.html)

Readings this book and others listed on the samba.org site.
Chapter 1 (What is a Name) 
NetBIOS names are allowed to be only 15 characters and can consist only of standard alphanumeric characters (a-z, A-Z, 0-9) and the following:
    ! @ # $ % ^ & ( ) - ' { } . ~

Is this wrong ? If so why am I reading it; and why did they put it on the samba.org site as some official document ?
Sorry about all this. Your are completely correct that this is suppose to be simple. However, I don't have any complicated setup.

So far I'm just trying to share a folder that 2 users, and 2 computers can access. It's not anything major.
You open a libre office document from any of the computers and put in some info and save it. 
It's not complicated but it's getting complicated reading and learning 44 chapter server documents for something that is suppose to be so simple.

---

### Post by bab1 on 2015-09-19
> **AgentZ86 said:**
> [https://www.samba.org/samba/docs/using_samba/ch01.html](https://www.samba.org/samba/docs/using_samba/ch01.html)

Readings this book and others listed on the samba.org site.
Chapter 1 (What is a Name) 
NetBIOS names are allowed to be only 15 characters and can consist only of standard alphanumeric characters (a-z, A-Z, 0-9) and the following:
    ! @ # $ % ^ & ( ) - ' { } . ~

Is this wrong ? If so why am I reading it; and why did they put it on the samba.org site as some official document ?

Be aware that the "book" you are referring to is very old.  It was written for Samba v2.  We are now at Samba v4.  The basics apply, but the details are different.

It is the only book written on Samba in the O'Reilly technical series.  It does cover the basics in excruciating detail.  Most of the information won't help you share anything via Samba, but it does explain how the Samba daemons (smbd and nmbd) work.  On the other hand you don't need to be a biologist to cook chicken; do you?
> 
Sorry about all this. Your are completely correct that this is suppose to be simple. However, I don't have any complicated setup.

So far I'm just trying to share a folder that 2 users, and 2 computers can access. It's not anything major.
You open a libre office document from any of the computers and put in some info and save it. 
It's not complicated but it's getting complicated reading and learning 44 chapter server documents for something that is suppose to be so simple.
It doesn't matter whether you share documents between 2 or 200 people.  The pertinent fact is whether you are sharing these files as private (only to you via multiple machines) or semi private (between you and other specific users) or public (between all users on the system) or with guest access( anybody that access your network).

If you want to read the book, go ahead.  it will tell you everything technical about Samba and relatively little about the practical means to set up file sharing.  Two days ago in post #15 I provided the basic steps you need to follow to setup Samba file sharing.  Pick a machine you want to be the server and we can start with the first section (i.e. preparing the file system).  If you are ready, all I need to know is whether the share is to be private or semi-private or public and what the partition configuration is (df -h).

---

### Post by AgentZ86 on 2015-09-20
I read #15 and understood this. I was hoping the book would provide commands list and more insight so I wouldn't have to ask about every little subject. This doesn't appear samba is the same process as learning other languages and code.

Anyhow, I'm ready for the file system prep.

---

### Post by bab1 on 2015-09-20
> **AgentZ86 said:**
> I read #15 and understood this. I was hoping the book would provide commands list and more insight so I wouldn't have to ask about every little subject. This doesn't appear samba is the same process as learning other languages and code.
Nope.  Too many variations.  Plus a lot of Linux system administration knowledge is assumed known.
> 
Anyhow, I'm ready for the file system prep.

So to quote myself...

"are [you] sharing these files as private (only to you via multiple machines) or semi private (between you and other specific users) or public (between all users on the system) or with guest access( anybody that access your network).".

[COLOR="#0000FF"]**Edit:** I'm assuming that you have a host (computer) that will be the server and is not going to have any local users other than you as the system administrator (i.e. a sudo user).[/COLOR]

---

### Post by AgentZ86 on 2015-09-20
>     "are [you] sharing these files as private (only to you via multiple machines) or semi private (between you and other specific users) or public (between all users on the system) or with guest access( anybody that access your network).".

    Edit: I'm assuming that you have a host (computer) that will be the server and is not going to have any local users other than you as the system administrator (i.e. a sudo user). 

- semi private (between you and other specific users)

- * yes host computer ubuntu 15.04 desktop for samba server and no other users. (However, I did create another user on this machines when experimenting with adding a samba user) Just FYI no problem to delete that users if I can figure out how.

I don't want any users to have any restrictions to the directory/sub/and files = full access including delete,edit etc.

Thanks

---

### Post by bab1 on 2015-09-20
> **AgentZ86 said:**
> - semi private (between you and other specific users)

- * yes host computer ubuntu 15.04 desktop for samba server and no other users. (However, I did create another user on this machines when experimenting with adding a samba user) Just FYI no problem to delete that users if I can figure out how.

I don't want any users to have any restrictions to the directory/sub/and files = full access including delete,edit etc.

Thanks
Typically when sharing files between users the admin creates a file system outside of the /home file system.  For your needs it can something like this```
/share

or 

/smb

or 

/data
```

To make that directory you use this terminal command```
sudo mkdir /<dir-name> 
```...where <dir-name> is the name of your choice.  I don't like to type long names out over and over so I tend to use names with less than 5 letters, no caps and NO SPACES.  ;-)

Once you have made the directory post the output of this command ```
ls -l /
```...I will step you through the process so you see the logic.  

Managing the users will be pretty simple.  The permissions scheme is based on*** user:group:others*** permissions.  To manage all the individual users we can add all of them to a common user group.  Ubuntu has a group available that we can use or if you like we can make a new group for these users.

---

### Post by AgentZ86 on 2015-09-21
Ok, 
I did learn very little about that part of making directory as root or sudo. However, I was unaware of putting it outside the home directories.

I changed my ideas a little.

I still want semi private
However, I also want a group access for all users of another folder. 
I really need to learn all of the above in case I need to do something else.

Thanks, I'll get started



P.S
One last thing I would like to ask about the ubuntu gui. When you right click a folder to share, what is this actually designed to do ? Is this the (private user only access) ? 
Meaning that you must actually be logged in as that user to access/read/write files to that folder ?

---

### Post by bab1 on 2015-09-21
> **AgentZ86 said:**
> 
I did learn very little about that part of making directory as root or sudo. However, I was unaware of putting it outside the home directories.

I think you don't know what you don't know.  But you have to start somewhere. 
> 
I changed my ideas a little.

I still want semi private
However, I also want a group access for all users of another folder. 
I really need to learn all of the above in case I need to do something else.

I think you are confusing the directory you just created with a directory that you are going to share.  They are not necessarily the same thing.  My advice is to just follow along and ask questions, rather than go away with only partial knowledge of what is going on.  Nothing we are going to do is irreversible.  In fact with only two or three simple commands it is all gone and you are back to ground zero.  Keep notes and ask questions after we reach the end of a section (i.e. file system prep or adding users or creating a share).

Here is my view on the last 40 posts; In a short while I will decide that it is not worth my time as we are not moving ahead.  I will just simply stop responding to your posts.
> 

One last thing I would like to ask about the ubuntu gui. When you right click a folder to share, what is this actually designed to do ? Is this the (private user only access) ?  Meaning that you must actually be logged in as that user to access/read/write files to that folder ?
When the user uses the Ubuntu GUI (GNOME Nautilus) interface to create Samba usershares.  they are creating shares that are  limited to being created in the that users home directory.  The GNOME developers arbitrarily created the code to allow that user to create a share.  They can't determine what you have modified in your own home directory or where in your home directory the folder to be shared is.  You don't have to use the directory named "Public" as the shared folder.  So the short answer is:  It's designed to allow the user to share folders in that users home directory.  How it does that is another long story that is not well documented.

---

### Post by AgentZ86 on 2015-09-22
Ok here is the list for ls -l /
my folder is main_serv

```
total 104
drwxr-xr-x   2 root root  4096 Sep 21 17:56 bin
drwxr-xr-x   3 root root  4096 Sep 21 21:53 boot
drwxr-xr-x   2 root root  4096 Sep 21 17:50 cdrom
drwxr-xr-x  19 root root  4600 Sep 22 11:15 dev
drwxr-xr-x 136 root root 12288 Sep 21 22:02 etc
drwxr-xr-x   3 root root  4096 Sep 21 17:52 home
lrwxrwxrwx   1 root root    33 Sep 21 17:54 initrd.img -> boot/initrd.img-3.19.0-15-generic
drwxr-xr-x  25 root root  4096 Sep 21 21:51 lib
drwxr-xr-x   2 root root  4096 Sep 21 21:51 lib32
drwxr-xr-x   2 root root  4096 Apr 22 08:01 lib64
drwx------   2 root root 16384 Sep 21 17:47 lost+found
**drwxr-xr-x   2 root root  4096 Sep 22 16:40 main_serv**
drwxr-xr-x   3 root root  4096 Sep 21 18:35 media
drwxr-xr-x   2 root root  4096 Apr 17 17:34 mnt
drwxr-xr-x   2 root root  4096 Apr 22 08:01 opt
dr-xr-xr-x 242 root root     0 Sep 22 03:36 proc
drwx------   2 root root  4096 Sep 21 17:54 root
drwxr-xr-x  26 root root   760 Sep 22 07:58 run
drwxr-xr-x   2 root root 12288 Sep 21 21:51 sbin
drwxr-xr-x   2 root root  4096 Apr 22 08:01 srv
dr-xr-xr-x  13 root root     0 Sep 22 03:36 sys
drwxrwxrwt  11 root root  4096 Sep 22 16:40 tmp
drwxr-xr-x  11 root root  4096 Sep 21 21:51 usr
drwxr-xr-x  13 root root  4096 Apr 22 08:11 var
lrwxrwxrwx   1 root root    30 Sep 21 17:54 vmlinuz -> boot/vmlinuz-3.19.0-15-generic

```

---

### Post by bab1 on 2015-09-23
> **AgentZ86 said:**
> ...
my folder is main_serv

```
**drwxr-xr-x   2 root root  4096 Sep 22 16:40 main_serv**
```
Now you have a directory that is the start of the* file system* you are going to share (e.g. /main_serv).  The owner (root) has rwx (Read/Write/eXeucute) permissions; the user-group has, in this case r-x (read and eXecute) permissions; all others have r-x (read and eXecute) permissions.  The read and write permissions are obvious in their intent.  The reason for the eXecute bit is a little more obscure.  It allows a user to have the right to read the contents of the directory and descend into that directory (traversal rights).  This bit is only set on directories by default.  The root user umask provides permissions on directories of **u=rwx and g=rw and 0=rx (rwxr-xr-x) and permissions on files of u=rw,g=r,o=r (rw-rw-r--)**.

All users have the right to read the contents and traverse the */main_serv *directory.  Only root has the right to create or modify a file or create a directory in the */main_serv* directory.  Just as we need it to be.

Now you need to make 3 test directories.  We can have root make all 3 directories with this one command
  ```
sudo mkdir -p /main_serv/data/test1 /main_serv/data/test2 /main_serv/data/test3
```

These are obviously sub-directoriies of /main_serv and we can check their existence with this command
```
 ls -l /main_serv/data/
```

Try creating a file to the /main_serv/data/test1 directory with this command 
```
touch /main_serv/data/test1/file1
```
... you _should not_ have the permissions to do so.

To allow a select group of users write permission to the sub-directories you need to change the group ownership of the shared directory by adding the users to a user group and change the group ownership of the directory.  For a Ubuntu systems you can use the already configured user-group named ***users*** 
```
getent group users
users:x:100:
```

The steps to do that are add the user to the group
 ```
sudo adduser <user> <group>
```
...where <user> and <group>  are the user and group of your choice.  To add the user *_john_* to the group *_users_* the command would be
```
sudo adduser john users
```

Then root (via sudo again) changes the group ownership of the /main_serv/data/test1 directory with this command
```
sudo chgrp -R users  /main_serv/data/test1

```
Check it with this command
```
ls -l /main_serv/data/
```

You should see that the directory test1 now has the ownership of root:***users***.  You need to provide permissions besides ownership so you need to have root change the user-group permissions with this command
```
sudo chmod -R ug=rwX,o=rX /main_serv/data/test1/
```

Look at it again
```
ls -l /main_serv/data/
```

You should see the permissions are these: *rwxrwxr-x*.  Since the the user is in the group that now has has ownership and the permissions allow read and write,  you should be able to create a test file now.  Try this again
```
touch /main_serv/data/test1/file1
```
Please post the output of the command 
```
ls -l /main_serv/data/test1/
```

You (and anyone else in the group) now are able to create files and directories, but there is still a problem with this setup.  If you create a file in this directory the ownership is *<your-user> : <your-user-group>*.  This is not what you want for a commonly  shared directory.  It should be: *<your-user> : **users***.  You need to set the *sgid* bit to provide group inheritance.  You do that with this command
```
sudo chmod -R g+s  /main_serv/data/
```
Setting the *sgid bit* will provide group inheritance to all the subdirectories of /main_serv/data/

Create a few files in the test1 2 and 3 directories to see if this all works.  Hopefully there are no errors (on my part or yours).  Ask if you have problems, questions or concerns.

Once you have all of this sorted out we can take the next step.

---

### Post by AgentZ86 on 2015-09-23
touch game me permission denied. I doubled checked my commands for typoes and ran through it again but got the same permissions denied.
I think I'm starting to see what's going on here though. The file setup is part of the requirement for the samba. Samba is more like a tunnel that needs matching permissions for the folders not just samba on it's own. Otherwise samba could gain control of your files permissions instead of the OS controlling things. 
Ok, anyhow this is what I got so far.

> agent86@agent86-desktop:~$ sudo chgrp -R users /main_serv/data/test1
agent86@agent86-desktop:~$ ls -l /main_serv/data/
total 12
drwxr-xr-x 2 root users 4096 Sep 23 09:25 test1
drwxr-xr-x 2 root root  4096 Sep 23 09:25 test2
drwxr-xr-x 2 root root  4096 Sep 23 09:25 test3



> agent86@agent86-desktop:~$ sudo chmod -R ug=rwX,o=rX /main_serv/data/test1/
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 12
drwxrwxr-x 2 root users 4096 Sep 23 09:25 test1
drwxr-xr-x 2 root root  4096 Sep 23 09:25 test2
drwxr-xr-x 2 root root  4096 Sep 23 09:25 test3

> agent86@agent86-desktop:~$ touch /main_serv/data/test1/file1
touch: cannot touch &#8216;/main_serv/data/test1/file1&#8217;: Permission denied

Thanks.

---

### Post by bab1 on 2015-09-23
> **AgentZ86 said:**
> touch gave me permission denied. I doubled checked my commands for typoes and ran through it again but got the same permissions denied.
It's hard for me to tell where you are with all the various steps.  The users group has rw permissions on the  */main_serv/data/test1*.  Have you added yourself to that group.  Post me that output this command
```
getent group users
```> 

I think I'm starting to see what's going on here though. The file setup is part of the requirement for the samba. Samba is more like a tunnel that needs matching permissions for the folders not just samba on it's own. Otherwise samba could gain control of your files permissions instead of the OS controlling things. 
Ok, anyhow this is what I got so far.
Thanks.
Samba is an application that assumes that the infrastructure is properly in place before you configure it.  Samba does not ever control the file systems permissions.  It authenticates users (who are you), provides access to the file system, and can provide some umask abilities.  Linux file system permissions are the final arbiter of the users access rights.

---

### Post by AgentZ86 on 2015-09-23
users:x:100:agent86

---

### Post by bab1 on 2015-09-23
> **AgentZ86 said:**
> users:x:100:agent86
Have you rebooted the machine of at least logged off and back on.  Some of the user configuration changes require that.  I forgot to have you do that,  

Post the output of these commands.  I'm looking to see if you have read and eXecute permissions all the way from / to /main_serv/data/test1

```
ls -l /

ls -l /main_serv/

ls -l /main_serv/data/

ls -l /main_serv/data/test1

```

---

### Post by AgentZ86 on 2015-09-24
> **bab1 said:**
> Have you rebooted the machine of at least logged off and back on.  Some of the user configuration changes require that.  I forgot to have you do that,  

Post the output of these commands.  I'm looking to see if you have read and eXecute permissions all the way from / to /main_serv/data/test1
> 
```
ls -l /

ls -l /main_serv/

ls -l /main_serv/data/

ls -l /main_serv/data/test1

```

agent86@agent86-desktop:~$ ls -l /
total 104
drwxr-xr-x   2 root root  4096 Sep 23 12:03 bin
drwxr-xr-x   3 root root  4096 Sep 23 12:10 boot
drwxr-xr-x   2 root root  4096 Sep 21 17:50 cdrom
drwxr-xr-x  19 root root  4600 Sep 24 08:17 dev
drwxr-xr-x 136 root root 12288 Sep 24 08:57 etc
drwxr-xr-x   4 root root  4096 Sep 24 08:56 home
lrwxrwxrwx   1 root root    33 Sep 23 12:07 initrd.img -> boot/initrd.img-3.19.0-28-generic
lrwxrwxrwx   1 root root    33 Sep 21 17:54 initrd.img.old -> boot/initrd.img-3.19.0-15-generic
drwxr-xr-x  25 root root  4096 Sep 21 21:51 lib
drwxr-xr-x   2 root root  4096 Sep 21 21:51 lib32
drwxr-xr-x   2 root root  4096 Apr 22 08:01 lib64
drwx------   2 root root 16384 Sep 21 17:47 lost+found
**drwxr-xr-x   3 root root  4096 Sep 23 09:25 main_serv**
drwxr-xr-x   3 root root  4096 Sep 21 18:35 media
drwxr-xr-x   2 root root  4096 Apr 17 17:34 mnt
drwxr-xr-x   2 root root  4096 Apr 22 08:01 opt
dr-xr-xr-x 238 root root     0 Sep 24 04:16 proc
drwx------   2 root root  4096 Sep 21 17:54 root
drwxr-xr-x  27 root root   780 Sep 24 08:43 run
drwxr-xr-x   2 root root 12288 Sep 23 12:06 sbin
drwxr-xr-x   2 root root  4096 Apr 22 08:01 srv
dr-xr-xr-x  13 root root     0 Sep 24 08:44 sys
drwxrwxrwt  11 root root  4096 Sep 24 08:44 tmp
drwxr-xr-x  11 root root  4096 Sep 21 21:51 usr
drwxr-xr-x  13 root root  4096 Apr 22 08:11 var
lrwxrwxrwx   1 root root    30 Sep 23 12:07 vmlinuz -> boot/vmlinuz-3.19.0-28-generic
lrwxrwxrwx   1 root root    30 Sep 21 17:54 vmlinuz.old -> boot/vmlinuz-3.19.0-15-generic
**agent86@agent86-desktop:~$ ls -l /main_serv/**
total 4
drwxr-sr-x 5 root root 4096 Sep 23 09:25 data
**agent86@agent86-desktop:~$ ls -l /main_serv/data/**
total 12
drwxrws--x 2 root users 4096 Sep 24 09:01 test1
drwxr-sr-x 2 root root  4096 Sep 23 09:25 test2
drwxr-sr-x 2 root root  4096 Sep 23 09:25 test3
*agent86@agent86-desktop:~$ ls -l /main_serv/data/tes1*  **oops**
ls: cannot access /main_serv/data/tes1: No such file or directory
**agent86@agent86-desktop:~$ ls -l /main_serv/data/test1**
total 0
-rw-rwSr-- 1 agent86 agent86 0 Sep 24 08:58 file1
-rw-rw-r-- 1 agent86 users   0 Sep 24 09:01 file2

agent86@agent86-desktop:~$** touch /main_serv/data/test2/file1**
touch: cannot touch &#8216;/main_serv/data/test2/file1&#8217;: Permission denied





OK this is strange.
since I got Permission denied the first time around for touch "file1"

Machine was reboot this morning, so I went through the entire instructions several times to make sure I didn't typo or make mistakes.
Several times in fact and it came to the same point as "permission denied" when trying to touch "file1" 

So in my limited knowledge I created another user thinking that the possibility of having my root user also being the user might create some problem. I really don't know but wanted to try something
I created a new user and added them to the group just as before.

This time I could touch "file1" without fail as you can see with the ls -l /main_serv/data/test1/file1
I could even create file2 etc.

However, touch /main_serv/data/test2/file1 failed with permission denied.
I was certainly surprised that creating another user would allow touch /test1/file1 and so on, but then also surprised that touch /test2/file1 failed

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> OK this is strange.
since I got Permission denied the first time around for touch "file1"

Machine was reboot this morning, so I went through the entire instructions several times to make sure I didn't typo or make mistakes.
Several times in fact and it came to the same point as "permission denied" when trying to touch "file1" 

So in my limited knowledge I created another user thinking that the possibility of having my root user also being the user might create some problem. I really don't know but wanted to try something
I created a new user and added them to the group just as before.

This time I could touch "file1" without fail as you can see with the ls -l /main_serv/data/test1/file1
I could even create file2 etc.

However, touch /main_serv/data/test2/file1 failed with permission denied.
I was certainly surprised that creating another user would allow touch /test1/file1 and so on, but then also surprised that touch /test2/file1 failed
I see one possible problem and a lot of confusion.  This is incorrect.  ```
agent86@agent86-desktop:~$ ls -l /main_serv/
total 4 
drwxr-sr-x 5 root root 4096 Sep 23 09:25 data
```...you haven't followed the instructions correctly.  I don't see evidence of a second user creating anything.

My suggestion is for you to delete everything below /main_serv and start over in smaller steps.  The simple way to do that is to do the following
([COLOR="#FF0000"]**BE CAREFUL:  you can do damage to your entire system if you don't do this exactly as shown**[/COLOR])  ```
sudo rm -rf /serv_main/data
```

When you have done the above post the output of these commands```
ls -l /main_serv

getent passwd |grep 100

getent group users
```

Please remember to use the [noparse]```
 
```[/noparse] blocks when posting text from the terminal.

I think it is best that you DO NOT try and diagnose the problem.  Too many variables means that you do not know what causes what.  Try to not wander off into the weeds.  ;-)

The notion of "my root user also being [your] user" is incorrect.  Your user is not the root user.  Your user has the ability to switch to the root user.  If you don't use sudo then you are not switching to the root user.  You're only using sudo when it is appropriate, I hope. 

So we start over...

---

### Post by AgentZ86 on 2015-09-24
```
agent86@agent86-desktop:~$ ls -l/main_serv
ls: invalid option -- '/'
Try 'ls --help' for more information.
agent86@agent86-desktop:~$ ls -l /main_serv
total 0
agent86@agent86-desktop:~$ getent passwd |grep 100
systemd-timesync:x:100:104:systemd Time Synchronization,,,:/run/systemd:/bin/false
agent86:x:1000:1000:Steve,,,:/home/agent86:/bin/bash
beth:x:1001:1001:Beth,,,:/home/beth:/bin/bash
agent86@agent86-desktop:~$ getent group users
users:x:100:agent86,beth
agent86@agent86-desktop:~$ 
```

It's true I didn't create anything with the second user even after adding the second user.
I only followed the instruction exactly as the admin/root user and while logged in as that admin user.

The first time around I added the user as instructed which was the same user as my admin/root user.
Was your instruction explicitly to ad a second user ?
Everything that was done was done with my user who is the admin and logged into the system.
Is this ok ? Or do I need to create the second user then login as that second user ?

Anyhow perhaps I didn't understand the instructions

Please advise

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l/main_serv
ls: invalid option -- '/'
Try 'ls --help' for more information.

agent86@agent86-desktop:~$ ls -l /main_serv
total 0

agent86@agent86-desktop:~$ getent passwd |grep 100
systemd-timesync:x:100:104:systemd Time Synchronization,,,:/run/systemd:/bin/false
agent86:x:1000:1000:Steve,,,:/home/agent86:/bin/bash
beth:x:1001:1001:Beth,,,:/home/beth:/bin/bash

agent86@agent86-desktop:~$ getent group users
users:x:100:agent86,beth

agent86@agent86-desktop:~$ 
```

Make a directory below /main_serv with this command```
sudo mkdir /main_serv/data
```

Try and not mash all the data together.  Use multiple code blocks if you want.

Post the output of ```
ls -l /main_serv 
```

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l/main_serv
ls: invalid option -- '/'
Try 'ls --help' for more information.
agent86@agent86-desktop:~$ ls -l /main_serv
total 0
agent86@agent86-desktop:~$ getent passwd |grep 100
systemd-timesync:x:100:104:systemd Time Synchronization,,,:/run/systemd:/bin/false
agent86:x:1000:1000:Steve,,,:/home/agent86:/bin/bash
beth:x:1001:1001:Beth,,,:/home/beth:/bin/bash
agent86@agent86-desktop:~$ getent group users
users:x:100:agent86,beth
agent86@agent86-desktop:~$ 
```

It's true I didn't create anything with the second user even after adding the second user.
I only followed the instruction exactly as the admin/root user and while logged in as that admin user.

The first time around I added the user as instructed which was the same user as my admin/root user.
Was your instruction explicitly to ad a second user ?
Everything that was done was done with my user who is the admin and logged into the system.
Is this ok ? Or do I need to create the second user then login as that second user ?

Anyhow perhaps I didn't understand the instructions

Please advise
When you talk in generalities I can't really tell what you are talking about exactly.  For example > The first time around I added the user as instructed which was the same user as my admin/root user.
Was your instruction explicitly to ad a second user ?..added a second user to what?  I can't really tell which of the commands you are specifically talking about.  I can guess, but we know what that gets.

Once again.  The fact that your user can invoke sudo commands has nothing to do with your problems.  That user is no different from any other user other than you can successfully use the command sudo.

---

### Post by AgentZ86 on 2015-09-24
```
ls -l /main_serv
total 4
drwxr-xr-x 2 root root 4096 Sep 24 11:41 data
```

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
ls -l /main_serv
total 4
drwxr-xr-x 2 root root 4096 Sep 24 11:41 data[\CODE]
The \ should be a / in the closing code block. You are better off clicking on the [SIZE=6]**# **[/SIZE] icon to create the code blocks.  Look at the top of the reply editor for that icon.

Now make a directory below /main_serv/data with this command[CODE]sudo mkdir /main_serv/data/test1
```

Post the output of this command```
ls -l /main_serv/data
```

---

### Post by AgentZ86 on 2015-09-24
```
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxr-xr-x 2 root root 4096 Sep 24 11:56 test1
```

I accidentally hit the html button the first time so I edited the post. Unfortunately the edit post page doesn't have the # button on it.

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxr-xr-x 2 root root 4096 Sep 24 11:56 test1
```

I accidentally hit the html button the first time so I edited the post. Unfortunately the edit post page doesn't have the # button on it.
Change the group ownership of the directory *test1* with with this command```

sudo chgrp users /main_serv/data/test1

``` 

Post the output of ```
ls -l /main_serv/data
```

Edit:  I originally got the main_serv name backwards.  Please use the correct directory name in all cases.

---

### Post by AgentZ86 on 2015-09-24
```
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxr-xr-x 2 root users 4096 Sep 24 11:56 test1
```

I saw that serv_main it's ok. I assumed /main_serv

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxr-xr-x 2 root users 4096 Sep 24 11:56 test1
```

I saw that serv_main it's ok. I assumed /main_serv

To allow read/write/eXecute permissions for the users group in all directories below /main_ser/data use this command```
sudo chmod -R ug=rwX,o=rX /main_serv/data
```

Post the output of these 2 commands ```
ls -l /main_serv

ls -l /main_serv/data
```

---

### Post by AgentZ86 on 2015-09-24
```
agent86@agent86-desktop:~$ ls -l /main_serv
total 4
drwxrwxr-x 3 root root 4096 Sep 24 11:56 data
```
```

agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxrwxr-x 2 root users 4096 Sep 24 11:56 test1
```

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l /main_serv
total 4
drwxrwxr-x 3 root root 4096 Sep 24 11:56 data
```
```

agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxrwxr-x 2 root users 4096 Sep 24 11:56 test1
```

Now make a file with this command```
touch /main_serv/data/test1/file1
```

Post the output of```
ls -l /main_serv/data/test1
```

---

### Post by AgentZ86 on 2015-09-24
```
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 0
-rw-rw-r-- 1 agent86 agent86 0 Sep 24 16:21 file1

```

---

### Post by bab1 on 2015-09-24
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 0
-rw-rw-r-- 1 agent86 agent86 0 Sep 24 16:21 file1

```

So it works.  You have permissions to access the test1 directory and create (write) a file.  I'm not sure what you did before but now you can create a file.  Now you can see that the file is only accessible for modification by the user agent86.  

In a share that is accessible by multiple users you need to have group inheritance so that the files and directories continue to be accessible by all.  To do that we need to set the sgid bit.  In the prior setup you set the sticky bit (S) and not the sgid bit (s).  You need a lower case s.

To set the sticky bit on the /main_serv/data/test1 directory you should use this command```

sudo chmod g+s /main_serv/data/test1

```
Post the output of this command```
ls -l /main_serv/data
```

---

### Post by AgentZ86 on 2015-09-25
I actually never really made it to g+s last time. 
If failed at touch

```
touch /main_serv/data/test1/file1
```
It was only after numerous tries and fails that I added another system users such as:
```
sudo adduser beth
sudo beth users
```
Then the above touch commands actually worked at this point for creating test1/file1


Was I suppose to run this similar code for test2 and test3 ?
```
sudo chmod -R ug=rwX,o=rX /main_serv/data/test1/
```

> Setting the sgid bit will provide group inheritance to all the subdirectories of /main_serv/data/

Create a few files in the test1 2 and 3 directories to see if this all works. Hopefully there are no errors (on my part or yours). Ask if you have problems, questions or concerns.

In short I did not run these codes below in my prior attempt but I guess the question is **should I have ?**
With the quoted statement above I assumed not.
```
sudo chmod -R ug=rwX,o=rX /main_serv/data/**test2/**
```
```
sudo chmod -R ug=rwX,o=rX /main_serv/data/**test3/**
```

Please clarify this subject if further commands were needed to alow write to test2, and test3 or does the inheritance make it possible for all files in the /data directory ?

Thanks
I'm looking forward to reading more linux and permissions documents. It appears I need major tutorials on these things.

> **bab1 said:**
> So it works.  You have permissions to access the test1 directory and create (write) a file.  I'm not sure what you did before but now you can create a file.  Now you can see that the file is only accessible for modification by the user agent86.  

In a share that is accessible by multiple users you need to have group inheritance so that the files and directories continue to be accessible by all.  To do that we need to set the sgid bit.  In the prior setup you set the sticky bit (S) and not the sgid bit (s).  You need a lower case s.

To set the sticky bit on the /main_serv/data/test1 directory you should use this command```

sudo chmod g+s /main_serv/data/test1

```
Post the output of this command```
ls -l /main_serv/data
```

Ok here it is
```
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxrwsr-x 2 root users 4096 Sep 24 16:21 test1
```

---

### Post by bab1 on 2015-09-25
> **AgentZ86 said:**
> Ok here it is
```
agent86@agent86-desktop:~$ ls -l /main_serv/data
total 4
drwxrwsr-x 2 root users 4096 Sep 24 16:21 test1
```

Now run this command```
touch  /main_serv/data/test1/**[COLOR="#ff00FF"]file2[/COLOR]**
```

Post the output of ```
 ls -l /main_serv/data/test
```

---

### Post by AgentZ86 on 2015-09-25
> **bab1 said:**
> Now run this command```
touch  /main_serv/data/test1/**[COLOR="#ff00FF"]file2[/COLOR]**
```

Post the output of ```
 ls -l /main_serv/data/test
```

```
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 0
-rw-rw-r-- 1 agent86 agent86 0 Sep 24 16:21 file1
-rw-rw-r-- 1 agent86 users   0 Sep 25 15:54 file2
```

---

### Post by bab1 on 2015-09-25
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 0
-rw-rw-r-- 1 agent86 agent86 0 Sep 24 16:21 file1
[COLOR="#FF0000"]-rw-rw-r-- 1 agent86 users   0 Sep 25 15:54 file2[/COLOR]
```

The file system */main_serv/data/test1 * with group inheritance has been successfully created.  Any file or directory that you create in *test1* will have **_users_** group ownership as you see in red above.

Now we need to share the test1 directory.  Edit the /etc/samba/smb,conf file by adding this to the very bottom of existing text
```

[MyTest]
        comment = Shared Data
        path = /main_serv/data/test1
        valid users = @users
        force group = users
        create mask = 0664
        force directory mode = 2775

```

Save the file and restart the smbd daemon with this command```
sudo service smbd restart
```...this is all the Samba configuration you need.

See if you can now browse to the share.  If this works we discuss what we have done.  We can add another share that is *public* to **all **users.

---

### Post by AgentZ86 on 2015-09-26
Can you explain users group ownership ?

ONLY users that I added to the users group right ? 
NOT just anyone that that logs into the network workgroup ?

I guess I'm asking who can actually use this folder as it stands at this point ? 
Just so I can understand what's going on.

Thanks

---

### Post by bab1 on 2015-09-26
> **AgentZ86 said:**
> Can you explain users group ownership ?

ONLY users that I added to the users group right ? 
Only _Ubuntu_ users that you add to the group (local users) .  > 
NOT just anyone that that logs into the network workgroup ?
The Samba workgroup is a collection of shares not users.> 
I guess I'm asking who can actually use this folder as it stands at this point ? 
Just so I can understand what's going on.

Thanks
The user-group named ***users*** has rwx permissions to the folder.  Only users that are part of the user-group ***users*** have access to this folder.  The users that you display with this command have read/write and traverse permissions```
getent group users
```
Bear in mind we could have configured a different user-group for this if we wanted to.  You could have created a group named smbusers and done the same thing.  Ubuntu has a few user-groups that are created by default.  I use the *_[COLOR="#008000"]users[/COLOR]_* group because I know it is available on all Ubuntu systems and is always gid=100.

When the user "logs in" to Samba, they are really only ***[COLOR="#0000FF"]authenticating[/COLOR]*** themselves (who are you).  Samba then allows you access to the share.  The Ubuntu permissions are for ***[COLOR="#FF0000"]authorization[/COLOR]*** (you can do that).  Authentication is NOT authorization.  You need both. 

Can the users access the shared directory?  Have you made files and subdirectories?  What about ownership and permissions?

---

### Post by AgentZ86 on 2015-09-27
Ok, so at this point only the (users group) of ubuntu can read/write to this folder via (local machine) ?

And ubuntu users will only be added to the group if I ad them.

Got it, thanks

---

### Post by bab1 on 2015-09-27
> **AgentZ86 said:**
> Ok, so at this point only the (users group) of ubuntu can read/write to this folder via (local machine) ?



You should also be able to access the shared directory via Samba too.  Are we done?

---

### Post by AgentZ86 on 2015-09-28
> **bab1 said:**
> You should also be able to access the shared directory via Samba too.  Are we done?

I cannot access the folder from the local machine nor my other ubuntu machine.
I can see the folder but when I click on it I get the pop box asking for password.
When I put in the password it will not let me access the folder and just keeps popping up.
I assume I am using the incorrect password but that's only because I cannot access the folder.
So I tried the following things below:

```
agent86@agent86-desktop:~$ sudo smbpasswd agent86
New SMB password:
Retype new SMB password:
Failed to find entry for user agent86.
```
```
agent86@agent86-desktop:~$ sudo smbpasswd beth
New SMB password:
Retype new SMB password:
Failed to find entry for user beth.
```

Users are there for the machine for sure:
```
agent86@agent86-desktop:~$ getent group users
users:x:100:agent86,beth
```

Browsing the web for command to see the samba users. This produced no output at all.
```
agent86@agent86-desktop:~$ sudo pdbedit -L
agent86@agent86-desktop:~$ sudo pdbedit -L -v
agent86@agent86-desktop:~$ 
```

OK, I tried a few more time this time with the -a option
I have no idea why this would make any different actually but it added them to the samba list. I have no idea why they were not there already. I thought we had confirmed that they were there. I am confused.........
It's acting like we never added them to samba.
```
agent86@agent86-desktop:~$ sudo smbpasswd -a agent86
New SMB password:
Retype new SMB password:
Added user agent86.
agent86@agent86-desktop:~$ sudo smbpasswd -a beth
New SMB password:
Retype new SMB password:
Added user beth.
```
```
agent86@agent86-desktop:~$ sudo pdbedit -L
agent86:1000:Steve
beth:1001:Beth
```

I can browse the folder. I'll read/write some from here and the other machine and post back.
Thanks

When I rebooted this time. Then browse network does not show samba shares at all. 
I only see (windows network, then inside this is WORKGROUP, then agent86-desktop, then inside this is MyTest folder
I can go inside the folder but can not read/write anything says permission denied. Can't edit file1, cannot add any folders or new files
Everything says permission denied (read only file system)

From the networked ubuntu computer/my other desktop.
I can see the samba share, and access the MyTest folder but ends with the same permission messages.

I know that we didn't cover adding any smbpasswords but only added users to the group.

Am I getting too far ahead of myself here ?

---

### Post by bab1 on 2015-09-28
> **AgentZ86 said:**
> ...
Am I getting too far ahead of myself here ?
I believe so.  I want to see that you can access the directory* /main_serv/data/test1* a a local user (Not via Samba).  Do the first command and post the output of the second command```
touch ls -l /main_serv/data/test1/file10

ls -l /main_serv/data/test1

```
I want to see the share definition. Post the output of ```
cat /etc/samba/smb.conf
```

Nothing extra needed at this time.

Don't try and repair anything.  Certainly not multiple things at one time.  It make it hard to reproduce your problems on my machine.  I have a test share setup on y laptop that is almost identical to what you are attempting.  It works fine.  I diagnose step by step.  Not by trying a bunch of things and hoping it will start working.

Once again, just the tests I asked for above.  ;-)

---

### Post by AgentZ86 on 2015-09-29
> **bab1 said:**
> I believe so.  I want to see that you can access the directory* /main_serv/data/test1* a a local user (Not via Samba).  Do the first command and post the output of the second command```
touch ls -l /main_serv/data/test1/file10

ls -l /main_serv/data/test1

```
I want to see the share definition. Post the output of ```
cat /etc/samba/smb.conf
```

Nothing extra needed at this time.

Don't try and repair anything.  Certainly not multiple things at one time.  It make it hard to reproduce your problems on my machine.  I have a test share setup on y laptop that is almost identical to what you are attempting.  It works fine.  I diagnose step by step.  Not by trying a bunch of things and hoping it will start working.

Once again, just the tests I asked for above.  ;-)


I think you meant touch /main_serv/data/test1/file10 right ?
The  ls -l is giving me invalid error messages.
Anyhow please confirm as I have done below

```
agent86@agent86-desktop:~$ touch /main_serv/data/test1/file10
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 8
-rw-rw-r-- 1 agent86 agent86 12 Sep 28 09:30 file1
-rw-rw-r-- 1 agent86 agent86 12 Sep 28 09:30 file1~
-rw-rw-r-- 1 agent86 users    0 Sep 29 09:13 file10
-rw-rw-r-- 1 agent86 users    0 Sep 25 15:54 file2
agent86@agent86-desktop:~$ 
```

```
agent86@agent86-desktop:~$ cat /etc/samba/smb.conf
#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
	server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# Server role. Defines in which mode Samba will operate. Possible
# values are "standalone server", "member server", "classic primary
# domain controller", "classic backup domain controller", "active
# directory domain controller". 
#
# Most people will want "standalone sever" or "member server".
# Running as "active directory domain controller" will require first
# running "samba-tool domain provision" to wipe databases and create a
# new domain.
   server role = standalone server

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped
# to anonymous connections
   map to guest = bad user

########## Domains ###########

#
# The following settings only takes effect if 'server role = primary
# classic domain controller', 'server role = backup domain controller'
# or 'domain logons' is set 
#

# It specifies the location of the user's
# profile directory from the client point of view) The following
# required a [profiles] share to be setup on the samba server (see
# below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each
# user's home directory as \\server\username
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.
# Un-comment the following parameter to make sure that only "username"
# can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

[MyTest]
        comment = Shared Data
        path = /main_serv/data/test1
        valid users = @users
        force group = users
        create mask = 0664
        force directory mode = 2775
```

FYI today the samba (network browse) shows my agent86_desktop and the other PC on the network.
I can browse to the My_Test but still no permissions to create or edit files etc. 
Just wanted to let you know and I have no idea why it seems to intermittently appear and disappear randomly on both machines running 15.04 fresh installs
Sometimes you see the _desktops and sometimes you only see the windows network folder

---

### Post by bab1 on 2015-09-29
> **AgentZ86 said:**
> I think you meant touch /main_serv/data/test1/file10 right ?
The  ls -l is giving me invalid error messages.
Anyhow please confirm as I have done below

```
agent86@agent86-desktop:~$ touch /main_serv/data/test1/file10
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 8
-rw-rw-r-- 1 agent86 agent86 12 Sep 28 09:30 file1
-rw-rw-r-- 1 agent86 agent86 12 Sep 28 09:30 file1~
-rw-rw-r-- 1 agent86 users    0 Sep 29 09:13 file10
-rw-rw-r-- 1 agent86 users    0 Sep 25 15:54 file2
agent86@agent86-desktop:~$ 
```
Yes, what you did in the end was correct.  It was my fault, I'll blame it on "cut 'n paste".  ;-)> 

```
agent86@agent86-desktop:~$ cat /etc/samba/smb.conf
...

[MyTest]
        comment = Shared Data
        path = /main_serv/data/test1
        valid users = @users
        force group = users
        create mask = 0664
        force directory mode = 2775
```

Please add this to the share definition```
	writeable = yes
 	browseable = yes
        guest ok = no		
```

The share definition should look like this```

[MyTest]
        comment = Shared Data
        path = /main_serv/data/test1
        valid users = @users
        force group = users
        create mask = 0664
        force directory mode = 2775
[COLOR="#FF0000"]        writeable = yes
 	browseable = yes
        guest ok = no		[/COLOR]

```

What we have done is to explicitly allow browsing, and file write ability and deny guests of any kind.

Reboot the machine or restart the Samba server with this command```
sudo service smbd restart
```
You should now be able to browse to the share and create and modify files.

You should be able to use a remote machine and browse to the share.  Once you are authenticated you should be able to create another file and a directory.  If you can have both users access the share and create a file and directory.

Go back to the Samba server and post the output of this command (again)```
ls -l /main_serv/data/test1
```

You should see the new file and directory listed.  I want to see who owns the file and what the permissions are.

---

### Post by bab1 on 2015-09-29
> **AgentZ86 said:**
> FYI today the samba (network browse) shows my agent86_desktop and the other PC on the network.
I can browse to the My_Test but still no permissions to create or edit files etc. 
Just wanted to let you know and I have no idea why it seems to intermittently appear and disappear randomly on both machines running 15.04 fresh installs
Sometimes you see the _desktops and sometimes you only see the windows network folder

There are multiple reasons that you would have to drill down through the "Windows" folder.  It's unfortunate that the "Windows" folder is named as such.  It is not named that for the reasons you would think.  The Windows Folder contains **all **the WORKGROUPS **available** on the network.  Since this normally includes just the one WORKGROUP you have configured you should always see it in the Windows Folder.  The Samba server that you see outside of the Windows folder is configured with the WORKROUP that the client is also configured with.

All this is to say; For a single WORKGROUP you should see the same thing outside as well is inside the Windows folder.  Usually when the Samba server has a delay accessing the share you will not see the Server outside of the Windows folder.  Normally it's temporary only.

At this point we are just talking in theory.  I need to see what happens with the setup we modified in the previous post.

---

### Post by AgentZ86 on 2015-09-30
```
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 16
-rw-rw-r-- 1 agent86 users   12 Sep 30 09:29 file1
-rw-rw-r-- 1 agent86 agent86 12 Sep 28 09:30 file1~
-rw-rw-r-- 1 agent86 users   13 Sep 30 09:28 file10
-rw-rw-r-- 1 agent86 users   12 Sep 29 09:21 file2
-rw-rw-r-- 1 agent86 users    0 Sep 25 15:54 file2~

```

Shows in network browser right away as I expected and can read/write any document in there from both ubuntu computers on the network

Thanks

---

### Post by bab1 on 2015-09-30
> **AgentZ86 said:**
> ```
agent86@agent86-desktop:~$ ls -l /main_serv/data/test1
total 16
-rw-rw-r-- 1 agent86 users   12 Sep 30 09:29 file1
-rw-rw-r-- 1 agent86 agent86 12 Sep 28 09:30 file1~
-rw-rw-r-- 1 agent86 users   13 Sep 30 09:28 file10
-rw-rw-r-- 1 agent86 users   12 Sep 29 09:21 file2
-rw-rw-r-- 1 agent86 users    0 Sep 25 15:54 file2~

```

Shows in network browser right away as I expected and can read/write any document in there from both ubuntu computers on the network

Thanks
Remind me; are there other computers on the network?    Can you see the share from those machines also?

---

### Post by AgentZ86 on 2015-09-30
Yes there are other computers on the network. 
I have not tried any other windows computers yet. Just the 1 other Ubuntu 15.04 computer so far and I can access the files and read/write from the other computer on the network as well.

When the pop up asks for user and pass I put in the user/pass of the samba user I created previously and not just the local user/pass

The local user/pass did not allow access to the folder and the pop up just kept asking for credentials. So I put in the samba user/pass.
I hope that is what I was suppose to do.

---

### Post by bab1 on 2015-09-30
> **AgentZ86 said:**
> Yes there are other computers on the network. 
I have not tried any other windows computers yet. Just the 1 other Ubuntu 15.04 computer so far and I can access the files and read/write from the other computer on the network as well.

When the pop up asks for user and pass I put in the user/pass of the samba user I created previously and not just the local user/pass

The local user/pass did not allow access to the folder and the pop up just kept asking for credentials. So I put in the samba user/pass.
I hope that is what I was suppose to do.

All of the humans using my network have the same username/password.  That way it does not matter whether that person is logging in locally or across the network via Samba (or Windows sharing).

[COLOR="#0000FF"]**Edit: **To clarify, if user John has an account john and and a pass of xyz, then  the Samba user and pass is also john with a pass of xyz.  Each user has their own username/password.[/COLOR]

---

### Post by AgentZ86 on 2015-10-02
OK, so the user/pass does not seem to allow any of my machines to access the samba share. 

I don't understand what you mean by "John has an account" and that this would also be the samba user and pass ?

How does this John get a user/password on samba share unless I actually create a samba password. This is where I'm confused and don't understand the difference between an account on the local machine and the samba shares. 

For now I can only say that my **users/accounts cannot access the samba share MyTest **without using the samba user/password that I created when using the smbpasswd command.
I go to network browsers, then navigate to MyTest, screen comes up asking for credentials. I put in my user/pass of this local machine(NOT networked) Just local login using the same credentials that I use to login to my ubuntu account.
This fails. Screen gets dim and makes me cancel for anything that does not (succeed)
If I use my (ubuntu user) and password I created for samba for this user. Then it can read/write for everything in MyTest. I can also navigate to MyTest with any computer on the local network and login with (any ubuntu user) And a samba password that I created. 
However, NO local network computer can access MyTest with their own user/passwords. They can only access with a samba passward that I created with this command:
```

sudo smbpasswd -a <user>
```

So as I understand it from what your telling me is that I should be able to access MyTest with a simple user/password without specifically adding any samba user or samba passwords etc. ? 

I'm sorry for this long winded response but I'm confused about what's going.
Thanks

---

### Post by bab1 on 2015-10-02
It might be helpful to have a list of terms that define some of the concepts we are using here.
[LIST]
[*]host = A machine running that provides a compting environment
[*]local host = The host you are initially logged into
[*]remote host = A host that is on your network that you are able to access from your local host
[*]OS - Operating System (e.g Linux or Windows or Mac OSX)
[*]Samba = Application (processes) running on a host 
[*]Server = A process that is continually running on a host that is waiting for a request from a client (Samba server)
[*]Client = A process that requests a service from the corresponding server (Samba Client)
[*]Linux users --
    - root user (uid=0) - The user that administers the system
    - system user (uid=1-999 on Ubuntu systems) - Users that can' login to the system but are useful in running the system
    - mortal users (uid=1000 to 65000+ on Ubuntu systems) - Human user accounts
[*]Windows users - human user accounts on a Windows machine
[*]Samba users - users of the Samba application on a specific host (a Samba file server)
[/LIST]
> **AgentZ86 said:**
> OK, so the user/pass does not seem to allow any of my machines to access the samba share. 

For now I can only say that my **users/accounts cannot access the samba share MyTest **without using the samba user/password that I created when using the smbpasswd command.

Pardon me, but I've rearranged your comments for clarity.  So can you or can't you access the Samba share?  The machine (computer) does not access the share.  A mortal user with a user name and password accesses the share.  The mortal user should have both a Linux user name and password as well as a Samba user name and password on the host the is the Samba server.  
> 
I don't understand what you mean by "John has an account" and that this would also be the samba user and pass ?

How does this John get a user/password on samba share unless I actually create a samba password. This is where I'm confused and don't understand the difference between an account on the local machine and the samba shares.

In a Samba Client/Server environment each mortal user has an OS user name/password on the local host (the Client) and also on the remote host that is functioning as the Samba server.  In addition, the Samba application (the server) requires each user to have a Samba user name and password.  If you do not have both types of user accounts the user will not be authenticated to the Samba share.  You, as the admin (via sudo) create each of these accounts.  Since these accounts, for a specific user, all refer to the same mortal user, it is less confusing if they are all the same user name and password.  EACH user needs to have a OS user name and password and a Samba user name and password to access a Samba or Windows share.
> 
I go to network browsers, then navigate to MyTest, screen comes up asking for credentials. I put in my user/pass of this local machine(NOT networked) Just local login using the same credentials that I use to login to my ubuntu account. This fails. Screen gets dim and makes me cancel for anything that does not (succeed)

If I use my (ubuntu user) and password I created for samba for this user. Then it can read/write for everything in MyTest. I can also navigate to MyTest with any computer on the local network and login with (any ubuntu user) And a samba password that I created.

However, NO local network computer can access MyTest with their own user/passwords. They can only access with a samba passward that I created with this command:
```

sudo smbpasswd -a <user>
```

So as I understand it from what your telling me is that I should be able to access MyTest with a simple user/password without specifically adding any samba user or samba passwords etc. ? 

No that is NOT what I am saying.  You need to create a Samba user for each Linux user using ***sudo smbpasswd -a <user>***.  This way all users of the Samba server have their own separate Samba user accounts as well as a separate Linux user account.  Using the John as an example we would have these items```

John = mortal user who needs accounts
john = Linux user  (created via adduser)
john = Samba user (created via smbpasswd -a)
password = the same on both accounts
```

---

### Post by AgentZ86 on 2015-10-02
Please look at post #44
I did not see any instructions to add any Samba users/passwords.

I'm confused about how to apply the terms you outlined for a local host on the host, while using samba client to access samba server all on the same single machine.

Let's just narrow this down to one machine without any networking.
For now I can access the MyTest folder with my samba password that I created.
This **samba client password** for the local host user is different then the **local host login password**.

Would a user who has the same login password and samba password get the poppup to access samba share ? 
I don't know anything about how it treats things so I can't say what I don't know about.

---

### Post by bab1 on 2015-10-02
> **AgentZ86 said:**
> Please look at post #44
I did not see any instructions to add any Samba users/passwords.

Because you kept going off and doing your own thing.  In post #73 you show that you have created 2 Samba users.  I assumed you know what you were doing.  Silly me.
> 
I'm confused about how to apply the terms you outlined for a local host on the host, while using samba client to access samba server all on the same single machine.

You can have a client and a server on the same host.  When you do that the user is acting like a remote user even thought there is no physical difference (both are on the same machine in this instance).  The best way to explain that is this way:  The local user uses no networking to access the files.  That user uses the OS's internal methods to access the files.  That user would use the file manager to browse the file system tree to access the files at */main_serv/data/test1*.

On the other hand the Samba client sends a request to the Samba server via the SMB networking protocol to see the files at //Server-Name/Share.  These are to radically different methods to get to the same data.
> 
Let's just narrow this down to one machine without any networking.
For now I can access the MyTest folder with my samba password that I created.
This **samba client password** for the local host user is different then the **local host login password**.
This does involve networking or you would not be using Samba at all.  The reason the local password is not the same as your Samba password is because you set it that way.  So I would change the Samba password.  As the user ***agent86*** used the command *smbpasswd* and follow the prompts to reset your Samba password to be the same as the local user named ***agent86***.

Would a user who has the same login password and samba password get the poppup to access samba share ? 

Yes.
> 
I don't know anything about how it treats things so I can't say what I don't know about.
Then follow my instructions.

At this point you should be able to access the Samba share as user ***agent86***.  If not We may have to delete the Samba user and recreate it.  It also helps if we have a few exchanges a day.  That way we have some continuity to the questions and answers.

---

### Post by AgentZ86 on 2015-10-03
Yes, at this point I can access the MyTest folder with my user, and Samba password

---

### Post by bab1 on 2015-10-03
> **AgentZ86 said:**
> Yes, at this point I can access the MyTest folder with my user, and Samba password
You should be able to access that share from another host then; using your user/pass.  Is the Samba password the same as your Linux password?

---

### Post by AgentZ86 on 2015-10-04
> **bab1 said:**
> You should be able to access that share from another host then; using your user/pass.  Is the Samba password the same as your Linux password?

Well the password was not the same. However, I have changed them now so that each host user has a samba password that matches their user login password.

Now remote hosts can also access MyTest folder

---

### Post by bab1 on 2015-10-04
> **AgentZ86 said:**
> Well the password was not the same. However, I have changed them now so that each host user has a samba password that matches their user login password.

Now remote hosts can also access MyTest folder
**_Users_** at remote hosts can access the share.  Try adding a second Linux/Samba user now.

---

### Post by AgentZ86 on 2015-10-07
> **bab1 said:**
> **_Users_** at remote hosts can access the share.  Try adding a second Linux/Samba user now.

You want to add the linux/samba user to the same machine that is the samba server right ? Not just a samba user/client to another machine ?

---

### Post by bab1 on 2015-10-09
> **AgentZ86 said:**
> You want to add the linux/samba user to the same machine that is the samba server right ? Not just a samba user/client to another machine ?
If a person is to have access to a Samba share they must have a user account at the Samba server.  That means the user must also have a Linux account on that host also.  If the user does not have an account on the client machine then obviously there needs to be a user account there also.  To simplify this the accounts should all have the same user name and password.

---

### Post by AgentZ86 on 2015-10-13
Ok

I want to say everything is working but as soon as I start using the folder for various things; and counting on it to be there, then it's gone.

I just don't see the folder on the network consistently. 

Most of the time it's there but sometimes it's not and neither is the host computer that you would normally see in network browser and/or windows network folder.

I am confused why it would appear and disappear like this.
Now it seems to be gone and has not appeared for quit a few days now. I checked the folder to see it's existence and further checked the permissions and the smb.conf file again with the information you have posted over the course of this post.

I don't see anything that has changed. It all seems just as it did when it first started working and was working for the past week or more. I did not make any change and only rebooted a few times to see if that could cause the folder to show itself once again.

---

### Post by bab1 on 2015-10-14
> **AgentZ86 said:**
> Ok

I want to say everything is working but as soon as I start using the folder for various things; and counting on it to be there, then it's gone.

I just don't see the folder on the network consistently. 

Most of the time it's there but sometimes it's not and neither is the host computer that you would normally see in network browser and/or windows network folder.

I am confused why it would appear and disappear like this.
Now it seems to be gone and has not appeared for quit a few days now. I checked the folder to see it's existence and further checked the permissions and the smb.conf file again with the information you have posted over the course of this post.

I don't see anything that has changed. It all seems just as it did when it first started working and was working for the past week or more. I did not make any change and only rebooted a few times to see if that could cause the folder to show itself once again.

There are several situations that can cause the browse function to behave as you have described.  It all has to do with how the Master Browse List (MBL) is constructed.   When you have all machines off the MBL is lost.  Booting up all the machines starts a process to determine what machine will hold the MBL and then the creation of a new MBL on the machine that is elected to be the holder of the MBL.  This can take up to 15 minutes.

If you have to shut off the machine that holds the MBL the other machines that have Windows shares (SMB) will elect a new Master Browse machine.  This can interrupt your browsing for shares also.  Neither of these issues will remove the actual share.  You should always be able to access the share by either: //IP_addtess/share-name or //Sever-Name/share-name.  In the file manager you should be able to user "Cntl+l  (control+ell) to open a location bar to enter the complete URL (i.e. smb://Server-Name/share-name) or just the server (smb://Server-Name).  You can substitute the IP address for Server-name also.  Frome the command line you can also see the share this way```
smbclient -L <server>
```...where <server> is either the SERVER-NAME or the IP Address of that machine.  See if when the browsing stops if you can still see the share with the more direct method I have described.  

All of this is predicated on you using the default smb.conf file and just adding the share definition at the bottom of that file.  If it is different than that post the output of this ```
cat /etc/samba/smb.conf
```

---

### Post by Linuxisfast on 2015-10-15
Ubuntu has the easiest folder sharing around, right click and click share, samba gets installed, however it might not install libpam-smbpass so install that manually, relogin and voila, samba works and works good. Compare that to Arch and you will see how easy and functional it is and I do run Arch on my other machine as well.

---

### Post by AgentZ86 on 2015-10-20
> **Linuxisfast said:**
> Ubuntu has the easiest folder sharing around, right click and click share, samba gets installed, however it might not install libpam-smbpass so install that manually, relogin and voila, samba works and works good. Compare that to Arch and you will see how easy and functional it is and I do run Arch on my other machine as well.

According to bab1 and various other posts NO this does not work (unless you are logging in with the same user) otherwise samba does not allow permissions to read/write/execute.

Which means YES you can right click and share but if your user doesn't have a samba account on the samba server then NO you cannot simply share and ad files/folders and later edit them from another computer or another user.

Unfortunately this is the problem I'm having. I have more then 1 user on the network and as long as I have each computer with the same login credentials then I can do things like create libre office document, make changes edits etc. Then from another computer I can login with same credentials users/pass and do the same.

However, if I login as user1, and ad a libre office documents and save it. I can NOT login to another PC as user2 and edit the file. You will get permission denied messages. This appears to be the default setup of ubuntu which unfortunately means I can't login and simply share files with other users. 

This entire post was bab1 trying to explain and walk me through the actual fault proof setup for this. I was expecting it to be a right click and share but this does not appear to be the case. 

I never actually realized this until I started reinstalling stuff and creating new users on other computers on the network. Then I realized my backup programs were failing to backup over the network and then I also lost the ability to edit files and could only open them in read only mode from the other users computers on the network.

I wish is was that simple but unfortunately it's not. I have no idea why it's so complicated exactly, but it really stinks that I can't seem to get it working with such a simple home use setup.

Even after all the processing of setting up the share as listed in this post I still have yet to have a functional share that will share a folder with full access to all users on the network. Not just sharing pictures but documents and needs editing etc. 

Pics are typically simple because everyone is only using read only access in most cases, but documents appears to make the subject way more complicated.

Currently my shared folder appears, and disapears. Sometimes it's accessible and other times says permission denied read only access. 
Getting bored with this and gave it a pretty good try to make it work correctly. Read a lot of stuff and learned quite a bit about samba and file permissions along the way, but still no success with file sharing.

---

### Post by Morbius1 on 2015-10-20
>  Which means YES you can right click and share but if your user doesn't  have a samba account on the samba server then NO you cannot simply share  and ad files/folders and later edit them from another computer or  another user.
Please don't state that as an absolute fact since it's simply not true.

I have created many simple local networks with a shared public folder in one user's home directory, made it accessible to everyone on the local lan without having to pass credentials so there is no need for "samba accounts", forced the remote user to appear to be the user who owns the Public folder so that everything he adds is as that user and it works reasonably well.

Samba can be as simple or as complex as you want to make it or as your requirements demand.

You seem to have a host of other problems like actually being able to connect to the server depending on lunar cycles and such but that's another issue.

---

### Post by AgentZ86 on 2015-10-21
> **Morbius1 said:**
> Please don't state that as an absolute fact since it's simply not true.

I have created many simple local networks with a shared public folder in one user's home directory, made it accessible to everyone on the local lan without having to pass credentials so there is no need for "samba accounts", forced the remote user to appear to be the user who owns the Public folder so that everything he adds is as that user and it works reasonably well.

Samba can be as simple or as complex as you want to make it or as your requirements demand.

You seem to have a host of other problems like actually being able to connect to the server depending on lunar cycles and such but that's another issue.

Perhaps your right, I am stating something that I do not know for sure is a FACT for myself. I only stated what seems to be listed and posted as general knowledge across google and ubuntu.

In fact the public folder option was taken out of later Ubuntu version and needs to be either reinstalled or extra software installed. I have no problem doing this either. However, the fresh install of 15.04 on every machine does not have any option to allow guest. And additionally guest does not mean that you have full read/write/execute access. 

This seems to be something listed by the ubuntu team as well as others who have similar problems trying to share files.

So your telling me that you have a shared folder setup. That anyone on the network can access ? And access means to read/write/execute. Can you confirm this ? 
Do you create text documents on one machine inside this folder ? Then go to another machine on the network and edit them as a different user on that machine ?
I have in the past shared a folder and had full access as long as I log into the other machines on the network as the same user. I have been unsuccessful at simply right clicking anything to allow full access of any other users which would include editing documents on the share from a remote computer on the network. 

I have done fresh installs and right clicked said folder that I want to share and attempted to share as everyone / guest whatever. This does allow "access" but does not allow editing of files that were added by one user. This only provides read only access; and does not seem to allow for editing by another user on the network. 

This feature is simply not simple at all. It either does not work or as bab1 suggests that the ownership/group/user permissions must be setup first, then samba users must be added. This seems to be what others are also talking about too.

I would not state this as fact because I am not knowledgeable enough about file permissions and samba, but I also would not state it as fact that right clicking alone allows all users to share the folder will full access equally. That does not appear to be the case according to MANY Ubuntu documents and/or forum posts.

If it was so easy then my initial post title states exactly what this post is about and I am begging for simple instructions. 
bab1 explained this to me and it does not appear to be as simple as that from what I can tell.

If you have simple instructions that will do this please post them.

After this complicated setup, and no other changes to my setup, the shared folder is gone from the network browsing for good. 
Cannot even see from it's own self when network browsing.

Even right clicked to share other folders with 15.04 and did this on every computer on the network with 15.04 in the house and they got snake eyes.  

smb.conf and permissions still enact as they should be but got snake eyes all the way around now.
Folder still exists and permissions are still entact. smb.conf and users/passwords all appear to be as they should be.

Bored with this, 
Happy blogging.

---

### Post by Morbius1 on 2015-10-22
> **AgentZ86 said:**
> In fact the public folder option was taken out of later Ubuntu version and needs to be either reinstalled or extra software installed. I have no problem doing this either. However, the fresh install of 15.04 on every machine does not have any option to allow guest. And additionally guest does not mean that you have full read/write/execute access. 
You are confusing something called Personal File Sharing (gnome-user-share) with a samba usershare ( nautilus-share ). And yes you can allow guest access in a samba usershare. This is from a 15.04 system:
[ATTACH=CONFIG]265093[/ATTACH]
The user that creates this share has to be a member of the sambashare group of course.

And yes the guest user will have read / write access to the share and it's contents if you do it as I described in my first post.

Look, wild horses and a provocative suggestion by Scarlett Johansson couldn&#8217;t make me get further involved in this thread. My original post was admittedly a knee-jerk reaction to something that was blatantly false. 

Um .... I might reconsider with Scarlett.

[COLOR=#0000cd]**EDIT**[/COLOR]: After thinking about it for 5 nanoseconds I'm certain I would reconsider my involvement for Scarlett.

---

### Post by AgentZ86 on 2015-10-22
> **Morbius1 said:**
> You are confusing something called Personal File Sharing (gnome-user-share) with a samba usershare ( nautilus-share ). And yes you can allow guest access in a samba usershare. This is from a 15.04 system:
[ATTACH=CONFIG]265093[/ATTACH]
The user that creates this share has to be a member of the sambashare group of course.

And yes the guest user will have read / write access to the share and it's contents if you do it as I described in my first post.

Look, wild horses and a provocative suggestion by Scarlett Johansson couldn’t make me get further involved in this thread. My original post was admittedly a knee-jerk reaction to something that was blatantly false. 

Um .... I might reconsider with Scarlett.

[COLOR=#0000cd]**EDIT**[/COLOR]: After thinking about it for 5 nanoseconds I'm certain I would reconsider my involvement for Scarlett.

It appears you should have spend more then 5 nanoseconds thinking about it.
As if I didn't already try to right click a folder, as shown in your picture.

As I mentioned, I could not simply share by right clicking as I expected to
Since others in this post have communicated various instructions about why I might have trouble with this; and further instructed me to setup file permissions and sharing via samba. I tried that route.
Google searches and scouring the ubuntu forums for others with similar problems seemed to share the instructions of setting up permissions and samba for sharing files.

However, as I mentioned that this complicated attempt has also failed. I would have preferred a right click and share. I really don't know why the shares are giving file permissions for either guest or user/password. All are permissions failures. 

As it stands:
These complicated attempts have various intermittent problems ranging from disappearing shared folder to permission failures. 
The right click and share method has permission failures. Users on the network can read only but not write to shares; and that is with or without user/passwords or as anonymous user logins.

Any other ideas ?

---

