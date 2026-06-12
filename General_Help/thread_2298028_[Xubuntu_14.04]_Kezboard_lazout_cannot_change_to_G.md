---
title: "[Xubuntu 14.04] Kezboard lazout cannot change to German anz more"
date: 2015-10-08
forum: General Help
---

### Post by mario882 on 2015-10-08
Hi,

I have an issue with mz kezboard lazout! I can|t set it to anz other language than English after I installed compiy using these instructions> [http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html](http://www.webupd8.org/2012/11/how-to-set-up-compiz-in-xubuntu-1210-or.html)
All worked fine before I installed compiy, but now I can|t switch to German anz more. Bz @I can|t switch@ I mean that I still can select @German@ in the kezboard settings, but this setting has no effect. Even though I set it to German, the kezboard lazout is still English. I have no Idea how this is related to compiy at all, mazbe compiy or anz of the actions to install and setup compiy has damaged something on mz szstem, or this is just a coincidence.

I also ran
```
sudo dpkg-reconfigure keyboard-configuration
```
and selected German, then rebooted, but still English lazout.

I found lots of users with similar issues on the internet, but all solutions somehow involved IBus, which doesn|t work for me, because [Xubuntu 14.04 doesn|t ship with IBus]("https://wiki.ubuntu.com/TrustyTahr/ReleaseNotes/Xubuntu"). I have no IBus settings in mz control panel, and I can|t select IBus as mz default input method.

So I need another solutions which will also work for Xubuntu 14.04.

Please help. What can I do_

P.S. Some characters are wrong due to mz kezboard lazout>  y and z are interchanged, @ should be quotation marks, > should be a colon, | should be an apostrophe and _ should be a question mark.

---

### Post by tgalati4 on 2015-10-08
Welcome to the forums.  Trz to turn off compiy.  Open a terminal:

```
metacity --replace
```

Then rerun the reconfigure command that zou tried earlier.  Then reboot.

---

### Post by mario882 on 2015-10-08
Back on my Windows machine, now I can type normally. :wink:

Turning compiz off doesn't work. I tried this already. (Besides the fact that I really want to use compiz, because xfwm4 has horrible screen tearing)
There is something damaged on my system.
I don't even know how it was damaged. I only know that I followed the instructions I posted above to install compiz, then some times later I noticed that my keyboard layout was broken and it was not broken before I installed compiz. It could be a coincidence or not, I don't know.

Is there some repair procedure that I can try? I could reinstall Xubuntu, but that is the last thing I want to try.

---

### Post by tgalati4 on 2015-10-08
Open a terminal:

```
gnome-keyboard-properties
```  Look in the "Layouts" tab and post what Layouts you have installed.  Try removing the "English US" keyboard and install something else.  What keyboard hardware do you have listed?  It should be "Generic 105-Key (Intl) PC", unless you changed it something else.

---

### Post by mario882 on 2015-10-08
I found a workaround: Create a startup application with the following command:
```
setxkbmap <your language>
```
This worked for me, but it's just (another) dirty workaround.

EDIT: Sorry, I did't see your secound post.

```
gnome-keyboard-properties
```
Returns commmand not found.

---

### Post by tgalati4 on 2015-10-08
Either install it or find the Xubuntu equivalent to the keyboard properties GUI.

---

### Post by mario882 on 2015-10-08
In Xubuntu, there is a similar properties GUI which looks like this:
[http://i.stack.imgur.com/gedBd.png](http://i.stack.imgur.com/gedBd.png)
(On my system it's German of course, this is just a sample picture)
However, you cannot install or uninstall specific languages. You can only "add" or "remove" them. When I click the "Add" button, a list with all possible languages shows up, which are build into the system.
I have already set this to German and removed all other languages, this doesn't help. "Use system defaults" doesn't work either.
And yes, it is set to "Generic 105-Key (Intl) PC".

Meanwhile I think the main issue is that the keyboard layout settings doesn't survive a reboot.
Because as I told in my initial post, I always performed a reboot after changing any settings. This gave me the impression that the keyboard layout settings doesn't have an effect at all. But actually they have just been reset during reboot.
If I don't do a reboot, then these keyboard layout settings (*sudo dpkg-reconfigure keyboard-configuration* and properties GUI) indeed change my keyboard layout for the current session.
Login / Logout also resets the keyboard layout back to English.

---

### Post by tgalati4 on 2015-10-08
Examine your keyboard settings file:  [http://www.linuxquestions.org/questions/linux-desktop-74/where-is-keyboard-layout-stored-under-xfce-881555/](http://www.linuxquestions.org/questions/linux-desktop-74/where-is-keyboard-layout-stored-under-xfce-881555/)

A bad keyboard (one that disconnects due to cable problems or other issue) can cause your problems:  [https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/944468](https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/944468)

Check /var/log/Xorg.0.log, /var/log/syslog, ~/.xsession-errors for keyboard errors.

---

### Post by mario882 on 2015-10-09
None of these files contained any error messages regarding my keyboard. I have a Logitech K350 OEM keyboard with Unifying wireless receiver. My keyboard-layout.xml looks fine: "[...] <property name="XkbLayout" type="string" value="de"/> [...]" just as expected.

Personally I think it's a bug. If you search the internet for "Ubuntu keyboard layout reboot" you'll find tons of threads or bug reports about the exact same issue that the keyboard layout settings don't survive a reboot.

For now, I will stick with my workaround. Actually I just wanted to use Xubuntu. I didn't expect such a big hassle just to get the very basic functionality right (like tearing free video output, or keyboard layout settings). Ubuntu and especially Xubuntu have a long way to go until it's ready for the general public.

However, if anyone is interested in getting to the bottom of this issue and needs further informations about my system, I will be of assistance.

---

### Post by tgalati4 on 2015-10-09
Change your battery in your keyboard.  Weak batteries can cause keyboard resets, which can also reset the keyboard to English.  Or get a wired keyboard and see if you have the same problem.  If it happens on both a wired and wireless keyboard, then you can be pretty sure it is a bug.

---

