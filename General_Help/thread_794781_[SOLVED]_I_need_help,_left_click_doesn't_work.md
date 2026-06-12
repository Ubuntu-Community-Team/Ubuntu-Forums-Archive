---
title: "[SOLVED] I need help, left click doesn't work"
date: 2008-05-14
forum: General Help
---

### Post by VayHow on 2008-05-14
I was trying some effect and settings in CCSM last night. After I changed a setting (I can't remember which one now), I know it needs some time to take effect and looks not responding. That's the question! I don't know what I clicked during that time. When I closed CCSM, I found that left click doesn't work. Wherever I move the cursor in a window and left click, nothing happens. The only thing I can do is to left click and hold so I can drag the window! I don't have to put the cursor in title bar, anywhere in the window is OK! I think this could be the result of some setting, can anyone help me on this?

PS: I can left click those buttons and menus in system bar on top of the desktop.

---

### Post by tommyhakinen on 2008-05-14
re-install the CCSM should reset all the settings to default.

---

### Post by EXCiD3 on 2008-05-14
Delete the compiz settings from your ~/.compiz directory and this should revert the settings back to default without needing to reinstall.

---

### Post by VayHow on 2008-05-15
Could you please give me the exact path of this config file? I'm a newbie on this. Thanks in advance.

---

### Post by EXCiD3 on 2008-05-15
Its a hidden folder in your file browser. Open your Home folder and press Ctrl-H to view hidden files/folders. there should be a .compiz folder in there. ~/.compiz is the same location when you do it in terminal. ~ means your home directory for future reference ;)

---

### Post by VayHow on 2008-05-15
Thank you very much for your help! Now I know what ~ means, thanks!

And this problem has been solved. I enabled "Move Window" in CCSM, and I changed the bind key for mouse from "Alt+Button 1" to "Button 1" inadvertently. So wherever I put the cursor, of course it can only drag the window. I've set this back to default, OK now.

---

### Post by EXCiD3 on 2008-05-15
Haha yeah that would be a problem :P Glad to help!

---

