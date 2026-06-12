---
title: "Chrome steals default from Firefox. Any fix?"
date: 2015-08-12
forum: General Help
---

### Post by Declan_Lowe on 2015-08-12
Hi, I have Firefox set as my preferred application for web browsing, but I also have Chrome on my machine. When I click on html files or when, for instance, a program wants to open a browser window, it always opens Chrome--and not my default Firefox.

Does anyone know of a fix for this?

Many thanks, Dec:p

---

### Post by deadflowr on 2015-08-12
Quick fix for individual files is to right click on the file (the html file, in this case), go to properties, got to open with and reset it with firefox as the default.
Then from now on all html files will open directly in firefox.
Or at least they should.

---

### Post by Declan_Lowe on 2015-08-12
Thanks--done! But other programs, when they want to spawn a weblink, still open Chrome. Chrome is definitely not my default. It's strange that Chrome should do that. It seems to insert itself right after installation. I mean, I had a new install of Linux. I used Firefox. I then installed Chrome and, before I'd even used it, it was stealing weblinks from programs.

---

### Post by Dennis N on 2015-08-12
> **Declan_Lowe said:**
> Thanks--done! But other programs, when they want to spawn a weblink, still open Chrome. Chrome is definitely not my default. It's strange that Chrome should do that. It seems to insert itself right after installation. I mean, I had a new install of Linux. I used Firefox. I then installed Chrome and, before I'd even used it, it was stealing weblinks from programs.

You might use this command and see what it gives you. It will tell you what is the system default browser, which may be the one used when links are opened from within other applications (maybe a link in LibreOffice, for example). 

**update-alternatives --get-selections | grep x-www-browser**

Here is mine. 

```
dmn@Sydney:~$ update-alternatives --get-selections | grep x-www-browser
x-www-browser                  auto     /usr/bin/firefox

```

Can be changed if it's not the one you want.
-------------------------------------------------------------------------
P[316]

---

### Post by Declan_Lowe on 2015-08-12
Ah, I see, mine comes out as:

> x-www-browser                  auto     /usr/bin/google-chrome-stable

Can you tell me how to change it? :)

---

### Post by Dennis N on 2015-08-12
I booted into another OS that has Firefox and Chrome both installed. I ran the command I suggested, and sure enough, Chrome has set itself as the default. It was installed second, and did not ask.


```
dmn@Sydney:~$ update-alternatives --get-selections | grep x-www-browser
x-www-browser                  auto     /usr/bin/google-chrome-stable

```

To change it to Firefox, run the following:

```
dmn@Sydney:~$ sudo update-alternatives --config x-www-browser
[sudo] password for dmn: 
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                           Priority   Status
------------------------------------------------------------
* 0            /usr/bin/google-chrome-stable   200       auto mode
  1            /usr/bin/firefox                40        manual mode
  2            /usr/bin/google-chrome-stable   200       manual mode

Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /usr/bin/firefox to provide /usr/bin/x-www-browser (x-www-browser) in manual mode

```

Firefox is now the default browser.

---

### Post by Declan_Lowe on 2015-08-12
Awesome! Thanks! :)

---

### Post by Dennis N on 2015-08-12
Forgot to include this: To confirm the result run the query again:

```
dmn@Sydney:~$ update-alternatives --get-selections | grep x-www-browser
x-www-browser                  manual   /usr/bin/firefox
```

Notice **auto** has changed to **manual**. That means it has been set by the user. **manual** mode is permanent until changed again by the user.

---

### Post by Dennis N on 2015-08-12
To be absolutely sure it works as advertised on embedded links, I had a LibreOffice Writer document with a few web links within the text, and these open now in Firefox, not Chrome, even when Chrome is already open and Firefox is not.

---

