---
title: "User Account - Recommended or waste of time?"
date: 2014-05-03
forum: General Help
---

### Post by mikeebean on 2014-05-03
In Windows, it is standard practice to create a user account without administrative privileges for security reasons. I'm not sure what the standard is for Macintosh, I never created an account in OS9 and haven't had the opportunity to use a Mac since then.

Is this common procedure for linux systems? When I first installed Ubuntu 12.04, I didn't create a user account. Later I decided to do a clean install, and created both an admin and user account.

I ask because I plan to install 14.04 and computer security is a bit of a mystery to me. While I fully understand the need for security, I often find myself struggling to figure out the best way to apply administrator permissions without leaving the user account. There are times where I spend many minutes of frustration, only to realize I'm in the wrong directory, or using the wrong sudo procedure. (Other times I wonder if my installation is set up incorrectly, such as when I forget to "su -- admin" and terminal asks for my password for the user account, which I feel it shouldn't even ask as the user account has no root privileges.)

Thanks for any advice on this!

Michael

---

### Post by vanadium on 2014-05-03
In linux, you always create a user account. In Ubuntu, the first user that is created also has root privileges. In order to execute a command with root privileges, it is preceded with the "sudo" command. At that point, the user has to authenticate again.

---

### Post by mcduck on 2014-05-03
No need to worry about it, creating a separate admin account isn't really needed in Ubuntu, the default setup is fine as it is.

The reason you'd need to do that in Windows is that running a desktop and all your applications with full admin privileges exposes the system to a lot more (and more serious) security threats as any bug or security issue in any program would now become a system-level threat rather than just affecting a single user.

On the other hand, the default setup in Ubuntu doesn't have that kind of admin users, instead admins are only able to run things with full privileges when they specifically ask to do so and confirm with password (this is what *sudo* is for). So the desktop and all applications will run with normal user-level privileges only, solving the issue without having to actually deal with two separate user accounts.

(the slightly more detailed answer of course is that there actually already is a separate administrator user, *root*, but it's locked and instead admins can only temporarily run things using that account by using *sudo*)

Being a Unix system, OS X has a similar approach to Ubuntu, although as far as I know it's slightly less strict by default in some things.

---

### Post by TheFu on 2014-05-03
Linux is NOT windows. They are very different OSes with extremely different philosophies.

From the beginning, Linux/UNIX was designed as a multi-user OS.  It uses file owners, groups and permissions at the center of the security model.  Further, almost everything on the system is "a file" - that includes the way that the OS talks to the screen, keyboard, mouse, network, HDD, almost everything.  Controlled access to resources is managed by group membership and group permissions to the input/output device files under /dev/  ... Processes also have owners and permissions (userids and effective userids).  By managing group memberships it is possible to provide many sorts of permissions whereby the end-user doesn't need root-level authority at all for dealing with applications and files.  Of course, some applications are poorly written and demand root.

So ... to the end an understanding of groups, users and file/directory permissions is central to understanding how Linux manages security.

There is almost ZERO need to ever use 'su' on a modern Linux system.  sudo replaced that years ago.
Having a separate account just for administrative needs is not considered a best practice anymore either.

Thinking multi-user takes a little time, but after you get that down, it becomes very clear, even elegant, in the simplicity and amazing capabilities.  Give it time to sink in.

---

### Post by mcduck on 2014-05-03
> **mikeebean said:**
>  (Other times I wonder if my installation is set up incorrectly, such as when I forget to "su -- admin" and terminal asks for my password for the user account, which I feel it shouldn't even ask as the user account has no root privileges.)

I suppose this will make more sense when you keep in mind that "sudo" is not justa  comand for doing admin stuff, but actually can e sued for a lot more, and can be configured in more detail than just if an user has the full admin rights or not. For example you can give a non-admin user the permission to run a single, specific command with sudo, and choose if the suer needs a password confirmation to do that or not. Or you can give an user the permission to run commands a s a specific other user, etc.

So, to prevent people who get an access to user account from just running random commands to poll what kind of sudo permissions that user might or might not have, sudo will always ask for the password first (unless of course it was configured to allow that specific command without a password).

---

### Post by TheFu on 2014-05-03
@McDuck is correct.  sudo is a-m-a-z-i-n-g.  The manpage for it is one of the best written documents on all our systems.
man sudo
man sudoers
has lots of information about the use of those programs, but an understanding of users, groups, and permissions will still be necessary.
[https://help.ubuntu.com/10.04/serverguide/user-management.html](https://help.ubuntu.com/10.04/serverguide/user-management.html) and [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) is where I'd recommend starting.

Not every user account is created equal. Some are for processes, some for managing a suite of programs and others are for end-users.  Then there are userids with an id of 0 (zero) - those are root or root-equivalent userids. Some interesting (and dangerous) tricks can be performed with this knowledge. The username doesn't matter, it is all about the uid for almost every program on a UNIX system.

---

### Post by bapoumba on 2014-05-03
> **mcduck said:**
> 
Being a Unix system, OS X has a similar approach to Ubuntu, although as far as I know it's slightly less strict by default in some things.

Just to answer that part (and not willing to derail the thread), sudo is, to my knowledge, working the same on Mac OSX and Linux. On Mac OS, the sudoers file is in /etc/sudoers and the root account is disabled. I have never felt a difference, but may be I have never pushed it either.

Quite interesting read here [http://www.sudo.ws/sudo/history.html](http://www.sudo.ws/sudo/history.html) and there [http://www.sudo.ws/sudo/license.html](http://www.sudo.ws/sudo/license.html)

---

### Post by Habitual on 2014-05-03
> **mikeebean said:**
> In Windows, it is standard practice to create a user account without administrative privileges for security reasons. Standard for whom? Certainly not the end user of Windows. They know jack all about security.
Every Windows Account created has Administrative privileges unless explicitly set otherwise.

---

### Post by mikeebean on 2014-05-07
Thank you everyone for your answers. When I install 14.04, I'll be creating just the initial user account, and I'll read the links posted to try and get a better grasp on Linux security.

Thanks again!
Michael

---

