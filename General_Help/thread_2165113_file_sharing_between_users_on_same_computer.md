---
title: "file sharing between users on same computer"
date: 2013-08-03
forum: General Help
---

### Post by Buntu Bunny on 2013-08-03
Is there a way to share files with another user on the same computer? I've found lots of information on file sharing between different computers, but cannot find how to share files on the same computer between different user accounts.

---

### Post by Mike_Pearson on 2013-08-03
Me too 
I have the exact same question/problem
Help from  someone out there would be mos appreciated

---

### Post by ibjsb4 on 2013-08-03
I just use a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9") and [symlink]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=symlink&sa=Search&cof=FORID:9") everyone.

---

### Post by Buntu Bunny on 2013-08-03
> **ibjsb4 said:**
> I just use a [data partition]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9") and [symlink]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=symlink&sa=Search&cof=FORID:9") everyone.

Ok, that's an idea. Currently we are emailing files to one another. It's okay but somewhat slow. (Your links, however, come up blank  :confused:).

---

### Post by SuperFreak on 2013-08-03
> **Buntu Bunny said:**
> Ok, that's an idea. Currently we are emailing files to one another. It's okay but somewhat slow. (Your links, however, come up blank  :confused:).

Is Ghostery or other anti tracking software blocking site. I whitelisted Ghostery for  Googlubuntu and links worked

---

### Post by The Cog on 2013-08-03
I think it's quite common to use the /tmp folder as a place to drop shared files.

---

### Post by Buntu Bunny on 2013-08-03
> **SuperFreak said:**
> Is Ghostery or other anti tracking software blocking site. I whitelisted Ghostery for  Googlubuntu and links worked

Gosh, I have a whole suite of security addons. I switched browsers and gave googlubuntu permission and the pages did come up, so thanks for that. It's odd though, because that's never happened before. 

> **The Cog said:**
> I think it's quite common to use the /tmp folder as a place to drop shared files.

File System > Tmp ? Is that the one you're talking about? Properties tells me the owner is root and won't allow changes in access.

---

### Post by Petro Dawg on 2013-08-03
An easy solution is installing Ubuntu1 or Dropbox on each login.  You'll be able to share files between different logins on the same computer or sync files on other computers or even phones.  

The upside is that it is a very versatile solution, the downside is that you have to wait for files to be uploaded/downloaded  (no instant gratification).

---

### Post by Buntu Bunny on 2013-08-03
> **Petro Dawg said:**
> An easy solution is installing Ubuntu1 or Dropbox on each login.  You'll be able to share files between different logins on the same computer or sync files on other computers or even phones.  

The upside is that it is a very versatile solution, the downside is that you have to wait for files to be uploaded/downloaded  (no instant gratification).

Thanks Petro Dawg. I didn't realize Dropbox was a paid service, so that's out. Ubuntu1 is an option, but likely the same as simply emailing the files and (mostly) photos, especially in terms of up and downloading times. 

I'm kind of hoping for an offline solution which, at this point, would seem to be a data partition, assuming it would be easy to access.

---

### Post by SuperFreak on 2013-08-03
DropBox and Ubuntu1 both have free versions with minimal storage options ([DropBox]("https://www.dropbox.com/pricing"))

Perhaps this is my own ignorance but wouldn't be simplest to do as ibjsb4 suggested and create a data partition that can be shared across accounts. personally I am not sure I trust cloud services; it is only a matter of time before these services have security breaches

---

### Post by Dennis N on 2013-08-03
For different users A and B of the same OS installation on same computer:
Change permission on B's Public folder to 757.
User A can then read and write to B's Public folder.

You can extend this to work both ways.

BTW, User A can READ (only) files in B's home folder in a default setup.

---

### Post by The Cog on 2013-08-03
> **Buntu Bunny said:**
> File System > Tmp ? Is that the one you're talking about? Properties tells me the owner is root and won't allow changes in access.

That's the one - /tmp. Here are the permissions:
```
$ ls -ld /tmp
drwxrwxrwt 8 root root 4096 Aug  3 16:17 /tmp
```
So anyone can use the folder to drop files /folders into, and see what's in there. The "t" (sticky) flag means that although anyone can write to the /tmp folder (change its contents),  files in there can only be deleted by their owners.

Try it and see.

---

### Post by Buntu Bunny on 2013-08-03
> **SuperFreak said:**
> Perhaps this is my own ignorance but wouldn't be simplest to do as ibjsb4 suggested and create a data partition that can be shared across accounts. personally I am not sure I trust cloud services; it is only a matter of time before these services have security breaches

What happened to Ubuntu Forums is a good lesson regarding security breaches, and I have to agree with you in regards to trusting any online service. 

For my situation, there is an issue with spotty internet connection when the weather is bad, so being able to share without having to go online is a plus. Because of that, I have to agree that a data partition may be the best route to take.

---

### Post by Buntu Bunny on 2013-08-03
> **The Cog said:**
> That's the one - /tmp. Here are the permissions:
```
$ ls -ld /tmp
drwxrwxrwt 8 root root 4096 Aug  3 16:17 /tmp
```
So anyone can use the folder to drop files /folders into, and see what's in there. The "t" (sticky) flag means that although anyone can write to the /tmp folder (change its contents),  files in there can only be deleted by their owners.

Try it and see.

Thanks! I appreciate the specific details. I will definitely give this a try. Can I directly copy and paste? Or do I need to change anything such as the time stamp?

---

### Post by Buntu Bunny on 2013-08-03
> **Dennis N said:**
> For different users A and B of the same OS installation on same computer:
Change permission on B's Public folder to 757.
User A can then read and write to B's Public folder.

You can extend this to work both ways.

BTW, User A can READ (only) files in B's home folder in a default setup.

Dennis N, I'm sorry I missed your post. I've been relying on email notification which seems to skip a few. 

Which do you mean by public folder? Not the home directory, right? I looked through the file system but didn't find anything labelled public.

---

### Post by Dennis N on 2013-08-03
> **Buntu Bunny said:**
> Dennis N, I'm sorry I missed your post. I've been relying on email notification which seems to skip a few. 

Which do you mean by public folder? Not the home directory, right? I looked through the file system but didn't find anything labelled public.

I use Xubuntu and it comes with a Public folder by default. Yes, it is in the user's home directory.  You can create it, or use (or create) any other sub folder of your home folder for this sharing purpose.

We use this method and it is very simple, but works as intended.

---

### Post by ajgreeny on 2013-08-03
Using /tmp is an answer that I did not even know was possible, nor did I realise what the Public folder in the home of my Xubuntu 12.04 was, and that may be worth trying, but that aside, I believe that a separate /data partition as lbsjb4 suggests would be the most sensible answer.  I can certainly see no logical reason for using dropbox, ubuntu-one or any other cloud storage option for what you want to do; why mess around with remote storage and the network when you are both on the same machine?

1. Boot to a live DVD/USB, run gparted and make a new partiton.  It would be useful to see what partitions you have already from a screenshot of the gparted window
2. Make a mount point with rw permission for everyone (if you use ext2/3/4 at least)
3. Add the partition to fstab
4. sudo mount -a                         

That is a very simplified list of actions to take, but it will work as long as the permissions are set properly on the mountpoint of the new partition.

---

### Post by Buntu Bunny on 2013-08-03
> **Dennis N said:**
> I use Xubuntu and it comes with a Public folder by default. Yes, it is in the user's home directory.  You can create it, or use (or create) any other sub folder of your home folder for this sharing purpose.

We use this method and it is very simple, but works as intended.

Well, duh. I use Xubuntu too and there Public was, in my home directory. 

Would the command to change permissions be

```
chmod 757 Public
```

? I'm sure it's not *that* simple. 

My husband uses Gnome Classic so I'd have to set up a Public folder for him as well, correct?

---

### Post by Buntu Bunny on 2013-08-03
> **ajgreeny said:**
> Using /tmp is an answer that I did not even know was possible, nor did I realise what the Public folder in the home of my Xubuntu 12.04 was, and that may be worth trying, but that aside, I believe that a separate /data partition as lbsjb4 suggests would be the most sensible answer.  I can certainly see no logical reason for using dropbox, ubuntu-one or any other cloud storage option for what you want to do; why mess around with remote storage and the network when you are both on the same machine?

1. Boot to a live DVD/USB, run gparted and make a new partiton.  It would be useful to see what partitions you have already from a screenshot of the gparted window
2. Make a mount point with rw permission for everyone (if you use ext2/3/4 at least)
3. Add the partition to fstab
4. sudo mount -a                         

That is a very simplified list of actions to take, but it will work as long as the permissions are set properly on the mountpoint of the new partition.

ajgreeny, if I can't get the public directory to work for both users, then I will definitely try as you suggest. I have a dual boot with Win7, so that complicates things a bit(?) Still, I've been thinking about a data partition for quite awhile. Let me try to work through the first idea and get back to you on your idea after that.

---

### Post by Dennis N on 2013-08-03
> **Buntu Bunny said:**
> Well, duh. I use Xubuntu too and there Public was, in my home directory. 

Would the command to change permissions be

```
chmod 757 Public
```

? I'm sure it's not *that* simple. 

My husband uses Gnome Classic so I'd have to set up a Public folder for him as well, correct?

Yes, it is that simple. Each user would have to change the permissions on the folder they intend to use for sharing. You can name the folder whatever you like.

You then just navigate with the file manager to the other user's shared folder and you have access for read and write.

---

### Post by Buntu Bunny on 2013-08-03
> **Dennis N said:**
> Yes, it is that simple. Each user would have to change the permissions on the folder they intend to use for sharing. You can name the folder whatever you like.

You then just navigate with the file manager to the other user's shared folder and you have access for read and write.

I did that for both users but the file in Public is only there on my side. Gnome Classic had a Public folder, but it was empty. Its properties window has a share tab, but it wants to install Samba to enable sharing.

---

### Post by Dennis N on 2013-08-03
> **Buntu Bunny said:**
> I did that for both users but the file in Public is only there on my side. Gnome Classic had a Public folder, but it was empty. Its properties window has a share tab, but it wants to install Samba to enable sharing.

That's for sharing with Samba. You don't want that. 

On the Classic, just have the owner (your husband?) change the permissions of the folder he intends to share to 757 using the terminal. Assuming it's called Public,

**chmod 757 Public** 

Then test by navigating there from the other user acct. and see that you can drag and drop back and forth, or save stuff directly there, and vice-versa.

---

### Post by Buntu Bunny on 2013-08-03
> **Dennis N said:**
> That's for sharing with Samba. You don't want that. 

On the Classic, just have the owner (your husband?) change the permissions of the folder he intends to share to 757 using the terminal. Assuming it's called Public,

**chmod 757 Public** 

Then test by navigating there from the other user acct. and see that you can drag and drop back and forth, or save stuff directly there, and vice-versa.

I did all that but cannot see files added from the other user account. :(

---

### Post by d2btoo on 2013-08-03
@Buntu Bunny: (just a thought)
If you just want to share some files with other user, why not just dump them in your Win partition (you are dual booting with Win right?), then everyone can access it, regardless whatever OS they are using at that moment.  Even better use dedicated FAT32 or NTFS partition for data sharing!

---

### Post by Buntu Bunny on 2013-08-03
> **d2btoo said:**
> @Buntu Bunny: (just a thought)
If you just want to share some files with other user, why not just dump them in your Win partition (you are dual booting with Win right?), then everyone can access it, regardless whatever OS they are using at that moment.  Even better use dedicated FAT32 or NTFS partition for data sharing!

Yes, that is a thought, except neither of us uses Windows! I just keep it in case I have to deal with my service provider's tech support, which is anti-Linux!

The two users I'm trying to share files between both use Ubuntu. We have different user accounts and our own desktops.

---

### Post by d2btoo on 2013-08-03
> **Buntu Bunny said:**
> Yes, that is a thought, except neither of us uses Windows! I just keep it in case I have to deal with my service provider's tech support, which is anti-Linux!
You don't have to use windows to set up data partition. :)
> **Buntu Bunny said:**
> The two users I'm trying to share files between both use Ubuntu. We have different user accounts and our own desktops.
Yes different user accounts. Also different machines? -- then of course this won't work! Your first post said "same computer" so I posted!
> **Buntu Bunny said:**
> Is there a way to share files with another user on the same computer? I've found lots of information on file sharing between different computers, but cannot find how to share files on the **same computer between different user accounts.**

---

### Post by Dennis N on 2013-08-03
> **Buntu Bunny said:**
> I did all that but cannot see files added from the other user account. :(

Just to be clear, you are both using the same installation of Xubuntu, but your husband is using Xubuntu + the Gnome Classic Desktop??

(As to this computer, both user accounts in question here are on the same installation of pure Xubuntu 12.04, not a desktop installed alongside Unity or Gnome. Also, I see no "Share" tab in any folder properties dialog, so maybe that comes from using Gnome Classic desktop.)

You are able to browse to the other user's Public folder, which you know contains files, but you cannot see any of them listed in your file manager window. Can you give the permissions of one of those invisible files? 

From terminal, ls -l giving something like:

-rw-rw-r--  1 dn dn   21 Mar 24 16:02 somefilename

What about other folders within his home folder? These and files within should be visible and browsable.

---

### Post by Buntu Bunny on 2013-08-03
> **Dennis N said:**
> Just to be clear, you are both using the same installation of Xubuntu, but your husband is using Xubuntu + the Gnome Classic Desktop??

(As to this computer, both user accounts in question here are on the same installation of pure Xubuntu 12.04, not a desktop installed alongside Unity or Gnome. Also, I see no "Share" tab in any folder properties dialog, so maybe that comes from using Gnome Classic desktop.)

Perhaps I haven't given enough information. Forgive me, we are heading into unfamiliar Linux territory for me. :???:

Original installation was Ubuntu 12.04 with two user accounts, one for me, one for my husband.
Husband didn't like Unity so he switched to Gnome Classic
I didn't like Unity, so installed the Xfce desktop, which gives me the choice of an Xfce session or Xubuntu session (usually use Xfce session)

> **Dennis N said:**
> You are able to browse to the other user's Public folder......What about other folders within his home folder? These and files within should be visible and browsable.

Okay, this is where I was having trouble. I had to figure out how to *browse to* his Public folder; I was just looking in my own Public folder (silly, I know, but I'd never tried this before LOL). 

Yes, I can browse everything there and vice versa. Whew. Thank you for hanging in there with me!

> **d2btoo said:**
> You don't have to use windows to set up data partition. :)
Yes different user accounts. Also different machines? -- then of course this won't work! Your first post said "same computer" so I posted!

Okay, I wasn't understanding what you were saying. Yes, we have different user accounts on the same machine. I definitely want to try setting up a data partition, but it will have to be later. I'll be back and asking for help then!

---

### Post by Dennis N on 2013-08-03
> **Buntu Bunny said:**
> 
Okay, this is where I was having trouble. I had to figure out how to *browse to* his Public folder; I was just looking in my own Public folder (silly, I know, but I'd never tried this before LOL).

Yes, that could be confusing, but you apparently through some exploration and dilligence sorted it out!  

> **Buntu Bunny said:**
> 
Yes, I can browse everything there and vice versa. Whew. Thank you for hanging in there with me!


No problem. You should find this meets your needs to move files back and forth.

---

### Post by bab1 on 2013-08-03
> **Buntu Bunny said:**
> **Is there a way to share files with another user on the same computer? **I've found lots of information on file sharing between different computers, but cannot find how to share files on the same computer between different user accounts.

All you really need to do is create a directory (folder) that has common access to all users (/tmp is one of these).  You could make a directory such as /data like this from the CLI```
sudo mkdir /data
```

Then you can change the permissions so all users have access for read and write like this```
sudo chmod 777 /data
```

All users will have equal access to that directory/  This means that a user can delete or modify any file of folder inside the directory /data.  You can have more restrictive permissions and ownership if you like.  Is this basically what you wanted?

---

### Post by Buntu Bunny on 2013-08-03
> **bab1 said:**
> ..... Is this basically what you wanted?

Exactly! bab1, thank you. I think I've managed it with both users' Public file. I also learned about [a lesson on permissions over at LinuxCommand.org]("http://linuxcommand.org/lts0070.php"), which explains what the numbers are. Very helpful.

---

### Post by amra.sonntag2 on 2013-08-04
Your problem is probably solved. But with the permissions given now everyone using the computer will be able to read those folders/files. If you and your husband aren't the only users, you might want to restrict access for everyone else.

One way to go about that is to create a group with your and your husbands account as members and give read/write permissions to everyone in this group only. You can create a group in Xubuntu via Properties -> Users and Groups -> Create Groups. And if you don't like using the console you can also change folder/file permissions by right-clicking and choosing Properties -> Permissions in your file manager.

Just a thought.

---

### Post by Buntu Bunny on 2013-08-04
@amra.sonntag2, you bring up a good point. I wasn't the only one interested in this topic, so your information adds to the conversation; especially for those with others using the same computer.

---

### Post by The Cog on 2013-08-04
In my opinion, that Public folder is misplaced. It is only visible to other users if they are already able to see all your files/folders anyway. 
If the user's home directory is private (as mine is) then other users are unable to see into it to access the Public folder.
```
steve@StevePC:~$ ls -ld /home/steve/
drwx------ 82 steve steve 40960 Aug  4 12:02 /home/steve/
```
I think the Public folder was intended for use in network file sharing, not local filesystem sharing to other users.

---

### Post by Buntu Bunny on 2013-08-04
> **The Cog said:**
> In my opinion, that Public folder is misplaced. It is only visible to other users if they are already able to see all your files/folders anyway. 
If the user's home directory is private (as mine is) then other users are unable to see into it to access the Public folder.
```
steve@StevePC:~$ ls -ld /home/steve/
drwx------ 82 steve steve 40960 Aug  4 12:02 /home/steve/
```
I think the Public folder was intended for use in network file sharing, not local filesystem sharing to other users.

The Cog, I have to agree, especially since my original intention was only one folder intended for sharing files. Sometimes names are misleading! In my personal situation, the privacy isn't as important, but would be if we had a guest who wished to used the computer.  

The solution would seem to be, to set up one folder on the desktop for the files one wishes to share specifically, and give group permissions for that file alone, correct? I'll have to experiment with this.

---

### Post by The Cog on 2013-08-04
It depends what you are trying to achieve. If you are just relying on good manners to keep others from looking at all your files, and they already have access to your home folder, then that's fine - just put the files in your Public folder and tell then that's where they are. Giving group permissions to that file alone is pointless because they can't see your Public folder unless they can already see what's in your home folder. And if they can already see all of your home folder, you are just relying on good manners. It's like telling a delivery boy "The money's on the kitchen table. Please don't touch anything else. I'll leave the front door open so you can get in." If the front door is locked, there is no point leaving the money on the kitchen table for him.

Dropping files in /tmp means you don't have to worry about what they can and can't see in your home folder - that remains as is. You can make personal folders in /tmp if it helps organise things. 

It occurs to me that it is common practice to place /home on a different partition to the rest of the system. So you could perhaps create a /home/shared folder that everyone can read/write, which would then be stored on the same large partition as all your home folders.

---

### Post by Morbius1 on 2013-08-04
You need to define what you mean by shared.

Let's say you created a shared directory at /home/Shared:

** If you  set it to 777 then everyone can add to or delete anything in that folder. What they can't do is edit a specific file owned by someone else.
** Even if you change ownership to say root:newgroup but set permissions to 770 then everyone who is a member of newgroup group can add to or delete but still cannot edit a specific file owned by someone else.
** If you want to give edit rights to individual files you need to do something else. For example:

Change ownership to root:newgroup:
```
sudo chown root:newgroup /home/Shared
```
Then change permissions to include the setgid bit:
```
sudo chmod 2770 /home/Shared
```
If you want edit rights but want to restrict the deletion of files only to the original owner change it to 3770: 
```
sudo chmod 3770 /home/Shared
```
The "2" is the setgid bit and the "3" is a combination of the setgid bit (2) and the sticky bit (1).

The setgid bit forces every new file added or copied to [COLOR=#0000cd]but not moved to[/COLOR] that directory to inherit the group of the folder. So if "husband" adds a file it will save as:
husband:newgroup and permissions of 664. Everyone who is a member of the newgroup group can edit the file.

Having the ability to inherit group ownership to files [COLOR=#0000cd]moved[/COLOR] into that directory requires something like bindfs.

---

### Post by Buntu Bunny on 2013-08-04
> **The Cog said:**
> It depends what you are trying to achieve. If you are just relying on good manners to keep others from looking at all your files, and they already have access to your home folder, then that's fine ...<*snip*>....Dropping files in /tmp means you don't have to worry about what they can and can't see in your home folder - that remains as is. You can make personal folders in /tmp if it helps organise things.....

Good points. For my situation, there isn't anything that can't be shared between just the two of us. My husband, however, has little interest in (and little patience with) computers, except for a few things. I need to keep this simple without a lot of browsing involved. (Plus I noticed that my tmp folder is full of stuff). That was why I'm thinking a desktop shared_files folder for each of us would be the best solution.

> **Morbius1 said:**
> You need to define what you mean by shared....

Morbius1, you're taking this to a whole new level for me, LOL; I'm just getting familiar with permissions, but it's needful. 

So, based on what I described to The Cog, I could create a desktop folder, shared_files, for each of us on our separate user desktops.

For my home folder [I](BTW, is there a difference between /home and /home/me ?  /home belongs to root and /home/me belongs to me? Is that correct?)
[/I]

I could set permissions for my home folder to

```
chmod 700 home/me
```

which would mean I alone could read, write, and execute files in my home directory. Is that correct?

The shared_files folder could have permissions (and here's where I have questions)

```
chmod 2777 me/desktop/shared_files
```

so that files are copied to the shared_files folder, and either of us can read, write, or delete. I would need to do the same for his shared_desktop folder.

My questions are:
[LIST]
[*]do I have the path correct, i.e. me/desktop/shared_files
[*]does it make any difference if the permission is 777 or 770
[/LIST]

The files we're sharing are mostly photos and pdfs

---

### Post by Morbius1 on 2013-08-04
Nope, that won't work.

If you set permissions of /home/me to 700 it doesn't matter what permissions are set at /home/me/*whatever* - the only person getting access to anything in /home/me is me. All file access is done through the entire path to the target. Throw a roadblock anywhere along the path and you've stopped access.

I would use Cog's suggestion of creating a completely separate directory outside of the users home directory - /home/shared_files.
Change permissions of that folder to whatever you want to accomplish.
And then each user can open Nautilus, go to /home/shared_files, and then bookmark it: Bookmarks > Add bookmark.

Then it will show up on the left side panel of Nautilus for easy access.

---

### Post by Buntu Bunny on 2013-08-04
> **Morbius1 said:**
> Nope, that won't work.

If you set permissions of /home/me to 700 it doesn't matter what permissions are set at /home/me/*whatever* - the only person getting access to anything in /home/me is me. All file access is done through the entire path to the target. Throw a roadblock anywhere along the path and you've stopped access.

Gotcha. 

> **Morbius1 said:**
> I would use Cog's suggestion of creating a completely separate directory outside of the users home directory - /home/shared_files. Change permissions of that folder to whatever you want to accomplish.

That worked. I didn't even have to create the shared_files folder in Husband's /home, it was already there when I went to check. Plus, since he uses Gnome Classic, the bookmark showed up in Places, making it easy to access. 

One last question (aren't you glad?), in general, what permission should be set for /home/me?

---

### Post by Morbius1 on 2013-08-04
I didn't quite understand you last post as it seems shared_files is in someone's home folder instead of by itself. If that's the case then don't do anything with /home/me.

---

### Post by Buntu Bunny on 2013-08-04
@Mobius1, sorry, the question about permissions for /home/me is a somewhat generalized one, because I am trying to understand the concept in a broader sense. Plus I know others have been trying to accomplish the same thing, but maybe with different circumstances. Perhaps the question is too broad for this thread.

---

### Post by Morbius1 on 2013-08-04
If you have multiple users on the same system then 700 on your own home directory insures that everything that is yours remains private to you.

But, if you are sharing subfolders of your home directory with other users - local or network - you have no choice but to leave it at the default.

---

### Post by Buntu Bunny on 2013-08-04
@Mobius1, I appreciate that. And thank you for your help. This was new ground for me so I'm grateful for all the thorough answers and help I received. I've learned quite a bit.

---

