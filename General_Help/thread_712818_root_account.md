---
title: "root account?"
date: 2008-03-02
forum: General Help
---

### Post by chrisx16x2008 on 2008-03-02
ok i was playing around with ubuntu and i took my admin rights away from myself on accident, i know they're gone because the System -> Administration is half gone.  I tried enabling the root account by doing sudo passwd root and it said password: i type my password and that as far as it went then i tried su root and it said password: i typed the same password and it said Authentication Failed, and now everytime i type sudo passwd root nothing happens.  can some help me get my admin rights back?

---

### Post by firebadger on 2008-03-02
In the command line type...

```
groups
```

You should get a list of groups you are a member of and if you can't see admin then you have indeed lost your admin rights.

To fix boot into single user (or recovery mode at the boot menu).  You will automatically be root.  Now use the command vigr to edit the groups file where you can add your username to the end of the admin line.  Save and reboot.

---

### Post by chrisx16x2008 on 2008-03-02
there is not boot selection screen is goes straight into Ubuntu and i tried using the live CD but it didnt load into the CD even when i pressed esc to force it to.

---

### Post by chrisx16x2008 on 2008-03-02
i got to recovery mode and the admin line looks like.. admin:x:110:   i type chris at the end but it acts weird sometimes it deletes the admin line and sometimes it turns out like.. admin:x:11$hris

---

### Post by amingv on 2008-03-02
This user had a problem similar to yours, try the solution on this page:
[http://ubuntuforums.org/showthread.php?t=713283&page=3](http://ubuntuforums.org/showthread.php?t=713283&page=3)

---

