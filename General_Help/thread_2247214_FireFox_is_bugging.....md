---
title: "FireFox is bugging...."
date: 2014-10-06
forum: General Help
---

### Post by paul_hubbarth on 2014-10-06
Thank you for visiting my issue. 

Since upgrading to 14.04 LTS I have had an issue with FireFox. It randomly opens new browser windows in the background. I have no idea why. Sometimes it seems like using the cut and paste commands triggers it, but as I type this post (not using said commands) a new window just opened! 

I am new to Linux and Ubuntu, using it mostly as a consumer, not as a developer. I'd guess that the problem comes from a virus or from some kind of macro that was 'accidently' set. 

Any ideas? Any help will be appreciated! 

Many, many thanks.

---

### Post by Habitual on 2014-10-08
Paul:
Can you please try starting firefox in safe-mode using
```
firefox -safe-mode
``` in a terminal and let us know if the problem persists?

You may see some diagnostics in the terminal, but you may disregard them (unless it's fatal and firefox will not start).
If it is fatal, please report the output from terminal.

Thank you.

---

### Post by frank18 on 2014-10-08
> **paul_hubbarth said:**
> Thank you for visiting my issue. 

Since upgrading to 14.04 LTS I have had an issue with FireFox. It randomly opens new browser windows in the background. I have no idea why. Sometimes it seems like using the cut and paste commands triggers it, but as I type this post (not using said commands) a new window just opened! 

I am new to Linux and Ubuntu, using it mostly as a consumer, not as a developer. I'd guess that the problem comes from a virus or from some kind of macro that was 'accidently' set. 

Any ideas? Any help will be appreciated! 

Many, many thanks.

Buggy: Not to me anymore, because i removed firefox and installed Google Chrome on all my linux and win  machines and was the best thing i ever did, since google chrome is far better and faster then firefox and has it's own flash Player,

---

### Post by speartip on 2014-10-08
Chances of it being a virus is close to nil. It's more likely to be a configuration file conflict after you upgraded to 14.04, or a dodgy add-on.
Depending on how much you have configured Firefox, you could delete your profile, & give Firefox a clean start.
To do that close firefox & delete the .mozilla file in your home folder.
 Then open up Firefox and see if the problem persists.

---

