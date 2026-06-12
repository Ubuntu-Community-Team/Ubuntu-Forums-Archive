---
title: "Sudo, Root, Nothings Working!"
date: 2007-03-09
forum: General Help
---

### Post by ComputerGuy56 on 2007-03-09
I'm trying to make Firestarter start on it's own and I read everything. I'm stuck at the part trying to edit /etc/sudoers. I try using the sudo /etc/sudoers. Didn't work. Tried sudo -i. Tried visudo. I got it to work once but right when I click save it says:... Well, I can't get it to work again but this stupid Root, no Root, Admin thing is really getting me mad!:confused:  I've looked around but I can't even find how to make yourself Root??? And no, I'm not going to login as root because I heard it's bad.

---

### Post by Gannin on 2007-03-09
If you really want to make yourself root temporarily, you can just type "sudo bash".

But, the default install of Firestarter automatically starts up and runs in the background when your computer acquires its IP address.  If you'd like to test this out, then find a security website that'll port scan you and do some security tests on your computer.

---

### Post by Gerard Barberi on 2007-03-09
To activate root

sudo passwd root (sets a password for it)

it'll ask for a new UNIX password twice

and then you just

su

enter that password and you're root

---

### Post by ComputerGuy56 on 2007-03-09
```
sly@sly-desktop:~$ sudo bash
root@sly-desktop:~# /etc/sudoers
bash: /etc/sudoers: Permission denied

```
Doesn't work

By the way, can you re-explain how to make yourself root. That one is confusing.

---

### Post by Gerard Barberi on 2007-03-09
Looking at your code, what are you using to edit the file?

Gedit, Vi, nano?

---

### Post by ComputerGuy56 on 2007-03-09
Applications -> Accessories -> Terminal. Then i go directly typing that in.

---

### Post by Gerard Barberi on 2007-03-09
No, I mean I don't see you selecting a text editor for the file like

sudo gedit /etc/sudoers

gedit is the text editor to open that file with, sudo grants root privledges

---

### Post by ComputerGuy56 on 2007-03-09
Oops:( . I'll try that.

---

### Post by zvacet on 2007-03-09
ComputerGuy56


If you want to install something you have to be  root (administrator).Common user can not use sudo,so they can not install anything.It is security reason,in the case somebody go in your comp can not go outside home directory,because he is not root.  that the reason to work as second user in everyday work.So,basicly,login as root,install what you are interested in and switch to normal user.To become root
```
sudo -i
```

---

### Post by ComputerGuy56 on 2007-03-09
I clicked save, this is what happend, or error message:Could not save the file /etc/sudoers. You are trying to save the file to a read only disk. Please check that you typed the location correctly and try again. But when i typed the sudo gedit in the terminal, this popped up: ALSA lib pcm_dmix.c:862:(snd_pcm_dmix_open) unable to open slave
But it still opened up the window so I don't know what that is.

---

### Post by ComputerGuy56 on 2007-03-09
Suggestions?

---

### Post by X-626 on 2007-03-09
**EDIT: I'd only do this if you *know* exactly how to edit the sudoers file.  If you are worried, see the posts below.**
The file sudoers is, by default, read only.  You can still change the file **without** changing the file permissions, however.  You can do it with vi:
```
sudo vi /etc/sudoers
```Just hit the Insert button, arrow to the line to change, change it, and then hit Escape.  After  that, type :w! to force vi to write the file.  Then type :q and you are out of vi, and your sudoers file is saved.

If you would rather use Gedit, you will have to change the file permissions first.  To do that:
```
sudo chmod 600 /etc/sudoers
```That will make the file writable by root.  After that, launch Gedit and change the file, but afterward, make sure to change it back to it's original permissions (440, at least on my computer it is):
```
chmod 440 /etc/sudoers
```I hope that helped.

---

### Post by aysiu on 2007-03-09
I thought the command to edit the /etc/sudoers file is ```
sudo visudo
```

---

### Post by X-626 on 2007-03-09
I've always used vi to edit it.  Besides, I like vi over nano for some strange reason.  Although, that works, too.  (I didn't actually think about that)

---

### Post by aysiu on 2007-03-09
If think editing with the *sudo visudo* command automatically makes a backup of the file and checks syntax (doesn't allow you to save if the syntax is bad).

---

### Post by X-626 on 2007-03-09
I checked on that just to see.  It **does** check the syntax (and gives you an option of what to do).  I've always used vi to do it, though.  Anyway, to be safer, I'd go with what aysiu said.  Sorry about that.  I guess I'm just used to doing it a little differently.  Like aysiu said, use:
```
sudo visudo
```
to edit the sudoers file.  Sorry about that.

---

### Post by the.phantom on 2007-03-09
firestarter is just a GUI !
all the setting you have done to it are working in the firewall just no gui 
so there is really no reason to have it start up?
you can go to a site like say  grc.com and check out the firewall with firestaerter runnin and without and you will get the same status ;-)
you can bring up firestarter in system /admin firestarter if you want

---

### Post by ComputerGuy56 on 2007-03-09
Wow, a lot of stuff. I'll do that sudo visudo and change the thing back and fourth and....

---

### Post by ComputerGuy56 on 2007-03-09
> **X-626 said:**
>   After that, launch Gedit and change the file, but afterward, make sure to change it back to it's original permissions (440, at least on my computer it is):
```
chmod 440 /etc/sudoers
```I hope that helped.

Does it matter if it's at or below 440?

---

### Post by ComputerGuy56 on 2007-03-09
```
sly@sly-desktop:~$ sudo chmod 600 /etc/sudoers
Password:
sly@sly-desktop:~$ sudo visudo /etc/sudoers
sudo: /etc/sudoers is mode 0600, should be 0440

```
Doesn't work....

---

### Post by ComputerGuy56 on 2007-03-09
Uh oh, I always get this error whenever I try to do something that contains sudo:
```
sly@sly-desktop:~$ sudo -i
sudo: /etc/sudoers is mode 0600, should be 0440

```

---

### Post by aysiu on 2007-03-10
Since you don't have *sudo* privileges, you cannot use *sudo* to fix *sudo*

So boot into recovery mode and type ```
chmod 0440 /etc/sudoers
reboot
``` and then boot into regular mode.

If you don't know what I mean by "recovery mode," this link will help you:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by ComputerGuy56 on 2007-03-10
Yey! The file is back to normal. But I STILL have to somehow edit the file....

---

### Post by aysiu on 2007-03-10
Well now that it's 0440, you can actually use *sudo* to edit it.

Back in normal mode, try ```
sudo visudo
```

---

### Post by ComputerGuy56 on 2007-03-10
WooHoo, It's working! I was so dumb, I was typing ```
sudo visudo /etc/sudoers
```
When it's just
```
sudo visudo
```
But, it's working now!

---

### Post by ComputerGuy56 on 2007-03-10
This is starting to get very confusing. I'll try to explain the whole thing. So I edited sudoers and put in
```
sly ALL= NOPASSWD: /usr/sbin/firestarter
```
Then I did the Sessions, added the
```
sudo firestarter --start-hidden
```
Restarted my computer, didn't start. I tried to start firestarter from System, Administration, Firestarter. That didn't work. So I took out
```
sly ALL= NOPASSWD: /usr/sbin/firestarter
```
from sudoers. But before I removed that, I noticed that sudoers now has a little Red X and when I click on it it says:
```
Cannot open: /etc/sudoers: No applications suitable for automatic installation for handling this type of file is not available
```
So I have to edit using     sudo visudo.
Isn't there a easier way to "just get" this to work.#-o

---

### Post by ComputerGuy56 on 2007-03-10
Thoughts?(This worked last time):popcorn:

---

### Post by ComputerGuy56 on 2007-03-10
I re-did all the steps, and found this out. When you put this:
```
sudo firestarter --start-hidden
```
It's supposed to do a hidden terminal.
Since it didn't start I manually put that in a Terminal and this is what I got:
```
sly@sly-desktop:~$ sudo firestarter
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5063): Gtk-WARNING **: cannot open display:  

```
I'm guessing someone will know what this is?

Also, I forgot to take the code out of the sessions but I took the code out of the sudoers file and this happend:

I went into System -> Administration -> Firestarter. I noticed that I got two Firestarter icons so it must be something with the sudoers file and the passwords.

---

