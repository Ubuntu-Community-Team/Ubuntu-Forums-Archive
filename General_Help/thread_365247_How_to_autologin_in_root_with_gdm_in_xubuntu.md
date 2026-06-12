---
title: "How to autologin in root with gdm in xubuntu?"
date: 2007-02-19
forum: General Help
---

### Post by stanon on 2007-02-19
Hello,
everything is in the title. No matter recalling me it's BAD, it's really what i want to do, so if you know how to do it, please, just teach me.

thanks

---

### Post by prensing on 2007-02-19
Ubuntu does not set up the root account by default. Yes, it exists, but the password is set to something impossible. Probably the easiest thing to do is log in with your own account and then use the sudo command. If you really want a working root account, then use sudo to set the password for root ("sudo passwd root").

---

### Post by moore.bryan on 2007-02-19
[I]i know you don't want to hear "don't do it;" so, can i at least inquire why you'd want to?

ps... and the reason why most people tell you not to is because once you'd login as root, any commands would run as root.
[/I]

---

### Post by stanon on 2007-02-19
In fact I can already login into root account. But i have to type root [enter] and root paswd [enter]. It is not convenient (even with a passwordless root account and a preselected root user) ... I would like to be logged in automatically. I added the following lines to /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom but it doesn't work :

```

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=root

[security]
AllowRoot=true

```

what can i do?

thanks

@moore.bryan : i have a feeling that if answer, this thread will turn in a debate... i am feeling protected (and i know the risk that comes with (hardware, personnal data and legal) ), furthermore million of people autologin into root account each day on windows and who cares?
but I don't want to turn this in a debate...

---

### Post by moore.bryan on 2007-02-19
[I]stanon... i really wasn't looking to debate, i was actually just trying to figure out why you'd want to login as root.  are you doing a lot of stuff which requires it?
as far as i know--and i hope an admin can correct if i'm wrong--it's not possible to autologin as root with gdm.  perhaps you can find a script to have you autologin?  i think if you follow the setup at [http://doc.gwos.org/index.php/Automatic_Login_No_Authentication](http://doc.gwos.org/index.php/Automatic_Login_No_Authentication), but use root instead of user name, maybe it will work?
ps... your point about windows logging users in as admin is exactly why many people consider windows so much less secure...
[/I]

---

### Post by v8YKxgHe on 2007-02-19
> furthermore million of people autologin into root account each day on windows and who cares?
That is half the reason Windows gets so many god damm virus and spyware. People care a lot about that, they are always on the guard for viruses etc.

Why exactly do you want to auto login as root?! That's just asking for disaster, any script you run will have root privileges which means it could and can delete you're entire system, all you're personal files and settings.

Why put you're self at such a risk, when you can VERY easily just use "sudo"?

---

### Post by Resurrection on 2007-02-19
I did this for one of my children (not as root of course) but I gave her the ability to logon locally without having to remember a password, she just clicks on her picture and it logs her in.  If you combine this solution with the gdm settings manager within gnome (forget what its called) to log you in automatically (without having to select the user) you should be good.

[http://ubuntuforums.org/showthread.php?t=12777]("http://ubuntuforums.org/showthread.php?t=12777")

Have a look at the bottom of that thread.

I won't lecture you on the risks, you are an adult and well aware I assume.  But be careful.
Linux is about choice, so I hope I provided you with the knowledge to make a choice.  The choice you make is up to you.

---

### Post by stanon on 2007-02-20
thanks you all.
you're right linux is about choice.

i tried your link moore.bryan but i got "User not known under the underlying authentication module".
Resurrection> your link neither worked (i also had to login into gdm)

---

### Post by aysiu on 2007-02-20
Alt-F2 ```
gksudo gdmsetup
``` and then you can easily select to auto login as root.

---

### Post by stanon on 2007-02-20
ok i tried with a new gdm (purged it and reinstalled it), and gdmsetup didn't made me autologin as root...

---

### Post by moore.bryan on 2007-02-20
> **stanon said:**
> "User not known under the underlying authentication module".
*that's a new one for me... never seen it; sounds like it's claiming root isn't a user.  hmm...*

---

