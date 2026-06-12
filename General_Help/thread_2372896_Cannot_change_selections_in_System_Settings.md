---
title: "Cannot change selections in System Settings"
date: 2017-09-29
forum: General Help
---

### Post by geomcd1949 on 2017-09-29
Ubuntu 16.04.03 LTS

Unable to change any setting in Systems Settings > Software & Updates. In Ubuntu Software, unable to uncheck any of the checked items.  Same in Other Software. &c. 

In Ubuntu Software, unable to select anything from the dropdown -- no matter which option I highlight, the server remains the same.

Thanks.

---

### Post by wildmanne39 on 2017-09-29
*Thread moved to **General Help for a better fit**.*

---

### Post by deadflowr on 2017-09-29
Are the options grayed out or is it that when you click on a checkbox nothing appears to happen?

---

### Post by geomcd1949 on 2017-09-29
No options are greyed out. All appear active, yet when clicked, do nothing.

---

### Post by deadflowr on 2017-09-30
Typically when you click to check or uncheck the first time any of the check boxes, it needs to be authenticated so a password pop-up usually shows.
I remember people having issues before where the password pop-up box wasn't showing correctly and instead was either hiding behind the main window or it was opening in another workspace.
You might see if those are the issues by clicking on alt+ Tab or even alt + ctrl +Tab (this is usually the setting to show all apps in all workspaces) and see if any of the open apps shown are an authentication box.

But it's been a while (several years now) since I've seen any users having this as the problem.
Might be, might not be the problem.

Best of Luck

---

### Post by geomcd1949 on 2017-09-30
Thanks, deadflowr, not it.

Is there a way to open the Systems Settings in Terminal with sudo?

Thanks.

---

### Post by geomcd1949 on 2017-10-09
First must make sure [COLOR=#000000] [/COLOR]**PolicyKit Authentication Agent is enabled. Then changes can be made. When a change is made, the authentication box pops up.**

---

