---
title: "Main menu not working"
date: 2007-12-18
forum: General Help
---

### Post by budgie9 on 2007-12-18
Can anyone  tell me how to get the System-Preferences -Main Menu window working again. As it simply refuses to show itself.

I have started Ubuntu today and this option is not working. I don't know why it is not working and I don't recall doing anything to prevent it starting up.

---

### Post by barbedsaber on 2007-12-18
I think you have to right click on the top menu bar, and select add to panel, then go down the the ubuntu symbol with menu bar written below it, and click on that one.

---

### Post by budgie9 on 2007-12-18
Sorry barbedsaber, that does not work.
The actual icon in the Preferences simply does not fire up the menu list it used to, The one where I can edit add/remove the icons showing in the Applications list.
At least you given me a way to get at a folder of icons I could not see.
However, as stated I still can not edit the applications list which I need to do.
Any further suggestions?

---

### Post by kaervos1024 on 2007-12-18
I don't fully understand your last response here, but the menu editing application is called Alacarte, from which you should be able to see the applications list at the left, and all possible sub categories. Select Applications to enable/disable sub categories, and select a category to add/edit programs in there. You can access Alacarte by simply running this at the command line:

```
alacarte
```

---

### Post by budgie9 on 2007-12-18
Sorry if I have not made myself clear It is the option icon named Main Menu within the System menu - Preferences    in Ubuntu 7.10  
This is the one that accesses the Applications menu.
This is the item that is not working. thus not allowing me to modify the Applications menu.
The report back from alacarte in terminal is  -

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
ImportError: No module named Alacarte.MainWindow
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/var/lib/python-support/python2.5/problem_report.py", line 17, in <module>
    from email.Encoders import encode_base64
  File "/usr/lib/python2.5/email/__init__.py", line 118, in <module>
    import email.mime
ImportError: No module named mime

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
ImportError: No module named Alacarte.MainWindow

---

### Post by eapache on 2007-12-18
Alacarte is launched by that menu item, but it is crashing. Try the following```
sudo apt-get purge alacarte
sudo apt-get install alacarte
```I'm not sure what dependecies it might have, so if it asks you to remove anything else during the first step, post them here before continuing.

---

### Post by budgie9 on 2007-12-18
Thank you eapache
That tip I will remember and I hope others find it useful also, because it worked 100%.
Thank you again

---

### Post by eapache on 2007-12-19
It's just a simple reinstall. The 'purge' option caused it to redownload the package though, fixing any corruption.

Please mark the thread as solved using the thread tools to save others time.

---

### Post by alekseyportland on 2007-12-24
> **eapache said:**
> Alacarte is launched by that menu item, but it is crashing. Try the following```
sudo apt-get purge alacarte
sudo apt-get install alacarte
```I'm not sure what dependecies it might have, so if it asks you to remove anything else during the first step, post them here before continuing.

Help! The above is not working.all my applications are gone from the Applications menu. All I see is a pixel pop up where the menu should, but Places and System menus work fine.
The last thing I did is try to add a shortcut to a program installed in wine, and the whole menu disappeared. "Edit Menus" does not work even after the fix above. I am using Gutsy.

---

### Post by alekseyportland on 2007-12-24
[http://ubuntuforums.org/images/icons/icon8.gif](http://ubuntuforums.org/images/icons/icon8.gif)

---

### Post by kaervos1024 on 2007-12-26
Run

```
alacarte
```

From a command prompt, and post the output if any.

---

### Post by alekseyportland on 2007-12-29
Already formatted. The menu worked fine for other users I created. 
Oh well... just won't mess with the shortcuts this time.

---

