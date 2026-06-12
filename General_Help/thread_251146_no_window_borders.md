---
title: "no window borders"
date: 2006-09-05
forum: General Help
---

### Post by frup on 2006-09-05
i just logged in to my computer to find out that my younger brother has been playing :evil: 

Stupid young man has gone and tried to install a metacity theme in my compiz/xgl session... i'm guessing this is what has caused the problem at least...

so basically i have no borders on my windows with no _ [] X buttons etc... this is only for the compiz session and returning to the gnome session has fixed this but i would really like to have compiz running properly again.. can anyone help me :(

---

### Post by grte on 2006-09-05
Not so.  The recent compiz updates have changed the startup script.  It is now located at /usr/bin/start-compiz.  Load from that and you'll have your window borders back.

Also, to edit compiz settings, you should use the program csm, instead of gconf-editor.

---

### Post by frup on 2006-09-05
i tried that... still dont get the window borders back :( although compiz itself did start working again...

```
laurent@ubuntu:~$ compiz-start
nohup: appending output to `nohup.out'

```

---

### Post by grte on 2006-09-05
You'll want to restart gdm, afterwards.

```
sudo /etc/init.d/gdm restart
```

You should be good to go once that's done.  Make certain that whatever method you use to start compiz (probably under the System > Preferences > Sessions menu) reflects the new script.

---

### Post by frup on 2006-09-05
```
laurent@ubuntu:~$ sudo compiz-start
nohup: appending output to `nohup.out'
/usr/bin/compiz-start: line 14: 19500 Aborted                 nohup cgwd --replace
```


i used this tutorial, [http://tazforum.thetazzone.com/viewtopic.php?t=2189](http://tazforum.thetazzone.com/viewtopic.php?t=2189) which made a startcompiz sh script... according to what i have been reading on the forums i am meant to change this to compiz-start? (i havent made this)  csm works... i just cant get compiz to show... it was before i tried to change the sessions etc... now it doesnt load at all and the xgl session still has no window borders...

restarting gdm just logs back in to the default gnome session.

i am very lost now.


```
laurent@ubuntu:~$ startcompiz
gnome-window-decorator: no process killed
laurent@ubuntu:~$ compiz: Couldn't load plugin 'gconf'

```

This is my old compiz start script located in usr/bin... i can see compiz-start in this folder too still..

---

### Post by XAsmodeanX on 2006-09-06
I'm having the same problem.  I'm running XGL as a session and when I log into it I get regular gnome running on XGL.  I then used to type in a command to switch to compiz but obviously that no longer works now.  

I tried typing in compiz-start and my window borders dissappear and I can't move anything and compiz is not started since nothing wobbles or anything.  When I run the command it sais:

nohup: appending output to `nohup.out'

That's it.  This is very frustrating, if anyone could help I would greatly appreciate it.

---

### Post by damagedspline on 2006-09-08
> **XAsmodeanX said:**
> I'm having the same problem.  I'm running XGL as a session and when I log into it I get regular gnome running on XGL.  I then used to type in a command to switch to compiz but obviously that no longer works now.  

I tried typing in compiz-start and my window borders dissappear and I can't move anything and compiz is not started since nothing wobbles or anything.  When I run the command it sais:

nohup: appending output to `nohup.out'

That's it.  This is very frustrating, if anyone could help I would greatly appreciate it.

i had the same problem (compiz-quinz packages), but once i installed vanilla it started working again. dont know y...

---

