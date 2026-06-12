---
title: "[xubuntu] Standard Browser setting not saved."
date: 2014-05-16
forum: General Help
---

### Post by gaseabra on 2014-05-16
Hello everyone,

I'm using Xubuntu 12.04 since november 2012 and my issue never bothered me until now. To the issue:

I use Google Chrome as my favorite browser and obviously, want to have it as standard browser. I've done so in Chrome's settings and in Applications Settings under system settings.

Everytime I start the first Google Chrome window, it asks me if I wish to set ip as standard browser.

Is there any script I can use to force the browser to be set as standard? GUIs are not working.

Thanks in advance.

---

### Post by slickymaster on 2014-05-16
Open xfce4-settings-manager as root either:
```
sudo -i
xfce4-settings-manager
```
or
```
gksu xfce4-settings-manager
```
then select preferred apps, and under browsers select other then paste:
```
/usr/bin/X11/google-chrome
```

---

### Post by gaseabra on 2014-05-16
Thanks for the reply, but it didn't work. :(

---

### Post by Dennis N on 2014-05-17
If "standard browser" is the same as "default browser" then you would set it using the update-alternatives command:

Here is the terminal command and output on my computer. You need only enter the selection number. Of course yours would not include chromium.

```
dmn@Roxanne:~$ sudo update-alternatives --config x-www-browser
There are 2 choices for the alternative x-www-browser (providing /usr/bin/x-www-browser).

  Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/bin/firefox            40        auto mode
  1            /usr/bin/chromium-browser   40        manual mode
  2            /usr/bin/firefox            40        manual mode

Press enter to keep the current choice[*], or type selection number:

```

That's it.

---

### Post by gaseabra on 2014-05-17
Here is what I have:


Selection    Path                       Priority   Status
------------------------------------------------------------
* 0            /usr/bin/google-chrome-stable   200       modo automático
  1            /usr/bin/arora                  90        modo manual
  2            /usr/bin/firefox                40        modo manual
  3            /usr/bin/google-chrome-stable   200       modo manual

How do I get rid of number 3?

---

### Post by Dennis N on 2014-05-17
> Selection Path Priority Status
------------------------------------------------------------
* 0 /usr/bin/google-chrome-stable 200 modo automático
1 /usr/bin/arora 90 modo manual
2 /usr/bin/firefox 40 modo manual
3 /usr/bin/google-chrome-stable 200 modo manual

How do I get rid of number 3? 

You should select number 3 (manual mode). A manual mode choice is never overridden until the user chooses to change that selection.

---

### Post by gaseabra on 2014-05-17
It seemed to have worked. I'll monitor it and give the feedback here. As for the 3, I'll leave as it is.

As soon as I confirm it worked, I'll set the thread as solved.

Thanks in advance, Dennis.

---

### Post by slickymaster on 2014-05-18
If Dennis N doesn't work, one other thing you can also try is to manually set the values in the **defaults.list** file to Chrome.

```
gksudo gedit /usr/share/applications/defaults.list
```
try to find _x-www-browser_ and set its value to your **google-chrome.desktop** location

_**EDIT:**_ If you won't find x-www-browser, then try to search for```

text/html=firefox.desktop;google-chrome.desktop
text/xml=firefox.desktop;google-chrome.desktop
application/xhtml_xml=google-chrome.desktop
x-scheme-handler/http=firefox.desktop;google-chrome.desktop
x-scheme-handler/https=firefox.desktop;google-chrome.desktop
x-scheme-handler/ftp=google-chrome.desktop
```

---

### Post by gaseabra on 2014-05-18
So, it worked. Thank you!

---

### Post by gaseabra on 2014-05-20
Here I am. After some days, Google Chrome is asking to be default browser again. So, it didn't work :S

---

### Post by slickymaster on 2014-05-20
Did you tried the solution proposed in [post #8]("http://ubuntuforums.org/showthread.php?t=2224472&p=13026893&viewfull=1#post13026893")?

---

### Post by Dennis N on 2014-05-20
> **gaseabra said:**
> Here I am. After some days, Google Chrome is asking to be default browser again. So, it didn't work :S

In post #6, I said you should select the manual mode when making a selection. Did you do that, or just leave it as it was with Chrome in auto mode? If so, rerun the same command from post #4 and check the mode (should be Chrome in manual mode, not auto) - reselect if needed.

Manual mode is not supposed to change to another option unless the user changes it.

---

### Post by gaseabra on 2014-05-20
> **slickymaster said:**
> Did you tried the solution proposed in [post #8]("http://ubuntuforums.org/showthread.php?t=2224472&p=13026893&viewfull=1#post13026893")?


I found this:

text/html=firefox.desktop;google-chrome.desktop
text/xml=firefox.desktop;google-chrome.desktop
application/xhtml_xml=google-chrome.desktop
x-scheme-handler/http=firefox.desktop;google-chrome.desktop
x-scheme-handler/https=firefox.desktop;google-chrome.desktop
x-scheme-handler/ftp=google-chrome.desktop
image/webp=google-chrome.desktop

---

### Post by gaseabra on 2014-05-20
> **Dennis N said:**
> In post #6, I said you should select the manual mode when making a selection. Did you do that, or just leave it as it was with Chrome in auto mode? If so, rerun the same command from post #4 and check the mode (should be Chrome in manual mode, not auto) - reselect if needed.

Manual mode is not supposed to change to another option unless the user changes it.


Did now again. Will get back to you next time I reboot my system.

---

### Post by gaseabra on 2014-05-20
> **Dennis N said:**
> In post #6, I said you should select the manual mode when making a selection. Did you do that, or just leave it as it was with Chrome in auto mode? If so, rerun the same command from post #4 and check the mode (should be Chrome in manual mode, not auto) - reselect if needed.

Manual mode is not supposed to change to another option unless the user changes it.

It didn't work.

Can we just go for a script to force it to be default browser at login time?

---

### Post by slickymaster on 2014-05-20
The problem setting it through **update-alternatives** is that it sets the system-wide default, and that default isn't actually used in Xfce given that &#8220;Preferred Applications&#8221; apparently takes precedence.

There's one last thing to try, though. You should have in the ~/.local/share/applications/mimeapps.list file the following lines:```
x-scheme-handler/http=exo-web-browser.desktop
x-scheme-handler/https=exo-web-browser.desktop
```Change the values of x-scheme-handler from http=exo-web-browser.desktop to _http=google-chrome.desktop_ in order the file to read like this:
```
text/html=google-chrome.desktop
x-scheme-handler/http=google-chrome.desktop
x-scheme-handler/https=google-chrome.desktop
x-scheme-handler/about=google-chrome.desktop
x-scheme-handler/unknown=google-chrome.desktop
```
Make sure these lines are under either the **[Default Applications]** or **[Added Associations]** section.

---

### Post by Dennis N on 2014-05-20
Well, I agree with slickymaster on the definition of default. I thought that was what we were trying to set - systemwide default. What does Chrome consider "default"? Is it what we call "preferred" as in the Preferred Applications (see below)?

I recently saw the message in Chromium on the new install of 14.04 about being the default browser, and just checked "Don't ask me again". No more messages. In Chromium settings, my Chromium currently says "Chromium is not currently your default browser".

As an experiment:

I changed x-www-browser to Chromium in alternatives, logged out and back in, started Chromium, checked its settings dialog and Chromium still says it its not the default browser. 

Next:

There is the dialog in Xubuntu's settings for "Preferred Applications". I changed Web Browser to Chromium, and now Chromium opens hyperlinks instead of Firefox (which did it previously). But, Chromium settings still claims it is not the default browser. 

Go figure. Hope slickymasters suggestions get you there. Just setting it in Preferred Applications may be all you need. It works for me. Doing that with your browser of choice seems to give it all the characteristics one might think goes with the term default.

---

### Post by gaseabra on 2014-05-20
> **Dennis N said:**
> Well, I agree with slickymaster on the definition of default. I thought that was what we were trying to set - systemwide default. What does Chrome consider "default"? Is it what we call "preferred" as in the Preferred Applications (see below)?

I recently saw the message in Chromium on the new install of 14.04 about being the default browser, and just checked "Don't ask me again". No more messages. In Chromium settings, my Chromium currently says "Chromium is not currently your default browser".

As an experiment:

I changed x-www-browser to Chromium in alternatives, logged out and back in, started Chromium, checked its settings dialog and Chromium still says it its not the default browser. 

Next:

There is the dialog in Xubuntu's settings for "Preferred Applications". I changed Web Browser to Chromium, and now Chromium opens hyperlinks instead of Firefox (which did it previously). But, Chromium settings still claims it is not the default browser. 

Go figure. Hope slickymasters suggestions get you there. Just setting it in Preferred Applications may be all you need. It works for me. Doing that with your browser of choice seems to give it all the characteristics one might think goes with the term default.


I want Google Chrome to be the default browser system wide, yes. 
[COLOR=#000000]slickymaster's solution didn't work. I've tried "Preferred Applications" several times. It does not work either.[/COLOR]

I was using Chromium previously, but had to uninstall it cause it refuses to play flash videos, even with the last update installed.

Now I'm stuck with Google Chrome and it keeps saying it's not the default browser.

---

### Post by bapoumba on 2014-05-20
I have read that somewhere some time ago but do not seem to find it again..
Seems that sometimes Chrome forgets where it is installed, so you have to give the full path to it.

---

### Post by gaseabra on 2014-05-20
Well, how would a script look like excuting update-alternatives --config x-www-browser with the option 3?


I want this to be excecuted automatically.

---

### Post by pretty_whistle on 2014-05-25
I had this same issue and just fixed it.  I have ubuntu 14.04 with xfce desktop so hopefully this will work on yours:

1st go into chrome and set it to default browser.  Then go into applications and hit the standard browser icon and it should be asking you to set it.  From here you surf to /usr/bin/X11/google-chrome.

That should fix it.  As I said, I just fixed mine this way.

Good luck.

---

### Post by gaseabra on 2014-05-26
Since last week my browser hasn't asked the question again. So it's solved.

---

