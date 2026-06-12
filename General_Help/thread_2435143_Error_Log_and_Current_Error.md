---
title: "Error Log and Current Error"
date: 2020-01-16
forum: General Help
---

### Post by attano on 2020-01-16
I recently started using Ubuntu on my laptop, and when I log-in I get a pop-up asking me if I want to report a problem that has been detected. It doesn't tell me what the problem is. Clicking report exits the window, and so does clicking cancel.

How can I figure out what the issue is, as well as what's causing it?

The app it shows in my dock that is displaying the window is labeled update-notifier.



Thanks.

---

### Post by deadflowr on 2020-01-16
Crash reports are placed in the /var/crash directory.
(You can find it in Files > Other Locations > Computer > var)

See if any crash reports are listed there.

---

### Post by ajgreeny on 2020-01-16
Which version of Ubuntu are you using; I am seeing that error occasionally but not too surprised, as in my case, it's in the development version 20.04, not released until April, so still very much "work in progress".

---

### Post by attano on 2020-01-16
I am using Ubuntu 18.04.3 LTS

There are three files from earlier in the week (none of which seem to be relevant) in my /var/crashes folder.

---

### Post by Redalien0304 on 2020-01-16
Same Here on Ubuntu 20.04 Development Version. Every time i boot up i see the "System program problem detected". 
With no Info what it is? I will check the /var/crash directory though.

---

### Post by deadflowr on 2020-01-17
Even if a few days old they can still be relevant.

---

### Post by ajgreeny on 2020-01-17
In spite of the crashes at boot of my 20.04 install, /var/crash is totally empty so no help there.

---

### Post by attano on 2020-01-17
I do see two files in the crash folder that might be relevant. They were new this morning.
One is called 

_usr_bin_gnome-shell.121.crash

and the other:

_usr_bin_Xwayland.121.crash

What info from the crash file would be helpful for me to provide?

---

### Post by corradoventu on 2020-01-17
If You click on the .crash file in /var/crash you should have a window describing the problem. Or you can authorize your user to open it with text editor with ```
sudo adduser $USER whoopsie
``` Note: you will have the new group after restarting your session.
Edit: sometimes whoopsie is unable to send the crash info to canonical, so the crash file remain flagged as 'to be sent' and you see the error message each time you login.
If you want avoid the message and don't want to open a bug you may simple delete the .crash file.

---

