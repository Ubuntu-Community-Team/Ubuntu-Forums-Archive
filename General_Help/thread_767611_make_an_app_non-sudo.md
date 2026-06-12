---
title: "make an app non-sudo?"
date: 2008-04-25
forum: General Help
---

### Post by oddworld on 2008-04-25
I need to run "sudo opendchub" at startup, but it only works as sudo.
If you run opendchub as non-sudo the app runs but with incorrect settings.
Is there any way to have opendchub run at boot with sudo privileges?

---

### Post by natrixgli on 2008-04-25
I know you could probably write a script to run it at boot, but an easier approach might be to use Webmin - a web based system administration tool. It allows you to create commands that run (as any user) at startup. 

You can get the .deb package from [http://www.webmin.com](http://www.webmin.com)

After it's installed, go to [https://localhost:10000](https://localhost:10000) and log in as a user with admin privileges and look for "startup and shutdown commands" or some such business....

If the machine is internet facing you might consider restricting logins by IP.

Cheers,

-n8

---

### Post by Novus on 2008-04-25
Im not sure this is what you want to do, but the way I'd do it is to make sudo never ask for the password when you run the command..

```
$ sudo visudo
```

in there add the line

```
ALL    ALL = NOPASSWD: /PATH/TO/THE/BIN
```

That will allow all users on all hosts to run the bin without being prompted for the password. the first ALL can be changed to your user name and the second to your hostname. then you just add a session. (System -> Preferences -> Sessions )

---

### Post by mike2357 on 2008-04-25
Another option that might work for you is to use "cron".  Cron is generally used to run options at specific times, but it can also be used to run options at reboot time.  Type "man 5 crontab" for details.

An example of a cron entry:
@reboot opendchub

You would need to give a full path to the opendchub program.  Also,  you would have to use the super-user's cron account, which you can access by:
sudo crontab -e

Good luck!

---

### Post by oddworld on 2008-04-26
Wow, I tried cron - and it worked wonderfully!
I wanted to try something new and its a really cool app.
--solved

---

