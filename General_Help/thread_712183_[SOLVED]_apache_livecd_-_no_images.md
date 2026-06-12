---
title: "[SOLVED] apache livecd - no images"
date: 2008-03-01
forum: General Help
---

### Post by depele on 2008-03-01
I installed apache on a livecd. 
I have installed a web-site on the live cd. 
But when I try to reach the webpage, it will not show me images.
(the webpage is the homepage on the livecd)

I also did an install of joomla cms on the live cd. 
Joomla works, ==> but no images, 

even phpmyadmin won't give me some images.


Normally the user rights are ok. (I gave them 777) (I know it is onsafe but is was to test)


Can somebody help me please.

Thank you.


Arne

---

### Post by depele on 2008-03-03
anybody ?

bump..

---

### Post by depele on 2008-03-05
bump*************

---

### Post by nlong on 2008-03-05
Are you getting image placeholders or the red x's where the images should be?  Also,  what type of images aren't being served; jpeg, gif, png, etc?

---

### Post by depele on 2008-03-05
no red x or placeholders, 


jpg not showed
gif not showed
no image type showed

---

### Post by Mithrilhall on 2008-03-05
View the page source and post the results.

---

### Post by depele on 2008-03-06
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>HACKBUNTU :: to hack or not to hack ??</title>
</head>
<body style="margin-top:0; background-color:#666666">
<table width="802" align="center" style="margin-top:0" cellpadding="0" cellspacing="0">
	<tr>
    	<td height="133" background="header.PNG"></td>
    </tr>
    <tr>
    	<td background="bckgr.PNG" style="margin-left:60px">
        <table width="95%" align="center" style="margin-top:0; margin-left:7px; margin-right:0; font-family:Tahoma; font-size:12px; color:#000000">
        <tr>
        	<td>
            <b>Feel free to use the following tools:</b><br />
            <hr color="#FFCC33" align="left" width="83%" /><br />
            <a href="./joomla">Joomla</a>
            <br />
            <br />
       	    <a href="./phpmyadmin">PhpMyAdmin</a>
            <br /><br />
       	    <a href="https://hackbuntu:10000/">Webmin</a>
            <br /><br />
       	    <a href="http://hackbuntu:8080/WebGoat/attack/">WebGoat</a>
            <br /><br />
            <hr color="#FFCC33" align="left" width="83%" />
            <br /><i>Place for your advertisement...</i><br /><br />
            <hr color="#FFCC33" align="left" width="83%" />
            <br />Sponsored by:<br />
            <img alt="" src="ubuntu_logo.jpg" /><br /><br />
            <hr color="#FFCC33" align="left" width="83%" />
   	      </td>
        </tr>
        </table>
        </td>
    </tr>
    <tr>
    	<td height="10" background="bottom.PNG"></td>
    </tr>
</table>
</body>
</html>

---

### Post by Mithrilhall on 2008-03-07
```

<img alt="" src="ubuntu_logo.jpg" />

```

Try this:
```

<img src="./ubuntu_logo.jpg" />

or

<img src="/ubuntu_logo.jpg" />

```

---

### Post by depele on 2008-03-08
It doesn't work.

I believe it is an Apache error.  But I don't find what.
Because all style tags are also not parsed.

---

### Post by comandrei on 2008-03-08
I've experienced this too. If you install the system, this problem goes away. It's probably a security measures in order not to consume too much memory.

---

### Post by depele on 2008-03-08
> **comandrei said:**
> I've experienced this too. [COLOR="Red"]If you install the system[/COLOR], this problem goes away. It's probably a security measures in order not to consume too much memory.

==> the problem is it has to be a live cd. (teacher)
You have no idea to avoid this security measure?

---

### Post by comandrei on 2008-03-08
try lighttpd or nginx instead. Apache is a very scalable server, but it consumes too much memory.

---

### Post by depele on 2008-03-08
can you do the same with lighttpd?

thanks a lot

---

### Post by depele on 2008-03-08
Tried so.
I think I am going to maken an asci page.
But thanks anyway.
But same thing here. (lighttpd)
Strange is that from the ch root environment it works.

---

### Post by depele on 2008-03-08
fixed!!!!

got this from 
[http://ubuntuforums.org/showthread.php?t=537722](http://ubuntuforums.org/showthread.php?t=537722) 

Re: Live-cd Apache installation not serving graphics files.
In case you haven't yet fixed this problem, see: [https://bugs.launchpad.net/ubuntu/+s...he2/+bug/95393](https://bugs.launchpad.net/ubuntu/+s...he2/+bug/95393)


```

You need to set EnableSendfile Off in apache2.conf

```

---

