---
title: "firebird crashes"
date: 2006-10-31
forum: General Help
---

### Post by sheine on 2006-10-31
I installed 6.10 several days ago and it worked well. Today, firefox started crashing whenever it is turned on. I uninstalled and then reinstalled firefox but the trouble is still there. I have not gone onto the internet as root but as a user.

---

### Post by sheine on 2006-10-31
To get around this problem I installed seamonkey. It crashes too.

---

### Post by yopnono on 2006-10-31
Are you talking about firefox? check your profile/extensions.

---

### Post by sheine on 2006-10-31
Yes it is firefox. I cannot check anything because it crashes almost as soon as it starts up. By the way, Opera works perfectly and is what I am using to send this message.

---

### Post by yopnono on 2006-10-31
you can start it in -safe-mode 

terminal:
```
firefox -safe-mode
```

Also open ypur home folder and show hidden files/folders using CTRL + H
then you have a folder named .mozilla rename it, and start fx, if that work there is a problem with you profile.

---

### Post by sheine on 2006-10-31
When I started firefox in safe mode, I got the information below. How do I correct whatever is wrong?


** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by sheine on 2006-10-31
I started in safe mode and one by one disabled everything. It still crashes.
Since I have the same trouble with seamonkey, I do not think that renaimng will work.

---

### Post by sheine on 2006-10-31
In safe mode, I removed all saved material. It still crashes.

I can find no "profile" in firefox. It did not show up in the index.

---

### Post by yopnono on 2006-10-31
> **sheine said:**
> In safe mode, I removed all saved material. It still crashes.

I can find no "profile" in firefox. It did not show up in the index.

```
Also open your home folder and show hidden files/folders using CTRL + H
then you have a folder named **.mozilla** rename it, and start fx, if that work there is a problem with you profile.
```

Find the folder **.mozilla**

---

### Post by sheine on 2006-10-31
Changing the name of the mozilla folder seems to have solved the problem for now. Thank you.

---

### Post by hikaricore on 2006-10-31
Have you tried this sollution?  [http://www.ubuntuforums.org/showthread.php?t=286069]("http://www.ubuntuforums.org/showthread.php?t=286069")

---

