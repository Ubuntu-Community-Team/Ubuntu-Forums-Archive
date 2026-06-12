---
title: "File Permissions"
date: 2007-10-10
forum: General Help
---

### Post by frostie on 2007-10-10
We have four users including a shared account where I store all our music and photos for everyone.
We also have in the shared account a shopping list which is just a text document. and is linked to from each users desktop so they can add to it throughout the week. Each user is a member of the 'shared' group and the permissions on the file are set at 775. The file is owned by 'shared' and in group 'shared'.
However...if for instance I add something to the list and save it, the ownership of the file is immediately changed to me and consequently no-one else can them edit it until I sudo in and change the ownership back to shared. This happens with everyone. Whoever edits the file takes over ownership and therefore blocks anyone else from adding to it.

Is there a way to set it up so any user can edit the file without blocking everyone else?

---

### Post by vanadium on 2007-10-10
I can't reproduce this behaviour. I did a test where I chowned a file to root:mygroup and changed permissions to 770. As a member of mygroup, I could open, edit and save the file although I am not the owner, but after the edit, the permissions were not changed.

---

### Post by mojoman on 2007-10-11
I'd suggest the following solution. Create a group where the necessary users are members (maybe you already have that). Make that group owner of the shared directory, using the command chown recursively. Also set the sgid to that group to make sure that all files and folders that are created or edited belongs to the group in question. Finally, you might need to add a change in each users .bashrc that makes all files created by the users in question readable to the group by setting to, for example, umask 003.

This setup will give you a shared directory that all members of that group can freely read and write within and all newly created files and directories will also be readable and writable for these members.

If this fits your bill and you need some more specific instructions on how to go about to do it, let me know and I'll help you out.

/mojoman

---

### Post by vanadium on 2007-10-11
This trickery should not be necessary. It should work like frostie wants to achieve right out of the box. frostie, you should probably give more details on how you proceed, because I really cannot reproduce this issue. A file normally does not change owner after editing by anyone permitted to. 

The only possibility I can think of is that your application you use to edit the file in fact opens the file, then first saves a modified copy of the file and then deletes the original (that would be an ms windows way of doing things). In other words, your application seems to create a new file rather than saving over the old one. I think of this possibility because I tried the experiment again with gedit this time instead of nano. gedit does save a backup copy. In the case of gedit, the backup is a newly created file, where I am the owner. Thus, tell is what application you use to edit the file.

In fact, you should not need something like a "shared account". You just need the regular user accounts, and be sure that the users belong to one common group, which can be called "shared" that is permitted to edit the file.

The "common" file can be owned by root, but should belong to the group "shared". It should not have permission 755, but 660, which means -rw-rw--- Indeed, there is no need to have the executable bit set. It should only be readable and writable by the owner and the group, nothing else.

---

### Post by frostie on 2007-10-11
Thanks to you all for looking in on this.

The shared account exists mainly to hold all our music and photos in one convenient place. they are all in folders on the desktop (Music, Photos etc) as well as one called 'Files' that has a text document 'Shopping'.
All users are members of the shared group.
First:
$ cd /home/shared/Desktop
$ sudo chown -R shared *
$ sudo chgrp -R shared *
$ cd Files
$ sudo chmod 775 Shopping
Then on my desktop click on the 'Shopping' icon. The file opens (yes, in gedit).
Add an item, (Beer!)
Save.
This gives:
$ cd /home/shared/Desktop/Files;ls -l
-rw------- 1 rfb    rfb    176 2007-10-11 20:08 Shopping
-rwxrwxr-x 1 shared shared 156 2007-10-10 20:00 Shopping~

and the shopping list is now owned by me and therefore no longer accessible to others to edit, so it seems vanadium may be on to something with the application theory.

---

### Post by frostie on 2007-10-11
However:
$ emacs22 /home/shared/Desktop/Files/Shopping

and editing still leaves me with:

-rwxrwxr-x 1 rfb rfb 172 2007-10-11 20:23 Shopping

when I'm done (but no backup file).

---

### Post by frostie on 2007-10-11
I changed ownership back to shared then logged in as shared and:

$ cd Desktop/
$ chmod g+s Files/

editing Shopping reverts ownership to me.

---

### Post by mojoman on 2007-10-11
I agree with vanadium that it seem cumbersome and unnecessary to have a shared account, and like I also said in my first post I too would use a common group instead to access the shared folders and files. However, I mucked about with this this a lot when I set up my computer (which has several users that share files and folders) and the only way I got it to work properly was to do it the way I described in my first post. If there is an easier way, and that would be a way that actually work and not one that should work, I'd sure like to hear about it.

cheers
/mojoman

---

### Post by frostie on 2007-10-11
I do have a group, shared, of which all users are members. All folders/files were changed recursively:
$ sudo chown -R shared /home/Shared/Desktop/*

then:

$ sudo chmod -R g+s *

The bit I'm not sure about is the syntax for the umask in .bashrc.

---

### Post by wesley_of_course on 2007-10-11
Was looking for a way to increase a " set "  file size and ran across this post  and this
   one  :  [http://ubuntuforums.org/showthread.php?t=410065&highlight=folder+to+small](http://ubuntuforums.org/showthread.php?t=410065&highlight=folder+to+small)

     Didn't read all of it but it seemed to go in your direction , hope it helps .

---

### Post by mojoman on 2007-10-12
> **frostie said:**
> I do have a group, shared, of which all users are members. All folders/files were changed recursively:
$ sudo chown -R shared /home/Shared/Desktop/*

then:

$ sudo chmod -R g+s *

The bit I'm not sure about is the syntax for the umask in .bashrc.

You could try and see if it works without changing the umask but I don't think it does (though I haven't really figured out why yet). However, changing the umask for group doesn't compromise security as users in a linux system primarily belong to the group named after their username (which no other are members of). So, you can use a umask of 007 to give the users full read, write and execute privileges and deny all other all privileges, or if you're uncomfortable about giving executable privileges by default you can set a umask of 117. Umask 'inverts' the number from the permissions so a umask of 000 would set permission to 777 and a umask of 777 would set permission 000

Just add the line

umask 007

in each users .bashrc which is located on their home directory and they default for files that they create is to give them permission 770 and as you have already set the sgid you should be ready to go. (I use 003 because I want to keep these directories world viewable).

By the way, where do you have the shared files located? I have mine in /home. Now in my setup this means the following. Files created in the users respective /home/~ are of course created as belonging to e.g. mojoman/mojoman. Files created within the /home/download, /home/music etc are created as belonging to mojoman/shared. The ordinary users have NO business creating files  outside /home.

/mojoman

---

### Post by vanadium on 2007-10-12
Strange enough, Frostie, your gedit seems to behave differently to mine. When I run this test, I got:

Before edit:

~$ ls -l | grep test
-rw-rw----  2 root  video        41 2007-10-11 09:27 test

After editing with gedit:

~$ ls -l | grep test
-rw-rw----  2 root  video        46 2007-10-12 10:29 test
-rw-r-----  1 chromium video        41 2007-10-12 10:29 test~

I belong to the group "video", thus I have the right to edit test as a user. If I chown test to group root as well, I cannot edit it as normal user. The backup is the one where I am an owner (chromium), and in accordance with my umask (0022), the group permissions are set to read only. The group owner is not changed though, although I was not logged in to the group video.

To be complete, I am working with Ubuntu Feisty and gedit 2.18.1. Frostie, mention your specs,  it might be your gedit version saving backups the Windows way (save the new file under a temporary name, then add .~ extension to origininal file and rename the new one. Result: new file with other inode, thus all hard links will be broken (will point to the old file) and permissions will be messed up). The proper Linux way to do it, is to save the updated file under the same inode and write out a separate copy of the backup. Less performant, possibly less secure, but maintains the integrity of the file management.

mojoman, I agree that your method works, but it is the brute force method. However, if we can not find out what is going on here (works for me, not for frostie), it might be the wasy to go.

---

### Post by frostie on 2007-10-12
Hi,
All the shared files are in /home/shared.

I set umask 007 in .bashrc and:

[20:26:47 Fri Oct 12 Files]$ l
total 4
-rwxrwx--- 1 shared shared 167 2007-10-12 20:22 Shopping

then edit from /home/rfb with gedit 2.20.1 0n Gutsy (+ all updates to now) :

[20:26:49 Fri Oct 12 Files]$ l
total 8
-rw------- 1 rfb    shared 168 2007-10-12 20:28 Shopping
-rwxrwx--- 1 shared shared 167 2007-10-12 20:22 Shopping~

(btw it took a lot longer than 2 secs editing so I'm not sure what's going on with the clock)

reset:

[20:32:13 Fri Oct 12 Files]$ l
total 4
-rwxrwx--- 1 shared shared 168 2007-10-12 20:28 Shopping

edit with Emacs 22.1.1 (which creates no backup):

[20:33:56 Fri Oct 12 Files]$ l
total 4
-rwxrwx--- 1 rfb shared 167 2007-10-12 20:33 Shopping

Ownership changed.

$ cat /etc/group
shared:x:1003:shared,userA,userB,root,rfb

---

### Post by mojoman on 2007-10-13
> **frostie said:**
> Hi,
All the shared files are in /home/shared.

I set umask 007 in .bashrc and:

[20:26:47 Fri Oct 12 Files]$ l
total 4
-rwxrwx--- 1 shared shared 167 2007-10-12 20:22 Shopping

then edit from /home/rfb with gedit 2.20.1 0n Gutsy (+ all updates to now) :

[20:26:49 Fri Oct 12 Files]$ l
total 8
-rw------- 1 rfb    shared 168 2007-10-12 20:28 Shopping
-rwxrwx--- 1 shared shared 167 2007-10-12 20:22 Shopping~

(btw it took a lot longer than 2 secs editing so I'm not sure what's going on with the clock)

reset:

[20:32:13 Fri Oct 12 Files]$ l
total 4
-rwxrwx--- 1 shared shared 168 2007-10-12 20:28 Shopping

edit with Emacs 22.1.1 (which creates no backup):

[20:33:56 Fri Oct 12 Files]$ l
total 4
-rwxrwx--- 1 rfb shared 167 2007-10-12 20:33 Shopping

Ownership changed.

$ cat /etc/group
shared:x:1003:shared,userA,userB,root,rfb

But the permission still isn't correctly set, is it? You do not, as far as I can see , have suid set. ls -l on one of my shared folders show this output (notice the 's' on permissions)
```

drwxrws---  30 root     private   4096 2007-10-01 11:08 music

```

---

### Post by vanadium on 2007-10-13
Who else can repeat this behaviour? I can't on Edgy. For me, the behaviour is as expected, also using vi (original file retains owner and group after editing by member of the group).

---

### Post by frostie on 2007-10-13
[14:55:14 Sat Oct 13 Files]$ l
total 4
-rwxrws--- 1 shared shared 220 2007-10-13 14:52 Shopping

Edit with gedit:

[14:56:16 Sat Oct 13 Files]$ l
total 8
-rw------- 1 rfb    shared 220 2007-10-13 14:56 Shopping
-rwxrws--- 1 shared shared 220 2007-10-13 14:52 Shopping~

---

### Post by vanadium on 2007-10-13
Let me write out the test that I would ask other people to try:

mkdir test; cd test; touch test
sudo chown root:video test
sudo chmod 660 test
ls -l
gedit test
ls -l

Post the resulting output here. We will test if the file "test" does or does not keep the user "root" and the group "video" after editing it as a user (in a default Ubuntu install, you do belong to a group "video". Mention your Ubuntu and gedit version.

Frostie uses Gutsy, and observes that the user changes after editing a file. I am on Edgy, and I observe that the user stays the same after editing the file. The latter is the correct behaviour: if I edit a file of another user (I used "root" here) for which I have permissions, neither the file owner nor group should change. I want to make sure that this is not an undesired behaviour introduced by Gutsy (apparently even emacs behaves weird in that respect!).

---

### Post by mojoman on 2007-10-13
I don't have gedit installed but I tried with nano and mousepad. I'm running 64-bit 7.04 xubuntu.

```
mojoman@jukejoint:~/test$ ls -l
total 0
-rw-rw---- 1 root video 0 2007-10-13 19:23 test
mojoman@jukejoint:~/test$ nano test
mojoman@jukejoint:~/test$ ls -l
total 0
-rw-rw---- 1 root video 0 2007-10-13 19:23 test

```

```
mojoman@jukejoint:~/test$ ls -l
total 4
-rw-rw---- 1 root video 2 2007-10-13 19:25 test
mojoman@jukejoint:~/test$ mousepad test
mojoman@jukejoint:~/test$ ls -l
total 4
-rw-rw---- 1 root video 3 2007-10-13 19:25 test

```

None of them changes permissions.

---

### Post by frostie on 2007-10-13
[19:25:24 Sat Oct 13 Files]$ mkdir test;cd test;touch test
[19:25:45 Sat Oct 13 test]$ sudo chown root:video test
[sudo] password for rfb:
[19:26:15 Sat Oct 13 test]$ sudo chmod 660 test
[19:26:24 Sat Oct 13 test]$ l
total 0
-rw-rw---- 1 root video 0 2007-10-13 19:25 test
[19:26:28 Sat Oct 13 test]$ gedit test
/home/rfb/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
[19:26:56 Sat Oct 13 test]$ ls -l
total 4
-rw------- 1 rfb  shared 6 2007-10-13 19:26 test
-rw-rw---- 1 root video  0 2007-10-13 19:25 test~
[19:27:04 Sat Oct 13 test]$

---

### Post by frostie on 2007-10-13
First one was in /home/shared.
In my own /home directory:

[19:31:00 Sat Oct 13 ~]$ mkdir test;cd test;touch test
[19:31:09 Sat Oct 13 test]$ sudo chown root:video test
[19:31:21 Sat Oct 13 test]$ sudo chmod 660 test
[19:31:34 Sat Oct 13 test]$ ls -l
total 0
-rw-rw---- 1 root video 0 2007-10-13 19:31 test
[19:31:43 Sat Oct 13 test]$ gedit test
/home/rfb/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
[19:32:11 Sat Oct 13 test]$ ls -l
total 4
-rw------- 1 rfb  rfb   6 2007-10-13 19:32 test
-rw-rw---- 1 root video 0 2007-10-13 19:31 test~
[19:32:19 Sat Oct 13 test]$

---

### Post by vanadium on 2007-10-14
We need another Gutsy user to confirm this issue. Can someone else currently using Gutsy copy  these commands, paste them in a terminal and post the output here (one command will load gedt: add a word, then exit gedit saving the file).

```

mkdir test; cd test; touch test
sudo chown root:video test
sudo chmod 660 test
ls -l
gedit test
ls -l

```

The  issue is that Gutsy changes the user and group properties of a file when saving (i.e. the edited data is not saved in the same, but in a different inode. As a result, permissions will change, and hardlinks will not work anymore (i.e., point to the old versions)

---

### Post by strabes on 2007-10-14
I'm a gutsy user and did what vanadium asked above.> alex@alex-laptop:~$ mkdir test; cd test; touch test
alex@alex-laptop:~/test$ sudo chown root:video test
alex@alex-laptop:~/test$ sudo chmod 660 test
alex@alex-laptop:~/test$ ls -l
total 0
-rw-rw---- 1 root video 0 2007-10-14 08:18 test
alex@alex-laptop:~/test$ gedit test
alex@alex-laptop:~/test$ gedit test
alex@alex-laptop:~/test$ ls -l
total 8
-rw------- 1 alex alex 7 2007-10-14 08:19 test
-rw------- 1 alex alex 1 2007-10-14 08:18 test~
alex@alex-laptop:~/test$ 

So it does look like the permissions are being changed.

Here's the output of the same set of commands, this time with the "Create Backup" option disabled in gedit:> alex@alex-laptop:~$ mkdir test; cd test; touch test
alex@alex-laptop:~/test$ sudo chown root:video test
alex@alex-laptop:~/test$ sudo chmod 660 test
alex@alex-laptop:~/test$ ls -l
total 0
-rw-rw---- 1 root video 0 2007-10-14 08:21 test
alex@alex-laptop:~/test$ gedit test
alex@alex-laptop:~/test$ ls -l
total 4
-rw------- 1 alex alex 8 2007-10-14 08:21 test
alex@alex-laptop:~/test$ 

---

### Post by vanadium on 2007-10-14
Many thanks. This shows there is a change in behaviour in Gutsy which I believe cripples the concept of permissions. Permissions should not change after accessing a file. Unfortunately I never filed an issue with Ubuntu before, so I will have to find out how.

You have edited and saved the file twice in your first example, which is why the user and group are changed both in the file test and its backup. Otherwise, we would have seen the original permissions in the backup.

---

### Post by vanadium on 2007-10-14
I managed to file this

[https://bugs.launchpad.net/ubuntu/+bug/152638](https://bugs.launchpad.net/ubuntu/+bug/152638)

so now the pros can confirm whether this is a bug or a feature.

---

### Post by mojoman on 2007-10-14
> **vanadium said:**
> I managed to file this

[https://bugs.launchpad.net/ubuntu/+bug/152638](https://bugs.launchpad.net/ubuntu/+bug/152638)

so now the pros can confirm whether this is a bug or a feature.

Good Call. We'll just have to wait and see but it sure sounds like a bug to me.

---

### Post by vanadium on 2007-10-14
Thanks. I am sorry I might be nagging, but it would perhaps be good if the Gutsy users also tried the following test (first remove your previous "test" directory if you still have it)

mkdir test; cd test; touch test
sudo chown root:video test
sudo chmod 660 test
ls -l
echo "added a sentence" >> test
ls -l

Instead of using "gedit", this just echos a new line to the file "test". If the issue persists even here, then it is not an application issue but a more fundamental issue at the level of the operating system.

---

### Post by frostie on 2007-10-14
[18:56:54 Sun Oct 14 ~]$ mkdir test; cd test; touch test
[18:57:03 Sun Oct 14 test]$ sudo chown root:video test
[sudo] password for rfb:
[18:57:19 Sun Oct 14 test]$ sudo chmod 660 test
[18:57:28 Sun Oct 14 test]$ ls -l
total 0
-rw-rw---- 1 root video 0 2007-10-14 18:57 test
[18:57:31 Sun Oct 14 test]$ echo "added a sentence" >> test
[18:57:44 Sun Oct 14 test]$ ls -l
total 4
-rw-rw---- 1 root video 17 2007-10-14 18:57 test
[18:57:49 Sun Oct 14 test]$

---

### Post by frostie on 2007-10-14
Just a note with the solution I've come up for my situation with our shared shopping list., this is what I did:
Create the shopping list in the shared directory, owned by ;shared', group: 'shared', chmod 660.
Open nautilus.
navigate to the 'Shopping' file in the shared directory.
Right-click the file and choose 'make link'
Drag the link to the taskbar.
Open, edit.
ownership/group of original file remain untouched.

Log in as  other users as required, create further links via right-click (ie do not delete existing ones present in the directory where the 'Shopping' file resides) and drag to taskbar (or wherever you want I guess).
Permissions of original file sem to remain as they were.

---

### Post by vanadium on 2007-10-14
Thanks so much, Frostie. This shows that it is just a gedit issue (and perhaps some other editors as well). I have been thinking about symbolic links as well, but because it works correctly here in the first place, I could not test that. It is funny to learn that it does work well with symbolic links.

---

### Post by vanadium on 2007-10-23
Good news: the issue is recognized and fixed already "upstream" (by the gnome developper) so it will probably be corrected soon in Ubuntu as well.

[https://bugs.launchpad.net/ubuntu/+bug/152638](https://bugs.launchpad.net/ubuntu/+bug/152638)

The gnome people picked up on our issue. Frostie, you have done a service to the open source community remarking and reporting this.

---

### Post by chrisccoulson on 2007-10-23
I haven't read through the whole thread, so I'm not sure if someone else has already mentioned this or not. For managing permissions on files/folders that Iu want multiple users to be able to write to, I prefer to use ACL's. Have you considered trying this? 

ACL would give you permission control similar to NTFS. Everything you need is in the repositories. You just need to remember that you need to mount the filesystem with the 'acl' option.

---

### Post by frostie on 2007-10-23
It all stemmed from our humble shopping list really.

I guess it makes you realise that everyone can contribute in some way, we don't all have to be hacking the kernel.

---

### Post by frostie on 2007-10-23
acl looks interesting, I hadn't heard of it before. I found a link here:

[http://tlug.dnho.net/?q=node/171](http://tlug.dnho.net/?q=node/171)

that gives you a quick intro.

---

