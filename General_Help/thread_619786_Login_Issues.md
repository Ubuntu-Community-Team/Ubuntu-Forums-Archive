---
title: "Login Issues"
date: 2007-11-21
forum: General Help
---

### Post by sine_wave on 2007-11-21
So I've been having major problems with Ubuntu to begin with.  It's been freezing on me, crashing, rebooting for no reason at all.  It's been horrible.  

Well to add to the list.  I turned off my computer and when I turned it back on this time there is no user name that is on the start up screen as before.  I used to be able to click on my user name and then type in my password.  For some strange reason it is gone.

Anyway, I thought...why don't I just type in my user name and password.  Doesn't work.  I've tried all different ways.  Made sure my caps lock wasn't on.  I had someone set it up for me when I bought the computer 2 weeks ago and tried the user name and password that they preset it with...no luck.  So...I'm stuck that the login screen.

Are there any ways that I can bypass this?

Thanks in advance, 

Frustrated

---

### Post by taurus on 2007-11-21
Boot into recovery mode from GRUB menu (usually the second option) and at the prompt, post the output of this command.

```
ls -la /home
```

---

### Post by sine_wave on 2007-11-21
Thanks for the reply.

Edit:  Found it, trying it now.

This is the output:

total 12
drwxr-xr-x 3 root root 4096 Nov 7 12:25 .
drwxr-xr-x 21 root root 4096 Nov 8 22:11 ..
drwxr-xr-x 41 steve user 4096 Nov 21 18:09 user

Alright:  Well I just guess that my user name was "steve" and I used it and it worked.  However, upon login at the screen it NEVER said "steve" but said my full name....so that's what I was trying.  What the heck?  Why would it do that?

Thanks for you help taurus....

---

### Post by taurus on 2007-11-21
> **sine_wave said:**
> Thanks for the reply.

Edit:  Found it, trying it now.

This is the output:

total 12
drwxr-xr-x 3 root root 4096 Nov 7 12:25 .
drwxr-xr-x 21 root root 4096 Nov 8 22:11 ..
**[COLOR="Blue"]drwxr-xr-x 41 steve user 4096 Nov 21 18:09 user[/COLOR]**

Alright:  Well I just guess that my user name was "steve" and I used it and it worked.  However, upon login at the screen it NEVER said "steve" but said my full name....so that's what I was trying.  What the heck?  Why would it do that?

Thanks for you help taurus....

Actually, your login name is user, not steve.  Not sure why steve is the owner of user so you need to change the ownership back to user again. 

While you're still in the recovery mode, run

```
chown -R user /home/user
ls -la /home
```
Again, your login name is _user_.

Now, you can reboot your machine with

```
shutdown -r now
```

---

### Post by sine_wave on 2007-11-21
> **taurus said:**
> Actually, your login name is user, not steve.  Not sure why steve is the owner of user so you need to change the ownership back to user again. 

While you're still in the recovery mode, run

```
chown -R user /home/user
ls -la /home
```
Again, your login name is _user_.

Now, you can reboot your machine with

```
shutdown -r now
```

well that maybe makes sense as to why i've been having problems, ever since i changed user to "steve" it's been doing this

i put in that code  

 ```
chown -R user /home/user
ls -la /home
```

and it says

chown: 'user': invalid user

---

### Post by taurus on 2007-11-21
What are the last few lines when you run this command?

```
cat /etc/passwd
```

Did you change your login name or anything like that?

---

### Post by sine_wave on 2007-11-21
> **taurus said:**
> What are the last few lines when you run this command?

```
cat /etc/passwd
```

Did you change your login name or anything like that?

gdm:x:108:118:Gnome Display Manager:/var/lib/gdm:/bin/false
steve:x:1000:1000:Stephen Lynn,,,,:/home/user:/bin/bash
statd:x:109:65534::/var/lib/nfs:/bin/false

---

### Post by taurus on 2007-11-21
So, your login name is _steve_ BUT your $HOME directory is /home/user!  Try changing your password to see if you can log in with the new one.

```
passwd steve
```

---

### Post by sine_wave on 2007-11-21
> **taurus said:**
> So, your login name is _steve_ BUT your $HOME directory is /home/user!  Try changing your password to see if you can log in with the new one.

```
passwd steve
```

i changed my password but i haven't been able to change the home directory back to what you told me to do yet.

Edit:  new password works fine

---

### Post by taurus on 2007-11-21
At this point, I think it's better if you use steve as your login name but change your $HOME directory from user to steve.  You need to edit /etc/passwd

```
nano -Bw /etc/passwd
```
and change the **/home/user** to **/home/steve**.  Save it with <Ctrl>o and exit with <Ctrl>x.  Then, run

```
mv /home/user /home/steve
ls -la /home
```

---

### Post by sine_wave on 2007-11-21
I understand what you are telling me to do, but I'm not sure what that first command you gave me does.

I just opened a terminal window and typed it in, and it came up with all this code (same ones that you asked me before what they said) and i tried to type over it but it didn't work.

I'm not sure what to do now?  Thanks for being patient with me/

---

### Post by taurus on 2007-11-21
After you run

```
nano -Bw /etc/passwd
```
scroll down to the second to the last line and replace /home/_user_ with /home/_steve_ so now it would look something like

```
steve:1000:1000:Stephen Lynn,,,,:/home/**steve**:/bin/bash
```
Save it and then change /home/user to /home/steve with the second command in the previous post.

```
mv /home/user /home/steve
```

---

### Post by sine_wave on 2007-11-21
Changed the first line...when I save it it says "file name to write [backup]: /etc/passwd

Not sure what to do there...

Edit:  Thanks for you help, I'm just going to install XP this has been a nightmare.

---

