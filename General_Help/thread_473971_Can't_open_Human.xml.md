---
title: "Can't open Human.xml"
date: 2007-06-14
forum: General Help
---

### Post by SDE on 2007-06-14
I'm running feisty server and enabled gdm.  When it starts up, I get an error: > Can't open file /usr/share/gdm/themes/Human/Human.xml

I press OK and I can login normally.

The directory Human did not exist, so I created it along with touched Human.xml.  I still get the error.

Any ideas how to fix this?

---

### Post by jasonlfunk on 2007-06-14
Change your Theme. :)

---

### Post by SDE on 2007-06-14
i can change my theme once i login.. but it has no effect on the logged out screen.  i should have been more specific.

i get this error when gdm starts up, .. or when i logout of a user.  it happens just before i'm presented with the login UI.

---

### Post by silentk940 on 2008-01-19
i have noticed the same problem, though i rarely run gnome on the server (usually just do remote terminal access). i found that if you set a user to automatically log in when gnome is started it will bypass the error. not sure if that will help you out but just in case its a tidy workaround for my system.

---

### Post by fcigoi on 2008-01-22
I know it won't be of much help, but I am experiencing the same problem when installing Ubuntu 7.10 server on a Netfinity machine. 
The only way is to make it load KDE....but I don't want KDE as I'm used to Gnome on the desktops and I'm happy with it. 
Anyone has had any luck with this ?

---

### Post by yuki on 2008-04-29
```
sudo gdmsetup
```
..will allow you to select another theme. Make sure you click the actual box, and not just highlight the theme before closing. It's not a crystal clear layout. 

For the record I found this out by looking at the man-page for gdm.

---

