---
title: "screen lockout (suspend) password"
date: 2023-10-05
forum: General Help
---

### Post by acefromspace on 2023-10-05
Using Ubuntu 20.04 I can't remember how to find this setting (I'm in my 60s) I'm not even sure if I'm using the correct term(s) I simply want to make it where I don't need to type in a password to "wake up" the screen.
Is there a command I can use in terminal?

---

### Post by Xian on 2023-10-06
Go into the Settings -> Privacy -> Screen Lock and make your desired changes.

---

### Post by MAFoElffen on 2023-10-07
There is no screen setting to disable the screen lock from asking for a password. Even if you set it up to autologin on boot, the screen lock does exactly what the name implies... It locks the screen for security and privacy.

 To do what you want to do, change your perspective on how you think about it.

Disable the screen lock by setting it to never, and disabling the screen lock for Automatic Screen Lock & Screen lock on suspend... Install a "screensaver". Set the screen saver to start after the desired amount of inactivity. After it goes to the screen saver, any activity and it will return to your desktop, without having to enter a password.

---

### Post by acefromspace on 2023-11-02
I resolved this issue (thank you) just to realize I didn't have suspend turned on in power settings. Forgot to mark this as solved (by the way... how do I do this?)

---

### Post by acefromspace on 2023-11-02
Found it. Tools... mark this thread as solved (I knew this but I'm 63)

---

