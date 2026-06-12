---
title: "Powertop unusable in Saucy, no menu navigation"
date: 2013-11-02
forum: General Help
---

### Post by rmcd on 2013-11-02
Fresh install of Saucy, running powertop 2.4 with a command shell on a lenovo x220.

I can't navigate the top-line menu in powertop. When I use the right and left arrow keys, powertop itself (the entire application) scrolls within the terminal window. I can't see how to move from "Overview" to "Idle stats" etc. This happens even when I maximize the terminal.

I have been a powertop user for some time. I've never seen this before. Is there a configuration choice somewhere that might affect the way powertop is interpreting the cursor keys? Is anyone seeing this same issue?

---

### Post by Toz on 2013-11-02
Try using the tab key to move from section to section.
You can also:
```
sudo powertop --html
```
...to create an html file that you can view in your browser.

---

### Post by rmcd on 2013-11-02
Thank you! Tab worked.

---

