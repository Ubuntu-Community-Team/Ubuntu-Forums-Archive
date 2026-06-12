---
title: "Kernel and other questions"
date: 2013-02-11
forum: General Help
---

### Post by rnerwein on 2013-02-11
> **thedardanius said:**
> ok,
 
so this problem started when I decided to update some of the kernel. Im totally new to ubuntu, and at first, the software updater seemed handy. I decided to update linux headers 2.3.0-23-generic or so, but the updater continuously stopped doing its job when reaching that update. So I needed to reboot while not having finished an update (sounds dangerous even for a windows user). Next time I entered, my desktop was gone. I was like **** did I do with my OS?
So I used recovery mode and choose "repair packages", dspgor dsgk or sth like that. It seemed that it didnt do anything, it only showed: fsck by linux, cleaned sth sth..."
then I rebooted again with the powerbutton (dangerous), checked with original boot if it worked and it was ok. I decided to retry the update, but again, it frooze at that linux header. I rebooted again, and saw in advanced options for ubuntu 2 OS, ubuntu with linux 2.3.0-17 and 2.3.0-23. Did I actually download a new kernel? I though I only dowloaded the header? Or does it boot the new kernel code? Pls... Im lost in this linux world.
Then I did the same, choose dskg or sth to repair broken packages. I rebooted and started ubuntu normally, apparantly, my nvidia driver doesnt pop up in the beginnin (normally i would see nvidia logo for a split moment) and I entered the desktop without mouse, wrong resolution... OMG i hope I havent ruined enough to be resorted to reinstall my OS...
hi follow
got the same probelm and they got a post from me. stay cool - hope they will answer.
but that shows me - i am not alone. every thing is working ok ( but i bet there is a hidden bug anywhere). 
cheers   :confused:

---

### Post by rnerwein on 2013-02-11
> **SlugSlug said:**
> open a terminal and post out put of

```
df -h
```
hi
what do you mean with "df -h" ?

cheers

---

### Post by rnerwein on 2013-02-11
> **codemaniac said:**
> Please do not bump your thread more than once every 24 hours.

Thanks!!
hi forum stuff
but for me it looks (see a lot of threads/posts) there is a "little" big problem - isn't it ?
can you tell me please what kernel i am running ? in /proc i see ***37 in menu.lst i see ****38 grub shows me only very old kernels
but not the newest one - (glad to have suse and solaris too). i guess something is going the wrong road at the moment - sorry
have a fun day
cheers

---

### Post by rnerwein on 2013-02-11
> **SlugSlug said:**
> In the applications menu click terminal then type in 

df -h 

and hit enter

post output here


Am just thinking problem might be that your out of space on your / or /boot partition. This would cause errors when trying to install a new kernel
hi
read my post - i debuged it a litle. on my system it isn't a space problem - it is just a bug.
some perl-scripts hang i a read and got no response (i make a fault too - i haven't degug it deeper)
have a nice day ( better to stay in rio today :-) )
cheers

---

### Post by rnerwein on 2013-02-11
> **Impavidus said:**
> Which version of Ubuntu do you have? Kernel version 2.3.0 sounds ancient. It was never used in Ubuntu. Did you mean 3.2.0? Anyway, we are at 3.2.0-37 now for Ubuntu 12.04, 3.2.0-23 is some time ago. Did you update the list of available software before updating the software itself?

And indeed, post the output of **df -h** (watch the space between the f and the -).
hi netherlands (52° N 6° E)
i know about that version - but it is an LTS version and in appendix you will see i run to newest updates ( i tried to update to the newest kernel. it's still there in / but my system is still booting the .....37 and :confused: no error messages because my / shows me:
lrwxrwxrwx 1 root root 29 Feb 11 08:58 /vmlinuz -> boot/vmlinuz-3.2.0-38-generic
lrwxrwxrwx 1 root root 29 Jan 29 08:56 /vmlinuz.old -> boot/vmlinuz-3.2.0-37-generic
and grub only shows me the "37".
and for you: 
here is my df -h for my primary (system disk) - there is a plenty of space.
Dateisystem    Größe Benutzt Verf. Verw% Eingehängt auf
/dev/sda7        68G    7,4G   58G   12% /
udev            1,8G     12K  1,8G    1% /dev
tmpfs           741M    992K  740M    1% /run
none            5,0M       0  5,0M    0% /run/lock
none            1,9G    624K  1,9G    1% /run/shm
/dev/sda8       157G     39G  111G   26% /home
/dev/sdf8       101G     89M  101G    1% /media/any_ntfs
oh - as you see i ain't get a seperata boot-partition
cheers

---

### Post by oldos2er on 2013-02-11
I've moved your posts to their own thread. It's very confusing for everyone when you ask questions in someone else's thread, so please start your own thread instead of "hijacking" someone else's. Thanks.

---

### Post by rnerwein on 2013-02-13
> **oldos2er said:**
> I've moved your posts to their own thread. It's very confusing for everyone when you ask questions in someone else's thread, so please start your own thread instead of "hijacking" someone else's. Thanks.
hi
i realy think you are an OLDOS2er. why you collect all my "very" different posts to one.
please the contense before. i am a unix user since 1984.
sorry i have to post this - but don't boredom me please.
but there is a apendix - may you give me an answer about this little problem.
my grub menue shows me only the *37 kernel. but you want have a look at my menu.lst (it's in /boot/grub).
oh yes i run all updates and update-grub and and and ..... --> no changes where made in the grub.cfg
and suprise here is my / :
lrwxrwxrwx 1 root root 29 Feb 11 08:58 /vmlinuz -> /boot/vmlinuz-3.2.0-38-generic
lrwxrwxrwx 1 root root 29 Jan 29 08:56 /vmlinuz.old -> /boot/vmli boot/vmlinuz-3.2.0-37-generic
don't ask me to look in /proc or /sys i did that. the kernel -->  /boot/vmli boot/vmlinuz-3.2.0-37-generic
is actually running !!!
oh sorry - i edit the post and i am now not able to send the apendix (don't know if it is possible). see my next post.
by the side: unix/linux is very very different to OS2
cheers

---

### Post by rnerwein on 2013-02-13
> **rnerwein said:**
> hi
i realy think you are an OLDOS2er. why you collect all my "very" different posts to one.
please the contense before. i am a unix user since 1984.
sorry i have to post this - but don't boredom me please.
but there is a apendix - may you give me an answer about this little problem.
my grub menue shows me only the *37 kernel. but you want have a look at my menu.lst (it's in /boot/grub).
oh yes i run all updates and update-grub and and and ..... --> no changes where made in the grub.cfg
and suprise here is my / :
lrwxrwxrwx 1 root root 29 Feb 11 08:58 /vmlinuz -> /boot/vmlinuz-3.2.0-38-generic
lrwxrwxrwx 1 root root 29 Jan 29 08:56 /vmlinuz.old -> /boot/vmli boot/vmlinuz-3.2.0-37-generic
don't ask me to look in /proc or /sys i did that. the kernel -->  /boot/vmli boot/vmlinuz-3.2.0-37-generic
is actually running !!!
oh sorry - i edit the post and i am now not able to send the apendix (don't know if it is possible). see my next post.
by the side: unix/linux is very very different to OS2
cheers
hope the upload works

---

