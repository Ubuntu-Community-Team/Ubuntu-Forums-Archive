---
title: "trouble editing the file apache.conf"
date: 2007-01-15
forum: General Help
---

### Post by oprogue on 2007-01-15
I feel like a total boob.

I need to edit the a apache.conf file, but when I go to save the file I receive an error saying it is read only and I don't have permission.

Ideas?  Suggestions?

](*,)

---

### Post by taurus on 2007-01-15
Applications -> Accessories -> Terminal
```
gksudo gedit apache.conf
```

---

### Post by oprogue on 2007-01-15
I had tried sudo gedit apache.conf earlier ... 

gksudo gedit apache.conf results in the error:

(gedit:29214):  GnomeUI-WARNING **: While connecting to session manager: Authentication Rejected, reason: None of the authenication protocols specified are supported and host-based authenication failed.

I attempted to use the gksudo again but only get the same error message.

There is something I'm missing here ... and I know it is easy.

---

### Post by taurus on 2007-01-15
Then try the basic text editor.

```
sudo nano -w apache.conf
```
(Hold down <Ctrl> while press x to exit.  Type Y for Yes and Return.)

---

### Post by oprogue on 2007-01-15
excellent!

what does the "-w" do??

---

### Post by taurus on 2007-01-15
So that lines are longer than 24 characters won't get "wrapped" to the next line.

---

