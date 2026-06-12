---
title: "Ubuntu 16.04: Opened applications not in Unity bar or Alt-tab"
date: 2016-05-04
forum: General Help
---

### Post by krvermeulen on 2016-05-04
Hello,

After I upgraded to Ubuntu 16.04 every application that I open does not appear in the Unity bar or when I press Alt-tab. So when I click on the Firefox icon in the Unity bar it doesn't give me the currently opened browser window but starts a new browser instance instead. 

How can I fix this problem?

Thank you!

---

### Post by krvermeulen on 2016-05-05
Got it. Just reset Unity with the command 

dconf reset -f /org/compiz/

and all was well :).

---

