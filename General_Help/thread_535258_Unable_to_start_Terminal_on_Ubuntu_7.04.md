---
title: "Unable to start Terminal on Ubuntu 7.04"
date: 2007-08-26
forum: General Help
---

### Post by tottto on 2007-08-26
When I clic on Application-Accessories-Terminal nothing happen. What shoud I do to regain access to the Terminal ?

thanks

---

### Post by seshomaru samma on 2007-08-26
click alt+F2 you will get a small window which will run any application
write 
```
gnome-terminal
```
or if you are not using gnome (like on kubuntu or xubuntu)
go
```
xterm
```

---

### Post by Selcal on 2007-08-27
Yeah i am having the same problem.  I did do the xterm and it will suffice when i need the terminal but i really miss my gnome terminal as of yesterday.

Does anyone else have this problem after the update?  I am kind of new to Ubuntu, and i have a little experience but this is a bit over my head.  most of my practice is all that .conf stuff that everyone has to learn about when you first start everything up. 


So yeah gnome terminal is dead.  What can i do about it?

---

### Post by Zootropo on 2007-08-27
> **Selcal said:**
> Yeah i am having the same problem.  I did do the xterm and it will suffice when i need the terminal but i really miss my gnome terminal as of yesterday.

Does anyone else have this problem after the update?  I am kind of new to Ubuntu, and i have a little experience but this is a bit over my head.  most of my practice is all that .conf stuff that everyone has to learn about when you first start everything up. 


So yeah gnome terminal is dead.  What can i do about it?

Try to run gnome-terminal from xterm and see if it prints some info

---

### Post by Selcal on 2007-08-27
well this is what i ended up with when i did that

<quote>
The program 'gnome-terminal' received an X Window System Error.
This probably reflects a bug in the program.
The error was 'BadValue' (intiger parameter out of range for operation)'.
 (Details: serial 105 error_code 2 request_code 78 minor_code 0)
 (Note to programmers: normally, X errors are reported asynchronously;
  that is, you will receive the error a while after causing it.
  To debug your program, run it with the --sync command line option 
  to change this behavior.  You can then get a meaningful backtrace from 
  your debugger if you break on the gdk_x_error() function.)

</quote>

well a simple un-instal re-install command line would be helpful.  I don't want to mess anything up.  Ubunutu will not let me uninstal it from the add/remove menu.

---

### Post by Selcal on 2007-08-27
I have it now.  





> 
sudo nvidia-settings


and disable Xinerama.

  Now my terminal works fine.  it seems that is uses the screen size to find its reference when you open it.  The huge Desktop xinerama gives you with multiple monitors is screwing it up.  Now if i can get my desktop effects to work correctly.

---

