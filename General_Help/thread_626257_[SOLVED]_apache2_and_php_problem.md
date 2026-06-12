---
title: "[SOLVED] apache2 and php problem ?????"
date: 2007-11-28
forum: General Help
---

### Post by myharshdesigner on 2007-11-28
i have changed the work folder to my **/home/username/work**

there are the list of this folder :-

> 
Index of /
[ICO]	Name	Last modified	Size	Description
[ ]	dbconn.php	28-Nov-2007 08:48 	344
[DIR]	gems/	28-Nov-2007 08:52 	-
[DIR]	images/	24-Nov-2007 07:55 	-
[ ]	imgview.php	25-Nov-2007 15:17 	703
[TXT]	index1.html	24-Nov-2007 07:59 	684
[ ]	index2.php	25-Nov-2007 15:17 	1.1K
[ ]	php1.php	26-Nov-2007 08:24 	20
[IMG]	small1.jpg	25-Nov-2007 15:17 	33K
[IMG]	small2.jpg	25-Nov-2007 15:17 	30K
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 80



now in php1.php file

i just only have [PHP]phpinfo()[/PHP]

this php1.php file working fine

but when i try to run index2.php

it shows me this :-

> 

Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Fatal error: Unknown: Failed opening required '/home/harsh/web/index2.php' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0




why pl help me

thanks

---

### Post by chippy99 on 2007-11-28
Without providing a listing of the contents of index2.php how can you expect anyone to help ?

---

### Post by myharshdesigner on 2007-11-29
here is index2.php code
```

<html>
<head>
<title>Index</title>
<script language="JavaScript">
function newWindow(url, height, width) 
{
	mywindow = "Mywindow";
 	window.open (url,mywindow,'height='+height+',width='+width+',scrollbars=2,resizable=0,menubar=0,toolbar=0,status=0,location=0,directories=0,left=150,top=200');
}
</script>

<style type="text/css">
a.link1:link 
{
    color: #000000;
    border-bottom: 1px; 
}

a.link1:visited 
{
    color: #FFFFFF;
    text-decoration: none;
}

a.link1:active 
{ 
    color: #FFFFFF;
    text-decoration: none;
}

a.link1:hover 
{
    color: #FFFFFF;
    text-decoration: none;
}
</style>
</head>

<body>
<table width="586" height="262" border="1">
  <tr>
    <td height="203" align="center">
	<A class="link1" HREF="javascript:newWindow('imgview.php?imgno=001',500,600);"><img src="small1.jpg" border="0" /></a>	</td>
    <td align="center">
	<A class="link1" HREF="javascript:newWindow('imgview.php?imgno=002',500,600);"><img src="small2.jpg" /></a>
	</td>
  </tr>
  <tr>
    <td height="51">&nbsp;</td>
    <td>&nbsp;</td>
  </tr>
</table>
</body>
</html>


```

---

### Post by scxtt on 2007-11-29
what's **ls -l /home/harsh/work** return?

you may be using 2 different directories, the error mentions: /home/harsh/web/ when dealing w/ index2.php (or you didn't mean to type work, you meant web - if that's the case, what's **ls -l /home/harsh/web** return?)

not to mention you're using straight html in a file you've named w/ a .php extension ... for phpinfo(), you should do something like:
[php]<?php phpinfo() ?>[/php]instead.

---

### Post by myharshdesigner on 2007-11-29
sorry my mistake it's not work it's web and its a folder.

> 
harsh@harsh-laptop:~/web$ ls -l /home/harsh/web
total 24
drwxrwx--- 2 harsh harsh 4096 2007-11-29 15:23 bill
drwxr-xr-x 6 harsh harsh 4096 2007-11-29 15:23 bill1
drwxrwx--- 2 harsh harsh 4096 2007-10-05 19:52 cal
drwxr-xr-x 2 harsh harsh 4096 2007-11-28 08:52 gems
drwxr-xr-x 2 harsh harsh 4096 2007-11-24 07:55 images
drwxr-xr-x 3 harsh harsh 4096 2007-11-29 15:23 untitled folder
harsh@harsh-laptop:~/web$ 



---

### Post by myharshdesigner on 2007-11-29
one more thing when i try

> 
htttp://localhost


```

Index of /
[ICO]	Name	Last modified	Size	Description
[DIR]	bill1/	07-Oct-2007 11:24 	-
[DIR]	gems/	28-Nov-2007 08:52 	-
[DIR]	images/	24-Nov-2007 07:55 	-
[DIR]	untitled folder/	29-Nov-2007 15:23 	-
Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at localhost Port 8

```

---

### Post by myharshdesigner on 2007-11-29
you can see the difference here some folder are not visible in localhost why ? i just copy and from windows folder to linux folder

---

### Post by scxtt on 2007-11-29
why don't i see index2.php in that ls -l?

that's what's referenced in the error code, where is that file?
```
Fatal error: Unknown: Failed opening required '[COLOR="Red"]/home/harsh/web/index2.php[/COLOR]' (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0
```

---

### Post by scxtt on 2007-11-29
> **myharshdesigner said:**
> you can see the difference here some folder are not visible in localhost why ? i just copy and from windows folder to linux folderyou can't see bill and cal because apache (the user/daemon) doesn't have permission to see them ...

i'm thinking that's the entirety of your problem.

---

### Post by myharshdesigner on 2007-11-29
i changed this :-

> 
DocumentRoot /var/www/
	
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>


to this


> 
DocumentRoot /home/harsh/web/
	
	<Directory /home/harsh/web/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>


---

### Post by myharshdesigner on 2007-11-29
any help ?

---

### Post by scxtt on 2007-11-29
here's why you can see bill1, but NOT bill:
```
drwxrwx[COLOR="Red"]---[/COLOR] 2 harsh harsh 4096 2007-11-29 15:23 bill
drwxr-x[COLOR="Green"]r-x[/COLOR] 6 harsh harsh 4096 2007-11-29 15:23 bill1
```

when apache serves up your index, it checks to see if it can read/write/execute files in /home/harsh/web ...

in the case of [COLOR="Red"]bill[/COLOR], "other" users (which apache is) can't READ or EXECUTE the bill directory - so it appears it's skipped ...
for [COLOR="Green"]bill1[/COLOR], it can read (i.e. do an **ls** on it) and execute (i.e. **cd** into it) - so you see it in the listing ...
```
d[COLOR="Red"]rwx[/COLOR][COLOR="Blue"]rwx[/COLOR][COLOR="Green"]---[/COLOR]

d=directory
[COLOR="Red"]rwx[/COLOR] = user perms (in your case, for harsh)
[COLOR="Blue"]rwx[/COLOR] = group perms (for your harsh group)
[COLOR="Green"]---[/COLOR] = other perms (anyone else who's not you)
```

---

### Post by myharshdesigner on 2007-11-29
ok how to change rwx mode of a file ?

---

### Post by myharshdesigner on 2007-11-29
thanks now its working

---

