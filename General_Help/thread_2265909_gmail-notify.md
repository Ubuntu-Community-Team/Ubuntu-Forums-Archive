---
title: "gmail-notify"
date: 2015-02-18
forum: General Help
---

### Post by ajgreeny on 2015-02-18
The gmail-notify panel applet which is still available in the repos does not work any more.

I know it is not very secure, but that aside, is this failure anything to do with the two stage authorisation that gmail have implemented and now require?  Using the correct username and password simply gives an error of "This is not a valid login" or similar words.

The xfce4-mailwatch plugin still works OK.

---

### Post by bapoumba on 2015-02-18
I do not use it anymore but I remember I had to set up a specific password in the 2-steps auth page for the applet (I use sylpheed now and imap sync my 2 gmail accounts and a yahoo one).

---

### Post by fx-marco on 2015-02-19
Hi !
You might want to check this:
- Allowing less secure apps to access your account : [https://support.google.com/accounts/answer/6010255](https://support.google.com/accounts/answer/6010255)

But if you want a gmail integration for xfce4 environement you can follow this simple steps
1 - Install Google Chrome (from the [website]("https://www.google.fr/chrome/browser/desktop/")), I don't know if it works with Chromium
2 - Allow Google Chrome to run in bakground mode ([Link to post]("http://askubuntu.com/questions/158216/how-to-make-google-chrome-not-start-as-service#answer-158279"))
3 - Install the [GMail Notifier]("https://chrome.google.com/webstore/detail/gmail-notifier/dcjichoefijpinlfnjghokpkojhlhkgl?utm_source=chrome-app-launcher-info-dialog") extension
4 - Launch google-chrome on "no startup window" mode when session starts :
  Settings Manager > [COLOR=#333333][FONT=Ubuntu]Session and Startup >[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Application Autostart > Add --->
     **Name :** Fill with whatever you want
     **Description :** Same as Name
     **Command :** [/FONT][/COLOR]/usr/bin/google-chrome-stable --no-startup-window

Works like a charm for me, you should try it.

+Plus: Right click on GMail extension on the extensions tab (on Chrome), last option in the menu allows you to create shortcuts on the desktop and the appmenu
(Sorry for my eventual bad english but i'm French)

---

### Post by ajgreeny on 2015-02-19
> **fx-marco said:**
> Hi !
You might want to check this:
- Allowing less secure apps to access your account : [https://support.google.com/accounts/answer/6010255](https://support.google.com/accounts/answer/6010255)

But if you want a gmail integration for xfce4 environement you can follow this simple steps
1 - Install Google Chrome (from the [website]("https://www.google.fr/chrome/browser/desktop/")), I don't know if it works with Chromium
2 - Allow Google Chrome to run in bakground mode ([Link to post]("http://askubuntu.com/questions/158216/how-to-make-google-chrome-not-start-as-service#answer-158279"))
3 - Install the [GMail Notifier]("https://chrome.google.com/webstore/detail/gmail-notifier/dcjichoefijpinlfnjghokpkojhlhkgl?utm_source=chrome-app-launcher-info-dialog") extension
4 - Launch google-chrome on "no startup window" mode when session starts :
  Settings Manager > [COLOR=#333333][FONT=Ubuntu]Session and Startup >[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Application Autostart > Add --->
     **Name :** Fill with whatever you want
     **Description :** Same as Name
     **Command :** [/FONT][/COLOR]/usr/bin/google-chrome-stable --no-startup-window

Works like a charm for me, you should try it.

+Plus: Right click on GMail extension on the extensions tab (on Chrome), last option in the menu allows you to create shortcuts on the desktop and the appmenu
(Sorry for my eventual bad english but i'm French)
NO THANKS!

I have absolutely no wish to, and in fact I refuse to use google-chrome.
It also sounds like a huge overkill to run it, even if running in the background, just to get a gmail notifier of some kind.

I am the sort of chap who does not login to anything unless it is absolutely necessary; I don't even leave my gmail account logged in as some do, and have to enter my password every time I visit it, even if it is an almost instant return.

In any case the xfce4-checkmail-plugin does work fine, as I said before.  I was simply checking out gmail-notify again, not having used it for a long time, and found that it would not work, even though all my old configuration was unchanged, and the files were still in my /home.

---

### Post by bapoumba on 2015-02-19
> **ajgreeny said:**
> 
In any case the xfce4-checkmail-plugin does work fine, as I said before.  I was simply checking out gmail-notify again, not having used it for a long time, and found that it would not work, even though all my old configuration was unchanged, and the files were still in my /home.

On several occasions (with other apps), I had to revoke a password and re-issue a new one.

---

### Post by ajgreeny on 2015-02-19
> **fx-marco said:**
> Hi !
You might want to check this:
- Allowing less secure apps to access your account : [https://support.google.com/accounts/answer/6010255](https://support.google.com/accounts/answer/6010255)

But if you want a gmail integration for xfce4 environement you can follow this simple steps
1 - Install Google Chrome (from the [website]("https://www.google.fr/chrome/browser/desktop/")), I don't know if it works with Chromium
2 - Allow Google Chrome to run in bakground mode ([Link to post]("http://askubuntu.com/questions/158216/how-to-make-google-chrome-not-start-as-service#answer-158279"))
3 - Install the [GMail Notifier]("https://chrome.google.com/webstore/detail/gmail-notifier/dcjichoefijpinlfnjghokpkojhlhkgl?utm_source=chrome-app-launcher-info-dialog") extension
4 - Launch google-chrome on "no startup window" mode when session starts :
  Settings Manager > [COLOR=#333333][FONT=Ubuntu]Session and Startup >[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]Application Autostart > Add --->
     **Name :** Fill with whatever you want
     **Description :** Same as Name
     **Command :** [/FONT][/COLOR]/usr/bin/google-chrome-stable --no-startup-window

Works like a charm for me, you should try it.

+Plus: Right click on GMail extension on the extensions tab (on Chrome), last option in the menu allows you to create shortcuts on the desktop and the appmenu
(Sorry for my eventual bad english but i'm French)
NO THANKS!

I have absolutely no wish to, and in fact I refuse to use google-chrome.
It also sounds like a huge overkill to run it, even if running in the background, just to get a gmail notifier of some kind.

I am the sort of chap who does not login to anything unless it is absolutely necessary; I don't even leave my gmail account logged in as some do, and have to enter my password every time I visit it, even if it is an almost instant return.

In any case the xfce4-checkmail-plugin does work fine, as I said before.  I was simply checking out gmail-notify again, not having used it for a long time, and found that it would not work, even though all my old configuration was unchanged, and the files were still in my /home.

PS: I already know about that link you gave regarding less secure applications and my system had already chosen to enable that; I had not knowingly made changes myself.
I know most users now seem to use IMAP, which is great on mobile tablets and phones, but on my desktop machine it is very worthwhile to me, to have my gmail set using pop3, meaning I have a large cache of very old emails which I can read without need to be permanently online.

---

### Post by kerry_s on 2015-02-19
i also just use the xfce mailwatch, use zenty or notify-send for the popup & your all set, you can even customize the icons, what more do you need ?

---

### Post by fx-marco on 2015-02-19
Solutions? some people want to try something new, I mean, you don't have to do like everyone else, in this case, use mailwatch.
That's why I clearly said "if you want", if you don't want to, just don't do it.

---

### Post by slickymaster on 2015-02-19
> **kerry_s said:**
> i also just use the xfce mailwatch, use zenty or notify-send for the popup & your all set, you can even customize the icons, what more do you need ?
Yeah, Mail Watcher still works.

---

