---
title: "&quot;Administrator Mode&quot; No Work :( (Solved)"
date: 2005-10-26
forum: General Help
---

### Post by matva on 2005-10-26
I'm trying to change over to my wireless network device, but to do this i need to be in "Administrator Mode." WhyTF?? First of all, is there a way to disable this? If not, can you help me switch to this mode? I click the button, type my password, but nothing happens. I remember i had a similar problem using 5.04, and there was a command i typed in the run to go straight to the "change network device" page. 

Anyone? 

Also, i like a particular color scheme in kde, but it seems to want to apply it so all other apps, even after i unchecked that option. In some apps, the color scheme just doesnt look right as some text you can't see. Is this a bug or something? 

I'm starting to get quite comfortable, but its these constant admin problems that keep holding me back. For example, i wanted to use the konq to transfer some files from a cd to another directory. It said the destination was access restricted so i had to use sudo in the command line to transfer the files. Needless to say, it took awhile, and was a bit annoying. What do i do when i encounter these restriction "root required" problems? I'm not so handy with the command line, so i like to use GUI wherever possible, but these constant restrictions are holding me down. 

thanks, and sorry for not staying on my topic.

---

### Post by aysiu on 2005-10-26
[QUOTE=matva]
I'm starting to get quite comfortable, but its these constant admin problems that keep holding me back. For example, i wanted to use the konq to transfer some files from a cd to another directory. It said the destination was access restricted so i had to use sudo in the command line to transfer the files. Needless to say, it took awhile, and was a bit annoying. What do i do when i encounter these restriction "root required" problems? I'm not so handy with the command line, so i like to use GUI wherever possible, but these constant restrictions are holding me down.[/QUOTE] I don't know about your other problems, but a simple solution to this would be to create a launcher in the panel or in the KMenu with this command ```
kdesu konqueror
``` When you click on that, it'll prompt you for your sudo password and allow you to browse around as root (just the open window).

That said, I don't know how married you are to the idea of using KDE, but you seem quite frustrated, and I have to say KDE is the buggiest desktop environment I've used: random Konqueror crashes, sucked up (not acknowledged) administrator passwords, slow responsiveness, automount errors and such. Gnome is not as buggy, and XFCE isn't buggy at all (at least I've never encountered any in XFCE).

---

### Post by tonysathre on 2005-10-26
if you really are, or want to be a linux user you cant expect everything to have a gui like in windows, a lot of times using the command line is faster than using the gui

i have heard a lot of ppl in kcontrol cant get admin mode to work and neither could i, sudo worked fine for me

to enable a differnet ethx interface i just logged into gnome and changed it there and it worked fine with the gui without having to use admin mode (if there even is one, i dont use gnome for anything else)

---

### Post by matva on 2005-10-26
Thanks man i appreciate it. Nah, i'm pretty newb...kind of spent awhile getting things setup though. oh well, i'll give xfce a shot. Any suggestions on getting that installed? Can i download it through adept manager, or do i have to get another distro?
Yes, konq is very buggy to me, especially as a web browser.

edit:
[QUOTE=tonysathre]if you really are, or want to be a linux user you cant expect everything to have a gui like in windows, a lot of times using the command line is faster than using the gui

i have heard a lot of ppl in kcontrol cant get admin mode to work and neither could i, sudo worked fine for me

to enable a differnet ethx interface i just logged into gnome and changed it there and it worked fine with the gui without having to use admin mode (if there even is one, i dont use gnome for anything else)[/QUOTE]

Welp, i'm learning it man. Yes, i agree the cl is faster in doing certain things, but for those other things?.. I expect to be able to do it through a functional gui. Sorry, but a  gui is just simple. You can't expect the average comp user to memorize commands for tasks as simple as moving some files from one place to another. lol, and i'd move back to windows before i switching to gnome just to enable a eth device.

---

### Post by tonysathre on 2005-10-26
dont worry everyone starts out as a newb, ive only been using linux for 5 or 6 months now but caught on to it fairly well, you'll learn with practice. im only 20 so i have a lot too learn yet but the way i see it i have plenty of time to do it. i havent been around as long as some of these other ppl who have been using unix for like 20 years

i havent used xfce but im pretty sure you can install it with synaptic but dont quote me on that

---

### Post by kairu0 on 2005-10-27
Install xubuntu-desktop in adept and you have XFCE.

I highly recommend XFCE.

---

### Post by lorenco on 2005-10-27
Well, I had a similar problem, There is a couple of things to do.

1. run "xhost +" in a terminal session.
2. run "sudo kcontrol" (This will start Control Panel as root)

The first step is only if you get an failure to connect to the xwindow system running the second step, so, it might be optional.

The other command is "kdesu" that is sudo but for KDE. 

Yet another option is to edit the K Menu item and click "run as different user" and select "root". (Not sure if you have to enable root account to do this one but if you do you can run "sudo bash" and then "passwd" in a terminal session.

---

### Post by matva on 2005-10-27
much thx guys, got it fixed. i also installed xfce, but had some problems, so i'm switching to ubuntu to see what the different between kde and gnome is. 

Thanks!

---

### Post by helwitch on 2005-10-29
[QUOTE=lorenco]Well, I had a similar problem
2. run "sudo kcontrol" (This will start Control Panel as root)[/QUOTE]
Oh, I love you! Thanks SO much, this was exactly the command I needed!

---

