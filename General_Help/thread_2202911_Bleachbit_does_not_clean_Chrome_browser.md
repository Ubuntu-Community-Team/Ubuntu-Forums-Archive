---
title: "Bleachbit does not clean Chrome browser"
date: 2014-01-31
forum: General Help
---

### Post by deaton25 on 2014-01-31
Hi
I have Bleachbit. It refuses to clean my Chrome browser because it says it is running----even after I have shut it down and even after I have gone off-line!
Anybody have any idea what I should do?

---

### Post by SuperFreak on 2014-01-31
You could try "system monitor" in dash and locate Chrome under processes and right click "kill process"

---

### Post by deaton25 on 2014-01-31
Now i am really confused! The system monitor tells me i have a Gnome desktop. but i always thought that i had Unity!
and Ubuntu Tweak says that i have Unity, too. What the ----???!! but, in the desktop recovery part of tweak it says i have a gnome setting!! what gives????  also, in the system monitor- processes- there about a dozen different chrome settings. Which one would i kill so i could use bleachbit? and once i killed it, could i turn it back on again so that it would be business as usual???

---

### Post by vasa1 on 2014-01-31
Alan, 
please open chrome://settings 
click on *advanced settings* at the bottom of the page 
Look for *System* at the bottom of the expanded page
See if *Continue running background apps when Google Chrome is closed* is ticked or not. 

BTW, I hope you're careful when using things like Bleachbit :) It's easy to overdo things.

---

### Post by deadflowr on 2014-01-31
You can open the google-chrome settings option "Tools'
and then select the option clear browser history.

On the topic of unity and gnome desktop, unity is *a* gnome desktop.

---

### Post by ubudog on 2014-01-31
You could try:
```
killall google-chrome
```

---

### Post by deaton25 on 2014-01-31
thanks! i will try that! but first, i need to know how do i restore google-chrome after i've killed it and cleaned it??? that is, how do i un-kill it?

---

### Post by deadflowr on 2014-01-31
Just start it like normal.
killall just stops the processes.

It's not like you send it to another dimension or something.

---

