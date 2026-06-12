---
title: "Help!!!  Trying to Terminal Install Gftp, but getting..."
date: 2008-04-06
forum: General Help
---

### Post by robelliott2125 on 2008-04-06
Since i'm a keen tech-head, i'm trying to learn the basics of ubuntu before using guis, so when trying to install gftp, i'm getting a problem...

Hoping this is a simple fix that someone can recommend.

> robert@robert-desktop:~$ sudo apt-get install gftp
sudo: /etc/sudoers is mode 0446, should be 0440
robert@robert-desktop:~$ apt-get install gftp
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Now I haven't a clue about the above, but i'm assuming that somethings been unlocked, and I don't know what / how & why.

Hope someone can help.

Thanks.

---

### Post by ghost_ryder35 on 2008-04-06
> **robelliott2125 said:**
> Since i'm a keen tech-head, i'm trying to learn the basics of ubuntu before using guis, so when trying to install gftp, i'm getting a problem...
 
Hoping this is a simple fix that someone can recommend.
 
 
 
Now I haven't a clue about the above, but i'm assuming that somethings been unlocked, and I don't know what / how & why.
 
Hope someone can help.
 
Thanks.
is this account a member of the sudoers?
 
try 
```

su -

```
after entering that command you should be prompted for root password, enter it and you should be good :)

---

### Post by robelliott2125 on 2008-04-06
> **ghost_ryder35 said:**
> is this account a member of the sudoers?
 
try 
```

su -

```
after entering that command you should be prompted for root password, enter it and you should be good :)

Thank you ghost_ryder, tbh bud, i haven't a clue if I'm a sudoer, but i've been able to do it till trying that.

About to try the above.

Just to make sure, it should be:
```

su apt-get install gftp

```

Thanks

---

### Post by robelliott2125 on 2008-04-06
```

robert@robert-desktop:~$ su apt-get install gftp
Unknown id: apt-get
robert@robert-desktop:~$ 

```

Am i doing something wrong?

---

### Post by ghost_ryder35 on 2008-04-06
yes you are doing something wrong...it is just 
```

su -

```
then
```

apt-get install gftp

```

---

### Post by robelliott2125 on 2008-04-06
I'm now getting this:

```

robert@robert-desktop:~$ su -
Password: 
su: Authentication failure
Sorry.

```

So I tried

```

robert@robert-desktop:~$ su
Password: 
su: Authentication failure
Sorry.

```

I've even rebooted and tried.  I know the password works for everything else, so any ideas?

I've actually been considering reinstalling ubuntu anyway, cause of all the crap which has been installed / uninstalled / messed around with.

Any other ideas will be welcomed.

Thanks

---

### Post by ghost_ryder35 on 2008-04-06
> **robelliott2125 said:**
> I'm now getting this:
 
```

robert@robert-desktop:~$ su -
Password: 
su: Authentication failure
Sorry.

```
 
So I tried
 
```

robert@robert-desktop:~$ su
Password: 
su: Authentication failure
Sorry.

```
 
I've even rebooted and tried. I know the password works for everything else, so any ideas?
 
I've actually been considering reinstalling ubuntu anyway, cause of all the crap which has been installed / uninstalled / messed around with.
 
Any other ideas will be welcomed.
 
Thanks
have you set a password up for root? I belive its under
System, Administration, Users, select root and then change password
or from terminal
```

sudo passwd root

```
[http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html](http://www.debianadmin.com/enable-and-disable-ubuntu-root-password.html)

---

### Post by ghost_ryder35 on 2008-04-06
i'll probally get flamed for telling you to do that :)

---

### Post by oldos2er on 2008-04-06
> **robelliott2125 said:**
> ```

robert@robert-desktop:~$ su apt-get install gftp
Unknown id: apt-get
robert@robert-desktop:~$ 

```Am i doing something wrong?

 Ubuntu doesn't set up a root account by default; try "sudo" in place of "su."

---

### Post by robelliott2125 on 2008-04-07
> **oldos2er said:**
> Ubuntu doesn't set up a root account by default; try "sudo" in place of "su."

[http://ubuntuforums.org/showpost.php?p=4664273&postcount=1](http://ubuntuforums.org/showpost.php?p=4664273&postcount=1)

Already done.

Sudo and su - are not working and coming up with the above errors.

I'm at a loss for ideas, i've only just changed from Whinedoze, so my ideas stretch to that, hence the need to learn everything from scratch for Ubuntu, so anymore ideas?

---

### Post by robelliott2125 on 2008-04-07
Just to update this...

I've just tried going through Synaptec and it part loads, then closes the window.

I'm just trying to load an FTP Prog!!!  Ghah!

<btw, add / remove works, but would rather the terminal / synaptec way>

Seriously considering now a reinstall.

---

### Post by robelliott2125 on 2008-04-08
Just to update this a little more...

I had someone recommend trying this yesterday:

```

sudo chmod 440 /etc/sudoers
```

But it returned with this still:

```

robert@robert-desktop:~$ sudo chmod 440 /etc/sudoers
sudo: /etc/sudoers is mode 0446, should be 0440
```

Anyone else got any ideas?

---

### Post by oldos2er on 2008-04-08
Have you tried "sudo chmod 0440 /etc/sudoers"?

 Another thing to try would be to boot from the live cd (if you have one), and change permissions from there.

---

### Post by robelliott2125 on 2008-04-11
> **oldos2er said:**
> Have you tried "sudo chmod 0440 /etc/sudoers"?

 Another thing to try would be to boot from the live cd (if you have one), and change permissions from there.

Hi Ann,

Thanks for your reply, i've been lazy and done it the cheats way out, so I've reinstalled.

I didn't like doing it, since i'd rather learn stuff, but it got me back up and running.

So now just need to figure out how to sort out my gfx card prob, which nobody's helping me out with on another thread.

Thanks to all who helped me with this issue, and hopefully I'll be seeing you all around!!!

---

