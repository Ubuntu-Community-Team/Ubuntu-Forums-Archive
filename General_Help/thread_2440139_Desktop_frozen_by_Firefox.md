---
title: "Desktop frozen by Firefox"
date: 2020-04-06
forum: General Help
---

### Post by bjngchn on 2020-04-06
There may be more than one issues here, like old computer, old kubuntu (14),.. and recently default panel was disappearing, or not  shown correctly when I start the computer and login as a user, and kmix was not working,.. such problems seem to have disappeared maybe after some trial and error (?)

I know you will recommend  that I make a copy of my data, and reinstall new kubuntu: ok, this would be a big job.
This computer is great, although it is 5 years old. I would buy 20 of the the same if I can find, but no,all new laptops are evil. 


Let me get back to the topic. Today  I have a new problem. I start the laptop, I can do everything normally. I connect to internet, and I run FIREFOX, and DESKTOP FREEZES sooner or later, maybe immediately. .. Then either I can't do anything, or only programs I started earlier work normally, all the rest can't be accessed. I can't move cursor over something t do something, unless the cursor is moving over one of programs I started earlier. For example although this chromium works perfectly, I will have to unplug this laptop to  shut down the laptop. I did this 10 times today.

So the problem is with firefox. How can I erase old firefox and reinstall a new version.?.. Something like sudo apt-get .. and then what.. I need a minor surgery, not something big..
 I need a minimal firefox which I would use mostly with JS disabled, but sometimes enable it.... I must say that even when JS is disabled, running firefox kills the desktop. 
Also the laptop gets very hot, and may die if I'm not careful..

---

### Post by owbizi on 2020-04-06
No need to reinstall Firefox in order to reset it: just delete your home profile and start it again, then it should create a new one for you:

> 
rm -r ~/.mozilla/firefox


If you only have Firefox installed from Mozilla, then you can also decide to delete the whole **.mozilla** folder.

---

### Post by sdsurfer on 2020-04-06
You can also check your system or crash logs for entries at the time of the freeze, this may provide insights. For example, my issues with system freezes have mostly been related to graphics drivers.

---

### Post by bjngchn on 2020-04-06
Thanks owbizi [COLOR=#000000] . And  , deleted,  looks like I will have to shut down the computer to see if it works. But desktop is still frozen when  I'm in this session. When I do 
ps ux
I don't see anything which resembles firefox there. I mean almost everything   (I mean everything except previously started programs, like terminal, chromium) has frozen
probably because of firefox, but also it looks like firefox is not running.  it doesn't appear among processes (there are several chromium processes)...
Can there be a solution for current freezing as well, like killing a process?
Are there other directories which  can be  erased without causing any harm ? [/COLOR]

---

### Post by bjngchn on 2020-04-06
Before I restart the computer I typed firefox  in terminal and I got this (sorry can't create screenshots, because panel is not working..)

~$ firefox


(process:5587): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed


(firefox:5587): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::sm-connect after class was initialised


(firefox:5587): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised


(firefox:5587): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::display after class was initialised


(firefox:5587): GLib-GObject-WARNING **: Attempt to add property GnomeProgram::default-icon after class was initialised

---

### Post by owbizi on 2020-04-06
If it opens correctly, then I'd guess you can safely ignore those warning messages.

As suggested by @sdsurfer, Firefox itself might not be the problem; further log inspection might reveal something else, such as a video driver failing.

Log messages are stored in **/var/log/**; if you want further help inspecting those, I'd advise creating a new thread just for it.

---

### Post by CelticWarrior on 2020-04-06
Please please please...

[B]There's no point in troubleshooting a release that is out of support for a year!!!
Please upgrade to a supported release which will also have an up-to-date FIREFOX. 
[/B]

---

### Post by owbizi on 2020-04-06
Yeah, @CelticWarrior is right - I missed you are using an old Kubuntu release. It's been 6 years since that version (14).

It is strongly advised to update to a new version. If you think your machine can't handle it, then I'd suggest trying a different flavour of Ubuntu, such as Xubuntu or Lubuntu.

If you are definitive about using Kubuntu,  you can just install **xubuntu-desktop** or other similar metapackage to try other flavour's desktop later on.

---

