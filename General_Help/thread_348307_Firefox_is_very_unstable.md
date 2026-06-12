---
title: "Firefox is very unstable"
date: 2007-01-28
forum: General Help
---

### Post by Riot5 on 2007-01-28
I just installed Breezy Badger on my IBM Thinkpad R31, and everything went great, except that the built-in build of Firefox would crash when I open new pages, but it seemed to be random as to which pages would cause it.  I have subsequently installed the latest Firefox build from Mozilla and also Swiftfox, but both of them exhibit the same behavior; some pages worked fine in one session, then in the next, they caused a crash.

Does anyone have any tips on how I can diagnose and fix this (e.g. command outputs)?

---

### Post by Stemp on 2007-01-28
Try to launch firefox from a Terminal (console).

---

### Post by thelocust on 2007-01-28
I have noticed this problem when you dont have flash properly installed.

---

### Post by Riot5 on 2007-01-28
I tried launching Firefox from the terminal and even completely removing Flash, but that still didn't solve it.

---

### Post by Ramses de Norre on 2007-01-28
Breezy badger is an old release and many bugs are fixed in the newer ones so I suggest you try dapper or edgy.

---

### Post by Stemp on 2007-01-28
I was telling to launch Firefox from a terminal to see if there is some error messages ;)
You may also try to install and use epiphany-browser to see if there is also some problems.

---

### Post by Buck2348 on 2007-01-28
This doesn't sound like the same problem, but won't hurt to try it.

[http://ubuntuforums.org/showthread.php?t=286069](http://ubuntuforums.org/showthread.php?t=286069)

---

### Post by Riot5 on 2007-01-29
No errors when I start Firefox from the terminal, and I amended the firefoxrc file as per the flash related errors, but it still crashes intermittently. 

Epiphany works fine, it seems the problem is only in the *fox browsers.

As for updating Breezy to Dapper or Edgy, I checked the Wiki on laptop compatibility, and found that Hoary and Breezy were the only ones tested on my specific model of laptop, so I opted for Breezy.  I had attempted to install both Dapper and Edgy, but ran into installation problems right from the get-go, prompting me to use Breezy which is working just fine, except for the mozilla browsers.

---

### Post by Stemp on 2007-01-29
> Epiphany works fine, it seems the problem is only in the *fox browsers.

Epiphany is a sort of *fox browser because it use the [Gecko]("http://en.wikipedia.org/wiki/Gecko_%28layout_engine%29") engine.
Memory problem ? configuration file ? 
Strange anyway if you don't have any error messages.

---

### Post by Riot5 on 2007-01-30
I enabled the Quality Feedback Agent and the only type of incidents it sends out are of the "Program Exception" type.  Is there any way to get a more verbose description of the error?

---

### Post by Stemp on 2007-01-30
Install package :

```
firefox-dbg - debugging symbols for firefox
```

---

### Post by Riot5 on 2007-02-02
I can't seem to find that package in any of the Breezy repositories, where else could I look?

---

### Post by geirgp on 2007-02-19
> **thelocust said:**
> I have noticed this problem when you dont have flash properly installed.

I have the same problem too. What do you mean by not having flash 'properly' installed?

---

