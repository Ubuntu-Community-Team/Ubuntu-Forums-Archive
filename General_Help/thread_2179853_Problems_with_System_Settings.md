---
title: "Problems with System Settings"
date: 2013-10-10
forum: General Help
---

### Post by James Wilde on 2013-10-10
I originally posted this in Desktop Environments, since it was the background I wanted to change, but I realise it is a problem with System Settings so I'm reposting it here, where I'm more likely to get a reply.

I'm running 13-04 64 bit on a HP 4540s.  Immediately after installation I  installed gnome-classic-fallback as I think Unity sucks - although I'm  beginning to get used to it.

Since Unity looks a bit like the Mac Dock, I decided to see whether  there had been any rethinking on the question of being able to relocate  it to the bottom of the screen.  It was then that I found references to  cairo-dock and loaded that.  However, before I installed cairo-dock, I  was having the following problem, which is still there under cairo-dock.

I have had a problem with the sensitivity of the touchpad, went into  System Settings and Mouse and Touchpad and adjusted the speed of the  Touchpad.  There was no save button, so I assumed it's the same as the  Mac - change and exit and it is automatically saved, but no.  Another  issue I have had is the background picture.  I wanted to change the  standard background picture, so I went into System Settings and  Background.  I found a picture of the one I had but no way to scroll  through a bunch of alternatives, although I know they must be there  somewhere, and no way to select and save one if I had been able to see  them.

Now I'm coming to the conclusion that something is broken in my installation.  Can anyone suggest a course of action?

Later:  I just decided to try reverting to Ubuntu Unity environment.  I  went into system settings and Background and found about a dozen  pictures but no buttons to select and save.  One selected with the  mouse.  However, when I exited, the new choice was maintained.  I went  into Mouse and Touchpad - no save button, and changing and exiting did  not change anything.  When I went back in, touchpad sensitivity was back  to default.

Thanks in advance.

---

### Post by ian-weisser on 2013-10-10
I don't understand the problem.
Are you seeking help with the background picture?
Or are you seeking help with the touchpad sensitivity?

---

### Post by heir4c on 2013-10-10
For your background. Choose a background you want and set the background file in your user folder (not in Documents or pictures or...) Go than to the background settings in Systemsettings and click on the + button that you see under the backgroundpictures. That opens nautilus en than you go to your user folder, select the background and click in the bottom on "Open".

---

### Post by James Wilde on 2013-10-10
I have problems with both, Ian.  If I keep my cairo-dock, I can only see the current background, and can't change it.  If I revert to Unity I can.

And I can't get touchpad sensitivity to stay where I put it, neither in Unity nor in cairo-dock.  Since I can't do it in either place, this is the more serious problem.

---

### Post by James Wilde on 2013-10-10
I'm not sure you understood my problem, Heir4c.  My problem is that, in my gui of choice I can't see the alternative backgrounds at all, and no buttons at all to do things, like changing, paging, selecting or anything else.

---

### Post by mc4man on 2013-10-10
> **James Wilde said:**
> I have problems with both, Ian.  If I keep my cairo-dock, I can only see the current background, and can't change it.  If I revert to Unity I can.

And I can't get touchpad sensitivity to stay where I put it, neither in Unity nor in cairo-dock.  Since I can't do it in either place, this is the more serious problem.

In 13.04 those settings always are shown at default when the panel in system settings in opened.
The real question is whether when you changed them was the change noticeable & if so, **when do they go away**, if they  do.

You can check to see if  the values were changed in dconf-editor > org > gnome > settings-daemon >peripherals > touchpad and or mouse

At least here in 13.04 the changes were reflected in dconf & remain in effect irregardless of what system settings > .. shows **when re-opening**

note that in 13.10 the system settings panel always shows what you set at when re-opening the panel.

---

### Post by heir4c on 2013-10-10
> **James Wilde said:**
> I'm not sure you understood my problem, Heir4c.  My problem is that, in my gui of choice I can't see the alternative backgrounds at all, and no buttons at all to do things, like changing, paging, selecting or anything else.

Ok, so you mean there is something wrong with the program because you can't switch to another background not even the standard in the list?
You're sure you use Ubuntu and not Xubuntu or Lubuntu? Because I think that is in one of the two like you describes. If not than there is something wrong.

---

### Post by James Wilde on 2013-10-10
That fixed the touchpad speed problem, Mc4man.  Thanks.

---

### Post by James Wilde on 2013-10-10
Thanks, Heir4c.  I'm beginning to think there is something wrong, too.  I actually re-installed from a new download once because things didn't seem to be working as they should.  For example the page keeps scrolling down without my intending to.  I don't know whether this is because I rest my wrists on the computer beside the touchpad och what but it's very annoying.

One of my problems is solved, as you see above.  Maybe I should update to 13-10 before I get too involved in Ubuntu.

---

### Post by heir4c on 2013-10-11
13.10 is newer but therefore not stable. 
Use 12.04 instead. That is the LTS and have 5 years support. The versions between the LTS have only 9 months I believe.

---

