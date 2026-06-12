---
title: "screen resolution problem"
date: 2005-09-02
forum: General Help
---

### Post by fosgood on 2005-09-02
i got the cd in the mail today.  installed on a partition made with part magic.  when pc fianlly booted to new os the screen seemed to be sort of rolling and very unstable.  everything was doubled, even the mouse cursor.  things would open but very slowly.  also what is this thing where it is detecting network?  dhcp or something.  it doesn't work.  i tried the live cd and the same thing happened.  it is probably my pc because both things acted the same.
hp4550z pavillion
win 98se
466 mhz celeron
192 mb ram
maxtor 80 gb diamondmax ultra

i realize this is an old pc, but it's all i have.  disabled with no income. any help would be greatly appreciated.

---

### Post by xequence on 2005-09-06
Ok. The same thing happened to me when I used MEPIS (another distro) in anything over 800*600 resolution. I am guessing its something to do with the video card or something... Try using a lower resolution, if you can.

---

### Post by fox on 2005-09-07
[QUOTE=fosgood]i got the cd in the mail today.  installed on a partition made with part magic.  when pc fianlly booted to new os the screen seemed to be sort of rolling and very unstable.  everything was doubled, even the mouse cursor.  things would open but very slowly.  also what is this thing where it is detecting network?  dhcp or something.  it doesn't work.  i tried the live cd and the same thing happened.  it is probably my pc because both things acted the same.
hp4550z pavillion
win 98se
466 mhz celeron
192 mb ram
maxtor 80 gb diamondmax ultra

i realize this is an old pc, but it's all i have.  disabled with no income. any help would be greatly appreciated.[/QUOTE]
 i HAVE THE SAME

---

### Post by Arne Caspari on 2005-09-07
Try the following: 

When the machine is booted up showing the garbled screen, switch to a text console by pressing "CTRL+ALT+F1". 

Log in if neccessary and execute the following command: 
```
sudo dpkg-reconfigure xserver-xorg
```

Go through the dialogs:
```

Attempt to autodetect...?:  YES

<Accept the defaults for XServer driver, identifier and every other question until it comes to this question: >

Attempt monitor autodetection?
Select: NO

Accept the "Generic Monitor" string

Select the appropriate screen resolution in the list ( eg. 1024x768 ). 

"Choose a method for selectiong monitor characteristics:" 
 Select: MEDIUM

"Please select your monitor's best video mode":
 Select: 1024x768 @ 60Hz

"Write monitor sync ranges..."
 Select: YES

"Select desired default color depth..":
 Select: 24

```

Afterwards, enter: 
```
sudo /etc/init.d/gdm restart
```


Hopefully you now have a nice ubuntu screen ;-)  If you do this with the installed version, the change will be permanent. 

 Hope it helps, 

 -Arne

---

