---
title: "Installing packages for all users"
date: 2007-08-16
forum: General Help
---

### Post by guguma on 2007-08-16
I have installed compiz-fusion, xmms, xgl, propriatery drivers. But i see that only i can access and use them. When I create a second user that user does not have access to them. How can I install these packages so that all of the users have access to them.

Also I see that the second user I create cannot use audio. It says the drivers are not installed. I did not install audio drivers for the first user myself, they were just there.

Also if there is a way to just make a user access to these drivers and applications, how can I do that.

Thanks in advance

---

### Post by kevinlyfellow on 2007-08-16
Press alt-f2 to bring up the run dialog.  Then put in
```
gksu users-admin
```

Click on the properties for the second user and go to the "user privileges" tab.

---

### Post by guguma on 2007-08-17
I used that to enable the audio drivers, but the options are limited on this menu. I cannot get the second user activate the graphics drivers (even though I give administrative privilages it tries to install them again).

Thus I cannot start xgl or compiz.

---

### Post by kevinlyfellow on 2007-08-17
Ok, try this
```
usermod --append --groups cdrom audio video plugdev admin fuse
```

If that doesn't work, just see what groups the 1st user is in
```
sudo groups <1st user>
```
and add all of those groups.

---

### Post by guguma on 2007-08-17
I am doing this but It constantly gives errors, I think I am not doing something right.

In the man page of the usermod it says that the group names must be seperated by comma with no intervening whitespace. 
But when I do 

```
sudo usermod --append --groups audio,video
```

or

```
sudo usermod --append --groups audio video
```

BASH constantly says

user video,audio does not exist


or

user video does not exist.

By the way where will the login name of the user whose privilages are changed go in these commands. It has the worst man page I have ever seen.

---

### Post by guguma on 2007-08-17
it came out to be that the usage is:

```
sudo usermod --append <username> --groups <etc>
``` 

I really hate some man pages.

---

### Post by kevinlyfellow on 2007-08-17
Yeah, I've had to use that tool a few times and I always get it wrong the first five times.  Do things work yet?

If not, I think we will need to change the groups on certain devices.

---

### Post by guguma on 2007-08-18
Things do not actually work fine. 

I mean if I do as you have suggested, then it works all right, but for that I have to give the second user administrative privilages.

I think I must explain this in more detail. 

I am planning to use this second user to install Linux From Scratch and I do not want it to break anything. But while working on it, I think I must be able to listen to music and enjoy the eye candy. If I give this user admin privilages than it may break things.

The guide I am following for LFS creates a user with a very limited access. What I believe is that there must be a way to create a user such that it can enjoy the eye candy and listen to music, but cannot tinker with the controls and so.

Was I able to explain myself.

---

### Post by kevinlyfellow on 2007-08-18
> **guguma said:**
> Things do not actually work fine. 

I mean if I do as you have suggested, then it works all right, but for that I have to give the second user administrative privilages.

I think I must explain this in more detail. 

I am planning to use this second user to install Linux From Scratch and I do not want it to break anything. But while working on it, I think I must be able to listen to music and enjoy the eye candy. If I give this user admin privilages than it may break things.

The guide I am following for LFS creates a user with a very limited access. What I believe is that there must be a way to create a user such that it can enjoy the eye candy and listen to music, but cannot tinker with the controls and so.

Was I able to explain myself.

Yes, you want a user that isn't in the admin group (ie, not in the sudoers file).  So, be sure to take the second user out of admin group.  I have an idea.  Perhaps just graphically login as a normal user and then in a terminal
```
su <second user>
```
to login as the second user

---

### Post by guguma on 2007-08-18
That may really work well, what I am afraid is that I will be compiling many core libraries and applications and in the process I make them change their usual installation locations when I execute configure and make. 

If I do 

```
su <username>
```

I hope it will not use the host system paths to install and build these things. (I greatly presume that it will not be so but, sometimes one can get paranoid right :))

---

### Post by kevinlyfellow on 2007-08-19
> **guguma said:**
> That may really work well, what I am afraid is that I will be compiling many core libraries and applications and in the process I make them change their usual installation locations when I execute configure and make. 

If I do 

```
su <username>
```

I hope it will not use the host system paths to install and build these things. (I greatly presume that it will not be so but, sometimes one can get paranoid right :))

You have every right to be paranoid, because I would be too.

The man page says
[quote="man su"] The optional argument - may be used to provide an environment similar to what the user would expect had the user logged in directly.[/quote]

Usually that is done with root, but the manpage seems to suggest that it's ok, and su doesn't complain to me when I provide a user.  So perhaps you could log in by doing this
```
su - <second user>
```

I'm paranoid about that... it'd be great if someone could confirm if this works.  Ok, actually, I've been playing around before I posted this and it doesn't run .bashrc for the user...  Maybe that won't work, maybe it still will.

BTW, good luck with LFS.  Every time I try I end up loosing interest.  It's hard downloading all those tarballs.  But if you haven't already downloaded everything, I'd suggest just downloading the [LFS LiveCD]("http://www.linuxfromscratch.org/livecd/").  I may try sometime in the future if I ever have time again :-).

---

