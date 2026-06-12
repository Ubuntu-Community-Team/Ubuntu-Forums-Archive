---
title: "No Login Screen With Feisty.  Broken?"
date: 2007-06-20
forum: General Help
---

### Post by mikealive on 2007-06-20
i finally got my ubuntu installation how i want it.  everything has been working great, until yesterday. I  installed the newest version of Exaile! svn and was trying to get the equalizer to work by installing the version of gstreamer that are needed.  that didnt work.  also, i believe i installed something called ALSA mixer (something like that).  when i shut my computer down, everything was working fine.   

now, when i start my computer up, the first screen looks normal.  i try and let it start ubuntu, and it shows the ubuntu logo, with the progress bar, and it goes all the way.  now the next screen, instead of being the normal ubuntu login page, i get a black screen with simple white text and a bunch of mumbo jumbo, and below that, a place where i can login.  i type in my name and password, then i just get the option to write a command line like in terminal.  what do i do?  i tried running the safe mode and it does the same thing.  also, my windows xp still works just fine.

i really hope this can be fixed, without losing any files on that partition, and it was be awesome if i can fix this without messing up any of my ubuntu settings and programs.

thanks alot

---

### Post by taurus on 2007-06-20
What happens (error message) if you run this command after you log in?

```
startx
```
Perhaps you need to reconfigure your X again.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mikealive on 2007-06-20
thanks, i'll try the startx thing tonight.  last night night i did that reconfigure part, and still no luck.  im brand new at linux so im still a rookie. i really dont want to go back to windows.  

i wont be able to try this till tonight, so if you guys can post all possible solutions throughout the day, that would be awesome, and i'll try them when i get off work tonight.  

thank you very much for all the help.

---

### Post by mikealive on 2007-06-20
any other ideas?

---

### Post by Qu4k3R on 2007-06-20
try to run on live CD then mount your partitions then verify if is something wrong.

---

### Post by mikealive on 2007-06-20
ok i'll try that. is there any step by step instructions to follow, or just do what it says on the screen?  by mounting my partitions, will this erase my previous installation and all its files and settings?

---

### Post by mikealive on 2007-06-20
also, now that i recall, i was messing with the root passwords and stuff like that, in the administration menu.  something that had to do with grouping.  would that be the cause of the problem?

---

### Post by mikealive on 2007-06-20
ok.  i did the startx thing.  heres the error i got.

fatal server error:  caugt signal 11.  server aborted.

XIO: fatal IO error 
104(connection reset by peer) on X server.  "0.0" after 0 request....

what does this mean


when i first login, right above the command line, i see this...

kinit: no resume image

by the way when i reboot, it shows the ubuntu logo like normal.  

i'm starting to get frustrated because this happened for no apparent reason.  i really dont want to go back to windows.

---

### Post by mikealive on 2007-06-20
looks like theres no fix for this?

---

### Post by mikealive on 2007-06-21
bump.

---

### Post by mikealive on 2007-06-21
is this in the wrong forum, or is my installation just broken?

---

### Post by mikealive on 2007-06-22
one more bump i promise.  then im gonna re-install ubunut and give it another shot.

---

### Post by mikealive on 2007-06-25
anymore ideas?

---

### Post by jlh68 on 2007-06-25
*There is a fix for it.  You have to go to your /etc/X11 directory and list the contents.  You have to note the xorg.cong file name that preceded the time you broke your system.  It will look like this xorg.cont.????????????? with the ? representing the YEAR, MM, DD, HHMM,X.  for example it might look similar to this xorg.conf.20070610144124*

$ cd /
$ dir
$ cd /etc/X11
$ ls
*#then note the xorg.conf.?????????????? file *
/etc/X11$ sudo rm xorg.conf   *#(this removes xorg.conf)*
$ sudo mv xorg.conf.?????????????? xorg.conf   *#(this renames the backup version)*
$sudo shutdown -r now  [I]#(this restarts the machine)
[/I]
*I hope this works for you.  It did for me.*

---

### Post by mikealive on 2007-06-25
thanks i'll try this when i get home tonight.

---

### Post by strabes on 2007-06-25
By the way, > kinit: no resume image doesn't really matter.

---

### Post by mikealive on 2007-06-25
> **jlh68 said:**
> *There is a fix for it.  You have to go to your /etc/X11 directory and list the contents.  You have to note the xorg.cong file name that preceded the time you broke your system.  It will look like this xorg.cont.????????????? with the ? representing the YEAR, MM, DD, HHMM,X.  for example it might look similar to this xorg.conf.20070610144124*

$ cd /
$ dir
$ cd /etc/X11
$ ls
*#then note the xorg.conf.?????????????? file *
/etc/X11$ sudo rm xorg.conf   *#(this removes xorg.conf)*
$ sudo mv xorg.conf.?????????????? xorg.conf   *#(this renames the backup version)*
$sudo shutdown -r now  [I]#(this restarts the machine)
[/I]
*I hope this works for you.  It did for me.*

i got to the sudo mv xorgconf?????????? part and then i get this..

missing destination file operand for xorg.conf

---

