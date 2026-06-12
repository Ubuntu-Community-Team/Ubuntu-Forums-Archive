---
title: "How do I get permissions to edit /etc/fstab?"
date: 2008-05-08
forum: General Help
---

### Post by grs on 2008-05-08
I'm trying to use vi through the terminal to edit the /etc/fstab file so I can mount a drive from my Samba server.
When I try to edit the file with vi I get a message saying its readonly. From what I've researched I need to be logged in as root but Ubuntu doesn't have root, or at least its locked out. and I should use sudo, but I can't get this to work either.

Can someone tell me how I can go about editing the file?

---

### Post by Whiffle on 2008-05-08
sudo vi /etc/fstab

sudo gives you root permissions.  Ubuntu uses this in place of a root account.

---

### Post by amingv on 2008-05-08
```
sudo vi /ect/fstab
```

---

### Post by grs on 2008-05-08
Thought you might say that. I had a go at the sudo command and here is the reply I got

E325: ATTENTION
Found a swap file by the name "/etc/.fstab.swp"
          owned by: root   dated: Thu May  8 15:30:04 2008
         file name: /etc/fstab
          modified: YES
         user name: root   host name: ubuntu
        process ID: 22400
While opening file "/etc/fstab"
             dated: Thu May  8 13:31:48 2008

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/fstab"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.fstab.swp"
    to avoid this message.
"/etc/fstab" 9 lines, 480 characters


I hit enter and the file open for editing I hit 'i' to insert text but when I use the arrow keys to move around up produces an A, left - B, down - C and right - D. I've only used vi on a ClarkConnect machine which I think is based on Red Hat, maybe it runs slightly differently?

---

### Post by tamoneya on 2008-05-08
you might feel more comfortable in gedit.  Hit alt-F2 and type ```
gksudo gedit /etc/fstab
```

---

### Post by grs on 2008-05-08
gksudo gedit /etc/fstab

That opens up the text editor in a separate window, typing alt and f2 brings up a small windows to run an application. But it does allow me to edit and save the file.
Thanks

---

### Post by tamoneya on 2008-05-08
sorry i missed the part about doing it through terminal.  Use nano instead of vim or vi then.

---

### Post by FakeOutdoorsman on 2008-05-08
Make sure to create a backup before editing your fstab file:
```
sudo cp /etc/fstab /etc/fstab.bak
```
or
```
sudo cp /etc/fstab{,.bak}
```

Also, vi acts kind of strange for me in Ubuntu so I usually use vim instead.

---

### Post by grs on 2008-05-08
> **FakeOutdoorsman said:**
> Make sure to create a backup before editing your fstab file:
```
sudo cp /etc/fstab /etc/fstab.bak
```
or
```
sudo cp /etc/fstab{,.bak}
```

Also, vi acts kind of strange for me in Ubuntu so I usually use vim instead.

I did try vim too but I got a message something about swap files and gave me a choice of 4 or 5 files to select, I didn't bother with it as tamoneya posted about gksudo by the time I got back o the forum!

---

