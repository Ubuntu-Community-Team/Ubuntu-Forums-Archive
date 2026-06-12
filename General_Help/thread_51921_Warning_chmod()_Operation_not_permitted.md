---
title: "Warning: chmod(): Operation not permitted"
date: 2005-07-25
forum: General Help
---

### Post by higgins on 2005-07-25
Hi there. I have just installed apache php and mysql. I have downloaded gallery 2 and installed it under /var/www.

The install went ok however whenever I view my gallery page I get the following:

Warning: chmod(): Operation not permitted

I am told the following after posting on the gallery forums:

> your php says we are not allowed to use chmod. but you don't have safe mode on, you use have disable_function or other exec stuff. all i see is the compile option --with-exec-dir=/usr/lib/php4/libexec', maybe that's involved.

as long as you can't chmod with php, G2 won't work on your box. that's all i can say.

My question is, how do i configure my ubuntu apache 2 and php setup to allow this?

---

### Post by evilghost on 2005-07-25
Chances are the code is trying to chmod 666 (ick) or just create an httpd/apache writable directory.  You may be able to circumvent that by using bash/terminal to manually chmod the temp/images directory to httpd writable so it can generate the thumbnails.  I bet the PHP is trying to do that for you.

---

### Post by higgins on 2005-07-25
Oh OK.

here is the line of code that gives the chmod error:

[PHP]chmod($tempFile, $this->_filePerms);[/PHP]

Is it the apache temp directory? If so where is this?

---

### Post by majikstreet on 2005-07-25
> **higgins]Oh OK.

here is the line of code that gives the chmod error:

[PHP]chmod($tempFile, $this->_filePerms) said:**
> 

Is it the apache temp directory? If so where is this?
 Somewhere in the beginning of that file or in another file that is included, $tempFile is defined.... It is a variable and will have to be defined somewhere. Not sure where tho.

---

### Post by evilghost on 2005-07-25
You could always:

echo($tempFile);

To see what the variable is set to and comment out the chmod line.

Example:

echo($tempFile);
//chmod($tempFile, $this->_filePerms);

If $tempFile is always in the same directory, you could chmod the directory to apache/httpd writable and leave that code commented out.  Sad the dev's forum couldn't help you with that.

---

### Post by higgins on 2005-07-25
Hey there. Thanks for the response.

It is now outputting

[PHP] /home/tim/G/albums/sessions/c729b4226a4f3d09d21c5536fcc4850d2dOUkn[/PHP]

How do I chmod the directory to apache/httpd writable? It already has chmod 777, but I'm not sure if that is for apache or myself "root usr"?

---

### Post by evilghost on 2005-07-25
If it's 777, just leave that chmod command commented out.  Apache/httpd should be able to write there.  Also, if in the app in the "config" or whatever, if you can define "Temp" as "/tmp" that may work even better.

---

### Post by higgins on 2005-07-25
evilghost, it is now working perfectly. Thank you so much for your help.  :smile:

---

### Post by evilghost on 2005-07-25
No problem, glad I could help.  Shame the dev folks took such a "Your PHP is the issue" even though they had some glaring code inefficiencies in there. :)

---

