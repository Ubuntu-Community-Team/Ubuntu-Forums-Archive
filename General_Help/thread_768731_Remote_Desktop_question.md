---
title: "Remote Desktop question"
date: 2008-04-26
forum: General Help
---

### Post by PreemPalver on 2008-04-26
Hi, I am an old Windows user and I have just installed Ubuntu 8.04 with no problems. Normally, I connect to my office using RDP client in Windows. With Ubuntu, I found the rdesktop client which works fine, however when I use full screen mode, I cannot switch to my Ubuntu desktop. Windows RDP client have an useful top bar which can be used to minimize the TS session and use your local desktop. Is there any way I can have an Ubuntu RDP client with the top bar functionality? 

Thanks in advance

Xavier

---

### Post by ryanhaigh on 2008-04-27
You are suposed to be able to do this by pressing ctrl+alt+enter although I recently read that others were having issues with this not working properly. Just so you are aware the terminal server client in applications>internet provides a GUI means of establishing rdesktop sessions.

---

### Post by gcastell on 2008-04-28
I use terminal server client all the time but ryanhaigh is rights, currently ctrl+alt+enter doesn't work :(

---

### Post by gcastell on 2008-04-28
After some research and some trying I found a way to make it work, even though it is not perfect,to me is good enough, you just need to set a specific screen size, once connect you can alternate between the screen size and full size using ctrl+alt+enter.

---

### Post by sh4d0w808 on 2008-04-28
Hello guys, I have a little bit advanced question, related to rdesktop.

I am using this to connect to a windows terminal server; when i start rdesktop from a terminal with -g option, no problem, the remote screen come up in an awaited size. I have created a launcher for this, but then the window is so little and cannot change the size of it. Do U have any idea, how to solve this problem?

Thanks in advance.

---

### Post by gcastell on 2008-04-28
Ok, I found the answer here:

[http://ubuntuforums.org/showthread.php?t=595384](http://ubuntuforums.org/showthread.php?t=595384)

there is an easier way without installing any software but you lose the prettiness of compiz, just go to system -> preferences -> appereance and select "None"

---

