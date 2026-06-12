---
title: "Ubuntu 12.04 - Close, Minimize, Maximize Buttons on Windows"
date: 2013-10-26
forum: General Help
---

### Post by Vannyi on 2013-10-26
In 12.04, LTS, the close, minimize, maximize buttons in the browser are in the top left corner.

Coming from Windows, I'm used to going up in the top right corner of a window to access these buttons.  Is there any way to change their position from the top left corner to the top right corner?

Thank you

---

### Post by fantab on 2013-10-26
NO and Yes.

When you maximize the windows, do you see window-control buttons on the left-corner in the top-bar? Well, you can't change those.

However you can change them on non-maximized windows. But that will break the consistency. Keep using ubuntu and you will get 'used' to it, just like you got 'used' to right-corner window-controls in Windows.

If you want to change then install 'dconf-editor'
sudo apt-get install dconf-editor

Open d-conf-editor:
Navigate yourself to: org-> gnome-> desktop-> wm-> preferences-> button-layout
change the settings to: ":minimize,maximize,close" (Without quotes).

The placement of colon decides where your buttons will be. if the colon is at the beginning of the line then the buttons will be on Right, if the colon is at the end then the buttons will be on the left.

EDIT: I don't have 12.04 at the moment to check if my above tweak is relavant. Someone with 12.04 can confirm this.

---

### Post by 3rdalbum on 2013-10-27
Yes, but only for non-maximised windows, which makes it rather pointless. (it's an old holdover from earlier versions of Ubuntu.

You'll adapt in a couple of days, don't worry. And then you'll find you always go to the correct corner no matter which OS you're using.

---

