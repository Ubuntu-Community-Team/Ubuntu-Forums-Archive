---
title: "Flashplugin and Opera"
date: 2007-06-02
forum: General Help
---

### Post by Freddy on 2007-06-02
Howdy all, I just recently installed Opera and what a wonderful browser it is :-). The second page a logged on to used flash for some nifty graphics and the plugin wasn't installed for my new browser but it directed me to the page where I could download a tarball of it.

The boring part of it is that on the download page it says that the plugin is only for 'Firefox, Mozilla, SeaMonkey', ohh I thought they forgot to add Opera and downloaded it anyways, but no, when I tried to install the plugin in /usr/lib/opera it says it's not compatible with that browser. Are there any ways around this little problem or will my Opera be flashless?

/// Thanks

Btw, I should add that I have firefox already installed and flash works with that browser.

---

### Post by Freddy on 2007-06-02
I managed to get it installed the ugly way, so nevermind this thread :-).

---

### Post by cotcot on 2007-06-02
I have Opera running well with flash plugin in feisty (32 bit) and gentoo (64 bit). I do not remember exactly how I installed it but found a tutorial [here]("http://ubuntuforums.org/showthread.php?t=413040").
I suppose you have installed java and validated the java path ? (mine is /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386)
If the flash plugin is not working try it after removing the mozilla path from your plugin paths.

---

### Post by Joseaa on 2007-06-13
For flash, Opera uses the same plugin as that of Mozilla(libflashplayer.so). But unfortunately, flash installer doesn't let to install it in Opera's plugin directory( Just something that adobe prefers to do). 

By default, Opera is set to search for plugins in Mozilla's plugin directory. So, if you install the plugins in for Mozilla, it will work fine with Opera.

---

