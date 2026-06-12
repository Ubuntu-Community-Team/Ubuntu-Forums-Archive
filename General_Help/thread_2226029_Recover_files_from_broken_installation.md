---
title: "Recover files from broken installation"
date: 2014-05-24
forum: General Help
---

### Post by j-andreas on 2014-05-24
Hey guys, I've been running Ubuntu for years now but as just a simple user with barely any use of the terminal.

Earlier this week I was trying to get my grumpy Lexmark Prestige Pro printer to work with 14.04 and somewhere in between following terminal commands found online and trying to set up Google Cloud Print for it I somehow broke my installation. I had to buy a new laptop with Windows 7 on it which is what I'm sitting on now.

So here's what happens now... The things that I can observe:

1. It boots up and into Ubuntu a lot slower than it used to and with a few pop-ups about system errors.
2. Everything is super-slow
3. The cursor blinks in and out of existence while I'm moving it
4. When I open certain menus, like the power button menu on the top right the text changes font and font size every 4 seconds or so.
5. I can't open any applications. Chrome, Thunderbird, System Monitor, none of them open.
6. I can access Dash and type into it but nothing happens when I try to open stuff
7. The system doesn't pick up my USB flash drive. The drive blinks a bit and then goes dark.
8. WIFI keeps connecting and disconnecting.
9. I connected an ethernet cable to the new WS7 laptop to see if I could access it that way but when I clicked to connect to the ethernet connection from the network menu it came up saying "Connection activation failed. (32) Not authorised to control networking"
10. I logged out of my session and into a guest session and everything ran perfectly fine. So I'm assuming whatever damage I did was to my own personal account.

I have no qualms about wiping it clean and re-installing ***AFTER ***I've recovered my business and personal documents from the drive


Please help?

---

### Post by j-andreas on 2014-05-24
Also, about the error windows...

```
System program problem detected
Do you want to report the problem now?
Cancel           Report Problem
```


Clicking report does nothing.

Also the "System program problem detected" part is changing font every 3 seconds or so, similar to the power menu. The error window is also resizing along with the font

---

### Post by j-andreas on 2014-05-24
One more addition...

I created a bootable USB with 14.04 on it and ran a live session on the affected laptop.
I can *see* all my files and folders there but I can't *get* to them.

For example, I can navigate to my home/user/Desktop directory and copy a JPG or a PDF I had on the desktop but if I try to copy a folder it comes up with an error message saying I don't have permission to do that :(

---

### Post by j-andreas on 2014-05-24
Alright!
After further fiddling, I finally managed to overcome the permission problem. I had to enable the universe repository and use

```
gksu nautilus
```

Once that was done it allowed me to copy the files out.
It would've been great if I could've just recovered without re-installing Ubuntu but I guess that's my punishment for just throwing lines into terminal without knowing exactly what they do :)

So, if a mod wants to close this, I'm all good :)

---

