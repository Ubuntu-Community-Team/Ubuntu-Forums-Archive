---
title: "Correct htaccess permission?"
date: 2007-01-23
forum: General Help
---

### Post by iluminate on 2007-01-23
Hi all,

I have a question regarding using correct permission on the root htaccess file.
Who should be the file owner? Root or www-data?
If it is www-data, is it  ok to set it to chomd 570 where group is "dev" and I belong to that group.
Or is it a big no no to have www-data as file owner?
Any help would be very much appreciated.

Cheers!

---

### Post by iluminate on 2007-01-23
Hmm....maybe 470 is better?

---

### Post by matthewstory on 2007-01-23
I strongly suggest that you don't use htaccess, and instead use the <Directory /var/www/> directive in the /etc/apache2/sites-available/default config file.  But if you insist on using htaccess, www-data needs to have read access, but should definitely not have write access.  Something like this:

chown root:www-data .htaccess
chmod 644 .htaccess

should do nicely.

I would almost certainly go with 644, or even 640 on this file.

---

### Post by matthewstory on 2007-01-23
even better would be:

chown root:root .htaccess
chmod 644 .htaccess

That way anyone can read it, but only root can alter it.

---

### Post by kosmic on 2007-01-23
> **matthewstory said:**
> even better would be:

chown root:root .htaccess
chmod 644 .htaccess

That way anyone can read it, but only root can alter it.

I think this is the most secure way you can configure your .htacess file

---

### Post by iluminate on 2007-01-23
Thank you guys for your tips!
Have changed now the permissions to 644!
The permissions on files is a little bit cryptic for me but I do understand (sort of) how it all works.
How about ordinary php files on webserver?
as is now I have www-data:dev where the permissions are 570 (group dev has full permission) and www-data has read and execute.
Ok? Or should www-data have just read?
What is the difference between execute and read? I mean to be able to read a file it has to be executed ? =)
Thanks!

---

### Post by matthewstory on 2007-01-26
For my webservers i use:

www-data:www-data

and 775 . . . 774 would work too.

Your umasks are a bit weird . . . no offense, it's just odd to see a umask where the owner has less permissions than the group.  Standard umasks are:

775
755
700
600
644
664

Those are the ones that i'm used to seeing . . . the difference between read and execute is that read allows one just to browse the contents of the file . . . whereas execute allows one to execute the script.  This gets a little tricky with webservers, as the proproccessor doesn't necissarily need permissions to execute the php script in order to process it.  Basically, you only want the execute bit set when it needs to be set, and then only for people that you want to be able to execute it.  Are you familiar with the numbering system?  I described it at great lengths in a previous post, which i would link to, but can't seem to find right now.  It's a good idea to have all the stuff web-accessable owned by www-data:www-data, it doesn't really matter if the last number is 4 because anyone on the web can read it anyway . . . unless of course you have a config file with a mysql password in it . . . in which case make it 770.  Hope this helps.

---

