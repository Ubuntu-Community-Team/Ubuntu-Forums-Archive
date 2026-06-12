---
title: "setting chromium-browser as standard/firejail"
date: 2018-01-13
forum: General Help
---

### Post by rosika on 2018-01-13
Hi,


a happy New Year to all of you.


I´ve got a question regarding _setting chromium-browser as standard-browser_.


Up and until now my situation is the following:


I start **thunderbird** **within firejail** and then I start **firefox** **within firejail**.
Whenever I click on a link within an e-mail in thunderbird the link immediately opens in firefox (which is already running within firejail).


What I want to do now is _making chromium-browser my standard-browser_.
Therefore I changed the system-wide settings:




```
xdg-mime default chromium-browser.desktop application/https

```I controlled everything by typing 


```
xdg-mime query default x-scheme-handler/https
xdg-mime query default x-scheme-handler/http
xdg-mime query default text/html

```In all cases "chromium-browser.desktop" is set. So it should work just fine.


But when clicking on a link from an e-mail within "firejail thunderbird" virtually nothing happens. The link won´t open in "firejail chromium-browser".
Neither does it in a non-sandboxed chromium-browser.


My question now is: why does it work with firefox but not with chromium-browser?
And is there anything I can do about it?


Thanks a lot in advance.


Greetings.
Rosika  :confused:

P.S.:
system: Linux/Lubuntu 16.04.3 LTS, 64 bit

---

### Post by &amp;KyT$0P# on 2018-01-13
> **rosika said:**
> when clicking on a link from an e-mail within "firejail thunderbird" virtually nothing happens.
Sounds like Chromium is trying to load within the Thunderbird firejail, but failing.

First make sure Chromium needed files are allowed in the Thunderbird firejail.

If that's not enough, does it work if you do this? -
```
firejail chromium-browser --no-sandbox
```

---

### Post by rosika on 2018-01-14
Hi halogen2,

thanks a lot for your answer.
I tried what you suggested but without any results.

I think the problem lies somewhere within **thunderbird.profile**.
Or perhaps there are differences between the profiles of chromium-browser and firefox which cause different behaviour.

In the meantime I tried the following:

I started thunderbird normally (without firejail). No browser was running. Then I clicked on a link within an e-mail.
And suddenly an instance of chromium-browser opened and displayed the respective page.

Then I tried the same but with an already running instance of chromium-browser. A click on the e-mail link resulted in opening another
instance of chromium-browser. So two chromium-browsers were running.

When trying the same with a sandboxed thunderbird nothing happens (as described).

So there seems to be a fundamental difference in the behaiviour of firefox/chromium-browser.

The thing is: When setting firefox as standard-browser there´s no problem in clicking on an e-mail link within a sandboxed thunderbird.
It readily opens the respective page in a (already sandboxed) firefox.

So it seems the only way to solve this problem is changing the respective profiles. Yet that´s beyond my "expertise".

Anyway thanks again for your help.

Greetings.
Rosika  :)

---

