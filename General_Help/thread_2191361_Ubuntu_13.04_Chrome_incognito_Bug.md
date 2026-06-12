---
title: "Ubuntu 13.04 Chrome incognito Bug"
date: 2013-12-02
forum: General Help
---

### Post by Sterbenlee on 2013-12-02
Hey I am new to the forums and I have ran into an issue with Google Chrome. When ever I open the browser it opens a normal window but the icon in the Unity bar shows the incognito icon and the page I was on when I was originally in incognito. I have un-installed and reinstalled but it hasn't fixed my issue, Can anyone Help

Here is an image, I hope it helps show you the situation.
[ATTACH=CONFIG]248269[/ATTACH]

Thanks, Lee

---

### Post by grier-devon on 2013-12-02
> **Sterbenlee said:**
> Hey I am new to the forums and I have ran into an issue with Google Chrome. When ever I open the browser it opens a normal window but the icon in the Unity bar shows the incognito icon and the page I was on when I was originally in incognito. I have un-installed and reinstalled but it hasn't fixed my issue, Can anyone Help

Here is an image, I hope it helps show you the situation.
[ATTACH=CONFIG]248269[/ATTACH]

Thanks, Lee
Interesting bug, I haven't seen this but honestly I feel like Chrome has gone down hill. I was currently using Chrome till 13.10 and, the chrome browser kept blue screening on a fresh install. First Chrome wouldn't install on Ubuntu 13.04 and it feels really buggy on Ubuntu 13.10, I don't doubt it will get better but FF especially the nightly builds are the way to go, maybe it is time to consider switching.

---

### Post by Sterbenlee on 2013-12-02
I agree but Chrome offers me more convenience for my work between Windows and Ubuntu and on multiple PCs.

---

### Post by grier-devon on 2013-12-02
> **Sterbenlee said:**
> I agree but Chrome offers me more convenience for my work between Windows and Ubuntu and on multiple PCs.

I checked the settings and didn't see anything that would duplicate your issue. I looked and there is no way to file a bug report through google, of course you cannot do this for Chrome but everywhere I look says to file bug reports for Chrome under Chromium.

[http://www.chromium.org/for-testers/bug-reporting-guidelines](http://www.chromium.org/for-testers/bug-reporting-guidelines)

Unless anyone has better ideas I would suggest trying to see if Chromium works better for you or it is time to upgrade to 13.10 cause that is what I am using and for some reason Chrome in 13.10 does not do that. Best of luck

---

### Post by zikhali110 on 2013-12-31
> **Sterbenlee said:**
> Hey I am new to the forums and I have ran into an issue with Google Chrome. When ever I open the browser it opens a normal window but the icon in the Unity bar shows the incognito icon and the page I was on when I was originally in incognito. I have un-installed and reinstalled but it hasn't fixed my issue, Can anyone Help

Here is an image, I hope it helps show you the situation.
[ATTACH=CONFIG]248269[/ATTACH]

Thanks, Lee

I had the same problem as you did. I fixed it by deleting the file google-chrome-stable.desktop in .local/share/applications :KS

---

