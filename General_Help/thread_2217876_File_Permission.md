---
title: "File Permission"
date: 2014-04-18
forum: General Help
---

### Post by Dz_NiT0 on 2014-04-18
Hello, 

I Coded a file which create new file on the same folder running on localhost ( the php file)

but the probleme that there is no created file on the folder ! i tried with permission but with no result ..

give me you ideals 

:popcorn:

---

### Post by Dz_NiT0 on 2014-04-18
up up up

---

### Post by QIII on 2014-04-18
Please wait 24 hours before bumping a thread.

When you do so, please be somewhat less insistent.

This is a forum populated by volunteers.

---

### Post by nothingspecial on 2014-04-18
> **Dz_NiT0 said:**
> up up up
down down down

---

### Post by davea42 on 2014-04-18
Sorry, but your comment is not very specific.  You created a script?  (php script?) which you put somewhere (where?) and attempt to execute the php how?

---

### Post by Dz_NiT0 on 2014-04-18
> **davea42 said:**
> Sorry, but your comment is not very specific.  You created a script?  (php script?) which you put somewhere (where?) and attempt to execute the php how?

well , 

I have a php script which content the "fopen;fwrite" functions but when i run it on localhost there is no created file which is supposed to be :/

---

### Post by Iowan on 2014-04-18
Perhaps you could post the code...

---

### Post by Dz_NiT0 on 2014-04-18
the php script :
[PHP]
<?php

$content = "some text here";
$fp = fopen("myText.txt","wb");
fwrite($fp,$content);
fclose($fp);

?>[/PHP]

when i run it on the localhost it's supposed to create a file named "myText.txt" in the same patch , but there is not

PS : i use ubuntu 12.04

---

### Post by Dz_NiT0 on 2014-04-19
i tried to change the patch permission and nothing happend the sema with the file :/

---

### Post by SeijiSensei on 2014-04-19
If you're running the script through localhost, I assume you are using a web server like Apache.

The server runs with the permissions of the user www-data, which has no permission to write files anywhere outside /tmp.

Enter a full file path in fopen(), like "/tmp/myTest.txt" and see if that works.  /tmp can be written to by any user.  If that works, then you need to decide where you want these files stored and grant write permissions to the www-data to that directory.

Also, you should always check the contents of /var/log/apache2/error.log to see if something went wrong.

---

### Post by Dz_NiT0 on 2014-04-19
Thanx Man

---

