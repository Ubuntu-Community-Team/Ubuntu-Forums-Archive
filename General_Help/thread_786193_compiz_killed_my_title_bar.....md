---
title: "compiz killed my title bar...."
date: 2008-05-07
forum: General Help
---

### Post by illbashu on 2008-05-07
every time i turn on custom (to use compiz manager) my title bar dies :/ 

btw i has emerald installed and it died after i upgraded and i was stuck with one title bar and after i turned on custom compiz that one title bar died :(

even pre instlled compiz (like normal and advance) kill my title bar.

---

### Post by ivansf92 on 2008-05-07
After Compiz Fusion is running, does pressing alt+f2 and entering the command "emerald --replace" do anything?

---

### Post by Lord Xeb on 2008-05-07
Try a complete removal of the two and reinstall compiz only. I have had problems with emerald before and thats what I did and it solve some problems with compiz (my title bars were gone or invisable).

---

### Post by illbashu on 2008-05-07
> **ivansf92 said:**
> After Compiz Fusion is running, does pressing alt+f2 and entering the command "emerald --replace" do anything?

THANK U! it worked :)

do you guys know how i can fix my minimizing animation, it doesn't work...

---

### Post by ivansf92 on 2008-05-08
Hmm, I had the same problem while using Ubuntu 8.04 beta... Unfortunately, I re-installed the whole OS when the stable version came out and I forgot how I fixed it.

But...

It had something to do with the animation and minimize effect plugins in Compiz Fusion. If you do not already have ccsm, install it with the following command in the terminal "sudo apt-get install compizconfig-settings-manager"

Then go to the effects section and mess around with the animation and minimize effect plugins is all I can say, since I can't reproduce the problem. However, I think I fixed it by disabling (un-checking) the animations plugin and checking the minimize effect plugin. (Although, this makes it so that there are less animation, although I didn't really need the others since the minimize and maximize effects (along with the wobbly windows) were the only ones I wanted.)

---

### Post by ivansf92 on 2008-05-08
O.O.. I think I found the solution in this thread which is titled *Animation plugin in compiz not working* [HTML]http://ubuntuforums.org/showthread.php?t=701193[/HTML]

> ...and i solved it (for my part at least)
system>preferences>advanced desktop effects settings>animations>minimize animation>
click on the top entry in that white box (default is zoom) and click edit. make the minimize effect "beam up," click ok, and then click back. minimize a window, and then bring it back up again. you should have this shiny sweet animation. you can choose random or any other effect and also mess with the duration. hope this works for you

---

### Post by sstusick on 2008-05-08
I don't know why Ubuntu doesn't include the compizconfig-settings-manager by default.

---

