---
title: "development server permissions issue"
date: 2008-03-14
forum: General Help
---

### Post by ameseisch on 2008-03-14
I Installed LAMP with taskel on a fresh install of gusty

if I add any htm file to the var/www it shows up in a list when I go to localhost but if i try to access the file it says:

forbidden

You don't have permission to access .../index.htm on this server.

and if there is a .php file in there i don't even get the list just:

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/var/www/test site/index.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

can anyone help me figure out what is going wrong here? seems like some apache setting needs changed, but to be honest i can't understand why this doesn't come pre-configured to work. seems like others have not had this problem so I must be making some novice mistake.

---

### Post by ayoli on 2008-03-14
If it's only for local use you can do 
```
sudo chmod -R a+rwx /var/www
```
Otherwise, create apache conf for needed sites that point to a directory where you can write and everybody can read.

---

### Post by ameseisch on 2008-03-14
i also have /home/~user/public_html setup to be accessed if i go to localhost/~user

the same problem happens there too.

so would i just 

sudo chmod -R a+rwx /home/~user/public_html

??

---

### Post by ameseisch on 2008-03-14
okay did the chmod on my public_html directory, and that worked, but folders within public_html are still not accessible

so lets say i want to have a list of sites each stored in separate folders within public_html how would i change permissions for all files contained in public_html?

All I am trying to do is set up a development server. I feel like this should have been a lot easier to do.

---

### Post by ayoli on 2008-03-14
> **ameseisch said:**
> okay did the chmod on my public_html directory, and that worked, but folders within public_html are still not accessible

so lets say i want to have a list of sites each stored in separate folders within public_html how would i change permissions for all files contained in public_html?

All I am trying to do is set up a development server. I feel like this should have been a lot easier to do.

for your user public_html try this:
```
sudo a2enmod userdir
```
and restart apache :
```
sudo /etc/init.d/apache2 restart
```

---

### Post by ameseisch on 2008-03-14
i had already enabled the userdir mod from following a tutorial on setting up LAMP

and what you gave me at first got me to the point that now if i put the entire site into public_html it works fine. So, public_html/index.php works.

but if I had something like

public_html/site1/

and 

public_html/site2/

the contents of those folders aren't accessible. i assume I could do your chmod method on each folder within public_html but is there a way to change permissions on all files and folders contained in public_html/ all at once and permanently?

basically what I m going for is being able to save a PHP file and test it without having to use FTP, for all i know i could be barking up the wrong tree entirely but from everything I have been seeing on the boards this is path I want to be on, right?

---

### Post by ameseisch on 2008-03-14
Solved the problem

probably would have been able to do this with the terminal too, but i don't really understand the chmod thing yet. 

with public_html or any folders in it you can right click and go to properties and change permissions in there. i changed it to "read and write" and now it works!

thanks for the help.

a note to anyone who has power to do so and might read this post. There should be a tutorial or some part in the LAMP tutorial that informs people of this problem, and how to solve it. would have saved me a couple hours.

so basically I am saying:
[https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP)
could use some improvement.

---

### Post by ayoli on 2008-03-14
All guides are incomplete it is very difficult to cover all problems.
offtopic : for your knowledge about chmod
a file folder can be (or not) readable/writeable/executable by owner (user) group or others
```
chmod -R u+rwx /path/to/change/perm
```
means change recucursively (-R) permisions on /path/to/change/perm and make it readable (r) /writeable (w) /executable (x) by owner (or user : u)
```
chmod -R u-rwx /path/to/change/perm
``` is the opposite make the path _not_ readable/writeable/executable.
the char before the + or - sign can be : u for user, g for group, o for others or a for all (user,group and other)
the permissions rwx can be set separately, ex: if you want to make a file writable for all you can do only:
```
chmod a+w /path/to/file
```
This syntax is pretty simple and easier than octal mode IMO
for ex th previous chmod to make a file writable for all in octal would be
```
chmod 666 /path/to/file
```
cheers.

---

