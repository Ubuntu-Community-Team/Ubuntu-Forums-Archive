---
title: "File / dir permission for users sharing &quot;work&quot; directories"
date: 2014-12-29
forum: General Help
---

### Post by astralix2 on 2014-12-29
Hi all!

I have a notebook that I use for work and for private embedded development.
For the company things I need to use my company login, real name and ssh keys, for my private things, I use my alias and other ssh keys.
So a mainline kernel for a company product shows "kernel 3.19+ [email]user@company.com[/email] while here it shows "astralix@crewrktablets.de".

To achieve this, I added astralix as a user of the notebook. Unfortunately I now ran into a trap...
As I do many things on command line, I linked most working directories via symlink into my initial [user] home directory. So I changed there just by "cd Projects/kernel1" or "cd Android/kk/"
Now all these working directories have permissions set to user:user and astralix is not allowed to change anything inside, or not allowed to even look inside.

So I added a group "users" and put both users inside.
I know how to change the permissions like chmod / chown and even tricky tricks like "find . -type d -exec chmod 775 {} \;"
But does this solve my problem? I need to reset the permissions by "chown :users *" and "chmod g+rw" every time I create new files in these projects with one account, if I need to access the project from the other account... That isn't funny.
Additionally I have to keep an eye on directory and file permissions in certain parts of initrd, Android and selinux as these generated file-systems need to follow strict permissions in subdirectories of the existing projects...

How can I modify the user rights used by default for my two users, that new files are keeping a certain initial rights structure so the two accounts can cooperate on the local harddrives?

Thanks for any hint or idea, or description how you have solved this

Astralix

---

### Post by Holger_Gehrke on 2014-12-29
Do you want to change the default-group for the users ? 
```

usermod -g users <username>

```
should do it ...

---

### Post by astralix2 on 2014-12-29
Thank you Holger,

that solved the first part... I just didn't see that... 
Now I only need to set the default mask for creating files... there was a thing called umask or such... I need to check how to put that into my .bashrc...

---

### Post by steeldriver on 2014-12-29
Sounds like what you are looking for is the setgid bit - if you set the setgid bit on your "shared" directories, then any files created there will inherit the group of the parent (so if your users belong to that group, they will have write permission with the default umask)

---

### Post by astralix2 on 2014-12-29
Hmmm, 

I need to check if that works for Android and such systems that prepare filesystems. If they use sort of fakeroot, then this might work.

---

### Post by bab1 on 2014-12-29
> **astralix2 said:**
> Hmmm, 

I need to check if that works for Android and such systems that prepare filesystems. If they use sort of fakeroot, then this might work.

The difference between using a common primary group (i.e. *_users_* in this case) and using setguid is important to note.  If you alter the primary user group for a user then ANYTHING anywhere in the entire file system that user creates is owned by this: user_name:**users**.  If you use setguid on a branch of the file system the user retains the original user:user ownership except when creating files/directories in the file system that is controled by the setguid bit.

I prefer the latter.  I only allow users to to belong to a secondary "common group" on a portion of the file system (such as /dev or /projects) and for that you need setguid and not setting the primary group to a common group such as *users*.

---

### Post by astralix2 on 2015-01-02
I still try to evaluate the difference, or better explained, the pro and con of setguid compared to the users group solution. 
For me, it doesn't look like any difference in my case, where I am still the only user of the machine, but only using two accounts.

For compiling Android or kernels, it seems not to make any difference too. However, if I create additionaly accounts for other people than me, it might have an effect. So can you explain the benefit of the setguid version?
For the home directory, it doesn't make a difference for me either, as all homes are encrypted, so one user cannot access a different users home even the group may be set permissive in that case.

Thanks for your ideas
Astralix

---

### Post by bab1 on 2015-01-02
> **astralix2 said:**
> I still try to evaluate the difference, or better explained, the pro and con of setguid compared to the users group solution. 
For me, it doesn't look like any difference in my case, where I am still the only user of the machine, but only using two accounts.

For compiling Android or kernels, it seems not to make any difference too. However, if I create additionaly accounts for other people than me, it might have an effect. So can you explain the benefit of the setguid version?
For the home directory, it doesn't make a difference for me either, as all homes are encrypted, so one user cannot access a different users home even the group may be set permissive in that case.

Thanks for your ideas
Astralix
As I said the use of a **common** primary group means that all users have access to all data in the /home directory (not encrypted).  This is because the default file creation is read/write for both the user and the group (umask = 775/664).  Some day completely encrypted directories will come back to bite you.  I only encrypt a small amount of data for very specific reasons.  This doesn't mean I want everyone looking at my files in my own personal home directory.  Ownership and permissions are enough to keep all but persistent hackers out.  With the Ubuntu default primary group being the user (e.g. user1:user1) only that user has permissions to write to the /home/user1 directories.  If you set the permissions on the home directory  to read/write for the user:group and no permission for the others then only the user has permissions to to access their home directory.

Why set the primary group to a common group with multiple users?  It's easier to administrate that in a large network when adding and deleting users.  The primary group could be either: wheel (adm), staff or users.  The  the entire file system should be configured with a concern for for a specific groups access.

On the other hand if you read up on [User Private Groups]("http://www-uxsup.csx.cam.ac.uk/pub/doc/redhat/redhat6.2/ref-guide-62/s1-sysadmin-usr-grps.html") you find that you only need to add the user to a secondary user group and use setguid on the specific section of the file system you want to share.  I don't keep common group data in /home.  It belongs in a file system branch that is separate from /home.  I think of /home as a place to put my personal file and directories.  For my now smallish network at home I prefer the User Private Groups scheme.  In the end this deals with the default umask for Linux (775 for directories and 664 for files)

There are traditional preferred ways of handling these matters and there are hacks.  If you "just make it work" it will some day cost you endless hours chasing down the problems that can crop up.  The command *chmod -R 777* is never the answer.  In the end it is up to you to make the decision as to how to proceed.

---

### Post by astralix2 on 2015-01-13
Thank you very much for the explanation, but sorry, I have to ask again...

Let me explain, what I expected and what I still miss... I renamed the group, so it is not to easy to mess things up with user / users...
I made a group programmers and put this group as primary group for both of my users.
I created a directory android:
775 astralix:programmers ... android
I extracted some files in it or checked out a git and the files are all astralix:programmers 644 while subdirectories are 755.
If I then switch to user beta, is can not checkout, commit or even re-compile, as groups are set 644/755 instead of 664/775
So ...

I followed your idea and revoked this "all users are in one primary group"... there are now beta:beta and astralix:astralix.
I deleted the android directory and created a new one:
mkdir android; chown :programmers android; chmod 775 android
Then I added: chown g+s android, what I guess is the SGID bit that tells the system to keep permissions on subdirectories?

Then I added files and subdirectories and they are 644/755 and of user astralix:astralix... Ouch!
Ok, I checked my .bashrc as long long time ago, I had to add umask 022 there, as it was required to sucessfully build Android systems and it did not do any harm to my other projects.
I removed that line again and so I solved at least the thing, that very new file is set as 644 / 755.
But still, even the upper directory has set astralix:programmers all files inside are astralix:astralix
So the user beta still cannot write-access these files or directories.

How do I set things up that I can create a directory with 775 user:group and all files inside are kept with x7x/x6x and group :programmers

I guess I had some complications caused by the umask 022 in both of my users ~/.bashrc
But I tested and the result was as I told above:
[FONT=courier new]drwxr-xr-x  32 astralix users     4096 Jan 13 22:15 ./[/FONT]
[FONT=courier new]drwxrwsr-x  10 beta     users     4096 Jan 13 22:07 ../[/FONT]
[FONT=courier new]drwxrwxr-x   3 astralix astralix  4096 Jan 13 22:11 abi/[/FONT]
[FONT=courier new]drwxrwxr-x  11 astralix astralix  4096 Jan 13 22:11 art/[/FONT]
[FONT=courier new]drwxrwxr-x   9 astralix astralix  4096 Jan 13 22:11 bionic/[/FONT]
[FONT=courier new]drwxrwxr-x   4 astralix astralix  4096 Jan 13 22:11 bootable/[/FONT]
[FONT=courier new]drwxrwxr-x   6 astralix astralix  4096 Jan 13 22:11 build/[/FONT]
As you can see the s bit is set with groups on beta:users but the files / dirs inside are set with astralix:astralix... this is wired!

However: I agree that only a very small amount of encrypted data is needed and so I only store company documentation there as long as I need it offline. If the encrypted data is dead or lost, who cares. The rest of the home directory is symlinked to a non encrypted home directory. It doesn't make sense to store pictures or music that I made, watch or listen too in separate directories.

However, I cannot imagine that it is impossible that two users work on the same project and compile the same source without each of them having to have a private copy of it...


Would be really nice if you could help me to understand this better, please...

Thanks in advance
Astralix

---

### Post by bab1 on 2015-01-13
> I renamed the group, so it is not to easy to mess things up with user / users...
You don't need to do this.  Just make a new group named programmers and add the users you want to that group.  Make sure you define the group number (gid) so you don't use a gid > 1000. 

> How do I set things up that I can create a directory with 775 user:group and all files inside are kept with x7x/x6x and group programmers?
Let's start with what the pieces to the puzzle really are.

The directory is a file that acts as a container for other directories and files.  The directory uses some of the permissions in a different manner than a regular file.  The eXecute bit is used to allow a user to access (read and descend into) that directory.  The write permissions allow you to manipulate the files in that directory.  Consider this: You can't write to the directory like it is a file and you can't eXecute the directory as you would a file.

The sgid (setgid) bit forces the file and directory **creation** to be done in the directory by the group assigned to to that directory.  This does not mean copied somewhere else or retrieved from git with a differing group (gid).  In fact the group name is not really what is followed.  it is the gid number.  If you have a group named programmers (gid=116) on one machine and the same group name with a gid=216 on another you will have problems.  The gid number is what is tracked.

The umask that is used is always the last one to be declared in the environment you are using.  If needed you can always user the command: umask=002 or umask=022 in a script just before creating a file.  In Linux all files are created with the permissions of 666 and a umask is applied.    If you create a file with the umask of 002 the permissions will ultimately be 664 (6-2 on the last permission).  If you do the same thing and the umask is 022 then the permissions would be 644 (-2 from the second to the last and -2 from the last permission).

The directory permissions are always 777 and the umask is applied in the same manner as above.  This yields either 775 (umask=002) or 755 (umask=022).  Both of these settings allow all user access to the directory but only the 775 permissions allow the user and the grroup to manipulate files in the directory.

A short answer to your second question is: You don't want the permissions to be 0775 at all.  You want the permissions on the root directory that will hold all the subdirectories to have the permissions of 2775 and the owner to be root:programmers.  An example would be if we made the root directory */test * like this ```
sudo mkdir /test

sudo chown root:programmers /test

sudo chmod 2775 /test 
``` 

Note that the the owner of this directory is root, but the group is programmers.  All you need is the access via the group permissions.  Test that you can create files and directories in this directory with these commands```
touch /test/file.txt

mkdir -p /test/dir1
```... note that you are using absolute addressing.  You could move to the directory /test (cd /test) and use relative addressing like this```
touch file1.txt 

mkdir dir2
```

Any problems you have with this will be due to **_copying existing files or directories_** to the directory /test.  These you will have to deal with on a case by case basis.

---

