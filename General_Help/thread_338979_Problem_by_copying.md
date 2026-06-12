---
title: "Problem by copying"
date: 2007-01-15
forum: General Help
---

### Post by ragtime on 2007-01-15
Hi I got some confusing problem, it is, I want to install some packets for my scratchbox,
and I want to put them in the packages folder,Than comes , that I dont have the permission to  write to this folder, so I thought I 'll do this over command line, so I put up some root shell and also come : Permission denied.....](*,) 
So, can anyone tell me please what I have to do, to copy sucessfully?
It would be very nice ^^

regards Pascal

---

### Post by taurus on 2007-01-15
Put the "sudo" in front of the command if you want to write to any place outside your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by majoridiot on 2007-01-15
> **taurus said:**
> Put the "sudo" in front of the command if you want to write to any place outside your $HOME directory.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
sudo cp /location/of/source/file /location/of/destination
```

---

