---
title: "Permissions that forbid standard user viewing content of specific files?"
date: 2015-07-02
forum: General Help
---

### Post by peter1897 on 2015-07-02
What permissions i can use to forbid standard users viewing the content of files i don't want them to see? For example, the permissions for the files /etc/group and /etc/passwd are 644 (-rw-r--r--). They are owned by the root user and root group but the "read" permission for "others" gives the right to standard users to view the content of the files. Can i set the permission for "others" to 0 (no permissions) for these files?

I know in some cases is not possible to set the permission for "others" to 0 (no permission), for example, in the directory /var/www, because the apache server, need to read and execute the files in this directory as "others", but this also give the permission to standard users to view the files in this directory.

---

### Post by bab1 on 2015-07-02
> **peter1897 said:**
> What permissions i can use to forbid standard users viewing the content of files i don't want them to see? For example, the permissions for the files /etc/group and /etc/passwd are 644 (-rw-r--r--). They are owned by the root user and root group but the "read" permission for "others" gives the right to standard users to view the content of the files. Can i set the permission for "others" to 0 (no permissions) for these files?

I know in some cases is not possible to set the permission for "others" to 0 (no permission), for example, in the directory /var/www, because the apache server, need to read and execute the files in this directory as "others", but this also give the permission to standard users to view the files in this directory.

You don't want to change the permissions on those two files.  For the very reason that you stated for Apache.  Those files are read by system users.  The files are used by the system for its own needs.  In fact,  when you list the file ownership,  the system (not root) uses those very files.  Your "standard" user I assume is a mortal user (human).  Both the system users and mortal users can be part of the ***others*** group and you should allow them to read the files for the system to work correctly.

You need to allow for all others to be able to read the information without the ability to write to the file.  That is why it is owned by root.  What security concerns do you have regarding /etc/passwd or /etc/group?

---

### Post by peter1897 on 2015-07-02
These two files were just examples. I was just wondering if it is possible to forbid users without admin rights to view some files.
So, the permission for "others" should never be 0 (no permission)?

---

### Post by bab1 on 2015-07-02
> **peter1897 said:**
> These two files were just examples. I was just wondering if it is possible to forbid users without admin rights to view some files.

You can forbid any grouping you want, as long you understand the restrictions.  You have three groups of users ownership.  They are: the creator (owner), the group (users in that group) and all others (the world).  In essence you restrict users by the group they are in.

There is another way to include or exclude users permissions.  You can use Linux ACL's.  It will get messy and you should understand the ramifications of using ACL's before you use them.  You can easily create security risks.  I would not try and circumvent any Apache settings by using ACL's.  Especially if you are trying to implement Wordpress, Joomla or Druple.

---

### Post by SeijiSensei on 2015-07-02
If you look in /etc, you'll see another file with 600 permissions, /etc/shadow.  That's where the actual hashes of the passwords are stored, and it is only readable by root and group "shadow."  

You can remove permissions for ordinary users by changing the values in the third "octet" of the permission mask.  A file with 600 permissions is only readable and writable by its owner.  You can also use symbolic permissions in the chmod command.  For instance, the command "chmod o-rwx /path/to/some/file" turns off read, write, and execute privileges for "**o**thers."

---

### Post by peter1897 on 2015-07-02
Yes, but my point is that you can't turn off permissions for "others" for files that are used by servers, like apache, and because of that users that are not owners or don't belong to group that have read rights for the files, will still be able to view the files.

---

### Post by Lars Noodén on 2015-07-02
> **peter1897 said:**
> Yes, but my point is that you can't turn off permissions for "others" for files that are used by servers, like apache, and because of that users that are not owners or don't belong to group that have read rights for the files, will still be able to view the files.

You could do so, if you really want to do a lot of extra planning and work with permissions.  For the web server example, Apache is in the group www-data, so if you make the directory 750 and the files 640 for the user:group root:www-data.  Then if you want other groups, such as webmasters to be able to edit those same files, you'd use ACLs to add write permission for just their group.  But since, unless you have the web site behind a password or more, the data is public any way.

---

### Post by SeijiSensei on 2015-07-02
> **peter1897 said:**
> Yes, but my point is that you can't turn off permissions for "others" for files that are used by servers, like apache, and because of that users that are not owners or don't belong to group that have read rights for the files, will still be able to view the files.

Nor should you be able to without a lot of effort and knowledge.  Permissions are carefully structured to ensure that applications work properly.  And you could still set /var/www/html so it is readable and writable only by the www-data user and not by other users.  
```

cd /var/www
sudo chown www-data:www-data html -R
sudo chmod 750 html 
sudo chmod 640 html/*

```
Apache will still function properly, but only the www-data user and members of the www-data group can see the files.

---

### Post by peter1897 on 2015-07-02
Changing the ownership of html folder to www-data user and group will not work for me because i need some users to have read and write access to the folder. I wanted to forbid the access of these users to some of the files in the folder but i guess there is no simple solution for this.

---

### Post by Lars Noodén on 2015-07-02
> **peter1897 said:**
> Changing the ownership of html folder to www-data user and group will not work for me because i need some users to have read and write access to the folder. I wanted to forbid the access of these users to some of the files in the folder but i guess there is no simple solution for this.

No simple solution but you could use ACLs to allow the group www-data read access while allowing some other group(s) write access.  

[https://help.ubuntu.com/community/FilePermissionsACLs](https://help.ubuntu.com/community/FilePermissionsACLs)

---

### Post by efflandt on 2015-07-02
If you are trying to limit local access to something web related, back in the days when Netscape was king of web browsers and Mosaic beta had not been reborn as Internet Explorer yet, my ISP had apache web space on Sun computers. Writing CGI scripts for that is what got me into Linux because it was much easier to compose and test scripts in Linux (with some symlinks to match paths in SunOS) and simply upload them, than to have to convert paths, line endings, etc. from Windows to Unix. There was no css or anything then, if you wanted something specifically formatted you would use .pdf instead of .html.

If I had a CGI script to store data that I wanted to be secure, not alterable by anyone else, or in some cases not even readable, I used an suid C wrapper as the CGI to run each specific script only (with as little as 700 permission) as me, and store the data in a file owned by me with as little as 600 permission. So I could access that from the shell, but no one else could. Although, more often for guestbook or other scripts, I gave the data file 644 permission with a link to it from the website. But that may depend how apache is configured and what it allows you to do.

---

### Post by SeijiSensei on 2015-07-03
Why don't you assign your Apache users to separate directories only they can write to, but readable by group www-data?

```

cd /var/www/html
sudo mkdir user1
sudo chown user1:www-data user1
sudo chmod 750 user1

```
If everyone is placing files in the same directory, then yes, it will be very difficult to limit one user from reading another's files. Still if these are web pages, everyone can read them from a browser, no?

---

