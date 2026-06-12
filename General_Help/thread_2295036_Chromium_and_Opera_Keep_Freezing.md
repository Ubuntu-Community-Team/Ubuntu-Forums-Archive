---
title: "Chromium and Opera Keep Freezing"
date: 2015-09-15
forum: General Help
---

### Post by LaughingHorse on 2015-09-15
I'm Using 14.04 LTS

This is a really weird problem.
I use Firefox for most of my browsing. It works fine.

Opera was working perfectly as was Chromium, except somehow from time to time pages would auto refresh to some ad site. ONLY happened using Opera and or Chromium.

For Opera I:

[LIST=1]
[*]Did a complete uninstall 
[*]After the uninstall (using synaptic) I rebooted my computer. 
[*]I did a new install 
[/LIST]

From that point on, every time I opened a new window my entire computer would freeze. The mouse will still work, but the screen and keyboard freezes. I have to turn off power and then reboot.

I installed Chromium using snyaptic.
From time to time I would get auto refreshes to an ad site.

So I:

Used the feature in Settings "Reset settings"
Now I can open a window, using the [ctrl] +T and the screen freezes.

With either Chromium or Opera, the desktop and keyboard freezes. The mouse does not.
[ctrl]=w does nothing. It should close the window.
Soft reboot [ctrl]+[alt]+[del] does NOT work.

The only thing I can do is to turn off the power and then restart everything.

This does NOT happen with Firefox.
Any idea on how to fix this?

Thanks in Advance For Your Helpful Advice.

---

### Post by monkeybrain20122 on 2015-09-15
Something hijacked your browser apparently. Uninstalling and reinstalling doesn't change your user profie, that won't do you any good. Instead you have to nuke the corrupt profiles. 

Closer browsers affected. Open your file manager to your home. Press ctrl+h or choose show hidden files from menu, locate the hidden directory .config (note the "." in front) open it, find the opera and chromium subfolders (I think it may be called google-chromium? I have no chromium so not sure), delete them. Now check by opening your browser and see if problem persists.

---

### Post by LaughingHorse on 2015-09-15
Monkeybrain20122 - Thank You!
It took a while to find the config files.
I had a look in the post
http://ubuntuforums.org/showthread.php?t=1362647</a>
 to find them. 

After deleting the entire folders, everything works perfectly... for now :)

Thank You!

---

