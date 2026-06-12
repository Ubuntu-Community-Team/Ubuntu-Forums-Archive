---
title: "Can I reinstall Ubuntu without formatting?"
date: 2007-03-05
forum: General Help
---

### Post by kuriharu on 2007-03-05
Hello,

Can I re-install Ubuntu without having to format my current partition? I will probably have to reinstall and I was hoping to get a list of all my installed software.

Basically, my Ubuntu install is sick. It won't go into xorg, and I've reinstalled my video drivers, tried using vesa in xorg.conf, etc. Nothing seems to work. I've backed up my /home directories but if I could reinstall like I've done with XP that would be a lot easier.

I will eventually have to wipe the partition and reinstall, but if I could use it once before I blast it would be nice.

---

### Post by dyous87 on 2007-03-05
> **kuriharu said:**
> Hello,

Can I re-install Ubuntu without having to format my current partition? I will probably have to reinstall and I was hoping to get a list of all my installed software.

Basically, my Ubuntu install is sick. It won't go into xorg, and I've reinstalled my video drivers, tried using vesa in xorg.conf, etc. Nothing seems to work. I've backed up my /home directories but if I could reinstall like I've done with XP that would be a lot easier.

I will eventually have to wipe the partition and reinstall, but if I could use it once before I blast it would be nice.

Well you could try mounting that partition off a live cd. Also have you tried reinstalling xorg, or gnome. Try a dist upgrade. It's worked for me before when I was in a situation such as yourself

As far as reinstalling ubuntu without formating, I'm not sure if it's possible.

Let me know how it goes

---

### Post by kuriharu on 2007-03-05
Thanks for the reply.

I've tried the dist-upgrade, and it aborts. What's the best way to reinstall xorg? I think I tried apt-get install xorg-core or something like that, but that, too, aborted.

---

### Post by Motoxrdude on 2007-03-05
I think if you do a manual partition editing you can reuse your current "/" partition and mount that as "/" in your new install without formatting it. Not sure how it will work, but i think it will.

---

### Post by dyous87 on 2007-03-05
yes i think that may be possible but its odd that it keeps aborting. can you try to uninstall x through apt?

---

### Post by IcemanV9 on 2007-03-05
Boot into recovery mode from the GRUB menu and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

Then, reboot.

```
shutdown -r now
```

---

### Post by kuriharu on 2007-03-06
MotorX - I can give that a try.

dyous - I tried that doing apt-get install xorg-something-core, and it said I needed libraries that it wouldn't install. This happens with apt every now and then. And yes, I did apt-get update before trying the install

Iceman -- I'm going to try that right now. I'll let you know the results. I haven't done that yet.

---

### Post by kuriharu on 2007-03-06
I tried dpkg-reconfigure xserver-xorg. What I got is:

dpkg-reconfigure: xserver-xorg is broken or not fully installed.

So I tried:

apt-get install xserver-xorg

and I got:

Following packages have unmet dependencies:
hula: depends hula-medweb (version) but it is not going to be installed.
xserver-xorg: depends on xserver-xorg-video-all but it is not going to be installed
xserver-xorg: depends on xserver-xorg-input-all but it is not going to be installed

I then tried :
apt-get install xserver-xorg-video-all

and got the same basic thing; it listed each video driver, then told me each one had dependencies that weren't going to be met.

I'm turning in now but I should be able to try something in the morning if you post a reply.

Thanks for all of your suggestions so far.

---

### Post by IcemanV9 on 2007-03-06
Two things to try ...

```
sudo apt-get -f install
```

If not success, then try ...

```
sudo apt-get **reinstall** xserver-xorg
```

---

### Post by kuriharu on 2007-03-06
Thanks, Iceman.

I've tried apt-get -f install, but it errors out (I'm not in front of that computer so I can't repeat it now). 

I'll try the apt-get reinstall xserver-xorg tonight, and post the results.

Thanks for being dilligent in watching this. I should have some results by 8 PM PST.

---

### Post by kuriharu on 2007-03-06
ICeman,

Okay, that didn't work either. apt-get reinstall <x> won't work, because apt-get reinstall doesn't exist on my system. I did apt-get upgrade xserver-xorg, and that actually worked, but it still won't go into X.

If I try startx at the prompt, I get "Xserver failed to start. Do you want to view the error file for details?" and then it's blank.

I tried kdeinit just to see if I could get kde to run, but it said "$DISPLAY isn't set". 

Any clues? I'd hate to give up on this setup, I have a lot of cool things on it.

---

### Post by kuriharu on 2007-03-07
Ok, no further posts. Typical of the forums.

Next person who says "Linux support is better than Windows" is gonna get a big punch in the mouth from me. 

Linux on the desktop is almost a waste of time. Linux sucks on the desktop, and that's all there is to it.

---

### Post by disturbedite on 2007-03-08
it helps to know that you *must* be willing to learn new ways of doing things, maybe everything...
and then of course there is the learning curve...

---

### Post by kuriharu on 2007-03-08
***************
it helps to know that you must be willing to learn new ways of doing things, maybe everything...
and then of course there is the learning curve...
***************

Have you read the posts? If you had, you'd see I've done all types of things that people suggested, with the same result. What other new ways of doing things should I try? 

Perhaps instead of assuming someone ins't willing to learn new ways, you should check to see if they have or haven't actually tried something. You can also suggest something yourself. Just a thought.

All I wanted was the latest version of Amarok. I had to upgrade to Edgy to do this, then it failed, and the whole install got f---ed up. I can't believe this. This would be like upgrading Winamp, needing to upgrade to Vista just to get it, then losing the whole install.

I can get my data off of there. but the whole process is ridiculous. (Sorry, I'm worn out, so I'm gonna rant here a little)

---

### Post by watson540 on 2007-03-08
with your apt database messed up you wont be able to install anything via apt until you do a working 'apt-get -f install' also what you NEED to install to totally re-install X is a meta package called ubuntu-desktop . remove it and then install it again if you have to but thats the package that has everything to run x and gnome in it. your welcome :)

---

### Post by kuriharu on 2007-03-08
Thanks, I'll do that.

I've tried run apt-get -f install a couple times and it tends not to work. Let me try it again.

---

### Post by watson540 on 2007-03-08
make sure there is a space in between apt-get and f and install

---

### Post by kuriharu on 2007-03-08
Success! That didn't quite work, as I can't seem to install ubuntu-desktop. It told me it depends on xorg which isn't going to be installed. 

However, I tried apt-get install xserver-xorg, which did actually work. I still couldn't get ubuntu-desktop to install, though, but since xserver-xorg did actually install, I just ran Xorg, and I got a window with a mouse pointer.

I rebooted and ran gdm and it worked, though it had to load the kde.desktop, not Gnome, even though it's Gnome that's running.

Either way, I can now list all the stuff I need and blast the install and start over fresh. Thanks to everyone for all of their help and for putting up with my rants. I can now sleep easy....

T H A N K S ! !

---

### Post by IcemanV9 on 2007-03-08
Sorry about that if you're upset that I have been away from my computer for a day. At least, you got some help from others. I agreed with watson540's suggestion.

Now that you just explained a bit more about what you have done with your box. You upgraded to Edgy from Dapper which means something went missing during the big upgrade process. It could be Apt database went corrupted. I don't know. It could be anything.

Next time, if you want the latest version of Amarok on Dapper, then enable the backports repo to see if it's there or not. If not available, then compile the source or install other app similiar to Amarok.

FWIW, I just checked to see if there is one in dapper-backports repo and yes, it is in there. The version is 1.4.3-0ubuntu8~dapper1. I don't know if that IS the latest one you want or not.

---

### Post by kuriharu on 2007-03-08
Thanks for being patient with me, Ice. It wasn't just you, I was getting help on several forums and they all seemed to go to 'radio silence' for 24 hours and I lost it. I will learn to be more patient.

The lastest Amarok is 1.4.5. The reason why I wanted it was that Amarok 1.4.3  can be very slow and on my system, it crashes or becomes non-responsive. In theory, Amarok is the greatest music player on Earth, and it looks it. But it didn't run well on my PC, and i have a relatively fast PC.

I can install from source next time. I try to avoid that, as installing from source leads to more time and frustration. Typically when I install from source I get errors that I need libraries that I don't have, then when I look for them I can't find them. But since I lost my install, I guess hunting down libraries is better than going through this.

I still like Linux and Ubunutu, but it still strikes me as a little silly to have to go through all this just for one app. What is so much more advanced in Edgy that would make Amarok require it over Dapper? 

Thanks for all of your help. I will pay it forward as much as possible.

---

