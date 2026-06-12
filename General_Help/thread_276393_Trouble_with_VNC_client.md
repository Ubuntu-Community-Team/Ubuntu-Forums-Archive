---
title: "Trouble with VNC client"
date: 2006-10-12
forum: General Help
---

### Post by agrimur on 2006-10-12
Hi,

I am one of many who are trying to free themselves from the claws of windows, am loving Ubuntu thus far.  I have run into a problem though, although small it is very annoying.  I have used VNC to remotely control another computer in my house, I was trying to figure out how I could do it the same way as I did in windows, make a shortcut so i would just have to click once and it wold send the IP address and the password and open the remote dasktop in a window without me having to input anything (IP number or password for the VNC server).  If figured out that if I executed the following line in the terminal: 

xvnc4client -passwd ~/.vnc/passwd xxx.xxx.xxx.xxx (ip number)

everything worked as it sould, but if I put this exact same line in the shourtcut on the desktop it would return a error saying that it couldn´t find the password file.  If i left the password part out of the line it would open the client and prompt me for a password.  It didn´t matter if i checked the "open inside terminal" option (or something like that), it still didn´t work.  I have tried with different VNC clients aswell.  I want to fix this for two reasons 1) I find it alot less sleek to have to input a password every time I I open this, and 2)  I find it very annoying that i cant figure out why this is not working.

Probably there is something obvious I am doing wrong or not doing at all, just blame it on my newbie-ness...

AG

---

### Post by agrimur on 2006-10-13
anyone?

---

### Post by nikhilk on 2006-10-13
What happens if you put the absolute path i.e. "/home/<user_name>/.vnc/passwd" instead of "~/.vnc/passwd".
I guess that should work.

---

### Post by agrimur on 2006-10-13
Yes, that worked! thanks alot!

---

### Post by nikhilk on 2006-10-13
> **agrimur said:**
> Yes, that worked! thanks alot!
You are welcome :)

---

