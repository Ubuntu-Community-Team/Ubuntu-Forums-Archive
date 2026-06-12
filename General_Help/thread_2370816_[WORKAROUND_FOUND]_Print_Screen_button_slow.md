---
title: "[WORKAROUND FOUND] Print Screen button slow"
date: 2017-09-07
forum: General Help
---

### Post by newtsoup on 2017-09-07
Hi,  I was hoping someone might be able to help me.

I play quite a few games and that means of course I often like to take screenshots.  Everything used to be fine, but lately I have found that screenshot ( I presume that's what is being run) takes 30 seconds or so to respond to the print screen button being pressed.

Does anyone know what might be going on and how to fix it?

Thanks in advance

(also why can't I type at my normal rate here?  If I type a sentence normally it's taking a few seconds for the text to appear, I seem to be limited to two characters per second)

---

### Post by RobGoss on 2017-09-08
What version of Ubuntu are you running? I use 16.04 and it's very responsive when taking screen shots

---

### Post by newtsoup on 2017-09-08
I'm also using 16.04.  Like I say it used to respond almond instantly but had got slow at some point in the last month.  Not sure when exactly.

---

### Post by vasa1 on 2017-09-08
What about when you're not playing games? Does PrintScreen seem normal then?

---

### Post by RobGoss on 2017-09-08
This may sound silly, but what are you taking screen shots of when this slowness happens?

I'm thinking Vasa1 may have a good point

---

### Post by newtsoup on 2017-09-08
To answer both questions at once - I'm most often playing Kerbal Space Programme, but also Shadows of Mordor,  Shadow Tactics and more recently Oolite.  However it does it in all programs, whether full screen or windowed including just the desktop ( I shut everything down that I could think of ).

---

### Post by newtsoup on 2017-09-08
Just to be sure I rebooted: Same issue

Did:
sudo apt-get update
sudo apt-get upgrade
sudo reboot

same issue

F12 in Steam ( Shoppe Keep) works fine but there is still a 30 second delay between pressing the print screen and the print screen dialog showing ( the image in the dialog is after 30 seconds have passed and not snapped at the instant I hit the print screen button )

---

### Post by newtsoup on 2017-09-08
I also just uninstalled gnome-screenshot, reboooted and then reinstalled gnome-screenshot and it still lags by 30 seconds :(

---

### Post by newtsoup on 2017-09-08
Found this:

[http://ubuntuhandbook.org/index.php/2017/07/fix-terminal-shortcut-printscreen-key-delay-in-ubuntu-16-04/#comment-3664733](http://ubuntuhandbook.org/index.php/2017/07/fix-terminal-shortcut-printscreen-key-delay-in-ubuntu-16-04/#comment-3664733)

The work around didn't help me at all but maybe it will give someone here an idea that will help.

---

### Post by newtsoup on 2017-09-10
> **newtsoup said:**
> Found this:

[http://ubuntuhandbook.org/index.php/2017/07/fix-terminal-shortcut-printscreen-key-delay-in-ubuntu-16-04/#comment-3664733](http://ubuntuhandbook.org/index.php/2017/07/fix-terminal-shortcut-printscreen-key-delay-in-ubuntu-16-04/#comment-3664733)

The work around didn't help me at all but maybe it will give someone here an idea that will help.


OH MY WORD IT DID WORK

I just tried to print a document and the keychain daemon restarted.  NOW the print screen button responds instantly!

I really hope this benefits others.

---

### Post by newtsoup on 2017-09-10
WORKAROUND

sudo killall gnome-keyring-daemon

send a document to the printer to restart the daemon ( or do anything else that will require a password input and restart the keyring )

Print Screen button should now respond normally until the next time you restart your machine ( which in my case is about once a month )

---

