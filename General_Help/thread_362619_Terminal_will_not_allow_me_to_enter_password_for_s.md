---
title: "Terminal will not allow me to enter password for sudo command"
date: 2007-02-15
forum: General Help
---

### Post by vitr0x on 2007-02-15
Basic problem: I cannot enter my password to configure my graphics card driver.

Story:  I've been using whatever graphics driver Ubuntu detected for my ATI Radeon 9200 AGP when I first installed linux on my computer.  Recently, the resolution was drastically lowered; after downloading and installing "xorg-driver-fglrx" from synaptic, I then tried to configure it in the terminal with: sudo dpkg-reconfigure xserver-xorg.  The problem is that when prompted for my password, I cannot type anything into the terminal.  I tried both right-click>>copy>>paste and manually typing the sudo command, but in both cases, I was still unable to type anything.  Is there a reason for this?  :confused:

---

### Post by Motoxrdude on 2007-02-15
Even though nothing will get displayed, you are still typing your password in. When it asks for your password type your password and hit enter even though nothing is getting displayed.

---

### Post by Maestro23 on 2007-02-15
You do know that when you type in your password in terminal, the cursor does not move and nothing is displayed for security reasons.

Are you saying that after you typed in your password and hit enter, that it gave an error msg or just didn't do anything?

---

### Post by aysiu on 2007-02-15
The lack of visual feedback when you enter your password in the terminal is a common problem for new users, and, unfortunately, it will never change. Just enter your password and hit the **Enter** key.

Read more about this issue here:
[Feedback on entering password in the terminal?](http://ubuntuforums.org/showthread.php?t=214393&highlight=terminal+password+feedback)

---

### Post by vitr0x on 2007-02-15
Thanks.  I've been using terminal commands a fair amount, but I think I've been staring at the keyboard since my password is out of the ordinary for me.

---

