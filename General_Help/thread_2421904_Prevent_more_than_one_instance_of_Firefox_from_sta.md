---
title: "Prevent more than one instance of Firefox from starting"
date: 2019-06-28
forum: General Help
---

### Post by raleigh3 on 2019-06-28
I want to to be able to prevent Firefox from starting if one instance is already running.

And give a message that it is already running.

I could probably use gxmessage for the message part if the solution involves a bash script.

Thanks for your help and consideration.

---

### Post by Impavidus on 2019-06-29
Firefox already prevents two instances from running simultaneously. The second instance you start detects the presence of the first, tells the first about it and terminates. The first instance then opens a new window.

But if you wish, you could write a wrapper script that uses ps to check for another Firefox instance by the same user and gives a message if there is one, else starts Firefox. That won't stop you from starting Firefox directly, without the wrapper script.

---

### Post by TheFu on 2019-06-29
The only way that multiple firefox instances would start is if they are running in different containers or sandbox namespaces.

Don't flatpaks and snaps use container namespaces, don't they?

I'm having a similar issue and don't have a good solution.  I run firefox in a firejail sandbox by default. Clicking on a URL inside a thunderbird instance, also running in a separate firejail sandbox always opens a new firefox instance.  If additional URLs are clicked from inside thunderbird, then the existing firefox running inside the same sandbox is used.   The flaw with this is that both high-risk programs are running inside the same sandbox. That is undesirable to me.

---

### Post by raleigh3 on 2019-06-29
> **Impavidus said:**
> Firefox already prevents two instances from running simultaneously. The second instance you start detects the presence of the first, tells the first about it and terminates. The first instance then opens a new window.

But if you wish, you could write a wrapper script that uses ps to check for another Firefox instance by the same user and gives a message if there is one, else starts Firefox. That won't stop you from starting Firefox directly, without the wrapper script.

[https://imgur.com/a/q7rTnzj](https://imgur.com/a/q7rTnzj)

---

### Post by CatKiller on 2019-06-29
That shows two windows. It doesn't show two instances.

---

### Post by raleigh3 on 2019-06-29
> **CatKiller said:**
> That shows two windows. It doesn't show two instances.

Ok, then how do I stop more than one instance?

---

### Post by yetimon_64 on 2019-06-30
> **raleigh3 said:**
> Ok, then how do I stop more than one instance?
I don't know if it is possible to stop that behaviour with firefox opening multiple windows; as  Impavidus explains in post #2 you don't have 2 instances with 2 windows open. See [[COLOR=#0000ff]--this screenshot--[/COLOR]]("https://drive.google.com/open?id=19KUlt9aluoJIxIc16GUE_j3ie4x85-pW") for 3 windows open but the terminal shows only 1 instance of firefox running.

There is however a [[COLOR=#0000ff]--firefox extension--[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/merge-window/?src=search") available for very easy merging of multiple windows with just 2 clicks that you may find useful. One right click to open a context menu then one left click to select the "Merge all windows" option.  

**Edit:** If the "merge all windows" option merges too much into one window it is also possible to manually merge/move tabs between windows by [s]holding down the shift key then[/s] clicking and dragging a tab between windows. **Edit 2** You may not even need to hold down the shift key, seems I can just drag and drop tabs between windows here.

Regards, yeti.

---

### Post by #&amp;thj^% on 2019-06-30
If I understand correctly
You can disable multi-process tabs in Firefox by setting
the related prefs to false on the **"about:config "**page. 
[list]
[*]browser.tabs.remote.autostart = false 
[*]browser.tabs.remote.autostart.2 = false 
[/list]
See if that helps.
```
**_wmctrl -lx_**
0x02e00006  0 mate-terminal.Mate-terminal  arch Terminal
0x00e00003 -1 mate-panel.Mate-panel  arch Top Panel
0x01200006  0 desktop_window.Caja   arch x-caja-desktop
0x02400003  0 plank.Plank           arch plank
0x03a00002 -1 conky.conky           arch conky (arch)
0x03c00001 -1 conky.conky           arch conky (arch)
0x03e00002 -1 conky.conky           arch conky (arch)
0x01204d61  0 caja.Caja             arch Downloads
0x03800003  0 Navigator.Firefox     arch firefox - How to avoid opening a second instance? - Ask Ubuntu - Mozilla Firefox
0x044000fc  0 pluma.Pluma           arch *Unsaved Document 1 - Pluma
0x02e000d6  0 mate-terminal.Mate-terminal  arch Terminal
0x04a00009  0 pamac-manager.Pamac-manager  arch Search

```

---

### Post by raleigh3 on 2019-06-30
Thanks yeti. I will look at it.

---

