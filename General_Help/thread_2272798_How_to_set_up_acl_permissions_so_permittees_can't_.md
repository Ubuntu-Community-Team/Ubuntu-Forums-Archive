---
title: "How to set up acl permissions so permittees can't see permitter's directory"
date: 2015-04-08
forum: General Help
---

### Post by Ralph L on 2015-04-08
I am trying to set up a simple way for a few people to share a computer, permit each other to access some files using acls, but keep the titles in the directory structure private.  As of now the only way I can allow a user, permitted to a certain file/folder, to find that file/folder is to give the permittee read and execute access to every folder is the chain leading to that file.  This is undesirable as it allows the permittee access to information he should not have.  For example, if I want to permit a file to Sam, which is in a sub-folder of a folder titled "Lawsuit of John against Jim", I would have to give Sam read and execute permission to "Lawsuit of John against Jim", when Sam should not even know that such a lawsuit exists.
I tried setting up a folder near the root of the director named "Files Permitted to Sam", and putting symbolic links in it to files/folders further down in the directory that Sam is permitted to.  However, this does help, as the symbolic link won't allow access to the permitted files/folders unless Sam has execute access to all folders in the chain.  I have thought about using hard links, but these are awkward to set up (no gui that I know of) and there may be other adverse consequences.
Does anybody know of a way to achieve my privacy goals using acls and whatever....

---

### Post by SeijiSensei on 2015-04-09
There are "ACLs" in Linux that permit more fine-grained control over access to files and directories than the basic numeric permissions.  I don't use ACLs myself, but this looks to be a decent [walkthrough]("http://xmodulo.com/configure-access-control-lists-acls-linux.html") using Ubuntu Server.  However Ubuntu versions 14.04LTS and later have a bug which "makes ACL usage ineffective" according to the [ACL documentation]("https://help.ubuntu.com/community/FilePermissionsACLs").

> Note: As of Ubuntu 14.04 coreutils 8.21~8.23 a 3+ years old bug makes ACL usage ineffective : [http://debbugs.gnu.org/cgi/bugreport.cgi?bug=8527](http://debbugs.gnu.org/cgi/bugreport.cgi?bug=8527)

Quick searching didn't uncover a similar warning about ACL usage in CentOS, so you could try that, or use Ubuntu Server 12.04LTS.

Since I haven't used ACLs, I can't tell you if they would solve your particular problem.  A quick glance suggests they might, but they also look rather complex to set up.  I don't know if there are GUI tools that work with ACLs.  Other people here might chime in.

I tried various combinations of (r)ead and e(x)ecute permissions on a test directory and could not find one that let a user read a file in a directory but not list the directory's contents.  I thought that excluding (x) on the directory, but granting ownership of a file and (r) privileges to a user would let her read the file but not list the directory.  Didn't work for me.  Granting (r) and not (x) on the directory generates a permission-denied error on the file but still lists it in the directory's content.  Apparently *nix permissions assume you must be able to list a directory's contents in order to read one of its files.

---

### Post by bab1 on 2015-04-09
> **Ralph L said:**
> I am trying to set up a simple way for a few people to share a computer, permit each other to access some files using acls, but keep the titles in the directory structure private.  As of now the only way I can allow a user, permitted to a certain file/folder, to find that file/folder is to give the permittee read and execute access to every folder is the chain leading to that file.  This is undesirable as it allows the permittee access to information he should not have.  For example, if I want to permit a file to Sam, which is in a sub-folder of a folder titled "Lawsuit of John against Jim", I would have to give Sam read and execute permission to "Lawsuit of John against Jim", when Sam should not even know that such a lawsuit exists.

Directory and file permissions are for access authorization not awareness prevention.  I understand you situation.  I'm a believer in a little more directory and file name obscurity than what you have. 
> 

I tried setting up a folder near the root of the director named "Files Permitted to Sam", and putting symbolic links in it to files/folders further down in the directory that Sam is permitted to.  However, this does help, as the symbolic link won't allow access to the permitted files/folders unless Sam has execute access to all folders in the chain.  I have thought about using hard links, but these are awkward to set up (no gui that I know of) and there may be other adverse consequences.
Does anybody know of a way to achieve my privacy goals using acls and whatever....
ACL's are nothing more or less than a more precise way of setting directory and file permissions.  From the ACL man pages```
CORRESPONDENCE BETWEEN ACL ENTRIES AND FILE PERMISSION BITS
     The permissions defined by ACLs are a superset of the permissions specified by the file
     permission bits.
```
The execute bit set on a directory allows you to descend into (traverse) the directory so it must be set for a user to open anything in that directory or pass into another directory.  Read permission for the directory allows the user to list the files only for that directory.  ACL's don't change any of this behavior.  What the ACL does allow is for you to set the permissions for an individual user.

I never nest less secure files in a more secure directory.  Flatten the directory hierarchy and provide the Sam user access to what he needs.  Then allow the more secure users access to what the user Sam has plus a directory of their own.  

[COLOR="#0000FF"]Edit:  Use group ownership rather than the user ownership with multiple user access.[/COLOR]

---

### Post by Ralph L on 2015-04-09
SeijiSensei
Thanks a lot for responding.  I was just looking to see if anybody had any better ideas on how to use permissions and acls than I do.  I have read quite a bit about them in [http://users.suse.com/~agruen/acl/linux-acls/online/](http://users.suse.com/~agruen/acl/linux-acls/online/) .  
My current thought is to, in the permitter's account, create a folder, at the highest level I can, for each user that the permitter wants to share with.  Folders would be named something like "John's Stuff Shared with Sam", and "John's Stuff Shared with Joe".  Then John would make copies of any items he wants to share, permitted appropriately with acls, and put them into the appropriate folder.  To allow Sam to access this folder, but not read the directory, John would give Sam (using acls) execute permission on higher level folders (hopefully only one or two), and read and execute permission to folder "John's Stuff Shared with Sam".  Now Sam could use the Terminal to set up a symbolic link to "John's Stuff Shared with Sam".  While doing this Sam could not list the contents of the higher level folder, but he could make a symbolic link as follows: (ln -s /media/Shared_Data/documents_john/"John's Stuff Shared with Sam").  Note: In my set up all user data is on a separate partition (Shared_Data) and John's documents are in (Shared_Data/documents_john).  John would have to tell Sam exactly the path to "John's Stuff Shared with Sam", because Sam could not do an "ls" on Shared_Data or documents_john.
The thing I don't like about this arrangement is that John is forced to make a copy of anything he wants to share in any other directory and put it in "John's Stuff Shared with Sam".  Now he has to keep track of multiple copies of the same thing--a nuisance.  It would have been much nicer if John could have just made a symbolic link to anything he wanted to share and put the symbolic link in "John's Stuff Shared with Sam".  But I couldn't make this work.

---

### Post by Ralph L on 2015-04-22
I am solving this by giving Others "execute" permission, but not read nor write permission.  I did this by setting umask to 026 in /etc/logindefs.  This lets everybody navigate everybody else's entire directory, but because they cannot see any folder/file names (no read permission), it is hard for somebody to spy on somebody else.  And because the only folder/files that are specifically permitted to other users can be accessed by other users, the rest of the folder/files should be safe from prying eyes.  Each user will also need to set up, at the lowest directory level possible, several folders to be shared with each other user.  In this, users will put symbolic links, with acl permission, to the folders/files they wish to share.  I am not completely happy with this use of permissions and acls, but unless I have missed something, I think it should work.
I put my notes in an attachment--maybe of some use to somebody.

---

