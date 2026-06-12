---
title: "[SOLVED] Cross-user install of firefox addons for april fools"
date: 2008-04-01
forum: General Help
---

### Post by Bored on 2008-04-01
Hi, I would like to install some add-ons for firefox as an April Fool's joke.  This is how my comp is set up.  I am running ubuntu 7.10 and I have the admin account.  My two friends each have non-admin user accounts that are password protected.  Is there a way I can get around their password to install a prank add-on or two on their version of firefox?  Here is a link to the add-ons in question for the curious, [http://www.instructables.com/id/Firefox-Pranks/?utm_source=rss&utm_medium=rss](http://www.instructables.com/id/Firefox-Pranks/?utm_source=rss&utm_medium=rss)

I was just wondering if there is a way to install the programs on their accounts, maybe using root access or using nautilus to copy the file to a certain folder?  I'm just not sure.

Oh, and I'm kinda new here so I'm sorry if this kind of request is not allowed.

---

### Post by cdenley on 2008-04-01
Easiest way, if you are an admin, would be to use their firefox profile and install it:
```

xhost +
sudo su -l them
export DISPLAY=:0
firefox
exit
xhost -

```

---

### Post by Slushdoot on 2008-04-01
There might be a better way to do this, but I'll tell you how I'd do it.  You'd start by creating a new user then logging in as that user.  You'd then install the extensions and such and exit the program.  You'd log out and log back in as yourself.  The reason for creating a fresh user is so that you don't accidentally give them *your* profile which might have passwords saved on it.

Next you'd copy their existing profiles so that they're backed up.
sudo cp /home/[Linux Login Name]/.mozilla/[Linux Login Name]/[random string] /home/[Your Login Name]/Desktop
do this again changing it to get your other friend's profile

Next copy the dummy user's profile to that same directory for each of your friends and change the name to match the random string.

When the joke's over, copy their old profiles back.

---

### Post by Bored on 2008-04-01
That sounds like it would work, thanks for the reply.  Where would you find the random string?

This is what I think you are saying, correct me if I'm wrong:

1.Create a new user and install the add-ons on firefox
2. Log back into my user and run sudo cp/home/[their username]/.mozilla/[their username]/[a random string of numbers from somewhere] /home/[my username]/desktop
3. find a file with a random string in the .mozilla file on the dummy account and copy it using root nautilus to their .mozilla file
4. change the name of the dummy profile to their random string
5. when I want to remove it I swap the copy for the dummy one

Right?

---

### Post by Slushdoot on 2008-04-01
The random string is the name of the directory in which the profile resides.  It's randomized as a security measure.  You'll find it if you browse to the indicated location in your friend's home, .mozilla/username/

Take a look at your own
ls ~/.mozilla/yourusername/

When you want to remove it, copy back the originals you saved to your home directory in the first place.  It would be mean-spirited to break somebody else's profile. :p

---

### Post by Bored on 2008-04-01
Hm, I think I found the folder in question, however it won't let me copy it to my desktop.  I run the command in the terminal and nothing happens.  I opened nautilus as root and navigated to the folder and tried to manually copy it but nothing happens.  What is wrong?

EDIT: Same problem happened when I tried to copy the dummy profile to my friend's profile folder... I re-booted and the problem continues.

---

### Post by Slushdoot on 2008-04-01
In Nautilus you go to drag the directory and it just plain doesn't do anything?  No error messages?

I'l like to test it myself to see if/how it'd work but I'm on OS X at the moment. :p

---

### Post by Bored on 2008-04-01
Exactly, nothing happens, no error messages, no nothing.  my cursor will pick it up and drop it, but as soon as I let go it zips right back to where it came from.  Kinda strange, nautilus hasn't ever done this to me before...

EDIT: trying opening the folder and copying everything in it over, but nothing in it will work either...

---

### Post by cdenley on 2008-04-01
It sounds like you are running into permissions issues. Try my method. If you want to be able to restore their profile, do this:
```

sudo tar cfv /root/user.tar /home/user/.mozilla
xhost +
sudo su -l user
export DISPLAY=:0
firefox
exit
xhost -

```
...installing whatever addons you want when firefox is opened.

then, when/if you need to restore it:
```

sudo tar xfv /root/user.tar

```

---

### Post by Bored on 2008-04-01
Sorry, I'm not exactly sure how to enter that code.  Do I enter that whole block of code at once, or is this what you mean?

sudo tar cfv /root/[their username].tar / home/user/.mozilla

then 

xhost +

then

sudo su -l user

then 

export DISPLAY=: 0

then

firefox

then

exit

xhost -

And that will open their profile of firefox on my account for me to install the addons?  Will it affect my profile?

and when I need to restore it do i type

sudo tar xfv /root/[their username].tar

or am I misunderstanding?

---

### Post by cdenley on 2008-04-01
You're correct. The "su" command is used to switch users. The root user can switch to any user without a password, and commands run with sudo execute as root. When you run the firefox command, you run it as the user you switched to, not yourself, so your profile won't be used. When you enter exit, you end that users session, and are yourself again. The xhost commands and setting the DISPLAY variable are necessary to run graphical applications as another user. You can run these commands in terminal by going to "Applications>Accessories>Terminal".

---

### Post by Bored on 2008-04-01
Yay!  It worked!  Thank you so much for the help.  You explained everything very clearly so a non-computer person like me could understand.  I really appreciate your help.

---

