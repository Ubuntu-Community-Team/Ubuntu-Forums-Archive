---
title: "Installing Flash plug-in on Lubuntu 14.04 makes impossible watching movies on Youtube"
date: 2015-01-11
forum: General Help
---

### Post by bartek6 on 2015-01-11
Hi everybody,

I've problem with Flash plug-in on Lubuntu 14.04.1. Installing it makes impossible watching movies on Youtube. After uninstalling it's became possible again. I need installed Flash plug-in for another purposes. Does anybody know how to solve this problem?

---

### Post by efflandt on 2015-01-11
Which browser are you using, or are you using the YouTube app from Software Center? I just tried that YouTube app from Software Center and it does not seem to work. There are thumbnails of parts of the vidio if you put the cursor along the progress bar at the bottom, but the main screen just keeps spinning and the video never starts.

But YouTube videos work fine in Firefox, so it is just the YouTube specific app that is broken, not whether there is some conflict between flash and HTML5 in general.

---

### Post by bartek6 on 2015-01-11
I'm using Firefox and I don't have YouTube app from Software Center.

---

### Post by ajgreeny on 2015-01-11
How did you install the flashplugin?

The best way is with software-center or synaptic and install **flashplugin-installer**, which will itself download and install the plugin from adobe or install **lubuntu-restricted-extras**, which will also do that and bring in a lot of other codecs and mstcorefonts.

---

### Post by Impavidus on 2015-01-11
If you have the flashplugin installed, youtube will default to flash. If you don't have flash or if you have disabled flash, youtube will default to html5. In my experience both work, but when using html5 it's slightly more responsive. So, instead of uninstalling flash, disabling it in Firefox may do the trick. Go to add-ons, find flash and choose "never activate". I keep the flashplugin disabled most of the time.

---

### Post by ajgreeny on 2015-01-11
Go to [https://www.youtube.com/html5](https://www.youtube.com/html5) to see what your settings are for using html5 or flash as default on youtube videos.

---

### Post by Ko_Char on 2015-01-11
You can disable/enable Flash plugin in Firefox add-ons manager.
Type about:addons in the URL. 
Go to Plugins
ShockWave Flash > Choose never activate
Youtube will play in html5
If you need Flash, you can choose Always Active again. 
Just a temporary workaround

---

### Post by Yellow Pasque on 2015-01-11
In one of your previous posts, you refer to installing Lubuntu on a system with an Athlon XP CPU. If that's the system you're talking about here, Flash will not work because the Athlon XP lacks SSE2 support, which Flash requires.

You can try an older version of Flash. Details: [http://ubuntuforums.org/showthread.php?t=2130640&p=12565189#post12565189](http://ubuntuforums.org/showthread.php?t=2130640&p=12565189#post12565189)

---

### Post by bartek6 on 2015-01-15
> **Temüjin said:**
> In one of your previous posts, you refer to installing Lubuntu on a system with an Athlon XP CPU. If that's the system you're talking about here, Flash will not work because the Athlon XP lacks SSE2 support, which Flash requires.

You can try an older version of Flash. Details: [http://ubuntuforums.org/showthread.php?t=2130640&p=12565189#post12565189](http://ubuntuforums.org/showthread.php?t=2130640&p=12565189#post12565189)

Direct hit! It was general problem with flash plug-in. Installing older version of Flash solved problem.

---

