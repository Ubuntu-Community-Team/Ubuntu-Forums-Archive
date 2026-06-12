---
title: "uk keyboard setup"
date: 2007-06-21
forum: General Help
---

### Post by AJB2K3 on 2007-06-21
During set-up i choose uk language with uk keyboard how ever when it logged in im on US ? WTF??
I went into the keyboard setup program and it was set to us not uk  (again WTF?) i tryed setting it to use Uk instead of the xorg setup bet every time i hit close it returns to us !!! 
Can someone help me?

---

### Post by rbmorse on 2007-06-21
How is that racist? 

It's silly. But I don't see where it is racist.

---

### Post by mali2297 on 2007-06-21
What does it say in /etc/X11/xorg.conf? I've got these lines (having a Swedish keyboard):
> 
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "se"
EndSection

If you haven't got "uk" perhaps you should edit the file or reconfigure.

...or are you messing with me? :-? How does the British keyboard layout differ from the American?

---

### Post by pickarooney on 2007-06-21
It should actually be "gb" instead of "uk". Presumably because Xorg is bigoted against Northern Ireland residents :D

---

### Post by akadruid on 2007-06-22
Hi

I have exactly the same problem.

It says gb in xorg.conf

@mali2297 UK keyboards different positions for lots of keys including "@~#|\/ 

akadruid

---

### Post by pickarooney on 2007-06-22
I've never had this problem in Ubuntu or Kubuntu, the keyboard always works as gb.
Is there something overriding the xorg setup?
Do all programs have the £ and @ moved around?

---

### Post by nodcero on 2007-06-22
@mali2297: And an important difference: the highly valued £-Key.
Currently we get basically 2 $-keys for it... ;)

And the setup at installation worked, by the way, like a charm for me and my keyboard. 
An obscure old make, but auto-detect was not fooled...

---

### Post by bapoumba on 2007-06-22
@ everyone: I've edited the thread title and every single post title.
@ OP: that was not a good and funny title...

---

### Post by pickarooney on 2007-06-22
@ bapoumba: ah, the old 'second degré', you guys will never quite get it :D
@ everyone else: are you using pc105 layout or something else?

---

### Post by akadruid on 2007-06-22
> **pickarooney said:**
> I've never had this problem in Ubuntu or Kubuntu, the keyboard always works as gb.
Is there something overriding the xorg setup?
Do all programs have the £ and @ moved around?

I only get it on 1 of my 3 ubuntu machines.
I have no idea if something is overriding the xorg setup - how do I tell?
Yes, the keyboard layout appears wrong in every program.

Also, my ALT-TAB, ALT-F1, ALT-F9 key combinations do not work, even after I change the keyboard back to UK.

@bapoumba, You are right to change the title but... it makes me sick that this thread gets loads of attention, but when I asked the same question yesterday with a sensible title a less 'WTF's in it, nobody even reads my question.... ([http://ubuntuforums.org/showthread.php?t=479729](http://ubuntuforums.org/showthread.php?t=479729))  I guess you have to have a stupid title to get people's attention.

---

### Post by akadruid on 2007-06-22
> **pickarooney said:**
> @ bapoumba: ah, the old 'second degré', you guys will never quite get it :D
@ everyone else: are you using pc105 layout or something else?

yeah using pc105, I have also tried with pc104, same problem

---

### Post by akadruid on 2007-06-22
I'm not at the computer with the problem right now so I can't try it, but maybe this is the answer?

[http://ubuntuforums.org/showpost.php?p=2848336&postcount=10](http://ubuntuforums.org/showpost.php?p=2848336&postcount=10)

If nobody has time to try it before tonight I will try it out when I get home

---

### Post by bapoumba on 2007-06-22
> **pickarooney said:**
> @ bapoumba: ah, the old 'second degré', you guys will never quite get it :D

May be it is also good to consider that it's not a matter of "me" getting "second degré" or not, but how fast that kind of title can stir up things, and that we've got a couple rules worth checking (Forum help link, top menu panel) ;)

> **akadruid said:**
> 
@bapoumba, You are right to change the title but... it makes me sick that this thread gets loads of attention, but when I asked the same question yesterday with a sensible title a less 'WTF's in it, nobody even reads my question.... ([http://ubuntuforums.org/showthread.php?t=479729](http://ubuntuforums.org/showthread.php?t=479729))  I guess you have to have a stupid title to get people's attention.
I understand that, and feel sorry about it.
I do not have time to check for bugs right now. Please do so (I'll come back later) and filling a bug reports sounds a good idea to me if there is no related bug around.

---

### Post by bapoumba on 2007-06-22
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/96020](https://bugs.launchpad.net/ubuntu/+bug/96020) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please have a look at this bug, and may be comment in it.
The report states there is one duplicate, but does not seem I can find it...

Edit: I copied this post here, as I answered by mistake in the other thread. Sorry.

---

### Post by akadruid on 2007-06-22
Could be related, but the workaround in the bug (removing other layouts) didn't work for me.  Even with gb as the only keyboard option, the keys are US layout when I log in.

The keyboard indicator applet in my toolbar shows gb, but it is lying.  Also 'Show Current Layout' shows the correct UK layout, not the one that is actually in place.

The other suggestion I linked to earlier (reinstalling xkb-data) did not work either

---

### Post by bapoumba on 2007-06-23
Ok, so I would suggest now that you open a bug report, as several of you have the same problem, state that the fixes you found did not work and may be link to this thread as well.

Please liink here to the bug you open so that I can subscribe to it. Thanks.

---

### Post by akadruid on 2007-10-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/gnome-control-center/+bug/103111](https://bugs.launchpad.net/gnome-control-center/+bug/103111) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It's probably a duplicate of one or both of the following:

I see this message: Unable to start the settings manager 'gnome-settings-daemon'
[https://bugs.launchpad.net/gnome-control-center/+bug/103111](https://bugs.launchpad.net/gnome-control-center/+bug/103111)

I have also done something like dpkg-reconfigure xserver-xorg while trying to get my ATI card to work.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/46046](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/46046)

I am now resigned to using US keyboard layout, or deleting and readding my uk layout after every reboot

---

