---
title: "[SOLVED] Bluefish - view browser button doesn't work"
date: 2007-06-26
forum: General Help
---

### Post by geovino on 2007-06-26
I trying to get used to  Bluefish, but I can't get the view browser button to view a browser. How does it work? 

If I click on External > Browsers > Mozilla, then Firefox views the code, but how do you get the View in Browser button to open Firefox? 

I like the quickness of Bluefish, but Quanta seems to work better.

---

### Post by merlinus on 2007-06-26
In Edit/Preferences/External programs, what does the mozilla line say?

-merlin

---

### Post by geovino on 2007-06-27
> **merlinus said:**
> In Edit/Preferences/External programs, what does the mozilla line say?

-merlin

mozilla -remote 'openURL(%s, new-window)' || mozilla %s&

What should it be?

---

### Post by krpnm on 2007-06-27
Try this:

1.  Open up Bluefish, click on edit -- prefences.
2.  Click on External programs.
3.  Click on Add.
4.  Double click on untitled.
5.  Type in Firefox.
6.  To the right of the new entry -- double click.
7.  Type in %s.
8.  Click on apply.
9.  Click on ok.

Done.

---

### Post by geovino on 2007-06-27
i did that, but it did nothing. What's missing?

---

### Post by merlinus on 2007-06-27
I wonder if it is some setting in Firefox?  You might check Edit/Preferences.

-merlin

---

### Post by geovino on 2007-06-28
I looked at Firefox preferences and don't see anything that would get in the way. All I can see in the Bluefish preferences is a mozilla listing that is:
mozilla -remote 'openURL(%s, new-window)' || mozilla %s&

but it only works when going to External > browsers in Bluefish. None of the browsers open with the View in Browser button.

Any other clues?

---

### Post by andrew.46 on 2007-07-06
Hi,

 Correct setting for Firefox is:

```
/usr/bin/firefox -new-window "%s" &
```

as long as this your path. The browser at the top of the list is the one that will open by the View in Browser button.

                     Andrew

---

### Post by geovino on 2007-07-08
Thanks. that worked :)

the path turned out to be:  /usr/lib/firefox/firefox

---

### Post by andrew.46 on 2007-07-08
Hi,

 I wish I could claim credit for that! Got the answer a while ago from a bug report:

[https://answers.launchpad.net/bluefish/+question/3279](https://answers.launchpad.net/bluefish/+question/3279)

 and I have been spreading the word ever since :-)

                         Andrew

---

