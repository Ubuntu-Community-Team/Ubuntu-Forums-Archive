---
title: "Double kernel?"
date: 2013-02-11
forum: General Help
---

### Post by thedardanius on 2013-02-11
ok,
 
so this problem started when I decided to update some of the kernel. Im totally new to ubuntu, and at first, the software updater seemed handy. I decided to update linux headers 2.3.0-23-generic or so, but the updater continuously stopped doing its job when reaching that update. So I needed to reboot while not having finished an update (sounds dangerous even for a windows user). Next time I entered, my desktop was gone. I was like **** did I do with my OS?
So I used recovery mode and choose "repair packages", dspgor dsgk or sth like that. It seemed that it didnt do anything, it only showed: fsck by linux, cleaned sth sth..."
then I rebooted again with the powerbutton (dangerous), checked with original boot if it worked and it was ok. I decided to retry the update, but again, it frooze at that linux header. I rebooted again, and saw in advanced options for ubuntu 2 OS, ubuntu with linux 2.3.0-17 and 2.3.0-23. Did I actually download a new kernel? I though I only dowloaded the header? Or does it boot the new kernel code? Pls... Im lost in this linux world.
Then I did the same, choose dskg or sth to repair broken packages. I rebooted and started ubuntu normally, apparantly, my nvidia driver doesnt pop up in the beginnin (normally i would see nvidia logo for a split moment) and I entered the desktop without mouse, wrong resolution... OMG i hope I havent ruined enough to be resorted to reinstall my OS...

---

### Post by thedardanius on 2013-02-11
What must I do to solve this? I dont even know the problem...

---

### Post by thedardanius on 2013-02-11
what?

---

### Post by codemaniac on 2013-02-11
Please do not bump your thread more than once every 24 hours.

Thanks!!

---

### Post by SlugSlug on 2013-02-11
open a terminal and post out put of

```
df -h
```

---

### Post by thedardanius on 2013-02-11
problem:
since my resolution is changed, and i cant see/move my mouse, i cant clikc the terminal...

---

### Post by SlugSlug on 2013-02-11
In the applications menu click terminal then type in 

df -h 

and hit enter

post output here


Am just thinking problem might be that your out of space on your / or /boot partition. This would cause errors when trying to install a new kernel

---

### Post by Impavidus on 2013-02-11
Which version of Ubuntu do you have? Kernel version 2.3.0 sounds ancient. It was never used in Ubuntu. Did you mean 3.2.0? Anyway, we are at 3.2.0-37 now for Ubuntu 12.04, 3.2.0-23 is some time ago. Did you update the list of available software before updating the software itself?

And indeed, post the output of **df -h** (watch the space between the f and the -).

---

### Post by thedardanius on 2013-02-11
guys, I downloaded the 3.5.0 (sry wrong number previous posts) - 23 -genereic headers. HEADERS...does taht mean that I download a kernel or the source> Pls anyone explain me how this linux updating works.. and luckily Im not alone with this problem.
 
I previously used the 3.5.0-17-generic linux kernel with ubuntu 12.10. Since i used software updater to download new linux headers... dont know why i did that just to test out/take a look at the source. But as i said the updater ALWAYS got stuck at downlading some of these headers. I hypothese that since im missing some headers, my new kernel is incomplete!?!? When I use ubuntue with 17-generic, it all works fine. However swtiching to 23-generic, i get the previously described error. 
 
I cannont get an error report at the 23-generic, since I cant even move my mouse. I cant even access most programs, only the shortcuts.. pls this should be a small bug causing all the pain in the neck

---

### Post by thedardanius on 2013-02-11
please help.

---

### Post by oldos2er on 2013-02-11
As mentioned, please don't bump your post more than once every 24 hours.

---

