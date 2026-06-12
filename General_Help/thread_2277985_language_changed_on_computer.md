---
title: "language changed on computer"
date: 2015-05-13
forum: General Help
---

### Post by TFSinclair on 2015-05-13
The language on my computer, Compaq Presarrio, Ubuntu 14.04, 4 gigs Ram,  suddenly changed from English to Gaelic for the whole computer. I did not make the change and this occurred just after an update when I rebooted the computer. I have gone onto settings-language support and set it to English and clicked to make the change system wide...no joy.  The computer is still in Gaelic. has anyone an idea on how I may correct this and have control of my languages again?

---

### Post by TFSinclair on 2015-05-13
bump

---

### Post by QIII on 2015-05-13
Hello!

Which point release is that?  14.04, 14.04.1 or 14.04.2?

---

### Post by TFSinclair on 2015-05-13
It is 14.04 LTS...that's the best I can do with not being able to read more details due to the language issue.

---

### Post by leunam12 on 2015-05-13
Try editing your locale:

[http://askubuntu.com/questions/133318/how-do-i-change-the-language-via-a-terminal](http://askubuntu.com/questions/133318/how-do-i-change-the-language-via-a-terminal)

---

### Post by TFSinclair on 2015-05-13
leuam12, I tried what was said on your link and either I am more inept at Terminal than I thought or I did it incorrectly.  Might you give me the straight terms to type in Terminal to resolve this. please?

---

### Post by TFSinclair on 2015-05-14
leuam12, I tried what was said on your link and either I am more inept at Terminal than I thought or I did it incorrectly.  Might you give me the straight terms to type in Terminal to resolve this. please?

---

### Post by leunam12 on 2015-05-14
```
sudo nano /etc/default/locale
```Press enter and find the line that says LANG= and whatever is after this change it to "en_US" (include the quotation marks). Same with the LANGUAGE= line, change whatever is after to "en_US:en". Your lines should look like this.```
LANG="en_US"
LANGUAGE="en_US:en"
```. Then press Ctrl+x and then Y to save the changes and enter to exit nano.

Next step is the same for your user locale: ```
nano $HOME/.pam_environment
``` and change your LANG and LANGUAGE lines so they look lke this:```
LANG=en_US
LANGUAGE=en_US
```Reboot.

---

