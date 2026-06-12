---
title: "Cookie problems with Firefox"
date: 2007-05-22
forum: General Help
---

### Post by p_quarles on 2007-05-22
For reasons that I'm unable to comprehend, Firefox suddenly began defaulting to having cookies disabled. I ran into the same problem described in  this thread ([http://ubuntuforums.org/showthread.php?t=446646&highlight=firefox+cookies](http://ubuntuforums.org/showthread.php?t=446646&highlight=firefox+cookies)), where I suddenly became unable to log in to registered sites (this one, my local newspaper, slashdot). I figured out, however, that the "accept cookies" option in Preferences had been unchecked. I checked it, and everything instantly started working again.

Until I restarted Firefox. On every start, it runs the program with "accept cookies" off.

Anyway, I have a couple dozen extensions, but I really don't think any of those are the issue, since no new ones had been installed when this happened. Happy to list them if it would help.

So, my question: is it possible to directly edit some data file that tells Firefox how to start? I've been using Ubuntu for about a month now (and loving it), and am getting comfortable with the command line, but I don't know enough about the way individual apps are stored in the directories to know where to begin to look. Thanks in advance!

---

### Post by orb9220 on 2007-05-22
You can try typing **about:config** in the address bar. Then type** cookies** in search bar which will show cookies settings.

Sorry that is all I can think of at the moment.

---

### Post by p_quarles on 2007-05-22
I toggled all the setting for cookies there, and nothing helped. Still, thanks for the reply: didn't know about the internal config editor, and I'm certain that'll be useful in the future.

2 minutes later edit: D'oh. It *was* an extension. At some point I must have turned on the "Stealther" extension, probably by accident. Turns out that this turns off cookie acceptance (duh). Anyway, all is well and I will now sheepishly retreat.

---

