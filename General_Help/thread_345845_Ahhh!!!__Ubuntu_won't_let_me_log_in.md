---
title: "Ahhh!!!  Ubuntu won't let me log in"
date: 2007-01-24
forum: General Help
---

### Post by axrh on 2007-01-24
Hi guys.  I can no longer log into ubuntu.  I type in my username and then my password.  It says that I have an incorrect username or password.  I have tried my normal username and root, and I know I have the right password (I've written it down, and I've used it a million times today).  

I have one theory on why I can't get it.  I had fedora core running on my laptop yesterday and the same problem happened.  I couldn't log in even though I knew the password was right.  I have an IBM thinkpad a22e.  Maybe some sort of key command is on, or something.  Any ideas?  I've typed my password into the username field and it appeared as it should.  The only correlation between the password I had on fedora and the one on ubuntu is that they both started with #  (please no one hack my comp now :D ).  What could be wrong.  I really don't want to reinstall.

---

### Post by louieb on 2007-01-24
Boot in recovery mode and set the password again. 
```
passwd yourloginname
```if that doesn't work add another user.
```
adduser newusername --ingroup admin
```just press enter at the prompts to use the default value
need the --ingroup admin so the new user can do sudo. 
Then you can play around with System>Administration>Users
and see if you can get yourself able to login again.

---

### Post by axrh on 2007-01-24
Thanks.  I just did that.  My computer is a little funky and slow, so it'll take a few minutes to test it.  I'll check back in if it still doesnt work.

Thanks!

---

### Post by axrh on 2007-01-24
Ahh, its fine.  Thank you so much.  I would love to know why this happened, but whatever.  Maybe I shouldn't start my password with a symbol?

---

### Post by strath on 2007-01-24
I have just installed Ubantu 6.06.1 on new Dell AMD 64 bit. I have gotten as far as the initial sign in to set up user accounts. I had recorded what I thought that I had the correct combination of initial log in info. What I have is sudo-oem-config-prepare. i have tried every variation and used the password I entered, but nothing seems to work. Help!

---

### Post by louieb on 2007-01-24
> **strath said:**
> IWhat I have is sudo-oem-config-prepare.
What is that?
See post #2, add a user and  use the GUI to  fix your user. or since it a new install  just install again. 
Don't remember if I've done and OEM install. Can you tell me the difference between it and a normal install?

---

### Post by strath on 2007-01-25
Because I can't get past the sign in page, I guess I'll try a couple of more times, then do a reinstall. When I had problems here before, I went back to PCLinux OS, but used the much more practical UBUNTU partitions, that combination was working great until the new computer. If the two first options don't work I know I can go back to PCLinux and do more research, on this one. One other thing that may help with the re-install is, I used OEM, which I thought might work better. I was uncertain of what TEXT install is. Is there a more friendly type of install. Everyone says this is a superior Linux version and I really want it to work. Thanks for any help /advice you can all give. I keep trying for a while then again tomorrow.

---

### Post by bangs on 2007-06-10
i just ran into the same problem ..so i decided to google it and found this .. but as I was reading
i was still trying more passwords and user names..   i finally got in.
here is a example
during set up it asked me for a real name i put down     chuck
it then asked me for a user name i put down chuck
then a password i put down chuck.

so with that im not sure of the combinatiion but i had to put
down   chuckchuck  for usename and
chuck for the password..it then logged me in.!?  

Im not sure if i had to put down real name username  or username twice heh ..cause i put all three
the same..

 anyways im in ..it may help others.
now im going to go play with this new toy..(new toy to me that is =) )

---

