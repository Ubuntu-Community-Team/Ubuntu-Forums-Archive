---
title: "Computer freezes when Firefox is closed"
date: 2023-04-13
forum: General Help
---

### Post by bjngchn on 2023-04-13
What a nonense. This computer is supposed to be very safe. I was using Firefox when javascript was turned off. I closed the last Firefox window. Now all the data is supposed to be erased automatically. Ok, but  why does the computer freeze. I can't even move the cursor. Feels like, Firefox is trying to send all my data to some external location, before erasing them.  ALSO, when JS is turned on, sometimes computer freezes immediatelty , once I visit a site. I can't close the tab. Sometimes I can, and computer remains slow or frozen for a while, or maybe even permanently.  Is there a about:config parameter  which I can modify, so such attacks would likely fail, and I have enough time to stop them?  I try to open a Firefox window, or just terminal window. I click an icon from desktop or a panel. Then I have to wait for 30 seconds, just to see that window. It should take less than a second, but instead, takes forever.  Most of the laptop is empty. It was not used abusively. It is not too old. It doesn't heat up.   I suspect either the operating system which is not old, like 20. something , or some parameters somewhere  is slowing things down, or I might have installed  a bad thing unknowingly , like some .pdf , .org .mp3. , or something from repository.   Also sometimes firefox updates itself, and forces me to restart and prevents any action without restarting.  I hate it. I don't do restart, because they want to run some scripts, while I'm using my favorite sites when logged in..   I mean, something wrong, and maybe some tricks can improve things.  For example most or all desktop effects are disabled.  Things should run fast.

---

### Post by raleigh3 on 2023-04-13
Have you tried un-installing Firefox and re-installing it ?

This link gives you the details.

[https://www.makeuseof.com/apt-get-uninstall/](https://www.makeuseof.com/apt-get-uninstall/)

You can get the newest version here.

[https://www.mozilla.org/en-US/firefox/new/](https://www.mozilla.org/en-US/firefox/new/)

---

### Post by ajgreeny on 2023-04-14
You tell us you're using version** 20 something** which is not enough info so give us all the detail you can and run command **inxi -Fzx** then show us the output using Code Tags (how-to in my signature below).

Maybe this is your first experience of the snap version of firefox which is the default in 22.04 and can be slow to open, not usually to close.

---

### Post by ActionParsnip on 2023-04-14
If you close other web browsers (install another if you need.....its just to test), is it the same?

---

### Post by TenPlus1 on 2023-04-15
You could try removing the snap version of Firefox and replacing it with a native .deb which tends to fix many issues:

[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

---

### Post by dragonfly41 on 2023-04-15
Or try creating a fresh user profile in Firefox, with no extensions attached to that profile.
Research how to create different profiles.

---

