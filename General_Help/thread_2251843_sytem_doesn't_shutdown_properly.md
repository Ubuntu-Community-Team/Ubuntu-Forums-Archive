---
title: "sytem doesn't shutdown properly"
date: 2014-11-07
forum: General Help
---

### Post by sean69 on 2014-11-07
When I apptempt to shut down it hangs on the lubuntu scree please assist

---

### Post by Bucky Ball on 2014-11-07
When you get to the black screen do you get a CLI if you hit ctl+alt+F1? If so, try this command. On reboot, see if it shuts down properly.

```
sudo reboot -f 
```

---

### Post by geoaraujo on 2014-11-07
I'm having the same issue on Kubuntu 14.10 after having upgraded from 14.04.1. 
The command ```
sudo reboot -f
``` does reboot the system, but then I get a blank screen instead of login screen and ctl+alt+F1 does not work.

---

### Post by sean69 on 2014-11-07
What is a CLI?

---

### Post by coldcritter64 on 2014-11-07
A CLI is a "command line interface". As compared to a GUI which is what you normally use, a "graphical user interface"

---

### Post by Bucky Ball on 2014-11-07
Like a big terminal with a blinking cursor asking you to login.

---

### Post by sean69 on 2014-11-07
Oh makes sense. I just get to a lubuntu loading screen then it hangs forever. (loading screen has 6 dots)

---

### Post by Bucky Ball on 2014-11-07
Yep, hit ctl+alt+F1 there. CLI?

---

### Post by sean69 on 2014-11-07
It locked up on the desktop/ didn't do anything since now I can do things. trying again

---

### Post by sean69 on 2014-11-07
can't use terminal now and tried reboot and it says wait-for-state stop/waiting
please advise

---

### Post by Roasted on 2014-11-08
Hi there. Sorry to hear about your headaches. As mentioned above, you could try hitting CTRL ALT F1 at that screen. To do that, simply hold CTRL ALT and press F1. You should be at a terminal screen. From there you can log in with your regular username/password.

If it were me, I'd run this command to see if the syslog is populating anything.

cat /var/log/syslog

The syslog as mentioned above is located within /var/log, so it's two directories deep. The cat command allows you to view the contents of a file, and since syslog is technically a text file... well you get the idea. ;)

To get back to your GUI mode, you would use CTRL ALT F7. If you see any errors in the syslog, take a picture on your phone and link it here, or else write them down so we have some idea as to what might be going on.

---

### Post by sean69 on 2014-11-08
> **sean69 said:**
> can't use terminal now and tried reboot and it says wait-for-state stop/waiting
please advise
I had to go through te GUI to rebbot as that command somehow disables the keyboard
therefore hitting any combination of keys is useless any other suggestions would be great

---

### Post by sean69 on 2014-11-10
> **Roasted said:**
> Hi there. Sorry to hear about your headaches. As mentioned above, you could try hitting CTRL ALT F1 at that screen. To do that, simply hold CTRL ALT and press F1. You should be at a terminal screen. From there you can log in with your regular username/password.

If it were me, I'd run this command to see if the syslog is populating anything.

cat /var/log/syslog

The syslog as mentioned above is located within /var/log, so it's two directories deep. The cat command allows you to view the contents of a file, and since syslog is technically a text file... well you get the idea. ;)

To get back to your GUI mode, you would use CTRL ALT F7. If you see any errors in the syslog, take a picture on your phone and link it here, or else write them down so we have some idea as to what might be going on.
thank you I was able to determine that it was a bad install, reinstalled now no issues.
thank you for all of your help

---

### Post by geoaraujo on 2014-11-11
> thank you I was able to determine that it was a bad install, reinstalled now no issues.
thank you for all of your help
How did you were able to determine that it was a bad install? I've upgraded from 14.04 to 14.10. It was not a clean install and I have the same issue.

---

### Post by Bucky Ball on 2014-11-12
> **geoaraujo said:**
> How did you were able to determine that it was a bad install? I've upgraded from 14.04 to 14.10. It was not a clean install and I have the same issue.

Perhaps posting a new thread re. your specific issues and setup and configuration might help. This thread is solved and you may not be doing your chances of support much good by burying yourself here. Good luck.

---

### Post by geoaraujo on 2014-11-12
> Perhaps posting a new thread re. your specific issues and setup and configuration might help. This thread is solved and you may not be doing your chances of support much good by burying yourself here. Good luck.

Ok, I've started a [new thread]("http://ubuntuforums.org/showthread.php?t=2252477"). Thanks.

---

