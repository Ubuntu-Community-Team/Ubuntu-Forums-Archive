---
title: "Running applications as a different user..."
date: 2007-07-19
forum: General Help
---

### Post by Hilipatti on 2007-07-19
I want to run some of my wine applications as a different Ubuntu user, however it isn't as simple I thought it would be.. Meaning that you'd just have to "su user2 command"..

X won't allow you to open another user's applications on your X :P

So, my question is:

What do I have to do in order to get commands like "su user2 wine C:/windows/notepad.exe" working? Well, this does mean using another user's applications on your X in general of course, not just wine applications..

Oh and please don't post something like "you can just get another wine/windows user by doing blabla" 'cause I wanna learn this potentially useful linux trick :P

Thanks!

---

### Post by PaulFr on 2007-07-19
**man xhost** might help. ```
xhost +
``` to enable anyone to connect to your X-Windows server.

---

### Post by Hilipatti on 2007-07-19
Aye, but isn't that a security risk to put something like that in there..

I'd rather permit the username to access my X, but I don't really understand how to put it into xhost.

> The xhost program is used to add and delete host names or user names to the list allowed to make connections to the X server.

It implies that you can add only single users that can access the other's X. So, what's the phrase to add usernames on the localhost to the list? 

> xhost +x username@localhost

Or something like that?

---

### Post by Hilipatti on 2007-07-19
Oh come on, answers please :D

/BUMP

I really need this :(

---

### Post by mbeierl on 2007-07-19
Well, xhost+ is only 'insecure' in that it allows other programs to display themselves on your X session.  If you're not directly connected to the internet, and you trust your own network, it's secure.

Secondly, you could always do xhost +localhost.  If someone's compromised your system and has local access to open programs, you've got a bigger concern than just xhost for localhost...

---

### Post by Hilipatti on 2007-07-19
Hmph, even

> xhost +localhost

doesn't work.

I have to use
> xhost +

in order for it to work.

And I AM directly connected to the internet, if you mean that I'm not behind a NAT.
This thing is pissing me off, since I can't get a working answer from anyone basically :p And I've been trying to solve this for ages.. I'm sure there's a way to just add that one user access to my X..

---

### Post by bodhi.zazen on 2007-07-19
See this thread for assistance (the problem is not exactly the same but you should be able to adapt the script)

[http://ubuntuforums.org/showthread.php?&t=411622](http://ubuntuforums.org/showthread.php?&t=411622)

---

### Post by PaulFr on 2007-07-20
One suggestion: When you are logged in, run ```
xauth nextract /tmp/xat $DISPLAY
``` to store an authority file. Then login as the user you want to give permission to, and run ```
xauth nmerge /tmp/xat
``` to add this authority (You can also use _xauth extract_ and _xauth merge_). I tested with ```
su <username> -c "export DISPLAY=0.0; <command with arguments>"
``` and this works fine. Maybe the "export DISPLAY=:0.0" is not needed, please test and see.

N.B. I got a warning as > Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed Didnt seem to cause any problems. Hope this helps.

---

### Post by PaulFr on 2007-08-08
I just found that ```
xhost +local:
``` works fine for local users whose DISPLAY is set to **:0.0**. Hope this helps someone.

---

