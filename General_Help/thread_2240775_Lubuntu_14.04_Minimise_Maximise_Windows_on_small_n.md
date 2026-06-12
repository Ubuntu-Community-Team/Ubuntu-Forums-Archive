---
title: "Lubuntu 14.04 Minimise Maximise Windows on small netbook"
date: 2014-08-22
forum: General Help
---

### Post by JLUbunt on 2014-08-22
Hello
I'm new to Lubuntu and like using it. It is installed on a 10 inch screen netbook. I have encountered a couple of problems:
1. A strange problem when I minimise a window it minimises as expected. Unfortunately when it disappears I can't find it at all to get it back to use.  
2. Sometimes when I looking at a webpage that requires me to click on a response at the bottom of the page when the document is long and extends beyone the bottom of the screen ther does not seem to be a way to scroll down to it. I tried resize but still could not get down far enough.

I'm sure the solutions are simple and looked for a guide to using it but have nto found one. Can someone point me in the direction on how to reopen a window that has been minimised, or generally on using the LXDE system.

Thanks

---

### Post by ajgreeny on 2014-08-22
Do you have a panel or taskbar at the bottom of the screen?  If you do, there should be buttons showing with application names showing for each minimised application.

If they do not show you may need to right click in the panel and choose to add "Window buttons".

My naming may be slightly wrong, but I hope you have the general idea.  If there is no panel showing you will need to add one, and not being on Lubuntu or lxde at the moment I can not remember how.

It is also possible that you are not running at the correct resolution for your screen therefore the panel is below the visible screen area.  You can see what the resolution is from Preferences ->Monitor (or display, I can't remember).

---

### Post by vasa1 on 2014-08-22
> **JLUbunt said:**
> ...
1. A strange problem when I minimise a window it minimises as expected. Unfortunately when it disappears I can't find it at all to get it back to use.  ...

Under normal circumstances, you should be able to see the icon in your panel and single-click on it. But since that isn't happening, what happens if you press and hold **Alt+tab**? Do you see an icon relating to the application window you minimized? If you do see it, among others, pressing [tab] repeatedly (while keeping the Alt key pressed) till you highlight the window and then releasing both Alt and Tab should restore that window for you.

---

### Post by vasa1 on 2014-08-22
> **ajgreeny said:**
> Do you have a panel or taskbar at the bottom of the screen?  If you do, there should be buttons showing with application names showing for each minimised application.

If they do not show you may need to right click in the panel and choose to add "Window buttons".
...
It's probably the task bar (window list) in the image below:

---

### Post by ibjsb4 on 2014-08-22
> 1. A strange problem when I minimise a window it minimises as expected.  Unfortunately when it disappears I can't find it at all to get it back  to use.  

I don't know if this is your problem, but I have encountered this on fresh installs before the installed has been updated.  Have you updated yours?

> 2. Sometimes when I looking at a webpage that requires me to click on a  response at the bottom of the page when the document is long and extends  beyone the bottom of the screen ther does not seem to be a way to  scroll down to it. I tried resize but still could not get down far  enough.

This does sound like the wrong resolution.  Try pressing Alt + left click (not on the title bar) and try to drag the screen up.

---

### Post by JLUbunt on 2014-08-22
Hi All
Problem solved on the finding minimised windows. Alt +Tab brings it and I've added the window list so everythin now shows. It seemed obvious but I could not get my head around finding the minimise windows.  
Thanks all.
Jeff

---

### Post by vasa1 on 2014-08-22
> **JLUbunt said:**
> ...  
2. Sometimes when I looking at a webpage that requires me to click on a response at the bottom of the page when the document is long and extends beyone the bottom of the screen ther does not seem to be a way to scroll down to it. I tried resize but still could not get down far enough.
...
Can you provide more details, a screenshot perhaps?

---

### Post by JLUbunt on 2014-08-22
Hi vasa1 The monitor resolution is 1024x600 which was detected by the system. It happened a few days ago I'llbe honest I can't remember the screen the document. I'll find it an screen dump it or let you know I've realised what I was doing wrong.  anks 

I've not been using Lubuntu for long do you know of a list of shortcuts/menu commands I could copy and lamintate so I can find my way around?

Thanks Jeff

---

### Post by vasa1 on 2014-08-22
> **JLUbunt said:**
> ...
I've not been using Lubuntu for long do you know of a list of shortcuts/menu commands I could copy and lamintate so I can find my way around?
...
There could be a difference between menu commands and shortcuts: menu commands for applications are mostly set by the applications themselves whereas you can create shortcuts you need for many things.

I think you'll find the links below quite helpful. If you do have questions after that please ask but preferably one issue per question as that will be more convenient for others:

pclosmag.com/html/Issues/201009/page02.html ::: LXDE: An Overview
pclosmag.com/html/Issues/201010/page07.html ::: LXDE: Configuring LXPanel
pclosmag.com/html/Issues/201011/page09.html ::: LXDE: Meet The Heart & Soul — lxde-rc.xml
pclosmag.com/html/Issues/201107/page08.html ::: Openbox - Edit rc.xml to Gain Control

There also are a few wiki articles here @ [https://help.ubuntu.com/community/Lubuntu](https://help.ubuntu.com/community/Lubuntu) offering suggestions on various aspects of Lubuntu.

---

