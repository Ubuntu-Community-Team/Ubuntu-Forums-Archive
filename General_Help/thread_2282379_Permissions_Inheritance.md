---
title: "Permissions Inheritance"
date: 2015-06-13
forum: General Help
---

### Post by Adam_Kleiner on 2015-06-13
So I've searched all over for this but all the results I get seem to be irrelevant. So I have all home directory permissions on my server set to 600. However, I've noticed that all files I create within my home directory are created as 644. Do I still need to chmod files that I do not want my users looking through (even though they're contained in a protected directory), or would their attempts be blocked anyway since they are contained within a folder set to 600? I know that chmodding a folder as such does block unauthorized users from LISTING the contents, but let's assume they know the exact path to a file. Still protected?

---

### Post by bab1 on 2015-06-13
> **Adam_Kleiner said:**
> ... I have all home directory permissions on my server set to 600.

I'm not sure what you intend to achieve with these permissions.  It appears that you are accessing the this home directory as root.  The user can't list the contents or traverse (descend into) the directory.  You have effectively blocked all users other than root.  And to what end.  If you are using a Debian distro It doesn't matter if you have 700 or even 770 permissions, no other user but you has the permissions to see or traverse your home directory.  I would assume that other Linux distros are similar.
> 
... I've noticed that all files I create within my home directory are created as 644. 

The permissions on all newly created files are set by umask.  A umask of 022 will result in files of 644 and a umask of 002 will result files with 664 permissions,  These umask settings also result in the default directory permissions of 755 or 775.
> 
Do I still need to chmod files that I do not want my users looking through (even though they're contained in a protected directory), or would their attempts be blocked anyway since they are contained within a folder set to 600? 

If you have blocked access to the directory then whatever is inside is not available no matter what the permissions on that specific file is.
> 
I know that chmodding a folder as such does block unauthorized users from LISTING the contents, but let's assume they know the exact path to a file. Still protected?
It should block them from listing anything lower than the root of the home directory. To allow the user access to their home directory you should use 700 or 770 rather than 600.

---

### Post by yetimon_64 on 2015-06-13
File and directory permissions are set at log in by the default umask value of 0022. This value is what is automatically setting the 0644 file permissions you are seeing (note all files are created WITHOUT an execute bit, folders are auto created as 0755 with an 0022 umask value).

To create a system where your files are only writeable to you, readonly for your group and totally inaccessible to others, use a umask value of 0027. That way only you can write to them, any people you add to the group with your name can only read them, and no one else can even see them.

This value (0027) would be the minimum umask to do the job for your use case. The umask value needed to set all files to 0600 would be "0077", but then anyone added to your personal group would also be excluded from even accessing the files. Adding other users to your group allows finer access controls than going the full 0077 umask value.

To do so only for your profile and not affect umask values for other users alter your ~/.profile file with gedit.

```
gedit ~/.profile
```

Look near the top of the file for the line
> #umask 0022

and change it to 
> ```
umask 0027
```

(edit: save the file) then log out of your desktop and log back in again to activate the ~/.profile changes.

Try creating a new folder and files etc and check the permissions. Either 0027 or 0077 will do what you want but the 0027 is a bit more flexible as it allows you to add others to your group for access. NO one else by default or without a sudo password can add themselves to your group, as it is an administrative task only. 0027 should work as well as 0077.

Folders and files created with umask 0027 will set permissions of 0750 and files created as 0640.
Folders and files created with umask 0077 will set permissions of 0700 and files created as 0600.

---

