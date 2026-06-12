---
title: "Text on LCD is hard to see"
date: 2008-02-12
forum: General Help
---

### Post by malfist on 2008-02-12
I've been having some problems with the text on my LCD with ubuntu. Subpixel smoothing is on and full hinting is too. I'm attatching some screen shots. The last one is particualy bad. The compression seems to have hidden the second one but the first one is still kinda bad.

---

### Post by camini on 2008-02-12
Making the system and application fonts look perfect for you is possible but takes a little time.
I had to do mutliple tryouts and download stuff like mstcorefonts, apple-like fonts and the such to actually be satisfied.
Blender does use his own fonts I think (not sure) so no luck there.

---

### Post by malfist on 2008-02-12
it wasn't always like this though. It happened one day after wine was running an app and it locked the X server and I restarted it and everything was like this. A temp fix for the command line was to make everything bold, but other apps that use the terminal like update manager and what-not ignores them.

---

### Post by apetresc on 2008-02-12
Are you sure it's not your monitor trying to adjust to a non-native resolution? Because those screenshots look *perfect* on my monitor, implying that the video driver outputs the right image, but the monitor doesn't display it properly.

You're also not the first person to complain about what appears to be flawless screenshots... either there's widespread problems with LCD monitors or I'm blind :|

---

### Post by Therion on 2008-02-12
Start by installing the MS Core Fonts package:
```
$sudo apt-get install msttcorefonts
```
Then regenerate the fonts cache:
```
$sudo fc-cache -fv
```
See if that helps.  Also, adjusting the DPI might help, as does choosing the "correct" font.  The heavier sans-serif fonts (e.g. Undotum, Verdana, Trebuchet) tend to display better in my opinion but your opinion/mileage may vary.

---

### Post by malfist on 2008-02-12
I've messed with the fonts but some apps always ignore the changes. Here's a full screen capture. (I installed msttcorefonts but that didn't seem to help).

Look at the tabs, see the extra color around them. That makes it really hard to read.

---

### Post by apetresc on 2008-02-12
Go to a friend's house and look at that screenshot on their monitor.

I cannot for the life of me figure out how the fonts are in any way distorted. I'm not being a snob or anything, they just actually look perfectly clear, etc. I think it's your monitor, not your fonts; go to some other monitor and look at your screenshot. Does it still look wrong? If so, where?

---

### Post by Therion on 2008-02-12
> **AdrianP said:**
> 

I cannot for the life of me figure out how the fonts are in any way distorted.
I would have to agree.  I scrutinized that screenshot as best I could, and while I would have chosen different fonts than you have, the fonts you are using look quite good to me.  I'm sorry but I'm not seeing the problem here either.

---

### Post by cdtech on 2008-02-12
Looks good to me.

---

### Post by malfist on 2008-02-12
It looks perfectly fine on a differenet monitor and computer :( (the screenshots that is). Maybe change resolution?

---

### Post by Therion on 2008-02-12
In my experience, it seems to be a matter of "a little of this, a little of that"; font selection, font-size, DPI, screen resolution... I had to tinker with them all till I found the right combination.  I don't think there is one answer that works for everyone.

---

### Post by apetresc on 2008-02-12
> **malfist said:**
> It looks perfectly fine on a differenet monitor and computer :( (the screenshots that is). Maybe change resolution?

Try to change Ubuntu's resolution to whatever your monitor's native resolution is. Then the monitor won't have to do any scaling, which means it won't do any interpolation, which means everything will look normal.

Also, your monitor may have an "Auto-Adjust" button that controls things like dimensions,stretch,etc. Try using that.

---

### Post by malfist on 2008-02-12
it does have the auto button, I normally have it set one size higher than it's normal resolution.

---

### Post by apetresc on 2008-02-12
> **malfist said:**
> it does have the auto button, I normally have it set one size higher than it's normal resolution.
Does the problem still occur if you set it down to its 'normal' (I assume you mean native) resolution?

---

### Post by malfist on 2008-02-12
I don't know, I'm at work right now. I assume it won't but it's a small monitor and I need the larger screen (but can't buy a larger monitor because it won't fit into my desk). It's either a 15 or 17 inch screen. Samsung SyncMaster 713.

---

### Post by malfist on 2008-02-12
w00t! Fixed, I had resolution set to 1280x960 and native is 1280x1024!

---

### Post by apetresc on 2008-02-12
Great, glad to hear it :)

This is the second thread *today* to have this exact same problem. It should be added to some FAQ somewhere...

---

### Post by malfist on 2008-02-12
Still had slight discoloration of console, turned off subpixel shading and that fixed it.

---

