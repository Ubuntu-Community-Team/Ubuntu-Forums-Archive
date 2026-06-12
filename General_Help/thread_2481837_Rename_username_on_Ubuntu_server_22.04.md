---
title: "Rename username on Ubuntu server 22.04"
date: 2022-12-10
forum: General Help
---

### Post by vjekobalas on 2022-12-10
I have a Ubuntu server 22.04 VM on which several applications for software development 
(ssh, Apache,mysql, php, VScode-server) have been installed by user_a.
Is there an easy way to change the username & password in this situation ?
I'm new to Linux and noticed that if I create a new user_b, directories related to the applications
are missing in the /home/user_b directory (guess I'm too used to seeing Windows applications 
being globally available to all users) .

---

### Post by #&amp;thj^% on 2022-12-10
To save myself from typing please see this basic start: [https://linuxize.com/post/how-to-add-and-delete-users-on-ubuntu-20-04/](https://linuxize.com/post/how-to-add-and-delete-users-on-ubuntu-20-04/)
I should though include this.
How to change a users password in Ubuntu
[list]
    [*]Open the terminal application by pressing Ctrl+Alt+T
    To change a password for user named tom in Ubuntu, type:
   ```
 sudo passwd tom
```
    [*]To change a password for root user on Ubuntu Linux, run:
    ```
sudo passwd root
```
    [*]And to change your own password for Ubuntu, execute:
    ```
passwd
```[/list]

---

### Post by vjekobalas on 2022-12-10
Thnaks for the  link. I'm dealing with a server/terminal. Maybe my goal was not clear from the post - 
I want to use all the applications that user_a installed but with my name/pw
 (the VM was given to the whole class for php development but I'm
tired of typing the username/pw of the person who sent us the VM). 

I added new user_b (my name/pw) via adduser command but noticed missing folders 
in my home/user_b directory so I guess accessing those applications via the new user 
will not work/ need to install them again (or am I missing something) or alternatively 
need to rename user_a + new pw ?

---

### Post by #&amp;thj^% on 2022-12-10
See my post above, I added the missing details.
If you need more just ask. :)

---

### Post by vjekobalas on 2022-12-10
I have the Ubuntu server with terminal only

it's a two part problem I'm trying to solve (if there is a problem)- I want to use my username/pw and be able to
use all the applications but everything was installed by another username/pw (application specific directories
are in his /home/user directory

---

### Post by #&amp;thj^% on 2022-12-10
> **vjekobalas said:**
> I have the Ubuntu server with terminal only

it's a two part problem I'm trying to solve (if there is a problem)- I want to use my username/pw and be able to
use all the applications but everything was installed by another username/pw

Yes i get/understand your thread, and this requires permissions changed (Th)is can get nasty)
but here you go, just be careful [https://unix.stackexchange.com/questions/244297/can-users-in-a-group-access-a-file-that-is-in-another-users-home-directory](https://unix.stackexchange.com/questions/244297/can-users-in-a-group-access-a-file-that-is-in-another-users-home-directory)
All applications installed should be available for all users, define some you can't use then.

---

### Post by vjekobalas on 2022-12-10
I though it may be nasty because of the applications /permissions etc. - just wanted to check - so better
put up with the username/pw or create new user and reinstall all applications again - right ?

---

### Post by #&amp;thj^% on 2022-12-10
> **vjekobalas said:**
> I though it may be nasty because of the applications /permissions etc. - just wanted to check - so better
put up with the username/pw or create new user and reinstall all applications again - right ?

That would be best, but don't forget you can also remove users to de clutter your sever. That should make sense right?

---

### Post by vjekobalas on 2022-12-10
Regarding removing users, you are just referring to de-cluttering and not helping with my problem - right ?
Just one more question so that I get my head around this business with the applications:
how does this work in a real world server environment - are all applications installed under one userid
and then down the road which ever admin needs to make changes uses that userid 
(because application directories are visible only under the installer's home directory )?
Excuse the stupid question - I'm new to linux/no admin

---

### Post by #&amp;thj^% on 2022-12-10
> Regarding removing users, you are just referring to de-cluttering and not helping with my problem - right ?

Clutter builds up like .conf's and other stuff, but a yes to both I suppose, more on that as you get your sea legs underneath you first.
> Just one more question so that I get my head around this business with the applications:
how does this work in a real world server environment - are all applications installed under one userid
if it is installed via the Software Center or apt-get it will be available to all users. This is true even if you download a current deb file.
> Excuse the stupid question - I'm new to linux/no admin 
My feelings on this is "The only dumb question is one not asked" we have all here have been new at one time.

---

### Post by ne29914 on 2022-12-10
Your user_a is the main user (created first) with sudo privileges. User_a can do anything using sudo.
User_b is to begin with a "normal" user with no special privileges.
A twist: user_b needs to login one time first to create his/her user directories and general /home/user_b files.
All users can try to execute all applications, but whether they have permission to do so is a different thing.

---

### Post by vjekobalas on 2022-12-10
During the class each person downloaded the Ubuntu server, installed with own username/pw
and then basically followed the Digital Ocean tutorial for the LAMP
Stack install:
[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu-22-04)
, so each application was installed via
sudo apt update
sudo apt install application_name (e.g. apache2)
Does that make any difference as to why adding a new username doesn't
show up the application directories also under the new user home/username directory
OR is it because normally it should have been installed somewhere else
which gives "global" access to all users i.e. you could add a new user (admin)
and all directories would also be visible to them ?

---

### Post by #&amp;thj^% on 2022-12-10
This seems like it is getting overly complicated and does not need to be.
I have question for you is this a home work assignment?
And why don't you just login as the Adim/usr's name.
But This would be the best way, >>>" you could add a new user (admin)
and all directories would also be visible to them" as it was intended.

---

### Post by vjekobalas on 2022-12-10
It's complicated because I don't understand it ;)
This is not an assignment - we've all been through installations and now the
teacher has given everyone his VM with his username/pw so that we're all on 
the same page so to say and now we're on to programming i.e. using VS code 
remote to the VM as php environment - I'm just trying to learn a bit more
about linux and wanted to change the username/pw.

The first user_a (the teacher who created the VM is admin)
and in his home/username directory are directories with names VScode, .ssh and git
from installation of those applications.

I created another user_b (me) making him admin also
sudo adduser newusername
sudo adduser newusername sudo   #add newuser to sudo group

The application folders are missing in the user_b directories (which is probably
normal as the application probably asked where to install/ don't remember
all of them except ssh). 

For the end user, who is getting output from the server it is clear,
all users will access the data from the server as apache serves to their
browser but I don't understand how the user/pw business works 
for admins who work on the server - would
they also login using user_a name/pw i.e. of the admin that installed everything ?
As an example the /home/user_a/.ssh/ directory holds the private key for access
to Github - if for some reason an admin needs to do something with that,
he needs to login with user_a name/pw - or is this a "school example" and
things would be installed differently so that any admin can access with their
username/pw

Uuiii - sorry I can see I'm boring you guys with this

---

### Post by Tadaen_Sylvermane on 2022-12-10
Using user a

```
sudo adduser user-b
```
```
sudo rsync -auv /home/user-a /home/user-b
```
```
sudo chown -R user-b:user-b /home/user-b
```

Now when you login as user b you will have it all. No need to eliminate the adm user.

Will make an exact copy of user-a folder. Your instructor may expect you to use the one he made though. Make sure it's ok with them first.

---

### Post by The Cog on 2022-12-10
I was going to suggest exactly what Tadaen_Sylvermane just said. Make a new user's directory, duplicate the original user's home directory into it and then change the ownership of the contents. 

Note that this may not work. Some of the applications may have saved the original username or the original path in its configuration files which could make things difficult. This might help with saved paths on the configuration (rename the original and then link the original home name to the new home folder:
```
sudo mv /home/user-a /home/user-a/original
sudo ln -s /home/user-b /home/user-a
```

---

### Post by TheFu on 2022-12-10
So, there are 2 levels, and nearly infinite methods, to install programs on all Unix systems.

Programs can be installed 
a) system-wide using a package manager with root or sudo privileges.
OR
b) programs can be installed by any user into their HOME (or anywhere else they have write permissions).  This is because Unix was always about letting users have control of everything they could without harming system security.   Certain types of programs won't run under end-user accounts because elevated privileges are required.


Ok, so in the Debian world, 
1) we can install programs using the package manager, this uses the "APT" system. root is required for this.
or
2) we can install programs using a snap package manager. root is required for this. In theory, any Linux distro can use this, but in reality, Ubuntu is it.
or 
3) we can install programs using a flatpak package manager. I don't know if root is required or not for this. Sorry, perhaps someone else can answer.
or
4) we can install programs by downloading the source code and following the README and/or INSTALL documentation for that program.  This method doesn't need root/sudo, provided no system directories are expected to be used.  For this method, the directories where the programs are installed into is what determines whether root is required or not.  For use by all users, it is customary to install programs from source into /usr/local.  That's called a PREFIX in nearly all README/INSTALL documentation.  /usr/local/ is a system directory, so installing there requires root/sudo privileges.  
But end-users can set the PREFIX to anything they want, so they can install programs/code into their HOME directory too. No root is needed for this, but other users may be prevented from accessing it, if the file/directory permissions don't allow it.

I think that was 1fallen's point.  Normal Unix permissions are important and can't be overridden magically.  The user who setup and owns the directories and files would typically be asked for access by other users.  Because of the way Ubuntu doesn't place all users into a "users" group, effectively, the owner of the program would need to allow "other" read permissions to the files and eXecute permissions to the directories and programs and scripts.  If a sufficient number of users ask for access, the owner should speak with the sysadmin to move the install under /usr/local/ for wider use.  
Now, if the programs have hard-coded directories where it is expected that writes, deletions and additions are allowed, then those won't be allowed (and shouldn't be allowed) into any specific user's HOME or under /usr/local/ system directories.  This means the programmer didn't think ahead. All Linux/Unix programmers should know better and assume multiple users will run the program concurrently, even on a single-user computer.

What is common is to have an environment variable that controls where write access is necessary for each user running the program.  It is also common to use the HOME variable as the top level, assumed, directory, which would mean that other users can run the same program, concurrently, but have their output, DB, logs, configs and other files that aren't read-only and shared stored in their own HOME "somewhere".  If the program expects directories to exist, then the program should attempt to create those when needed and generate a clear, concise error if that fails.  I've seen some Gnome programs crash when access to expected directories wasn't possible.  I've also seen Gnome get into a login loop over something like that.  What happened was someone with sudo logged in and the first thing they did was use "sudo gedit {some file}" before doing anything else.  Dutifully, gedit created directories under the user's  HGME, but because sudo was used, the owner of those directories was root:root.  At the next login, when any gnome programs tried to run, they didn't have any write access for any directories under the expected locations. Instead of providing a clear, concise error and closing cleanly, they just crashed.  Not good.  Please don't have your programs do that.

If multiple users want to share output directories, then they should be part of the same group and setup a specific directory just for sharing.  I always ensure that isn't in any HOME directories and the sysadm has to create the new group and place each of the users' into that group and setup the top level directory appropriately for multiple users to have the required access.  I've posted a little how-to in these forums a few times.  Search for my username and "Working Together" to find it.

Learning this stuff is basic knowledge, especially for a programmer.
Also, it would be good to know what things belong where in a Unix/Linux file system, so that surprises don't happen and your programs follow those standards. Wikipedia has an article "Filesystem Hierarchy Standard".  There's a table which is probably all you need to read.

Hope this is helpful and I didn't confuse even more.  In short, learn Unix permissions ASAP. You can learn 90% of them in about 45 minutes of specific effort. The other 10% are needed only seldom, so even admins don't all know those and have to look them up too.

---

### Post by TheFu on 2022-12-10
If all you want to do is simply change the username and leave everything else alone, you can edit the passwd, group, shadow, gshadow files and change the username from  user_a ---> user_b everywhere.  Don't dilly-dally. Changes take effect immediately and if the user is a sudo member, you can find yourself locked out.  If you make all the changes in under 10 seconds, it should be fine.  Much longer and bad things can happen, like being told that "you don't exist, go away."  I've seen that specific error, but not recently.  Be certain you know user_a's password, since that will still be used after the rename.  

And the edit needs to happen with root or sudo privileges.

If you mess this up, be prepared to restore from a backup or at least have a way to put those 4 files back when you've been locked out of the system.

I'm saying what I'd actually do and have done a few times over the decades. Only you can decide if you have the skill to accomplish this or not.  The manpages for all those files spell out the exact layout for each field. They are just text, but do have specific fields that need to be consistent.

---

### Post by vjekobalas on 2022-12-11
Much appreciated for all the detailed answers - very helpful  !!!

---

