---
title: "Help!"
date: 2008-06-11
forum: General Help
---

### Post by davideotape on 2008-06-11
Whenever I try and put an adress in the adress bar of firefox, this text comes up:

ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],alias)
5:()
6:SRCH_SVC_getEngineByAlias(hotmail.com)
7:getEngineByAlias(hotmail.com)
8:getShortcutOrURI(hotmail.com,[object Object])
9:canonizeUrl([object KeyboardEvent],[object Object])
10:handleURLBarCommand([object KeyboardEvent])
11:anonymous(textentered,[object KeyboardEvent])
12:fireEvent(textentered,[object KeyboardEvent])
13:onTextEntered()
14:handleEnter(false)
15:onKeyPress([object KeyboardEvent])
16:onxblkeypress([object KeyboardEvent])

Does anyone have any idea whats going on?

---

### Post by loell on 2008-06-11
from [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/238871]("https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/238871")


suggests that you disable your firefox extensions in **tools -> addons**

and then restart your browser.

---

