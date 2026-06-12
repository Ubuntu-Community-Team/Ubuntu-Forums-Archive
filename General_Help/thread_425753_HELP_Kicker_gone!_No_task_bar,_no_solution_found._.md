---
title: "HELP: Kicker gone! No task bar, no solution found. [Resolved]"
date: 2007-04-27
forum: General Help
---

### Post by Neobuntu on 2007-04-27
What's going on? No task bar. Then it came back suddenly, now it's gone!

Rebooting did not fix. Theme change did not fix. "sudo apt-get install kubuntu-desktop" did not fix.

I can think of no install or change that I have done that might cause this, other than upgrading to Feisty.

Where do I even start? (literally)

---

### Post by aysiu on 2007-04-27
Have you tried Alt-F2 ```
kicker &
```?

---

### Post by Pox on 2007-04-27
Try running "kicker" from a terminal and see if there's any errors.

---

### Post by Neobuntu on 2007-04-27
I did that too. With and without the "&" already. I just did it again.

That may have been why it later came back but then disappeared.

What's causing this?

---

### Post by Neobuntu on 2007-04-27
"ERROR: kicker is already running!"

But it has disappeared. This sucks.

---

### Post by Pox on 2007-04-27
Do a "ps -ef | grep kicker" to see if the process is running.

---

### Post by aysiu on 2007-04-27
Can you try this?

Log out of your regular user session.

Press Control-Alt-F1 (this will take you to a fullscreen terminal).

Log in as the regular user.

Type ```
sudo adduser testuser
exit
```

Press Control-Alt-F7 (this will take you back to the graphical login screen).

Then log in as *testuser* and see if the test user has the same problem as your regular user. If the test user has the same problem, it's a system-wide problem. If the test user *does* not have the same problem, it's something wrong with your user profile.

---

### Post by Neobuntu on 2007-04-27
> **Pox said:**
> Do a "ps -ef | grep kicker" to see if the process is running.



user       5284     1  0 21:04 ?        00:00:03 kicker [kdeinit]

But it's not showing.

---

### Post by aysiu on 2007-04-27
Try this in the terminal: ```
killall kicker
kicker &
```

---

### Post by Neobuntu on 2007-04-27
Ok, I did all that (which a newbie wouldn't know how without Kicker) and the testuser works. Reboot and my profile doesn't.

Now, remember. I'm not real new to this stuff and make notes about what I change. Other than regular upgrades, I don't know what it could be.

I can only guess that I must delete some KDE file and reset everything but I don't remember which one (or if I should).

Then, the question is, what is the problem? That would be a messy fix to have to do periodically.

---

### Post by Neobuntu on 2007-04-27
Results after killall kicker
and
kicker &> 
[1] 5204
 X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x45
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x160014e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x300021e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x45
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x30002d4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  155
  Minor opcode:  6
  Resource id:  0x30002d4
Then it hangs. Pressing [ENTER] yields "done". No Kicker seen!

---

### Post by Stephen Howard on 2007-04-27
I have also suffered from this problem.  The fix that always works for me is:

from the command line type the following to bring up the kicker configuration section of the KDE control centre:

```
kcmshell panel
```

Then click on the 'hiding' tab and change one of the visibility settings - I have my panel set to hide, so I select 'Only hide when panel button is clicked'.  The save/apply the change.  The panel should start up again, at which point just change the setting back the way you want it and save/apply once more.

Hope the above works for you.  As I said it works for me - in fact, I've put the above kcmshell command in a desktop icon so I can run it easily.

---

### Post by Neobuntu on 2007-04-27
FOUND

I want to thank everyone for the quick and friendly help. Stephen, you nailed it. Thank you for kindly helping, as usual Aysiu.

My guess is, it was clicked by accident or by another user. Why it came back and then left (now I know hidden) is still a mystery. Maybe it's time for other users to have their own login. Since I have the hide tab in the lower right corner (really slim), perhaps the mouse found it's way there and was clicked while I was away or not looking.

Sorry for the trouble.

I hope this helps others that may have this problem, anyway.

---

### Post by Stephen Howard on 2007-04-28
I'm glad the fix worked.  I don't think its simply that the hide tab was too small, I think its actually a bug.

---

### Post by Stephen Howard on 2007-04-28
PS:  the [I"]X Error: BadDevice, invalid or uninitialized input device 169"[/I] message you are receiving is because your xorg.conf file has the three Wacom input-devices sections.  Delete those and the ugly error will go away.

No idea why Ubuntu sticks that stuff in its default xorg.conf file.  Seems to me that it messes up everyone's configuration for the benefit of the eight people who actually have one of those screwy input tablets.

---

### Post by Neobuntu on 2007-04-28
Commenting them stopped X  from coming up, until I uncommented them again. 

Go figure?:confused:

---

### Post by Stephen Howard on 2007-04-29
Double check what you've commented out:

The entire InputDevice section for stylus, eraser and cursor.

The lines in the ServerLayout section for stylus, eraser and cursor.

It should work quite happily (that is assuming you don't have the devices).

---

### Post by V3XED on 2008-04-02
I actually registered here just so I could say how thankful I am for this information. I was just about ready to go and reinstall Linux which would have meant wiping my laptops hard drive etc..

So thanks a ton!\\:D/

---

