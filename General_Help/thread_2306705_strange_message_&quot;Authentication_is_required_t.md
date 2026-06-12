---
title: "strange message: &quot;Authentication is required to change your own user data&quot;"
date: 2015-12-17
forum: General Help
---

### Post by shochatd on 2015-12-17
I believe this started showing up in 15.04. It happens when switching back to my own account after having done a "switch user" to my wife's account. The message seems like a contradiction: Why would I need to (re-) authenticate to change my own data? And why does switching back to my own account entail changing any data? Typing in my password as requested seems to have no effect: The message doesn't go away. I can only get rid of this by hitting the close box on the message multiple times. I found some discussion of this on askubuntu, and someone said it can be fixed via Settings -> Session and Startup, and then unchecking "PolicyKit Authentication Agent". I assume "Settings" means "System Settings", but I see nothing there called "Session and Startup". What is going on here and how can I make it stop?

---

### Post by deepakdeshp on 2015-12-18
When youuse switchuser to your wifes name you become that user. When you come back the system has to assure that your wife is authrized to su to you. Hence the password. To avoid this use sudo command for switch user. It will be authenticated only the first time

---

### Post by shochatd on 2015-12-18
At the point where the message pops up, I have *already* typed my password, so I am already authenticated to the system. And as I said, supplying my password to this new prompt does not have any effect -- it just keeps prompting me until I force the window to close. Why did this problem only appear in 15.04? I have never experienced this in prior releases. You say to use sudo, but I only know sudo in terms of command line operations. I'm talking about switching users using the GUI (the "gear" menu).

---

### Post by shochatd on 2015-12-21
I decided to try having my wife log completely out of her session before going back to my own. But even in this case, after I type my password and see my desktop again, I *still* get the same ridiculous message asking me to (re-) authenticate. And as before, the only way to make it go away is to hit the close box of the window containing the message, 7 times in the most recent case.

---

