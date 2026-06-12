---
title: "Simple ping test webpage?"
date: 2008-02-26
forum: General Help
---

### Post by mikey12345 on 2008-02-26
Hi,

Anyone know a free linux tool that...

Displays a webpage. The webpage contains the servers from a list i can type that shows if they are on or offline. Like a simple red offline and green online.

So simple ping test but easy to view at a glance.

All the tools i can find online seem to be too complicated or not free.


Any ideas?

Thanks.

---

### Post by kesman on 2008-02-26
Why don't you just ping the site from your computer?
```

ping www.google.com

```
in terminal, and if there's response, then the server is online.

---

### Post by mikey12345 on 2008-02-26
It's for work. We've got like 300 servers.
We want to see at a glance what is offline and what is on.

We have more sophisticated monitoring but there is a need for the easy at a glance stuff.

Thanks.

---

### Post by negge on 2008-02-26
I don't know any existing ones but it would be fairly easy to do a PHP script that does what you want (as long as the list isn't awfully long 'cause it would take forever to execute even if you choose a short timeout like 5 seconds).

---

### Post by kesman on 2008-02-26
Put at "test.gif" which is a little green balloon into each server's public html -directory, and create a php file like this:

```

<?php
$serverlist = array(ip1,ip2,ip3...,ip300);
$n=0;
foreach($serverlist) {
   $server=$serverlist($n);
   if(include("<img src='$server/test.gif'>")) {
     include("<img src='$server/test.gif'>");
   }
   else {
   include("fail.gif"); //fail.gif is a red balloon in the same directory as this php file
  }
$n++;
}
?>

```

This is a bit rough and may have typos and errors since it's a long time from my last php-skripting session but you get the point :)

---

### Post by kesman on 2008-02-26
also this
[http://us.php.net/manual/fi/function.maxdb-ping.php](http://us.php.net/manual/fi/function.maxdb-ping.php)
could be an useful function to use in such script =D

---

### Post by negge on 2008-02-26
About the previous script:

How long does PHP wait before the include() function returns false? It could be 30 seconds or so, and then the script would be useless. I was thinking more of using fsockopen() with a timeout time of 2 seconds or so, if the server is fully functioning it should response faster than that.

---

### Post by mikey12345 on 2008-02-26
Thanks  -looks about what I am after. I'm not much of a scripter though - does anyone know of a free program?

---

### Post by jusmurph on 2008-03-10
I'm looking for something similar that will email me and post to a log if something fails.

---

### Post by atroph on 2008-07-02
Try looking at Groundwork Open Source, or Nagios. 

We used to run it when I worked for a WISP. We could see at a glance which stations had problems.

---

