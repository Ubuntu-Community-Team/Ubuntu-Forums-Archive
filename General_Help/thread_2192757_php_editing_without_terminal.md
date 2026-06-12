---
title: "php editing without terminal"
date: 2013-12-09
forum: General Help
---

### Post by smoothedatol412 on 2013-12-09
I have using ubuntu to write php files but I can only use the terminal  to have root access the pathway /var/www.
My question is, can there be a  better way to access this folder and its contents without always having  to have root
access in the terminal, so I might be able to use an IDE  to edit my source code... thank you.

---

### Post by dragonfly41 on 2013-12-09
I frequently find that I have placed files with root ownership in my document root. 
In my setup in ~/public_html.

I use Krusader as my two pane file manager and navigate to my file locations.

You can install by [COLOR=#0000ff]sudo apt-get install krusader[/COLOR]

When Krusader launches (in user mode) I go to Tools > Start Root Mode Krusader to have another instance of Krusader running with root permissions. 

Right click in either open pane allows new folders or files to be placed.

Right click on any file allows the file to be launched by say Geany, or Komodo edit (both favourite editors).  But you can setup your own association.

Now after you have edited any content in /var/www/ you may find that some content has root permissions.  
Apache expects this folder and sub-folders to be owned by www-data:www-data

So using Krusader I just navigate to /var/www/ 

Right click > Properties > Permissions > Ownership

and set /var/www/ permissions to www-data:www-data (remembering to tick for subfolders).

Sometimes I have to apply this to files at the lowest level.


There might be an easier workflow using commands in command terminal but I've now got used to applying Krusader and Geany or Krusader and Komodo Edit (free version).

---

### Post by Lars Noodén on 2013-12-09
If you are the only user of that machine, you can simply take ownership of the directory and you will get write access without adversely affecting the web server process' security.

```

sudo chown -R smoothedatol412 /var/www

```

If you are sharing that directory with others, then you have to use group permissions instead, which is almost as simple.   Then you can use any group *except* www-data or any other in use by the web server.  
 
In either case, /var/www should not be given to www-data.  That user and group is to provide an unprivileged account for the web server.  Giving write access defeats that.  The  important thing is that the web server (www-data) should not be able to write to the same files that it serves to the public, especially if they are scripts.  Think on the principle "write XOR execute".

---

### Post by dragonfly41 on 2013-12-09
I stand corrected. Now you've got me doing more research into proper use of www-data.

---

### Post by smoothedatol412 on 2013-12-09
Well like I said before, I have been playing around with PHP using the root account on my computer to access the folder. I know there is a better way to do this, I know I could just change the permissions of the folder but I dont not know if that was the best course.

---

### Post by atkinskev on 2013-12-09
It's horses for courses - as mentioned previously, if you're the only user of the machine, simply changing permissions on /var/www-data is fine. My personal preference is to make use of user directories instead - enable Apache's userdir module, create a public_html directory in your home folder and you can then access using 'http://localhost/~username/' If you do decide on this, be aware that Ubuntu, by default, disables execution of PHP scripts in user directories - to enable, take a look at the instructions here: [https://wiki.ubuntu.com/UserDirectoryPHP](https://wiki.ubuntu.com/UserDirectoryPHP)

---

