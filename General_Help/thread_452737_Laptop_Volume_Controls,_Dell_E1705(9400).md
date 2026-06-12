---
title: "Laptop Volume Controls, Dell E1705(9400)"
date: 2007-05-23
forum: General Help
---

### Post by grogger13 on 2007-05-23
On the Dell entertainment series laptops they have the volume control as well as other media buttons on the front of them so you can push them when the laptops close, in windows these buttons will work no matter the lid closed or opened, but in ubuntu when i close the lid the buttons don't respond until i reopen the lid and put my password in.

Is there anyway to get these buttons working all the time, or is this more of a bug in Ubuntu/Linix

---

### Post by codesplice on 2007-05-23
Hi **grogger13**,
The problem is probably that your system is set up to automatically lock your login session when your laptop lid is closed.

Try disabling that functionality.  System --> Preferences -->  Power Management and make sure that the dropdown menu next to "When laptop lid is closed:" says "Do Nothing".  Your screen display will still be displaying whatever's on the screen before you close the lid, so this probably wouldn't help too much if you're closing the lid to conserve the battery, but it won't lock the screen so you'll still have use of your media keys.

Hope this helps.

---

### Post by grogger13 on 2007-05-25
I realised that, but what i was hoping there was a way to have ubuntu lock the screen and still change to volume controls

Think about it, i should be able to control the volume when i close the lid without having to sacrifce keeping my screen on and not being able to lock it.

---

### Post by fragos on 2007-05-25
Can see your point in this case but in Linux, Locked means just what it says and designed so when you step away for lunch or a bio break, no one can get access even though you're running some background application like a very long bittorrent download.

---

