---
title: "[SOLVED] can't view xp partiton whith ubuntu"
date: 2008-06-04
forum: General Help
---

### Post by se user on 2008-06-04
i can't view my xp partition (i have two diver in xp c and a d) i can't view the c drive i get a error (see attached image)

---

### Post by rraj.be on 2008-06-04
This shows that

```
You jhave not shut down your windows in last usage.
```

you might have hibernated or just restarted.

else you might have just turned off the system.

Windows locks its NTFS drives when its being mounted in it.

It is not a big issue.

the solution is

```
Just get back into your windows.

Shut it down properly
```

Again boot into your ubuntu and you can see all drives and you can mount all of them.

---

### Post by se user on 2008-06-04
i am little confused how do i shut down xp properly then?

---

### Post by leito666 on 2008-06-04
Try this, go to windows command console, and type: 

chkdsk /f  

then reboot and select windows again so chkdsk will start working.

---

### Post by rraj.be on 2008-06-04
Nothing to do any thing specialy.


```
Just get into windows and shut it down.

wait till your computer turn off.
```

Thats all.

Hibernating or restarting windows could lead to this problem.

so always shut down your windows before geting into ubuntu.

---

### Post by se user on 2008-06-04
thanks rraj.be it woks now i can get my work from xp and put it on ubuntu thanks again

---

### Post by rraj.be on 2008-06-04
if you feel that the post really helped you and if you want to thank any one you can just click the MEDAL symbol near at the bottom of all each post near the EDIT QUICK REPLY icons.

```
Mark a thread as solved if its solved.
```

See my signature for further details

To mark solved click on ```
Thread tools at the top and click "mark this thread as solved"
```

---

### Post by se user on 2008-06-04
done

---

### Post by rraj.be on 2008-06-04
Mark solved everytime because 

-->another user may have same problem and he/she may see this for solution.


-->even you may search for solution for this same problem again after a week or two.

At that time it will be helpfull.

Bye. good night.

---

### Post by se user on 2008-06-05
how do i make the xp drives mount on start up? so they show on the desktop?

---

### Post by rraj.be on 2008-06-05
Just un mount all NTFS drives by right clicking on them and selecting unmount.

Go to

```
Application's-->system tools-->NTFS configuration tools
```

Select each NTFS drive and select mount points to them as 

```
  /media 
```


you can chose acording to your wish too.


Then click Apply.

It will show another window  asking 


```
select enable write support for internal drives
```

Click ok.


now each time when you boot all your NTFS drives will be mounted Automatically.

---

