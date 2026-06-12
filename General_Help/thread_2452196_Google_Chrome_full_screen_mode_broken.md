---
title: "Google Chrome full screen mode broken?"
date: 2020-10-18
forum: General Help
---

### Post by bn701 on 2020-10-18
Has anyone had their Google Chrome browser go a bit bonkers when going to full screen mode recently? Hitting F11 gets to full screen but the grey highlighted message text telling me to hit F11 again to exit full screen mode just sits there flashing and doesn't go away. From this point on, I won't be able to do anything else with the tab - no keyboard or mouse scrolling possible - and if I hit F11 again, although the browser returns to normal mode, random UI elements may still be flashing with the screen layout changing at the same rate. The browser is now unstable and unusable and the only way to recover the situation is to quit and re-open. Other programs - e.g. Firefox - are still behaviing nicely, by the way. I posted a bug report a few days ago - [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1899270](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1899270) - but haven't had any response or acknowlegement. Though, to be honest I'm not actually sure that's the place to report problems with Google's version of Chrome.

Anyway, this behaviour is still driving me slightly dotty and any suggestions for more things to try - e.g. clearing cache, reinstalling the browser (neither of which worked) - or just point out other things that I might need to clean up or might be doing wrong would be very much appreciated.

Thanks

[COLOR=#333333][FONT=monospace]Chrome: Version 86.0.4240.75 (Official Build) (64-bit)[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]System: Ubuntu Studio,[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Distributor ID: Ubuntu[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Description: Ubuntu 20.04.1 LTS[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Release: 20.04[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]Codename: focal[/FONT][/COLOR]

---

### Post by deadflowr on 2020-10-18
> Though, to be honest I'm not actually sure that's the place to report problems with Google's version of Chrome.
It's not, Ubuntu developers have no real say or input on the functions of google-chrome, they do have a say or input for chromium, though, or at least Chromium built for Ubuntu.
The correct place to report is inside Google Chrome, first, in Help click on the report an issue item to report issues.
Secondary is to report bugs to chromium: [https://www.chromium.org/for-testers/bug-reporting-guidelines]("https://www.chromium.org/for-testers/bug-reporting-guidelines")

---

### Post by bn701 on 2020-10-19
> **deadflowr said:**
> 
The correct place to report is inside Google Chrome, first, in Help click on the report an issue item to report issues.


Yes, thank you. I also found that out just after posting here as I carried on looking for ideas. Ironically, though, when I tried using it I hit similar UI problems to those I'd already encountered trying to go full screen. (Choosing the option didn't appear to do anything at first. Then I realised that it had opened another top level window with a form to fill - there was an icon for it in the task bar - but just hadn't drawn it. If I played around with the maximise and unmaximise controls I could get it to draw and I even managed to submit some text, though I had to copy and paste from another app rather than type directly.) It's a bit of a dead end when you can't communicate the problems you're having because the problem you're having is with the mechanism needed to communicate it. 

Grr ... :)

---

### Post by bn701 on 2020-10-19
Update: after searching for more general redraw problems with Chrome on Ubuntu I came across the suggestion that similar problems were concerned with hardware accelleration. On the off-chance I turned it off on my PC and now things are behaviing properly (if more slowly). And now that I've searched more widely for hardware acceleration issues in general with Chrome on Ubuntu, I gather that this is actually quite a can of worms. (e.g. [https://www.omgubuntu.co.uk/2018/10/hardware-acceleration-chrome-linux](https://www.omgubuntu.co.uk/2018/10/hardware-acceleration-chrome-linux)). I have to wonder, though, how the option ended up 'on' in my installation in the first place and why, after a year or two of trouble free use, things started to misbehave.

---

### Post by CelticWarrior on 2020-10-19
Maybe an kernel or graphics drivers update triggered the problem. BTW, how about posting your hardware specifications, namely the graphics?

---

### Post by ActionParsnip on 2020-10-19
If you make a fresh Ubuntu user and log in as that, is the behaviour the same?

---

### Post by bn701 on 2020-10-19
Interesting questions from both of you, thank you.

I'm on an old ThinkPad X230. Graphics hardware reported as "VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)"

And yes, when logging in with a fresh Ubuntu user ID I still get problems. (Specifically, I went full screen on the Google home page, found that I (apparently) couldn't type in the search box, but when I quit full screen again I could see my text had been entered after all.) I tried this first without signing in to Google/Chrome and then again after signing in. Behaviour is the same in both cases.

Thanks,

B

---

### Post by CelticWarrior on 2020-10-19
Baffling... Intel typically just works, even old ones and yours is only oldish.

Just out of curiosity can you try Chromium?

---

### Post by zasran on 2020-10-20
I have the same problem, it appeared in Chrome first (maybe a week or so ago) but now Chromium behaves the same. Added more details in [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1899270](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1899270).

This is the first mention of the same problem I've found so far. There are similar rendering problems that appeared in the past but this seems to be new. It might be Intel related cause I have another machine (also latest Ubuntu updates) where I don't have the same problem. I am using xorg (Wayland crashes on my machine), 'intel' driver, video card is Intel Corporation Iris Plus Graphics 655 (rev 01).

---

### Post by bn701 on 2020-10-20
> **zasran said:**
> I have the same problem, it appeared in Chrome first (maybe a week or so ago) but now Chromium behaves the same. Added more details in [https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1899270](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1899270).


Thanks for adding to the bug report. Someone has picked it up now. They've also asked that we share output from chrome://gpu, in case you haven't seen the request.

B

---

