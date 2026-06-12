---
title: "Trying to create a user with read-only access to all files (a read-only root)"
date: 2019-08-27
forum: General Help
---

### Post by ralphclintellis on 2019-08-27
I've seen information on creating a 'roroot' group/user.  I've created a user with that group membership - but I can't su - <user>; I get
su: Authentication failure

---

### Post by SeijiSensei on 2019-08-27
Most ordinary users have read-only access to most files on the system.  The only ones they cannot see are ones created by other users with more limited permissions like 600.  But  they can certainly read files in /etc, /usr, and /var for instance.  In fact, Ubuntu is much less stringent about file access than are "enterprise" distributions like RedHat.  On RH-flavored systems, only root can read files in /var/log.  That's not true for Ubuntu. And RH systems create home directories with 700 permissions; on Ubuntu they have 755 permissions making all users' home directories readable by other users on the system.

---

### Post by Skaperen on 2019-08-27
is [this]("https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash") what you were reading for "read-only root"?

---

### Post by Skaperen on 2019-08-27
to make a *user* that has _read-only access_ to *all* files, the only way i can think of doing that is isolating that user in a _container_, and i'm not even sure you can put all host file systems in that container in read-only mode.

---

### Post by ralphclintellis on 2019-08-27
No.  It was a general linux forum.  A summary of the steps
[COLOR=#2f4f4f][FONT=century gothic]1. Create a group (roroot)[/FONT][/COLOR]
[COLOR=#2f4f4f][FONT=century gothic]2. Apply the group id to all directories.  (Not sure about this step - not sure what they mean)
3. Make the permissions for the group bits to be r--
4. create user account (rorootuser) and make it a member of roroot only.
5. Edit the /etc/passwd file, look for rorootuser and edit it to be: rorootuser R0:512:450:Root user R0:/home/rorootuser:/bin/bash
[/FONT][/COLOR]
I skipped step 2 - not sure I want to do that (nor do I understand how that would be done).
My basic question here is that I can not seem to create a user which then allows me to log in with it via su.  I have created a simple new user without the roroot group and I still can't log in with it.

---

### Post by ralphclintellis on 2019-08-27
So a regular user could see and read any file wherever they are on the system?

---

### Post by The Cog on 2019-08-27
> 2. Apply the group id to all directories. (Not sure about this step - not sure what they mean)
Ooh! I suspect that you would have to reinstall after that to get everything working again. Several system things check permissions and refuse to work if they think they have been tampered with. sudo for instance.
On top of which, that won't work anyway. Having read permission to a directory allows you to list the names of the contents, but not to read the files - that requires read access to the file. And if you change the group and permissions on every file, then you will definitely need to reinstall.

---

### Post by SeijiSensei on 2019-08-27
I still don't see the point of this. Replacing the root group with some other group would likely break things.

Can you give us a specific example of what you're trying to accomplish?  As an ordinary user, you only have write privileges in your home directory and in /tmp.  You will have read privileges across essentially the entire system except for root's home directory, /root.

Is this supposed to be a security enhancement?  Somehow *nix-based systems have operated securely for decades without this kind of manipulation.

---

### Post by ralphclintellis on 2019-08-27
I was looking for a safe way for non-administrators (non-root) to check things on the server.  (If authorized and necessary, they can sudo) It looks like a regular user would be good enough.  Thanks.

---

