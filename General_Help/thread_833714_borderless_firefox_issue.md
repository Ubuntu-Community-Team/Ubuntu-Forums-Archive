---
title: "borderless firefox issue"
date: 2008-06-18
forum: General Help
---

### Post by LeoSolaris on 2008-06-18
Firefox 3 in 8.04 64 bit has recently started coming up full screen without a border. I covers AWN( which is normally hidden, but it doesn't even pop up now) It covers new screens I open with the keyboard, and it covers the panel. Keyboard minimize does nothing.

I used to just log out and back in, but that stopped working today.

Any ideas?

Leo

---

### Post by geraldm on 2008-06-18
If there is no border, then the firefox application is maximized for the full screen.
Click on the maximize button, (usually the second from the right for most window managers) and the border should appear.  Then you can change it to occupy whatever part of the screen that you wish.  
If you close the application when it was maximized, then it will retain that for the next session, so be careful to choose the size you want to re-open in.

Gerald

---

### Post by fooman on 2008-06-18
try the F11 key.

---

### Post by LeoSolaris on 2008-06-19
@geraldm: Perhaps I didn't explain it right...  Without the border there is no max, min, or close buttons. The line that says the name of the page (or Firefox when it is on about:blank) is simply not there, otherwise I wouldn't have an issue. 

@fooman: Of course this session it is working fine so I could only test what F11 looks like on a normal window. It doesn't look the same, but that may force it into becoming "normal" when the problem comes up again. The address, bookmark toolbar, and "file Edit View" lines are all there when I get this glitch, just the little edge that has the close button on it is missing. It's what emerald would change if I were using emerald. (I am using compiz by the way)

This is on a Dell 1520 with a nVidia GeForce 8400GS. Every other progam I tried had a normal border complete with max, min, and close buttons, just Firefox 3 was effected. I wonder if some windows virus is causing a little hiccup, it's that random.

Leo

---

### Post by caiooiac on 2008-07-16
I have the exact same problem!! 

I also have compiz on, and a gforce.

I don't know if is the compiz or the nvidia...

Hope someone can help us

Thanks

---

### Post by spen25 on 2008-07-16
I had a similiar issue in the past and it was compiz being enabled.

---

### Post by LeoSolaris on 2008-08-14
I've figured something out... This issue may not be caused on my system.

I work with cyber patrol organizations to keep an eye out for things like child porn and exploitation, and I have noticed that it only happens after I find sites like that. I have found that it happens immediately after visiting certain pages. I finally got it to duplicate the error reliably by pasting back in one of the sites after forcing FF3 to recreate it's profile.ini. I am not sure what type of exploit this would be, or if it is an exploit at all. Computer security is not one of my strong suits. I picked up Linux to help with this, and perhaps I will have to move to using just the LiveCD.

I noticed that I seem to have less issues with FF2 verses FF3. I recently found a java applet that hung my entire system on a completely benign website. I haven't tried it yet with FF2, perhaps I should...   or break out Opera.

---

### Post by os.getlogin on 2008-08-14
I just had a similar issue and fixed it here:
[http://ubuntuforums.org/showthread.php?t=889881]("http://ubuntuforums.org/showthread.php?t=889881")

Basically add
```
Option "AddARGBGLXVisuals" "True"
```
to your x.org conf in the screen section.

hth.

---

### Post by LeoSolaris on 2008-08-14
I read through that thread, and thank ya but it isn't exactly the same type of bug...   I do not lose all of my window decorations, just the one around FF3. Everything else pops up normal. If it happens again, and I find a new site that causes this reaction (if it is the site like I think it is) I will do some diagnostics. I recently picked up a few tips about how to go about doing that.

That's if it happens again. The site I used to make the decorations vanish has been taken down. (woot, one for the good guys!)

Thank ya though!

---

### Post by mpgarate on 2008-09-16
is it possible for ubuntu to release automatic updates for things like this? If ubuntu is inteneded for non-power users, it would be ideal

---

### Post by wfp on 2008-09-16
I have continued to have that problem, and seems like it happens everytime i have compiz enabled or when i am changing visual effect to extra. I have had it happen around 10 times now on 2 different comps. I found that setting  visual effects back to normal brings back my border. Some times i have to restart ubuntu which also fixes the issue.

---

### Post by wynneth on 2008-12-27
This thread is old, but I figured I would update it since no one seemed to actually post the latest on this.
There are two workarounds to this issue, one being to disable Legacy Fullscreen Support in your window manager, and the other being to go into ~/.mozilla/firefox/YOURPROFILE/localstore.rdf and change the information in #main-window. Links and full workaround text below:

Localstore workaround:
<RDF:Description RDF:about="chrome://browser/content/browser.xul#main-window"
screenX="-1"
screenY="-15"
width="1024"
height="768"
sizemode="maximized" />

Change the X and Y to be 0 and the width and height to the size of the content area of the pane (1022x737) instead of the monitor, and replace "maximized" with "normal".


For compiz:
**Workaround :
Step 1 - Install compizconfig-settings-manager (sudo apt-get install
compizconfig-settings-manager)
Step 2 - Start ccsm (either from the commandline or by pushing Alt+F2 and
typing ccsm)
Step 3 - Click on "Workarounds" plugin in the "Utility"
section
Step 4 - Uncheck "Legacy Fullscreen Support".


Bug reports are numerous and are:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740)
[https://bugzilla.mozilla.org/show_bug.cgi?id=465880](https://bugzilla.mozilla.org/show_bug.cgi?id=465880)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150506](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/150506)
etc...

---

### Post by prunand on 2009-01-09
I just had this same issue, and the cause (for me anyway) was actually a firefox feature - "Full Screen".  This is available via View -> Full Screen or F11.  Simply pressing F11 resumed me to normal state.

I am not sure how I turned this on, but I suspect it was the last time I powered down I may have pressed F11 as I hastily turned off my laptop.

---

### Post by buffybot5 on 2009-01-11
I've had similar problems.  I press F11 twice every time I open a window in firefox to restore it to normal size. I've uninstalled compiz and I have pressed F11 and immediately closed Firefox, all to no avail.  I don't have (at least to my knowledge) the Legacy Full Screen manager mentioned above. I'm scratching my head (not surprising, given my lacking tech abilities). This is a recent problem, too. I'm guessing like others have mentioned, when Firefox 3 was added to the system.  Any thoughts?

---

### Post by king.pest on 2009-01-15
> **wynneth said:**
> 
For compiz:
**Workaround :
Step 1 - Install compizconfig-settings-manager (sudo apt-get install
compizconfig-settings-manager)
Step 2 - Start ccsm (either from the commandline or by pushing Alt+F2 and
typing ccsm)
Step 3 - Click on "Workarounds" plugin in the "Utility"
section
Step 4 - Uncheck "Legacy Fullscreen Support".

man, I had same issues with my radeon, and I've already tried many different solutions. you saved my day!

---

### Post by Belak on 2009-01-26
> **wynneth said:**
> 
For compiz:
**Workaround :
Step 1 - Install compizconfig-settings-manager (sudo apt-get install
compizconfig-settings-manager)
Step 2 - Start ccsm (either from the commandline or by pushing Alt+F2 and
typing ccsm)
Step 3 - Click on "Workarounds" plugin in the "Utility"
section
Step 4 - Uncheck "Legacy Fullscreen Support".

Thanks so much.
This was starting to get on my nerves.

---

### Post by caro on 2009-01-26
> **buffybot5 said:**
> I've had similar problems.  I press F11 twice every time I open a window in firefox to restore it to normal size. I've uninstalled compiz and I have pressed F11 and immediately closed Firefox, all to no avail.  I don't have (at least to my knowledge) the Legacy Full Screen manager mentioned above. I'm scratching my head (not surprising, given my lacking tech abilities). This is a recent problem, too. I'm guessing like others have mentioned, when Firefox 3 was added to the system.  Any thoughts?

I had this happen a couple of times.  I am running compiz.  This fixed it for me:

If FF opens in full screen mode, then
Press F11 twice.
Click on the unmaximize button.
Resize the window .
Click the maximize button. Firefox should be be maximized now but not covering your top or bottom panels.
Exit FF.

Relaunch and your previous settings should have been saved.

---

