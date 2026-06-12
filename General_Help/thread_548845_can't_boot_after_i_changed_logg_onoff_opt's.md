---
title: "can't boot after i changed logg on/off opt's"
date: 2007-09-11
forum: General Help
---

### Post by asdfguy on 2007-09-11
i'm about 10 days old as far as my linux experience goes.  i had linux set so automatic log-on so that i didn't have to sign in w/ my name and password all the time.  yesterday i decided i wanted to switch it back.  so i went to the options where it allows me to change that and i changed it back to the default.  then i clicked on "log off" w/o restarting it or anything (not sure if that matters, just thought id let you know).  my computer froze.  now when i restart it, it boots up to just before the log in screen and just waits with the little animated ball.  i can boot into linux's safe mode equivalent, but it's all text based and i have no idea what im doing.  id be more than happy to give any more info, i realize i'm an idiot when it comes to linux, but im trying.  can anyone please help?  tia!

---

### Post by jamvegan on 2007-09-12
I'm not familiar with this problem, and I've never used the auto login feature, but I did find where it appears to be configured.  If you could log in to recovery mode and take a look at the file, maybe it will shed some light on the problem.  The command that I'd recommend that you use to look at the file is called "more".  Here's exactly what you can type at the command prompt:
```
more /etc/gdm/gdm.conf
```
You can then use the space bar to page forward through the file, and the "b" key to page backwards.  The "q" key will get you out of more, or more will terminate automatically when you reach the end of the file.

Near the beginning of the file is the section which seems to be relevant.  Here's what mine looks like (this is how it was set up by default):
```
. . .

# Have fun!

[daemon]
# Automatic login, if true the first local screen will automatically logged in
# as user as set with AutomaticLogin key.
AutomaticLoginEnable=false
AutomaticLogin=

# Timed login, useful for kiosks.  Log in a certain user after a certain amount
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=30

. . .

```

Does yours look the same?  If not, what is different?

---

### Post by asdfguy on 2007-09-12
i tired that and it displayed exactly what your says.  is there a way to manually edit it so that it reads

AutomaticLoginEnable=true   

like i said, i dont know what im doing, but my thought is that i could possibly bypass the problem.

---

### Post by jamvegan on 2007-09-12
Yep.  I don't know if it will help, either, but you can type:
```
nano /etc/gdm/gdm.conf
```
You can use your arrow keys to move around the file, and type your changes.  You probably need to add your login name to the "AutomaticLogin=" line, too.  At the bottom of the screen are listed the commands that are available to you in nano, and the "^" represents the control key.  So, when you're finished making changes you will hold down the control key and type "o" to write your changes to the file, and then "x", again while holding down the control key, to exit nano.

Hope this works!

---

### Post by asdfguy on 2007-09-13
that worked, thank you very much!

---

### Post by Konix on 2007-09-25
it helped me also, but in another way, because I had the same code as jamvegan

But then I entered TRUE on 

**AutomaticLoginEnable=false**

and here 

**AutomaticLogin=**

I entered username that I know it will automaticly login.. then I save that document and type EXIT in command line

And after that it automaticly loged me as that user I entered. Then I went to System -> Administration -> Login Window and correct the things I faild firt time :-)

So now it works fine..

---

