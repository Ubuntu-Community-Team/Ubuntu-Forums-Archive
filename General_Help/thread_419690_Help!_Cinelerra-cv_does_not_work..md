---
title: "Help! Cinelerra-cv does not work."
date: 2007-04-23
forum: General Help
---

### Post by lakersforce on 2007-04-23
I want to use this excellent video-editing tool, but when I run it I get the following message:

```
rune@rune-desktop:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on Sun Apr 15 00:09:28 UTC 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
Illegal instruction (core dumped)
```

---

### Post by bpont on 2007-04-23
I am having a similar problem.

I follow these steps to install cinelerra on my system:

[http://www.kiberpipa.org/~gandalf/ubuntu/README](http://www.kiberpipa.org/~gandalf/ubuntu/README)

Everything install smoothly, apparently...no error messages.

When I try running cinelerra, I get the following error message:

```
cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader
```

...and the program won't open.

I am copying gandalf -at- owca.info and hopefully someone will be able to help us both get cinelerra up and running!  :(

---

### Post by JureCuhalev on 2007-04-23
Hi,

I'm the maintainer of these packages. There is also a number of other people writing about this in comments ([http://www.kiberpipa.org/~gandalf/blog/?p=77]("http://www.kiberpipa.org/~gandalf/blog/?p=77")). It seems there is a problem with 3d accelerated opengl drivers both on nvidia and ati.

I'll see if I can compile non-opengl version and see how that works.

---

### Post by JureCuhalev on 2007-04-25
> **JureCuhalev said:**
> I'll see if I can compile non-opengl version and see how that works.

I've uploaded the new build and it seems to work for most of people having errors before.

---

### Post by florian_roger on 2007-04-27
For me the problem is this message when I launch the program:
```
florian@florian:~$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecClose
```
I would like to use cinelerra on Feisty...
Thanks for help,
florian

---

### Post by antimoni on 2007-05-01
I am still getting this error:
```
antimoni@olkkari:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on Tue Apr 24 13:45:37 UTC 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
Illegal instruction (core dumped)
antimoni@olkkari:~$ 

```

My system is: Feisty, Athlon XP, Nvidia GeForce 7600 GS (restricted driver)

I tried i686 and Athlon Xp versions and both give same error. I also tried edgy version (deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./) and it seems to work somehow.

---

### Post by bpont on 2007-05-09
> **JureCuhalev said:**
> Hi,

I'm the maintainer of these packages. There is also a number of other people writing about this in comments ([http://www.kiberpipa.org/~gandalf/blog/?p=77]("http://www.kiberpipa.org/~gandalf/blog/?p=77")). It seems there is a problem with 3d accelerated opengl drivers both on nvidia and ati.

I'll see if I can compile non-opengl version and see how that works.

Now Cinelerra opens, but I get this error message:

```
void MWindow::init_shm():Warning:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

---

### Post by Thomaseov on 2007-05-15
> **bpont said:**
> Now Cinelerra opens, but I get this error message:

```
void MWindow::init_shm():Warning:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

I'm getting the same error message straight from install.  I've got an athlonx2 4200 running feisty i386.  I installed cinelerra from the feisty i686 debs on the cinellera page.  I sudoed the code in the quote, but still got the same error.  Anyone know what this is all about and how to fix it?

thomas

---

### Post by antimoni on 2007-05-17
```

void MWindow::init_shm():Warning:/proc/sys/kernel/shmmax is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax

```
To get rid of this error, I typed this in terminal:
```
antimoni@olkkari:~$ sudo -s
Password:
root@olkkari:~# echo "0x7fffffff" > /proc/sys/kernel/shmmax
root@olkkari:~# exit

```
and to make it permanent (from [this post]("http://osdir.com/ml/video.cinelerra-cv.general/2006-12/msg00077.html")):
```
antimoni@olkkari:~$ sudo gedit /etc/sysctl.conf
Password:

```
and added these lines:
```
# make cinelerra happy
kernel.shmmax = 2147483647
```
save file and quit gedit.

BTW I still use Edgy version of Cinelerra.

---

### Post by Thomaseov on 2007-05-19
antimoni,

Thanks.  Editing sysctl.conf did the trick and now works fine.

Thomas

---

### Post by Spam Banjo on 2007-08-09
> **antimoni said:**
> and added these lines:
```
# make cinelerra happy
kernel.shmmax = 2147483647
```

Didn't work for me. I had:
```
# make cinelerra happy
kernel.shmmax = 2147483647=1
```
In that file anyway, but added the line you suggested.

No change.

Can anyone help me here?

---

