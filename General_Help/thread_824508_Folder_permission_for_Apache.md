---
title: "Folder permission for Apache"
date: 2008-06-10
forum: General Help
---

### Post by Chosen320 on 2008-06-10
Hi there,

I've recently installed apache, php5 and mysql in ubuntu on my laptop for development purposes.

For my first project I decided to take a look at the silverstripe CMS. 
I downloaded it put it in the www folder that I created for it and am now trying to install it. These are the remaining file access errors I'm getting before installation will continue.


> Is the .htaccess file writeable?	User 'www-data' needs to be able to write to this file:
/home/gareth/www/Insight/.htaccess
Is the mysite/ folder writeable?	User 'www-data' needs to be able to write to this file:
/home/gareth/www/Insight/mysite
Is the tutorial/ folder writeable?	User 'www-data' needs to be able to write to this file:
/home/gareth/www/Insight/tutorial
Is the assets/ folder writeable?	User 'www-data' needs to be able to write to this file:
/home/gareth/www/Insight/assets

How do I give write permission to this user and how do I create the "www-data" user if it does not exist already?

I'm new to linux so please don't assume I know where to find any files I might need to edit.

Thanks

Gareth

---

### Post by neilneil2000 on 2008-06-10
The adduser command will allow you to add users to your system

And to change permissions use chmod

i.e.

sudo chmod -R www-data /etc/<THEFOLDER>

---

### Post by Chosen320 on 2008-06-10
Thanks,

Another quetion though, how do I tell chmod to only grant access to that specific user and not to all users which is the default action if I understand the man page on chmod correctly. Unforunately I was unable from the man page able to answer my own question :)

---

### Post by Chosen320 on 2008-06-10
Ok... so I typed in "sudo chmod -R -u /home/gareth/www/Insight/.htaccess"

And now I can't access the page at all.

How do I go about reversing this. I assumed from the question that I asked, that this would have given write permission to the file. It seems I'm now worse off. Apache no longer has permission to access the folder at all, never mind silverstrip CMS having write access to the .htaccess file.

Please, as I stated I am a linux newbie. I've checked out the man page on chmod and it is mostly greek to me at this point.

Regards,

Gareth

---

### Post by neilneil2000 on 2008-06-11
Don't worry, I know exactly how cryptic the mad pages can be!

this command will give all permissions to everyone...not very secure but it will work!

sudo chmod -R 777 <FOLDER NAME>

the way the permissions work is by setting read, write and execute bits.  These are trios of bits which can be represented in Octal notation.

if you run ls -l you will see a list of files/directories and on the left will say something like

-rwxrwxrwx (some of the characters may be dashes, this means permissions denied.)

The first rwx refers to the owner user
The second rwx refers to the owner group
The third rwx refers to other users

The owner user and group are shown to the right of the rwx string

for example the following 

-rw-rw---- neil neilgroup

means that neil and all other users in neilgroup have read and write access and everyone else has no permissions

-rwxrw-rw- neil neilgroup

means that neil has read write and execute permissions and everyone else has read and write permissions.

The Octal works by placing a binary one where a letter exists and a binary ero for every dash

Therefore to get

-rw-rw---- neil neilgroup

you would use chmod 660

for 

-rwx------ neil neilgroup

you would use chmod 700

These pages are quite useful but let me know if you have any more questions

[http://en.wikipedia.org/wiki/File_system_permissions#Additional_Permissions](http://en.wikipedia.org/wiki/File_system_permissions#Additional_Permissions)
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

