---
title: "Running firefox on remote machine opens local copy instead?!"
date: 2008-03-13
forum: General Help
---

### Post by vav on 2008-03-13
From my work machine, sometimes I log in to my home machine and run software. I just open an ssh terminal and run whatever I want from there... both are Gutsy.

e.g. I run swiftfox (or firefox) from my home machine when I want access to some plugins I've installed at home. Works beautifully.

However, today I had a swiftfox window open on my work machine, and then I logged in to my home machine and typed 'swiftfox' in the terminal window, and the copy that opened up had all the plugins from my work machine instead...! then I closed the window from my work machine and tried again, this time it opened with the home machine's plugins.... This is really odd! :confused:

How do I make sure other programs that I open are not using my work machine's home directory? (e.g. this would totally mess up plugins like Zotero) :confused:

---

### Post by the-edmeister on 2008-03-13
You can't run more than one version of Firefox at the same time, all that happens when you try to open the second version is that you get another window of the one that is already running. There is a command line argument ```
 **-no-remote** 
``` that allows you to run multiple, simultaneous versions.

I am new to Linux and I'm not sure how to do it on the remote PC, but this is an example of how it is done in Windows, on the same PC.
```
"C:\Program Files\Mozilla\ Firefox\firefox.exe" -no-remote -P "default"
```
[http://www.mozilla.org/docs/command-line-args.html](http://www.mozilla.org/docs/command-line-args.html)
[https://bugzilla.mozilla.org/show_bug.cgi?id=308076](https://bugzilla.mozilla.org/show_bug.cgi?id=308076)
[https://bugzilla.mozilla.org/show_bug.cgi?id=325509](https://bugzilla.mozilla.org/show_bug.cgi?id=325509)


Ed

---

### Post by vav on 2008-03-14
huh... I thought any program just gets tunneled through the ssh connection and appears as a dumb X client window on the client side...  i.e. the client is not aware if it's firefox or openoffice or matlab running in that window since it's running on the server!

i.e. I run GUI programs through the ssh connection which dont exist on my client machine...!

---

