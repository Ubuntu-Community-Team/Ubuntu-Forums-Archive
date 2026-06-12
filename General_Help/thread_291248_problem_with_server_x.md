---
title: "problem with server x"
date: 2006-11-02
forum: General Help
---

### Post by yoniman on 2006-11-02
hello all.
everything worked fine with my ubuntu until today.
there was an error
that somthing is wrong with the X server and the graphic thing cant come up.
so i was in a black screen and i was able to type in commands.
so i thought to my self mybe there is a problem with gnome so i wrote
sudo apt-get install kubuntu-desktop
in order to get kde(in the installation i have chosen kdm)

now when i start my computer i get the blue screen of kubuntu loading.
but after it finished loading i see that screen again but with a red bar which isnt moving and strange colors.

what can i do to fix this? 
thanks in advance

---

### Post by taurus on 2006-11-02
Try reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by yoniman on 2006-11-02
yes but its a bit too late though i think..
i cant even get to the black screen with commands anymore

---

### Post by taurus on 2006-11-02
Then boot into recovery mode from GRUB and type that command except don't put sudo in front since you are currently logged in as root (in recovery mode)!

```
dpkg-reconfigure xserver-xorg
```

---

### Post by yoniman on 2006-11-02
ok and after i'll write that what should i do?

---

### Post by taurus on 2006-11-02
It will allow you to reconfigure your X again.  Just follow the instructions on the screen and when you're done, it will write the new xorg.conf to your /etc/X11.  Then, see if you can run X again with

```
startx
```
If it works, reboot and just log in as a regular user...

---

### Post by yoniman on 2006-11-03
well i tried what you wrote.
i re configured and after i have finished i wrote
startx
and then it writed some stuff and then:
Fatal Error:no screens found

Fatal IO Error 104(connection reset by peer)
on X server ":0.0"
after 0 requests

what should i do?

---

### Post by taurus on 2006-11-03
> **yoniman said:**
> well i tried what you wrote.
i re configured and after i have finished i wrote
startx
and then it writed some stuff and then:
Fatal Error:no screens found

Fatal IO Error 104(connection reset by peer)
on X server ":0.0"
after 0 requests

what should i do?
Looks like you either didn't reconfigure your X again or you skipped a section, especially about your monitor!  So, did you run that command and if yes, did you go thru the whole thing?

```
dpkg-reconfigure xserver-xorg
```
p.s.  And when it asks you if you want to overwrite your old /etc/X11/xorg.conf, answer "yes" since the current version is no good anyway!!!

---

