---
title: "braids screen saver"
date: 2007-11-30
forum: General Help
---

### Post by SaltyCrak on 2007-11-30
hi guys.

i have a pretty serious problem...
now if you've read any of my previous posts then you'll know that i'n a noob. 

off topic: i don't feel as bad admitting to this fact as i would on other forums because so far, i have only met decent people over here... Respect to South Africans. we can actually do something right.

back to my problem...
i got bored of the standard blank screensaver, so o decided to change it. as i was scrolling down the list of standard screen savers on a gutsy install, i hit onw called "braids". as soon as it loads, my machine freezes and the only thing that respomds is the hard reboot. 

this wouldn't be a problem if i had set the timeout to be -t. but of course, it's sitting at 10 mins. 
essentially, this means that i have 10 mins of idle time before my machine dies... not cool...

so, my question id:
what config file (and where do i edit it) do i need to edit to switch my screem saver off?

cheers,
kev

---

### Post by FuturePilot on 2007-11-30
I have this same problem. It's related to Compiz. If you do
```
metacity --replace
```
you'll notice it works fine.
Then you can change it to something else. Then reactive Compiz
```
compiz --replace
```

---

