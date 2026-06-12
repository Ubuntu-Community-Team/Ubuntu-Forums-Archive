---
title: "Google Chrome Resets Itself as Default Browser Every Time It's Opened"
date: 2016-07-19
forum: General Help
---

### Post by loboes41 on 2016-07-19
I prefer Firefox as my default broswer, but I do often open Google Chrome. Unfortunately every time I run Chrome, it automatically becomes the default browser on the system. Every time, I change Firefox back (either through the FF modal, or through Unity System Settings -> Details -> Default Applications) but it never sticks.

I am running 14.04 with Unity on a Dell XPS developer edition laptop pre-installed with Ubuntu.

Setting the configuration through update-alternatives seems to have no effect. Here is the current output: 

```

:~$ sudo update-alternatives --config gnome-www-browser 
There are 2 choices for the alternative gnome-www-browser (providing /usr/bin/gnome-www-browser).

  Selection    Path                           Priority   Status
------------------------------------------------------------
* 0            /usr/bin/firefox                40        auto mode
  1            /usr/bin/firefox                40        manual mode
  2            /usr/bin/google-chrome-stable   30        manual mode

Press enter to keep the current choice[*], or type selection number: 


:~$ sudo update-alternatives --config x-www-browser 
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                           Priority   Status
------------------------------------------------------------
* 0            /usr/bin/firefox                40        auto mode
  1            /usr/bin/firefox                40        manual mode
  2            /usr/bin/google-chrome-stable   30        manual mode

Press enter to keep the current choice[*], or type selection number:

```

Is there no way to stop Chrome from doing this? This is driving me crazy.

---

### Post by &amp;KyT$0P# on 2016-07-19
Why are you using specifically Google Chrome when you can just use Chromium from the repositories?

Anyway, in Chrome/Chromium, navigate to [FONT=Courier New]chrome://settings[/FONT] and there should be a section there "Default browser" where you can change the behavior, no?
(Mine only says "Chromium cannot determine or set the default browser.", but that's probably due to quirks of my specific setup.)

---

### Post by loboes41 on 2016-07-19
When I open Chrome, it has already set itself to the default. It does not allow you to "unset" Chrome as the default from there. It just says: "The default browser is currently Google Chrome" with no other options.

---

### Post by &amp;KyT$0P# on 2016-07-19
Does this help? [http://playingwithsid.blogspot.com/2012/05/unset-chromium-as-default-browser-on.html]("http://playingwithsid.blogspot.com/2012/05/unset-chromium-as-default-browser-on.html")

---

