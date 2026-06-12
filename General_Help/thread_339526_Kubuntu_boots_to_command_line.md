---
title: "Kubuntu boots to command line"
date: 2007-01-15
forum: General Help
---

### Post by WarLocke on 2007-01-15
After fixing some booting problems, Kubuntu will now boot into the command line. I can login, so I type "startx" and it gives me this error: 

```

xauth:   creating new authority file /home/locke/.serverauth.44220


Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

```

and then after I wait around 30 seconds, it logs me into KDE.  I can end my session and it will take me back to the command line.  If I type "startx" again, it will load up without the error.

So my questions are:
1. How do I set it up to boot back into the GUI login?
2. Should I worry about that error?

Thanks for any help in advance!

---

### Post by WarLocke on 2007-01-15
nvm, I am going to reinstall Kubuntu in the morning....

---

### Post by Mike_Longbow on 2007-01-16
Hold on! hehe
I think there shoud be a problem regarding kdm, try running:
```
sudo update-rc.d kdm defaults
```
That should re-enable kdm (the login manager) to start at boot.
Lastly, if that doesn't work you can just reinstall it.
```
sudo apt-get install kdm
```

---

### Post by Mike_Longbow on 2007-01-16
Oh, and about that error, it means that there's already a graphical session running on one of the virtual terminals, altought I don't think you should worry about that, you can try using: 
Ctrl+Alt+F1, or Ctrl+Alt+F2, or Ctrl+Alt+F3, ...F4, ....F5, ....F6, ...F7
to navigate trough the virtual terminals and see if something is running on them.

---

### Post by WarLocke on 2007-01-16
> **Mike_Longbow said:**
> Hold on! hehe
I think there shoud be a problem regarding kdm, try running:
```
sudo update-rc.d kdm defaults
```
That should re-enable kdm (the login manager) to start at boot.
Lastly, if that doesn't work you can just reinstall it.
```
sudo apt-get install kdm
```

I appreciate your help, altho, I tried to fix it on my own and I think I just made it worst... (hence the post "I will reinstall in the morning")  

I am not too worried, I already had everything backed up anyway.  :-D 

Thank you again.  If I run into this problem again, I now have my answer :p

---

### Post by Mike_Longbow on 2007-01-16
> **WarLocke said:**
> I appreciate your help, altho, I tried to fix it on my own and I think I just made it worst... (hence the post "I will reinstall in the morning")  

I am not too worried, I already had everything backed up anyway.  :-D 

Thank you again.  If I run into this problem again, I now have my answer :p

Hehehe... Ok, ok...
We're all here to help (and be helped, thankfully :p )
Happy ubuntuing!

---

### Post by tansu on 2008-03-20
I just installed kubuntu desktop and exactly the same problem.
I tried the methods above but not worked..
What else can I do?

---

