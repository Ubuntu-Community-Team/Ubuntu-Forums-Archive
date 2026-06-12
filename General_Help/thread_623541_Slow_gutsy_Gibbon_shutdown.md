---
title: "Slow gutsy Gibbon shutdown"
date: 2007-11-26
forum: General Help
---

### Post by erickdh on 2007-11-26
I upgraded two of my feisty fawn installations to gutsy gibbon.  Now, when I click on the icon to shutdown, restart, or lock the screen, it take about 60 seconds before the menu appears.  This happens only on the two gutsy gibbon upgrades.  As a workaround, I've be shutting down and rebooting from the command line, which work just fine.  I don't know if I can lock the screen for the command line.

---

### Post by nikoPSK on 2007-11-26
What are your pc's specs?

---

### Post by erickdh on 2007-11-26
See attached files for PC specs.

---

### Post by skymera on 2007-11-26
make sure gnome-power-manager is running in sessions :)

---

### Post by nikoPSK on 2007-11-26
> **erickdh said:**
> See attached files for PC specs.

well, it's not pc slowness. Try checking what this does. Tell me if it's slow or not:

```
sudo shutdown -h now
```

---

### Post by erickdh on 2007-11-26
That command ran just fine, but like I said there is no problem running commands.  It's the  
GUI that having the problem.

---

### Post by nikoPSK on 2007-11-26
hmm, well, All I can say is google your way to happiness.. :(

---

### Post by erickdh on 2007-12-01
Installing the latest updates resolved the problem

---

### Post by nikoPSK on 2007-12-01
good! Glad this was fixed, please mark this thread as solved.

---

### Post by Bheegerji on 2007-12-01
Hey, I've the same problem. And my system is up to date but the prob still persists. The GUI appears only after 50 seconds. And I cant "SUSPEND" or HIBERNATE".

---

### Post by nikoPSK on 2007-12-01
does your motherboard support suspend?

---

### Post by Bheegerji on 2007-12-01
how do i check that?
Only thing I know is that I can STANDBY in windows.

---

### Post by Bheegerji on 2007-12-01
yes, my motherboard is capable of suspending to RAM as well as to disk. now, can anyone help.

---

### Post by nikoPSK on 2007-12-01
Power applet then you should see this:

Alternatively you could go system > quit....

---

### Post by erickdh on 2007-12-02
This is the only other thing i installed on my system, but I don't think this is what fixed it. But It's worth a shot.

 sudo apt-get install build-essential

I also have multiuniverse turned on.

---

### Post by nikoPSK on 2007-12-02
that shouldn't affect shutdown time.:(

---

### Post by Bheegerji on 2007-12-02
> **skymera said:**
> make sure gnome-power-manager is running in sessions :)

Thanks, I had disabled this earlier. Now, after enabling the Gnome-Power-Manager, there is no delay. The GUI appears promptly.

But still have problems with Suspend/Hibernate:):). Any workarounds?

---

### Post by Bheegerji on 2007-12-02
> **nikoPSK said:**
> that shouldn't affect shutdown time.:(

There's no problem with the shutdown time, the problem is only with the GUI appearing late after the quit button is pressed. Enabling the Power Manager in System>Preference>Session solved it.

---

### Post by nikoPSK on 2007-12-02
so all's well in Bheegerji ubuntu land? :lolflag:

---

### Post by Bheegerji on 2007-12-03
> **nikoPSK said:**
> so all's well in Bheegerji ubuntu land? :lolflag:

Not all mate.

Still have Suspend/Hibernate problems, and cannot play VCD. And both these problems happen to be major bugs.

But any workaround is welcome guys:lolflag::lolflag:

---

### Post by nikoPSK on 2007-12-03
I remember seeing a shutdown auto thing somewhere.... I'll see if I can find it for you when I get home.

---

### Post by Bheegerji on 2007-12-04
Thanks dude. And seasons greetings.

---

### Post by nikoPSK on 2007-12-04
welcome, haven't found it yet and I'm going to be gone till thursday, I'll see if I can find it while I have my laptop.

---

### Post by bpsod10 on 2007-12-14
Hi, I am new to ubuntu and had experienced the same issues with shutting down taking 50 seconds for the screen to prompt me.
It appears fixed now.
I did 2 things,
I installed the build essentials as mentioned further up the thread, and also
I modified by power saving by following this link.
[http://ubuntuforums.org/showthread.php?t=603054&page=2](http://ubuntuforums.org/showthread.php?t=603054&page=2)
Worth a try, 
Brian
:guitar:

---

### Post by KenRoberts on 2007-12-18
Had the same problem with approx 45 second delay, after clicking on "logout" icon, or selecting System>Quit from menu ... could not resolve by fooling around with the good ideas in this and related threads, but have done so much misc tweaking that I'm sure it is something mis-configured on my part.  In any case, however, the following hack which I'm using, may be beneficial to others...

- Created new launcher on top panel, which runs "application in terminal", new script /usr/local/bin/shutdown.sh as follows...
 echo "some message to ask for confirmation ..."
 read ANS
 case $ANS in
   [Yy]*)
     echo "Enter password to shut down system"
     sudo shutdown -h now
     ;;
  *)
    echo "Shutdown cancelled..."
    sleep 1
   ;;
esac

- A convenient icon to be associated with that launcher is /usr/share/icons/gnome/scalable/apps/gnome-shutdown.svg

Then removed the old icon (with delay) from the top panel.

Cheers!
kr

---

### Post by Psykotik on 2007-12-28
Another user annoyed by the time to get the logout gnome menu. Here are some facts:

1/ Both gnome-power-manager and gnome-session-properties have for result an insulting "Cannot connect to session manager".

2/ In the system > session menu, 2nd tab, gnome-power-manager is set to "order 50" and "style normal"; gnome-session-properties is set to "order 50" and "style trash". I don't understand what it means.

---

### Post by KenRoberts on 2007-12-28
Thanks ... that was the clue needed.  I used synaptic to re-install gnome-power-manager and gnome-session, and went into System>Preferences>Session and marked Power manager for startup (was not marked). Then quit request produced prompt display of options screen. Still worked after rebooting.

About those session properties, clicking on the help icon brings up documentation.  But I don't understand the significance of the descriptions - ie, normal vs trash vs ... - why to choose them.  And there is a third colum, status, which shows as icons only (possibly one of them means 'connected'???), for which did not notice any doc. At least should have tooltip display when one hovers over the icon! Ah, so many nice-to-do things...  we are fortunate, that not everything worth doing has already been done.

Here's a question ... is there somewhere a log of what synaptic has done?  When I said above that I re-installed  gnome-power-manager and gnome-session, that was true, but in the same session I also choose to re-install a few other things that looked possibly relevant, and installed one package that just looked interesting.  But with no log, I cannot tell you want that was ... in case it turns out to have been relevant.  

Anyway, good discussion, and appreciate the help.

---

### Post by Psykotik on 2007-12-28
It worked also for me! Nice collaborative work :)

Maybe someone would let us know the meaning of the session properties.

---

### Post by KenRoberts on 2007-12-28
Glad to help and be helped.  By the way, found the log of synaptic actions.
See /root/.synaptic/log/ files organized by date and timestamp.  Very nice.

---

### Post by sewmyheadon on 2007-12-28
I was having the same issue with the taking 30 seconds + before the gnome logout menu would pop up, but it was fixed by enabling the gnome power manager under Sessions. Thanks!

---

### Post by liassic on 2008-05-17
I had the same problems and turning power-management back on worked great for me as well.
Cheers,
Paul

---

