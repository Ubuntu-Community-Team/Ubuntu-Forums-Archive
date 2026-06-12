---
title: "become SUPER USER?"
date: 2008-03-07
forum: General Help
---

### Post by cabal2000 on 2008-03-07
I am very new at this. I basically got it installed the past few days working the bugs out and installing programs via add/remove. I am trying the install the newest ATI drivers but its telling me I need to be the SUPER-USER. I am the only using the system and wish to change the setting to make me the the super user. How do I do this?
I am using 7.10 with all the updates.

Much thx

---

### Post by taurus on 2008-03-07
Just put the sudo in front of the command that you need to run.  That would give you the root privilege.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by cabal2000 on 2008-03-07
that some what works but the problem here is that the file is a .run and it opens in it oun window. I also wish to simply cut and paste a skin file to the amsn folder but it won't let me do it.

---

### Post by taurus on 2008-03-07
From a terminal, install it like

Applications -> Accessories -> Terminal
```
sudo ./filename.run
```
And if you want to copy something outside of your $HOME directory, just use 

```
gksudo nautilus
```
Now, you have the ability to write or move whatever you want to wherever you want.

---

### Post by cabal2000 on 2008-03-07
I have the file saved to my desktop. It called
ati-driver-installer-8-3-x86.x86_64.run
How do I install this?
It would be much easier if I were defaulted as the super user.

---

### Post by taurus on 2008-03-07
I am not sure why you keep insisting on being or login as super user.  Just include the sudo/gksudo in front and it works even better.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 ati-driver-installer-8-3-x86.x86_64.run
sudo ./ati-driver-installer-8-3-x86.x86_64.run
```

---

