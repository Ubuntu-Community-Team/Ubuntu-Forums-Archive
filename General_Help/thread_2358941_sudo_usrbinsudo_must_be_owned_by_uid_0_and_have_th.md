---
title: "sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set"
date: 2017-04-19
forum: General Help
---

### Post by sasab on 2017-04-19
N00b that I am, I have ran chown command improperly and now i have this error
```
sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set

```I can't use sudo. I can't remember exactly what I did. It's a remote Ubuntu 14.04 as web server. I have root access over putty.

So i tried this
```
chown root:root /usr/bin/sudo && chmod 4755 /usr/bin/sudo
```
and now I have different output when using sudo chown
```
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'sudo: /usr/lib/sudo/sudoers.so must be owned by uid 0
sudo: fatal error, unable to load plugins

```
Be gentle

---

### Post by Irihapeti on 2017-04-19
What was the original "chown" command that you ran incorrectly? That may give us some idea how to proceed from here.

---

### Post by sasab on 2017-04-19
I can't remember, but i wanted to get ownership to current admin user for all subfolders while in that folder
Maybe something like ```
sudo chown mario:mario / -R
```

---

### Post by howefield on 2017-04-19
> **sasab said:**
> I can't remember...

Have a look for it in your ~/.bash_history file, it keeps a history of previously entered commands.

---

### Post by Irihapeti on 2017-04-19
You're not the only one who's done this. I remember doing something very similar when I was new to Ubuntu. I ended up backing up my personal files and reinstalling.

Unfortunately, I think it's very likely that you'll have to do the same. From memory, I've not seen anyone recover from this without reinstalling.

Of course, I'd be glad to be proven wrong, and if anyone else can offer better advice, then they're welcome to speak up.

---

### Post by sasab on 2017-04-19
You think I know how to do that? I managed to do it with vim.
I think It was one of these. It was a couple of days ago.
```

sudo chown marioftp:ftpaccess Ajmo/ -Rsudo chown marioftp:ftpaccess Ajmo/ -R
sudo chown mario:mario / -R
sudo chown mario:mario marioftp/ -R

```

---

### Post by Irihapeti on 2017-04-19
This one:

```
sudo chown mario:mario / -R
```

would definitely be difficult to recover from. Unfortunately, trying to reverse it with
```
sudo chown root:root / -R
```

doesn't work. I only messed up /usr or /usr/bin, and I couldn't reverse the damage.


Unless someone else chimes in with a solution, I unfortunately think you need to investigate how to reinstall. That will depend on your server setup and how easy it is to get access.

---

### Post by sasab on 2017-04-19
I have done root chown on everything it prompted me to and i can at least do the sudo command now and the website works.
Who knows what I will find wrong in the future but I can do something now.

---

### Post by Irihapeti on 2017-04-19
Good to hear that it's working.

---

### Post by sasab on 2017-04-19
That works, but now i can't logon to my FTP user marioftp. winscp and putty not working. Tried to change password with root user for marioftp and still won't connect. It must be the same reason. I just don't know how to fix it.

---

### Post by ajgreeny on 2017-04-19
I think you are going to go from one permissions/ownership problem to another, and that you will never get to a situation where you can trust your OS to do what is should, when it should.

Regrettably I believe that you will be best served by accepting the mistake, reinstalling, and making sure you never use a recursive chown command like that again within the root filesystem.

A reinstall of a Ubuntu OS takes me about 30 minutes or often less; trying to sort out your problem will take for ever, and you will still not be certain all is as it should be.

---

### Post by sasab on 2017-04-20
Can you tell me exactly what i have done?
Did i change ownership to mario user for the entire filesystem?

---

### Post by Irihapeti on 2017-04-20
> **sasab said:**
> Can you tell me exactly what i have done?
Did i change ownership to mario user for the entire filesystem?

Yes. You set the ownership of the entire system to mario.

The filesystem has a lot of different users besides root. That's what makes it virtually impossible to go back and fix the ownership settings.

---

### Post by sasab on 2017-04-20
I don't have enough hands for facepalming.

---

### Post by Irihapeti on 2017-04-20
As I mentioned, I did something very similar. Except it wasn't the whole file system, but it still made a complete mess of things.

I remember another crazy thing I did. I wanted to remove all backup files - that is, files ending with a ~, from the top two levels of the whole filesystem. Don't ask me why, because I don't remember now.

I do remember that, instead, I removed *all* the files in the top two levels. :oops: So of course, nothing worked, and I had to reinstall. Good backups at least helped.

I wouldn't mind betting that quite a few long-time users have crazy stories of this kind, though they might not want to talk about them. One thing at least, having done this sort of thing once, you're highly unlikely to do it again. :)

---

### Post by ajgreeny on 2017-04-20
> **Irihapeti said:**
> I wouldn't mind betting that quite a few long-time users have crazy stories of this kind, though they might not want to talk about them. One thing at least, having done this sort of thing once, you're highly unlikely to do it again. :)

Oh yes, indeed we, or I do!
As you say, I try to keep quiet about such silly activities, however, unless it will help someone make a decision when in a situation such as sasab's.

Reinstalling is usually a last resort but in this situation I believe it will be impossible to ever restore all the ownerships as they were previously, therefore it it probably the one and only option available.

Think of it as a lesson learned the hard way!
At least, as Irihapeti says, you are very unlikely to do it again.

---

