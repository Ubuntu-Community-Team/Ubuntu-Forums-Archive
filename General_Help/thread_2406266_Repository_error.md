---
title: "Repository error"
date: 2018-11-18
forum: General Help
---

### Post by serapis5 on 2018-11-18
I am currently running 18.04 and am getting a new repository error that says Google has changed their name from Google, Inc. to Google LLC.  I tried downloading and installing the latest version of Chrome but this has not corrected the issue.  Can anyone tell me what file I need to edit to correct this error?  Any help is greatly appreciated.

---

### Post by oldos2er on 2018-11-18
According to [this]("https://medium.com/@andrea_45267/how-to-solve-the-changed-its-origin-value-from-google-inc-to-google-llc-apt-error-4675f891be1f"), you would run ```
sudo apt update
``` in a terminal.

---

### Post by PaulW2U on 2018-11-18
> **serapis5 said:**
> Can anyone tell me what file I need to edit to correct this error?  Any help is greatly appreciated.
You don't need to edit any file but just agree to the change of name.

if you run **sudo apt update** in a terminal then you will receive a prompt to enter 'y' or 'N'. Hitting 'y' and Enter is all you need to do. **sudo apt upgrade** will then complete the installation of any updates. I don't know what happens when updating using a GUI application as I usually update using variations of the apt command in a terminal.

---

### Post by serapis5 on 2018-11-28
Thanks for your help.  I'll give it a try.

---

