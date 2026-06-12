---
title: "Ubuntu logout"
date: 2008-06-28
forum: General Help
---

### Post by maaltan on 2008-06-28
Is it normal in linux to kill all applications upon shutdown/reboot/logout without allowing them to clean up?  I am used to windows where it warns all programs that it is shutting down allowing you to save data and allow the application to terminate gracefully.

When i shutdown my computer all applications act like they crashed unless i close everything manually.  Firefox 3 restores tabs even though I tell it to clear private data, Evolution has given me corrupt mailbox errors several times, I have lost several text files i was editing.  I have also had to reinstall firefox because the config data became corrupt.

Is there a script i can run that emulates a graceful shutdown?

I am trying to use kill but i have not found the signal that the "x" button at the top of the window sends.

Thanks

---

### Post by hopelessone on 2008-06-28
In Terminal:

```
sudo shutdown -h now
```

Hope that helps... :)

---

### Post by maaltan on 2008-06-28
Thanks, but I have tried that.  It is even more brutal and rude (at least it's faster..  full shutdown in less that 10 seconds most of the times). 

The more i research the more it seems like this is normal for X termination.  Assuming that is true how do I completely disable crash/tab/session recovery in firefox 3.  This is a mobile computer and I dislike saving any personal data on it.  The tab restore can be a privacy risk.

---

### Post by hopelessone on 2008-06-28
it's in the firefox preferences...here's mine

---

### Post by unutbu on 2008-06-28
This works in Firefox 2.0.0.14; I'm guessing FF3 works similarly:

Edit>Preferences
Click on the Privacy tab.
Change your setting to those shown in the attachment.

---

### Post by maaltan on 2008-06-28
thanks but no good, 

If you could get one of you that posted the privacy fixes to try the following.  I am interested if someone else is seeing this.

1:  make your privacy settings to match the screenshots posted by unutbu and hopelessone.
2:  on options-> main tab set "when firefox starts" to "open my home page".
3:  open several tabs to multiple sites (i also see this with a single "tab")
4:  logout of ubuntu using the "little green running man" applet. do not close firefox.
5:  login
6:  restart Firefox.
7:  I see that firefox is restored to exactly how it was before I logged out.  

I want my home page only in a single tab.

I am also interested in firefox 2 behavior.

I am about to try a workaround for firefox 2 for windows (bug supposed to be fixed in 2.0.0.2, but worth a try) that is indicated by similar behavior.  It involves disabling crash recovery completely.  I would prefer not to have to do this since firefox still crashes a lot in unbuntu :)

thanks

-------------------
update:  Disabling crash recovery (set browser.sessionstore.resume_from_crash to false) has no affect.  I was reading that gnome/ubuntu has some session saving settings of it's own.  how can i disable/modify those?

---

### Post by hopelessone on 2008-06-28
Damn it you are right...i just selected start new session...doh!

BTW...you don't have to log out to test it go to system monitor in the admin and right click and select "kill" application...does the same thing as brutal restart...

---

### Post by maaltan on 2008-06-28
> **hopelessone said:**
> Damn it you are right...i just selected start new session...doh!

BTW...you don't have to log out to test it go to system monitor in the admin and right click and select "kill" application...does the same thing as brutal restart...

That seems to be something different.  I get a crash recovery dialog when I kill firefox.  when i logout/in it gives me nothing. It just reopens tabs.

Are you seeing different behavior?

---

### Post by unutbu on 2008-06-28
I opened a bunch of tabs,
Clicked Mr. Green-running-Man, to shutdown, booted back up, launched FF2, and was asked if I wanted to restore my previous session. 

I then put "about:config" in the uri line, set the filter to "crash", and set browser.sessionstore.resume_from_crash to false.

I again clicked Mr. Green-running-Man, shutdown, booted back up, launched FF2, and this time was shown my homepage.

I then killed FF2 with the command

```
killall -r ^firefox
```

and launched FF2 again. Again, I just get my homepage. It appears for me,

Setting browser.sessionstore.resume_from_crash to false works.

[Edit: I get the same behavior when I close the FF2 window abruptly, and also when I logout without closing FF2.]

---

