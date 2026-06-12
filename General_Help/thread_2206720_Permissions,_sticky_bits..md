---
title: "Permissions, sticky bits."
date: 2014-02-20
forum: General Help
---

### Post by Drenriza on 2014-02-20
I am wondering what the sticky bits are being used for in the current LTS version of Ubuntu.

From what i can tell the sticky bit is used for two things.
[LIST=1]
[*]Raise user permissions to execute a script with the permissions of the owner of the script.
[LIST=1]
[*]Is it the SUID that is set here?
[/LIST]

[*]Prevent users which is member of the same group, with delete permissions on group level from deleting eachothers files and or folders.
Also from what i remember it is the write permission that allows a user to delete a file or folder.
[LIST=1]
[*]From what i can tell the SGID needs to be set here on the parent folder, and then all sub folders will have this effect?
[/LIST]
[/LIST]
If i'am wrong please let me know, since i'am trying to understand how these features work.[B]

Questions
[/B]If you set the sticky bit for others, then it gets indicated with a capital T, what does this mean?

Anyone who has some good resources(examples) to how the sticky bits are being used, to either raise permissions and or prevent deletion from others then the creator and the root user.
I've been around wikipedia and other resources, but either i find material that is to old and outdated. Or material that doesnt show examples but just theori.

Thanks on advance.
Kind regards.

---

### Post by Impavidus on 2014-02-20
Usually everyone with write access in a directory can delete files and subdirectories there. If there is for example a file owned by root in my home directory, I can't write to the file, but I can delete it, simply because I can write to the directory. The sticky bit in the directory can prevent this and only allow deleting files by the owners of those files and by root. Have a look at the **/tmp** directory:```
$ ls -ld /tmp
drwxrwxrwt 14 root root 24576 feb 20 14:30 /tmp
```It has write permissions for everyone, but has a sticky bit too. Therefore every user on my system can create files in /tmp, but can only delete files owned by himself. The sticky bit has no longer any meaning when set on ordinary files instead of directories.

The setUID and setGID bits on files are a different thing. They cause the files to be executed as the user or group who owns the executable, instead of the user and group of the person invoking the executable. For example, the tool **passwd** has the setUID bit set and is owned by root:```
$ ls -l /usr/bin/passwd
-rwsr-xr-x 1 root root 41284 sep 12  2012 /usr/bin/passwd
```This allows the passwd program to modify the /etc/shadow file where the password is stored, which only has write permissions for root, so that people cannot modify other user's passwords. passwd has been designed to only allow changing your own password, unless it is used by root.
An example of a setGID program is **kobodl**:```
$ls -l /usr/games/kobodl
-rwxr-sr-x 1 root games 472032 nov 24  2011 /usr/games/kobodl
```By setting the group to games, this little game has permission to modify the score file, something the ordinary user cannot do to prevent cheating. It could have done so too by being setUID root, but that would be less secure as a security hole in a simple game as this would give access to the entire system. This way, a security hole in kobodl can at most give full access to directories in the games group. For security reasons, setUID and setGID bits only work on binary executables, not on scripts.

The setGID bit on directories causes any new files and directories created in them to inherit the group of the directory, and any subdirectories will inherit the setGID bit. For example, on my system some directories in **/usr/local/share** have this bit set by default:```
$ ls -ld /usr/local/share/texmf
drwxrwsr-x 7 root staff 4096 aug 23 11:43 /usr/local/share/texmf
```This means that any user in the staff group, instead of just root, can install, update or uninstall latex packages, even if they were previously installed by someone else. I don't really need this, as I am the only user om my system (and haven't even added myself to the staff group), but on big systems it's useful to grand extra permissions for maintenance of specific subsystems to groups of people other than those with root access.

On Linux, the setUID bit has no meaning on directories.

---

