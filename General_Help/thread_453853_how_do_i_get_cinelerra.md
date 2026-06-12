---
title: "how do i get cinelerra?"
date: 2007-05-24
forum: General Help
---

### Post by atlfalcons866 on 2007-05-24
cinelerra i cant find it in package manager

---

### Post by tgoose on 2007-05-24
edit: Oops, I quoted myself instead of replying!

---

### Post by tgoose on 2007-05-24
[QUOTE=tgoose;2715829]Cinelerra hasn't (as far as I know) been properly compiled for Ubuntu, which is why it's neither in the normal package manager nor Ubuntu Studio. I think the Studio team are working on this, which hopefully means by the time of Gutsy this will be possible and simple. At the minute I don't know of any packages of it, which means that the only way to install it is to compile it yourself (this is not really recommended unless you know what this entails!)

edit: Sorry, I was wrong about there not being any packages - I just found some at [http://cv.cinelerra.org/getting_cinelerra.php](http://cv.cinelerra.org/getting_cinelerra.php)

To make Cinelerra available from Synaptic, you need to go to 

System > Administration > Software Sources

Then click "Third-Party Software"

Then "Add..."

and copy and paste one of these, depending on what processor you have

For i686 (this should be fine if you have neither of the others)
```
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
```
For AthlonXP
```
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
```
For Pentium 4
```
deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./
```

Then Cinelerra should appear like any other programme in the Package Manager.

---

### Post by rapsball4 on 2007-05-27
Hi,

I'm brand-new to Ubuntu (a little bit of experience with Suse) and am also trying to get Cinelerra installed.  I also tried to do it the way it is mentioned on the official site to no avail, and this alternate way isn't working either.  I've added the sources, but it still isn't showing up in the "Add/Remove" or in "Automatix".  When I try to do it in the terminal by typing "apt-get update" and "apt-get install cinelerra" as it says on that site, it doesn't work and won't log me into the superuser to try from that.

Any help would be greatly appreciated.

---

### Post by dawillonline on 2007-05-28
You have to type it like this:

```
sudo apt-get update
```

```
sudo apt-get install cinelerra
```

---

### Post by rapsball4 on 2007-05-28
Alright, that seemed to work to install it.  When I opened it, I got the error message:

void MWindow::init_shm(): WARNING: /proc/sys/kernel/shmmax is 0x2000000, which is too low
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax

How can I do this if the Terminal still won't let me sign in as root?

---

### Post by rapsball4 on 2007-05-28
Nevermind, there's something different messed-up with this.  It was accepting my root password for everything except in the terminal.  So I found somewhere to change it and it wasn't the same as I was entering everywhere (1 more character) including the one to go in and see that.  I changed it to the one that I've been entering, and it worked.  I don't understand this, but...works now, and that's the most important thing to me.  Thanks again.

---

### Post by tgoose on 2007-05-29
> **rapsball4 said:**
> Nevermind, there's something different messed-up with this.  It was accepting my root password for everything except in the terminal.  So I found somewhere to change it and it wasn't the same as I was entering everywhere (1 more character) including the one to go in and see that.  I changed it to the one that I've been entering, and it worked.  I don't understand this, but...works now, and that's the most important thing to me.  Thanks again.

This sounds a bit odd. There shouldn't **be** a root password by default in Ubuntu. Unless you've edited the configuration files it should be your user password that authenticates you with sudo. If that's what you meant then that's OK, but if you're actually using su now instead of sudo then things might not work as expected.

---

