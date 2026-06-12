---
title: "How to Cut Down Sensitivity of the Laptop Track Pad"
date: 2008-05-13
forum: General Help
---

### Post by one4house on 2008-05-13
How do you adjust the Sensitivity? Every time I have the slightest touch on the pad my cursor or window of operation changes. Annoying as duck.

---

### Post by ctsdownloads on 2008-05-13
> **one4house said:**
> How do you adjust the Sensitivity? Every time I have the slightest touch on the pad my cursor or window of operation changes. Annoying as duck.

Yeah, it can be annoying. Try this: Goto System, Preferences, Mouse. Slide the sensitivity to low as it will go.

---

### Post by strabes on 2008-05-13
You can do this manually by editing xorg.conf:```
gksudo gedit /etc/X11/xorg.conf
```

Find the section that looks like this:> Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
EndSection

Add the following options before EndSection:> 
	Option		"MinSpeed"	".1"
	Option		"MaxSpeed"	".3"
	Option		"AccelFactor"	".0017"

Save the file and restart your x server using ctrl+alt+backspace. Tweak the settings as you see fit. In the future please search the internet for simple questions like these before posting on these forums.

---

### Post by one4house on 2008-05-14
Thank you for your help.  Sorry that you feel that I am a dumb *** for asking such a simple question.  I bow to your expert knowledge.  In three post of varying difficulty, I have been told how to manage my post.  Is this how the Linux forums greet those that try and make the move to a better product?   Seems somewhat counter-productive to me.  Oh well.

Thanks for the help.

---

### Post by one4house on 2008-05-14
P.S. [http://ubuntuforums.org/showthread.php?p=4951957#post4951957](http://ubuntuforums.org/showthread.php?p=4951957#post4951957)

---

### Post by p_quarles on 2008-05-14
> **one4house said:**
> Thank you for your help.  Sorry that you feel that I am a dumb *** for asking such a simple question.  I bow to your expert knowledge.  In three post of varying difficulty, I have been told how to manage my post.  Is this how the Linux forums greet those that try and make the move to a better product?   Seems somewhat counter-productive to me.  Oh well.

Thanks for the help.
Err, what? No one said anything the least bit rude to you. If you didn't understand the advice, feel free to ask for clarification, but please don't attack those who are trying to help you.

---

### Post by one4house on 2008-05-14
> **strabes said:**
>  In the future please search the internet for simple questions like these before posting on these forums.

I beg to differ.

---

