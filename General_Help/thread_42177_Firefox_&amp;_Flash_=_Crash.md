---
title: "Firefox &amp; Flash = Crash"
date: 2005-06-16
forum: General Help
---

### Post by Miggy on 2005-06-16
Hi,

I have a very strange problem. 
I've used firefox with flashplayer-plugin (the macromedia one) for weeks now and didn't encounter any issues. All pages worked.

Since today when the flash-plugin is installed, firefox reproducable crashes.
for example when going to 

[www.wetter.de](http://www.wetter.de) 
[www.yahoo.de](http://www.yahoo.de) 

The strange thing is, when I disable Javascript firefox doesn't crash with [www.yahoo.de](http://www.yahoo.de) , even if flash-plugin is installed, while [www.wetter.de](http://www.wetter.de) always crahes firefox if flash-plugin is installed.
When starting form console the following error message appears after firefox crashes:

> 
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 117 error_code 8 request_code 147 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I tried to reinstall firefox and the plugin. But still firefox crashes.
Only removing the flash-plugin results in a stable firefox.
Does anyone has suggestions. As already mentioned, it's strange, that everything worked fine until today.
To exclude a memory error I've already removed the memory and put another in my laptop. But this wasn't the problem.

Thanks for any help.
Miggy

---

### Post by jdong on 2005-06-16
What kernel version do you have? A recent kernel update has been causing various stability issues.

---

### Post by sapo on 2005-06-16
i have the same problem since i ve installed the 1.04 version of firefox it crashes everytime i open a flash movie  ](*,) 

it was working with sound and everything fine before...

---

### Post by Miggy on 2005-06-16
Hi,

uname says my kernel is: 2.6.10-5-k7

---

### Post by jdong on 2005-06-16
[http://ubuntuforums.org/showpost.php?p=211460&postcount=44](http://ubuntuforums.org/showpost.php?p=211460&postcount=44)

Downgrade your kernel and see if the problem persists.

---

### Post by Miggy on 2005-06-16
Thanks for your reply. I'll try as soon as I've time

---

