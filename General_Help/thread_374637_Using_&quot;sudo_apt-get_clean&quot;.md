---
title: "Using &quot;sudo apt-get clean&quot;"
date: 2007-03-02
forum: General Help
---

### Post by lottsm on 2007-03-02
Okay, so I got this message:

    Not enough free disk space

    The upgrade aborts now. Please free at least 159M of disk space on /var/cache/apt/archives/.     
    Empty your trash and remove temporary packages of former installations using 'sudo apt-get   
    clean'.

I have no idea how I go about "using" that.

Also, when I CTRL 2, I get:

    "

When I Shift ", I get:

    @

Thanks for your help,
Shelton

---

### Post by taurus on 2007-03-02
Try <Ctrl>x.  Then, type

```
sudo aptitude clean
```

---

### Post by ~LoKe on 2007-03-02
What does ctrl+x do? o_O

```
sudo apt-get clean
```
I don't know what this " and @ business is all about.

---

### Post by lottsm on 2007-03-02
Thank you for the quick reply.  Unfortunately, nothing happened when I keyed:

    Ctrl X

Shelton

---

### Post by taurus on 2007-03-02
I thought you need to get out of the upgrade.  Otherwise, just run the command from a terminal to clean up the cache, freeing up some space.

---

### Post by lottsm on 2007-03-02
Regarding " and @, the keys have become transposed for some reason.

Shelton

---

### Post by Kateikyoushi on 2007-03-02
You have to select the proper keyboard layout to get @ instead of ". System > preferences > keyboard.

---

### Post by lottsm on 2007-03-02
I am truly new to Linux, so I do not know how to "just run the command from a terminal".  How do I access the terminal?

Shelton

---

### Post by taurus on 2007-03-02
Applications -> Accessories -> Terminal.

---

### Post by lottsm on 2007-03-02
Hmm...the keyboard still won't work properly with those two keys, but thank you for the input; I will worry about that problem a bit later.  I am successful in accessing a "terminal" and pasting, "sudo apt-get clean".  However, at the "Password" prompt, I cannot type nor paste anything.

Shelton

---

### Post by Kateikyoushi on 2007-03-02
You can type there but it is not displayed for security reasons.
Just type in your password.

---

### Post by lottsm on 2007-03-02
I assume that that worked; there was no confirmation, just another, "ubuntu@ubuntu:~$"  My thanks, again, to all of you.  Oh, now it seems that I simply don't have enough room on this computer to install the upgrades, even after having done that.  I will just tinker with what I now have in order to see how I like Linux.  Have a good day, y'all. (I'm in Mississippi). :)

Shelton

---

### Post by taurus on 2007-03-02
What's the output of this command from a terminal?

```
df -h
```

---

### Post by lottsm on 2007-03-02
"bash: df-h: command not found"

Shelton

---

### Post by lottsm on 2007-03-02
Oops...I see that I didn't put in a space.

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop7            2.0G  1.7G  179M  91% /
varrun                252M  100K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb             10M  124K  9.9M   2% /proc/bus/usb
udev                   10M  124K  9.9M   2% /dev
devshm                252M     0  252M   0% /dev/shm
/dev/loop6            248M   33M  203M  14% /home
/dev/sdd1              38G   21G   17G  56% /media/Ext. hard driveSony DCR-PC105
/dev/sdb1              12G  6.9G  4.4G  62% /media/WIN98-SE
ubuntu@ubuntu:~$ 

Shelton

---

### Post by taurus on 2007-03-02
Looks like you only have about 2GB for / and that is not a whole lot of space if you are using Gnome or KDE.

---

### Post by lottsm on 2007-03-02
Yes, I will see about buying another hard drive soon.  Have a good night.

Shelton

---

### Post by Mr Mookie on 2008-05-06
When entering your password you will not be able to see that you are typing anything. Just enter your root password and hit enter and it will work. :)

---

