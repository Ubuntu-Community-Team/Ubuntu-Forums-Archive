---
title: "Default to Open New Windows in Workspace Windows"
date: 2017-04-14
forum: General Help
---

### Post by littlebobbytables2 on 2017-04-14
Hello,

So I recently started using workspaces in Ubuntu and I really like it, but it has one kind of annoying thing. If I'm in a workspace with no windows, either opened or minimized, and I click a program in my launcher that has an instance open in another workspace it just goes to that workspace. Is there I way I can make it so that it will default to opening a new window in the current workspace, rather than switching me to the workspace with the instance already open? I tried to find info on this and came up with absolutely nothing. 

Any help would be very appreciated!

---

### Post by TheFu on 2017-04-14
Do you mean workspaces?  I'm confused.

---

### Post by littlebobbytables2 on 2017-04-17
I do. Terribly sorry, I typed the wrong word there. I'll edit it to make the correction.

---

### Post by mc4man on 2017-04-17
The behavior is the way it's designed, likely no easy way to change.
In many cases if you right click on an app icon in the launcher, (quicklists),  there will be a new instance option. If not and the app allows multiple instances & has a new instance command available then a quicklist option for that  can be added.

---

### Post by deadflowr on 2017-04-17
middle clicks should open new instances.

---

### Post by TheFu on 2017-04-17
I think the Window Manager controls which workspaces get used for what.  I know in the old days, it was possible to force a program title to be used to determine which workspace it should be placed. Don't know anything about Unity and haven't checked the [openbox]("http://openbox.org/wiki/Help:Configuration#Placement") methods to control it.  I recall that FVWM could control it. [http://fvwm.org/documentation/faq/#miscellaneous](http://fvwm.org/documentation/faq/#miscellaneous)   I have no idea which window manager Unity uses or whether it overrides the WM control or not.

As for which programs launch new instances or always revert back to the main instance, I've seen this issue mainly with browsers which will use any existing already opened version - even if it is running on a different physical machine, but just being displayed locally. I have looked up the firefox open which will force a new instance regardless, so that did exist a few months ago. Don't remember it today.  Most programs that I've run do not prevent a new instance from running, so if you are seeing that, it is probably Unity doing it as a feature.  Try middle-click or right-click and shift/alt/cntl-click versions.  When Unity first came out they had plenty of tutorials and youtube videos which showed all the mouse and keyboard shortcuts. Might be worth looking them up and going through a few of them.

---

### Post by littlebobbytables2 on 2017-04-18
Okay. Thank you all very much! I'll play around with keyboard/mouse shortcuts!

---

