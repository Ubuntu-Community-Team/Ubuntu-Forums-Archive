---
title: "Autohinting on fonts"
date: 2005-10-14
forum: General Help
---

### Post by Schmoove on 2005-10-14
How can i get autohinting on fonts back. 
I had it in both Warthy and Hoary, but now in Breezy my fonts look a bit disappointing.
I tried various things (.font.conf file in home dir, edit local.conf in /etc/fonts and reconfiguring fontconfig), but none of the attempts made my fonts look any better.

Anyone knows how to accomplish this?

---

### Post by vayu on 2005-10-14
Both those two ways work for me.  Maybe you should post your entries of those files?

Also you might want to play with your settings in system/preferences/font.

---

### Post by Schmoove on 2005-10-15
My .fonts.conf looks like this:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <match target="font">
    <edit name="autohint" mode="assign">
      <bool>true</bool>
    </edit>
  </match>
</fontconfig>
```

---

### Post by vayu on 2005-10-15
That looks like right.  

To test if your file is being read, why don't you try commenting that out and use antialiasing. See if that makes a difference.   Here is the code to do that, I usually just log out and ctrl-alt-backspace to restart X and that makes changes to .fonts.conf take effect.

```
<match target="font">
 <edit name="antialias" mode="assign" >
  <bool>true</bool>
 </edit>
</match>

```

For me autohint doesn't look that good.  I've been planning on posting a thread to ask what is the difference between hinting, autohint and antialias and how do they relate to cleartype.

I found on my system (with an LCD flat panel display) that antialias looks the best.  I've tried having hinting set to different values, I've had antialias set to work on bold and above certain sizes and all kinds of combinations of the different options. So far just straight antialiasing on all font sizes seems to look the best for me.  It's still not quite right for all fonts but most of the times it looks as good as on Windows.

If you want to try some code for setting properties like hinting, antialias, etc.. conditionally for different font sizes or attributes there's a howto that describes it. Search for "cleartype".

---

### Post by Schmoove on 2005-10-15
I used the cleartype HOWTO and now my fonts look a whole lot better. Thanks for the pointer!

---

