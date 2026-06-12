---
title: "login - endless reprompt"
date: 2007-01-01
forum: General Help
---

### Post by imak on 2007-01-01
I've been running Ubuntu successfully for some months.

Now when I power up the PC:

- Ubuntu displays the login screen as usual
- I enter the usual login details
- Ubuntu switches to a blank (black) screen for a second or two, with just a prompt (machine name + "login:")
- Ubuntu redisplays the login screen

If I select shutdown, the shutdown looks normal.

The only unusual thing I did during the last working session was try to install an additional language, which failed.

Is there any way to repair Ubuntu without losing all the emails and personal files I have on the system?

---

### Post by taurus on 2007-01-01
At the GUI login screen, press <Ctrl><Alt>F2 to get to a console and log in with your username and password.  At the prompt, paste the output of this command here!

```
df -h
```

---

### Post by imak on 2007-01-02
> **taurus said:**
> At the GUI login screen, press <Ctrl><Alt>F2 to get to a console and log in with your username and password.  At the prompt, paste the output of this command here!

```
df -h
```

[FONT="Lucida Console"]

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda5             2.8G  2.8G     0 100% /
varrun                189M  120K  188M   1% /var/run
varlock               189M  4.0K  189M   1% /var/lock
udev                  189M   92K  188M   1% /dev
devshm                189M     0  189M   0% /dev/shm
lrm                   189M   19M  170M  10% /lib/modules/2.6.15-27-386/volatile
/dev/hda1             6.0G  2.4G  3.7G  40% /media/hda1
/dev/fd0              1.4M     0  1.4M   0% /mnt/adrive[/FONT]

I can see the 100% doesn't look good, but I'm surprised by the 0MB - just deleted about 30MB of files, so expected something higher than 0MB free...

---

### Post by fsando on 2007-01-04
Hi, I read somewhere that fiddling with language settings may change your keyboard layout which will also be in effect at logon time - according to my memory it would give you exactly that behavior.
I'm very new to linux so that's what I've got but it may give a clue as to what to search for.

---

### Post by imak on 2007-01-04
Thanks for the suggestions and the disc space command.

I managed to get a little free space using 'apt-get clean' that I found in another post, then logged in OK and removed some unwanted packages to give me a bit more breathing space.

---

### Post by taurus on 2007-01-04
2.8GB for / is not a whole lot of space so you just need to keep your eyes on the disk space...  Remove items in ~/.Trash & /root/.Trash whenever you can to free up some space.

---

