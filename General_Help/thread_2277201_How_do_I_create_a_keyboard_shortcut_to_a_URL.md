---
title: "How do I create a keyboard shortcut to a URL?"
date: 2015-05-07
forum: General Help
---

### Post by harry003 on 2015-05-07
Please excuse my re-asking a stupidly basic question, but I have looked through here and not found an answer that I could use.

I found and downloaded "Lubuntu_Shortcut_Creator" but it seems to be for programs but not URLs.

I found "DeskCut" in Firefox but I can't figure out how to open it and use it.

---

### Post by tgalati4 on 2015-05-07
In the command dialog box you can put:

```
firefox http://www.google.com
google-chrome http://www.google.com
```

---

### Post by Bucky Ball on 2015-05-07
*Thread moved to **General Help**.*

Presuming you're using Lubuntu. Right click the desktop and 'Create URL Link'? You don't need to install anything, or shouldn't.

---

### Post by harry003 on 2015-05-07
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

Presuming you're using Lubuntu. Right click the desktop and 'Create URL Link'? You don't need to install anything, or shouldn't.

I am using Ubuntu.

This does not work.

---

### Post by harry003 on 2015-05-07
> **tgalati4 said:**
> In the command dialog box you can put:

```
firefox http://www.google.com
google-chrome http://www.google.com
```

I am sorry, but I do not understand.

Where do I find the option to create the shortcut?

---

### Post by CantankRus on 2015-05-08
Hit the super(Windows) key to open the dash and type in "keyboard" and open the keyboard settings to the shortcuts tab.
Press the "**+**" button to add a custom shotrcut.
Enter the name of your shortcut and then in the command box enter the url preceded by either the **web browser** you want to use 
or **xdg-open** to use the default browser. 
Hit the apply button and then click on the "**disabled**" section to enter your keystokes. (backspace to clear)
 
eg: I have **opera-developer** and **google-chrome** installed.
The command to open [http://ubuntuforums.org](http://ubuntuforums.org) in my default browser opera-developer...
```
xdg-open http://ubuntuforums.org
```
or
```
opera-developer http://ubuntuforums.org
```

The command to open [http://ubuntuforums.org](http://ubuntuforums.org) in google-chrome...
```
google-chrome http://ubuntuforums.org
```
Test the command you use in a terminal first.

---

### Post by simon128 on 2016-03-01
That worked for me, thanx!

---

### Post by Bucky Ball on 2016-03-01
Which bit exactly? And with that, let's put the thread back to sleep permanently.

*Thread closed. *

---

