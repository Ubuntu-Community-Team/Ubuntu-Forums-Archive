---
title: "What is remote desktop?"
date: 2007-03-26
forum: General Help
---

### Post by BionicBigfoot on 2007-03-26
I just got Ubuntu and I am liking it very much. I have a friend who is visually impaired and likes it too. But she needs me to help her from time to time and lives over 50 miles away. So I was wondering what "Remote Desktop" is?

I tried playing around with it to remote her machine but I can't figure out how to actually use it? Is it something that needs to be started from terminal or inside a browser...I see this thing that says "email this" VNCVIEWER DESKTOP:0 (some text omitted for security) but what do I do after I email that? 

Any help would be appreciated

---

### Post by rich.bradshaw on 2007-03-26
Basically you enable remote desktop on the computer that you want to access, then on another computer you type what you just mentioned in their terminal.

I use it to access my ubuntu machine from Windows at university.

If you want to access it from Windows you will need something like ultravnc.

Step 1. Turn on Remote Desktop
Step 2. Try and remote desktop to yourself on the same computer - just to check. THis will hopefully open a "portal" showing you what is on your screen.

Type what it tells you.

Step 3. If you have a router, forward the relevant ports. (Google port forwarding if you aren't sure or read your router manual)

Step 4. FInd out what your IP address is. Google "What's my IP" to find out!
Step 5. On a different computer open either ultravnc on Windows, or type what you typed on your computer, and it should work.

It's very useful to remotely use a computer.

---

### Post by BionicBigfoot on 2007-03-26
Ok I will test that out again. But yesterday I tried doing it on my own machine and got an error when I typed in the terminal it said something like VNCVIEWER Would not start contact [www.sunmicrosystems](www.sunmicrosystems) for more information (or something like that - I took a screen shot of it and left home, as I am at work now) Not sure why I got this error.

Would it be better to start VNC Viewer using the exact IP addy of the person I am trying to remote. 

I guess, would a command like this work better than the command they give you?
$ VNCVIEWER @ 255.52.0.0 ) Not actuall IP, I just made it up

I tried looking up a walk thru at the wiki page and it seems it recommends using the I.P. but I am not 100% sure.

---

### Post by amdalex on 2007-03-26
Yes you do use the IP of the machine you want to connect to.

---

### Post by Ek0nomik on 2007-03-27
This this other person using Windows or Linux?

If Windows, I would have that person use UltraVNC.  If Linux, well, there's much debate over that.

As far as you're concerned, I would use xvnc4viewer to view other computers.  That's the one I use, and I haven't had any problems.

```
xvnc4viewer ip.address
```

That should do it if you have the server setup correctly.

---

