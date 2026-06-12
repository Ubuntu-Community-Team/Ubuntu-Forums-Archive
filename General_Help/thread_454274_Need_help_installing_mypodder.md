---
title: "Need help installing mypodder"
date: 2007-05-25
forum: General Help
---

### Post by schalicto on 2007-05-25
I've just installed Ubuntu and I'm trying out programs to synch podcasts with my iPod.  It seems like mypodder is the best way to go with that because that is exactly what the program does, but I need some help getting it installed.

I downloaded the tar and extracted it.  I was following the directions which said to go to a terminal and navigate to the unachived folder and type ./linux_start.sh so I did that and nothing happened.  The instructions said that I need execute authority in order to install so I racked my little noob brain and tried sudo ./ilnux_start.sh and the error it gave me was "bash: ./start_linux.sh: Permission denied"

I don't really know what I'm doing here.  I'm a total linux noob.  Any help would be greatly appreciated.

---

### Post by mbradlcu on 2007-05-27
make sure the file is indeed executable by:
```
chmod 777 ilnux_start.sh
```
if the program is trying to install to say,, /usr/foo or anywhere that's not your home dir then you'll need to run it using sudo

---

### Post by uzd4ce on 2007-05-29
Hey Schalicto,
Did you extract the files directly to your iPod?  If not, then you should because that's how MyPodder works, it runs straight from the iPod.  (Though now that I think about it, I guess there's no reason you'd have to run it from the iPod.)

In any case, the easiest way to get it to run is to navigate to the start_linux.sh file in the graphical file manager, not via the command line.  Just right click the file and check the box that says something like "Allow to be run as a program" or something like that.

Then when you double-click the file, you'll get a popup asking if you want to view or run it.  Just choose Run.

Now, I've got a question for you.  Are you running 1.6.5?  If so, I'd like to hear your experiences with it.

I've been using 1.6.3 for a couple of months now.  Works great, except that the podcast episodes do not appear in the Podcasts menu on the iPod, but rather you have to find them in the Albums.  Not a bug, that's how that version worked.

1.6.5 supposedly made it so that the episodes appeared in the Podcasts menu, but for me it never worked.   It would download the episodes, and I could see them when browsing the iPod with Nautilus, but they would not appear in any menus at all.  Not in Albums or Podcasts.  I couldn't play them at all.

So, I'm back to using 1.6.3.  I've posted in a couple forums to see if 1.6.5 just doesn't work with Linux or if it's just me.  I'd really like to hear how it works for you.

Thanks,
Uzd4ce

---

