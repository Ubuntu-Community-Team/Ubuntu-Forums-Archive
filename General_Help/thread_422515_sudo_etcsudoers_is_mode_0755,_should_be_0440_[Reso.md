---
title: "sudo: /etc/sudoers is mode 0755, should be 0440 [Resolved]"
date: 2007-04-25
forum: General Help
---

### Post by Amonlisa on 2007-04-25
Hi there, 

trying to mount an external HD, I used a tutorial I found on internet:[http://www.free-culture.fr/2007/01/10/activer-le-compte-root-sous-ubuntu-et-sy-connecter-en-mode-graphique/](http://www.free-culture.fr/2007/01/10/activer-le-compte-root-sous-ubuntu-et-sy-connecter-en-mode-graphique/)
Followings are the various steps I followed till my problem

I created a file to mount my EHD in with: 

                      sudo mkdir /media/HDD

Then in order to create a file in the root, I had to activate it, so:

                      sudo passwd root

then, I entered the password and wrote this command:

                      sudo chmod 755 /etc/sudoers

and then, in order to edit the document:

                      gedit sudoers
Where nothing was written on, and I was supposed to remove this line: %admin ALL=(ALL) ALL

So I directly passed to the next instruction:

                      sudo chmod 440 /etc/sudoers

Now, I am stuck, I was supposed to be able to use the root graphic interface ALT+CTRL+F1, then startx --:1, but it doesn't work. 

More important, Synaptic is not working and I cannot enter a sudo command without having this message appearing on the terminal: sudo: /etc/sudoers is mode 0755, should be 0440
or sudo: /etc/sudoers is mode 0440, should be 0755
when I use sudo chmod 755 /etc/sudoers to come back to what was the initial mode.

If you have any clue about how I could come back to my initail settings, I would be more than glad?

Thank u
Amonlisa

---

### Post by yoasif on 2007-04-25
In my opinion, the easiest way to add a new device to mount is pysdm.

open a terminal and do ```
sudo aptitude install pysdm
```

Then go to administration > storage device manager.

Using root is dangerous, by the way, you should really just use sudo if you need to do system maintanance tasks.

---

### Post by sisco311 on 2007-04-25
> Now, I am stuck, I was supposed to be able to use the root graphic interface ALT+CTRL+F1, then startx --:1, but it doesn't work.

More important, Synaptic is not working and I cannot enter a sudo command without having this message appearing on the terminal: sudo: /etc/sudoers is mode 0755, should be 0440
or sudo: /etc/sudoers is mode 0440, should be 0755
when I use sudo chmod 755 /etc/sudoers to come back to what was the initial mode.

start your computer in recovery mode.
(at boot press Esc for the grub menu and select: Ubuntu, kernel .......-c (recovery mode))

```
sudo chmod 0440 /etc/sudoers
```

reboot
```
sudo reboot
```

---

### Post by sisco311 on 2007-04-25
next time don't change the permissions of the /etc/sudoers file
use:
```
sudo visudo
```
to edit the file

Ctrl+o, Enter to save
Ctrl+x to exit

---

### Post by Amonlisa on 2007-04-25
Okay so I tried to change the chmod back to 0440, but it won't work.
After the command, I had same line has previously
i.e.: sudo: /etc/sudoers is mode 0755, should be 0440

sudo reboot is useless then.

Thanks anyway. 

Any other clue?

Next time I will defintly avoid playing with the root, and will stick to the ubunthu forum instead if roaming around on the web...

---

### Post by Amonlisa on 2007-04-25
Okay, 

Problem solved..

Didn't work as easily as merely following information shared.
here what I have done

In the terminal:
su

chmod 440 /etc/sudoers

sudo reboot

and now it's perfectly working. I did it from the main session, as I did not have the idea while tryinf from the recovery terminal. It might work though, but I won(t give a try just now...lol

Thank u for your help, especially sisco311, you showed me the light dude...lol

---

