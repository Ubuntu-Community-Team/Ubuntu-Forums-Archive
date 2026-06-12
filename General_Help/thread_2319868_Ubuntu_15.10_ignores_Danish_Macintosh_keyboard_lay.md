---
title: "Ubuntu 15.10 ignores Danish Macintosh keyboard layout completely"
date: 2016-04-08
forum: General Help
---

### Post by DaneGrinder on 2016-04-08
Hi

After loosing 2 full days of work, trying to install Ubuntu, I am just about to give up and go back to my Mac :(

The thing that has been the biggest problem is, that I can\t get my Mac keyboard working probably. I have tried everything I can find online, and nothing works.
The closest I have gotten is making a custom .xmodmap file, and loading it from terminal on every startup. This is of course unacceptable. When I turn on my
computer, I do it to work, not to start getting my computer ready to work :P and yes, I have tried .xinitrc files and scripts and .profile etc, nothing works.

VERY VERY long story short, I now know, that the newer versions of ubuntu uses xkb instead of xmodmap, BUT the system completely ignores any and all changes
in Systems Setting > Text Entry, so there is nothing I can do. I have tried random keyboard layouts, and nothing changes.

Then I tried sudo dpkg-reconfigure keyboard-configuration from terminal, but that also does not change the layout. It does how ever come up with an warning, that
I just gave up on trying to fix, because I am now 2 days behind on my work.

WARNING: Can not find "mac" in "macintosh_vndr/dk".
WARNING: Can not find "mac" in "macintosh_vndr/dk".

Can anybody tell my what is going on here question-mark :D

Side note. How do I become the admin of my machine, so I can actually make changes to files etc. without having to cd, cd, cd, cd, cd, cd, cd, cd, cd until I finally get to
the folder and the sudo gedit filename. Right of the bat, Ubuntu seems a lot more restricted or atleast overly complicated then OSX

Hope someone can help
Henrik

---

### Post by QIII on 2016-04-08
You say you are installing this on a Mac?

---

### Post by DaneGrinder on 2016-04-08
No, I am installing it on a desktop pc. Dual boot with Win 10. Just using a mac keyboard

---

### Post by coffeecat on 2016-04-08
You do seem to be making life difficult for yourself. With many languages, you can choose a Mac keyboard instead of a PC keyboard during installation. That has always worked just fine for me. 

But since you appeared to have missed that step, you can add a Macintosh keyboard layout from the GUI tools. I'll assume you are using standard Ubuntu with the Unity desktop. If you are using another GUI desktop, the details will be different.

Click on the cogwheel icon at top right of screen -> System Settings -> Keyboard. Click on the "Text Entry" link. Click on the + sign. Scroll down to your language and see if there is a Macintosh option. for English, there are several depending on the English variant. Click on your choice and it will be added to the list. You can use the up and down arrows to reorder your list of available keyboards to get your preferred default to the top. You may have to log out and in again to get that setting to take - I can't remember whether you have to, probably not. Or there's an icon near top right of the screen to choose which keyboard layout to make active. 

Having said all that, all the changes you've made to system files may over-ride any GUI setting you make. I really don't know. Moral of the story - see if there is a GUI way of changing configurations before rolling your sleeves up and digging around under the hood. A bit like MacOS really....

**Edit:**

On re-reading your post, I just noticed this:

> BUT the system completely ignores any and all changes
in Systems Setting > Text Entry, so there is nothing I can do. I have tried random keyboard layouts, and nothing changes.

Probably for the reason I've already stated - that your changes in config files are probably interfering. Have you made a note of all your changes? Try to change everything back to the way they were before you started. 

Also - Try running Ubuntu live from a live DVD or USB and add a Mac keybaord layout from the GUI. See if that works as a test. I'm sure it will, because for all the years I used Ubuntu with a Mac keyboard, I never experienced any problem getting it to work.

---

### Post by DaneGrinder on 2016-04-08
I only installed the danish mac keyboard under installation of ubuntu. I actually reinstalled 3 times already, to make sure I was working of a clean installation. Nothing changes.

It doesn\t use the danish mac keyboard. I doesn\t seeem to use any layout I can find. I have looked at maybe 10 different layouts, and none of them has the layout that i am actually using.

My layout now is like this

<1234567890-=
qwertyuiop[]
asdfghjkl;'\
`zxcvbnm,./

It doesnt seem to be any of the mac layouts. Also not English or us layout. I really dont know :confused: If someone recognizes this layout, please tell me which it is. If all fails, I can just reconfigure that one then.

I\m going to try to boot from the usb and see what happens. Maybe that could get us closer to an explanation

---

### Post by coffeecat on 2016-04-08
Curious. Out of interest, I added the UK English Mac keyboard the way I described to this 15.10 Ubuntu installation, and it worked OK after I selected the Mac layout from the icon top right. I haven't got a Mac keyboard available at the moment, but it behaved as though I was using one. That is, " and @ are swapped around for the UK layout, and there are a few other differences.

I'll have to plead ignorance of what happens with the Danish layout - perhaps there's a problem with that one. What I'll do as soon as I've posted is to edit your thread title to include "Danish Macintosh" in it. That might attract someone who knowns what the problem is. Sorry I can't be of more help. Let me know if you want something different for the thread title edit.

---

### Post by coffeecat on 2016-04-08
I don't know whether this is of any use, but if you click on the keyboard icon in the Text Entry window, you get a diagram of the layout for that keyboard type. This is what I get for "Danish (Macintosh)":

[ATTACH=CONFIG]268234[/ATTACH]

That's what you *should* be getting, but seemingly you aren't.

---

### Post by DaneGrinder on 2016-04-08
Dont apologies mate, the mere fact that you are in here trying to help, is all that I can ever hope for :D

That is the layout I should be getting yes. It is not how a danish mac keyboard looks, but if I could get that working, I could reconfigure it, and give it back to the community.
BUT, that is not what Im getting in the installed version of Ubuntu 15.10 on my pc. It is how ever, what I get when I boot from the usb. I still doesnt work, and I still get the same weird layout that I have now, and can not change it to any other layout when booting from the usb either. SOooooooo..... Flabbergasted I am :D

---

### Post by DaneGrinder on 2016-04-08
SO,,,,,, I will reinstall a 4. and last time, before giving up :D

I tried to logout. On the login screen, I then changed the keyboard to Albanian. Just a random layout I have tried before. That resulted in me not being able to put in the correct password, SO, that most mean, that it actually worked, when changed on the login window :)

Then I logged in, and set my account to login without password. Logged of. Changed the language to Albanian again, and logged in. But, low and behold, nothing changed, and I was right back to the same layout as always. A small step in the right direction never the less :D

Now something else came up though. I can now not enable password protection at login again. It goes through the whole procedure, but at the login screen, it does not ask for a password... Getting very very frustrated here. I really thought Linux had come a long way since I last gave up on it 5 years ago, but my experience up to now, unfortunately doesnt support that claim.

I will give it 1 last reinstall. If it doesnt work, I will cry myself to sleep tonight, and give it another 5 years to get over the child diseases.

I was so hoping to move the company over to Linux, so we didnt have to go back and forth between windows, linux and mac and different keyboards all the time :(

---

### Post by DaneGrinder on 2016-04-08
Installed 14.04. Upgraded to 15.10, and now it kind of works :-D

The layout in Ubuntu for the Mac keyboard, is still so far from the actual keyboard, that it is useless, BUT, now it actually changes between the keyboards, so maybe I can now make a new layout, and let that be my first (of hopefully many) contributions to the community...!

---

