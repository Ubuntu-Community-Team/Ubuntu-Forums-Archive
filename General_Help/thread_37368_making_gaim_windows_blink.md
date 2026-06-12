---
title: "making gaim windows blink"
date: 2005-05-26
forum: General Help
---

### Post by pete0r on 2005-05-26
hey all,

this is my first post. i've been a windows user forever, but i have a fileserver running gentoo so i'm alright with linux.

i just finally said screw it, and installed ubuntu.

anyway, i'm trying to figure out how to make gaim windows blink. using the plugin doesn't work.

i found a few threads about patching something, but none of them listed the folder path that i needed. i tried to search for it, but couldn't find anything.

could someone help me out?

thanks!

pete0r

---

### Post by pete0r on 2005-05-27
[QUOTE=pete0r]hey all,

this is my first post. i've been a windows user forever, but i have a fileserver running gentoo so i'm alright with linux.

i just finally said screw it, and installed ubuntu.

anyway, i'm trying to figure out how to make gaim windows blink. using the plugin doesn't work.

i found a few threads about patching something, but none of them listed the folder path that i needed. i tried to search for it, but couldn't find anything.

could someone help me out?

thanks!

pete0r[/QUOTE]
 any ideas?

---

### Post by basementjack on 2005-06-01
[QUOTE=pete0r]any ideas?[/QUOTE]

I just joined this forum to ask that very question....  :^o
I always run silent (no sound) and it is hard to see whether or not anyone has written to me. Although I tried the plugin guinotifications, it did nothing, but come with little popups in the lower right corner of the screen. That is just not what I wanted..

So, please, any ideas?..

---

### Post by Hydrant on 2005-06-01
I, also, am curious about this issue. If a how-to could be posted, there's clearly a lot of us here who would be eternally greatful :D

(I know it can be done on Gentoo, I've seen it, so surely it's possible on Ubuntu as well?)

---

### Post by Seth on 2005-06-01
[QUOTE=basementjack]I just joined this forum to ask that very question....  :^o
I always run silent (no sound) and it is hard to see whether or not anyone has written to me. Although I tried the plugin guinotifications, it did nothing, but come with little popups in the lower right corner of the screen. That is just not what I wanted..

So, please, any ideas?..[/QUOTE]
 Install gaim extended prefs and set it to add something like ** to the window on new messages. Gnome can't blink windows. If you are using KDE, choose "set window manager urgent hint" and the windows will blink.

---

### Post by basementjack on 2005-06-01
[QUOTE=Seth]Install gaim extended prefs and set it to add something like ** to the window on new messages. Gnome can't blink windows. If you are using KDE, choose "set window manager urgent hint" and the windows will blink.[/QUOTE]

Those ** are they shown in the taskbar (** NameOfPerson)?.. Or am I not getting it?..  :)

---

### Post by bored2k on 2005-06-01
[QUOTE=basementjack]Those ** are they shown in the taskbar (** NameOfPerson)?.. Or am I not getting it?..  :)[/QUOTE]
 Go to preferences > plugins > message notification > and enable everything, you would then see ths in the panel:
(*)(*)(*)(Number-of-new-messages-receiived)Person)

---

### Post by banjobacon on 2005-06-01
Openbox supports window flashing. Search the forum for how to install and setup the Openbox window manager.

The taskbar will remain unblinking, though.

---

### Post by basementjack on 2005-06-02
Yes, works just fine.. But it would have been better if it blinked or changed color.. So you from a distance can see, wheter you have gotten a message or not. Anyway, thanks for this info  ;-)

---

### Post by Daicogra on 2005-06-02
[http://www.ubuntuforums.org/showthread.php?t=33255](http://www.ubuntuforums.org/showthread.php?t=33255)

[http://www.people.virginia.edu/~mse5q/blink/](http://www.people.virginia.edu/~mse5q/blink/)

I'm still try to test it.... I don't know if it works at the moment.

---

### Post by zafar on 2005-06-05
the patch for libwnck has been commited into the gnome cvs repo and so i used that with another patch from the gnome bugzilla and made a deb. Flashing windows work great for me and it should work for everyone else. To use it:

1) wget 'http://z.narutochaos.com/ubuntu/libwnck16_2.10.0-0ubuntu1_i386.deb'
2) sudo dpkg -i libwnck16_2.10.0-0ubuntu1_i386.deb
3) sudo echo libwnck16 hold | sudo dpkg --set-selections
4) killall gnome-panel

after that, make sure you have message notification plug-in for gaim and in it check "set window manager "URGENT" hint. from then on, new im's and other actions will cause ur taskbar to flash  :)

---

### Post by ounn on 2005-06-06
UOuhhhh, thats exactly what i always want gaim to do. Tnks. By the way, how can i change the blinking color?

ounn

---

### Post by blicksky on 2005-07-31
[QUOTE=zafar]the patch for libwnck has been commited into the gnome cvs repo and so i used that with another patch from the gnome bugzilla and made a deb. Flashing windows work great for me and it should work for everyone else. To use it:

1) wget 'http://z.narutochaos.com/ubuntu/libwnck16_2.10.0-0ubuntu1_i386.deb'
2) sudo dpkg -i libwnck16_2.10.0-0ubuntu1_i386.deb
3) sudo echo libwnck16 hold | sudo dpkg --set-selections
4) killall gnome-panel

after that, make sure you have message notification plug-in for gaim and in it check "set window manager "URGENT" hint. from then on, new im's and other actions will cause ur taskbar to flash  :)[/QUOTE]
 I tired this and it seems to be working quite well.  One problem i've noticed is when you don't respond to a message and leave the taskbar flashing when the screensaver starts up, it will no longer be flashing when you return from the screensaver.

I was also curious if > the patch for libwnck has been commited into the gnome cvs repo means that this weill be included in the next release of Gnome/Ubuntu?>  >  >  >  > 

---

