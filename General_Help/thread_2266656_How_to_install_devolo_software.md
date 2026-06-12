---
title: "How to install devolo software"
date: 2015-02-24
forum: General Help
---

### Post by hermanvanharen on 2015-02-24
MSI using 14.04 LTS 

Can someone tell me how to install this?

[http://www.devolo.com/downloads/software/software-devolo-cockpit-linux-4-3.run](http://www.devolo.com/downloads/software/software-devolo-cockpit-linux-4-3.run)

I clicked on it, it's in my downloadsfolder, but nothing happens

Thanks!

---

### Post by slickymaster on 2015-02-24
Moved to the **General Help** sub-forum.

Did you chmod the file so it executes?```
chmod +x Downloads/software-devolo-cockpit-linux-4-3.run
```Once done that just run```
./software-devolo-cockpit-linux-4-3.run
```

---

### Post by hermanvanharen on 2015-02-24
Thank you for trying but no reaction whatsoever in the terminalwindow

---

### Post by hermanvanharen on 2015-02-24
Cannot get entrance to 'Documenten' : map or file does not exist (but it does exist)

---

### Post by ajgreeny on 2015-02-24
Have you navigated to the folder with the files in before running those commands from slickymaster?

If that **software-devolo-cockpit-linux-4-3.run** file is in your user Downloads folder use command cd Downloads first, then the slikymaster commands, but note there is a typo in his second command which must have the **.run** filetype suffix at the end.

---

### Post by slickymaster on 2015-02-24
> **ajgreeny said:**
> Have you navigated to the folder with the files in before running those commands from slickymaster?

If that **software-devolo-cockpit-linux-4-3.run** file is in your user Downloads folder use command cd Downloads first, then the slikymaster commands, but note there is a typo in his second command which must have the **.run** filetype suffix at the end.
Absolutely right. Thanks for spotting that ajgreeny. (Note to self, multitasking isn't always as productive as we might though it is)

I've corrected my post.

---

### Post by hermanvanharen on 2015-02-24
Thanks greeny and slickymaster, i'm moving ahead but now the machine doesn't trust my identity though I logged on as the administrator?
how to convince it that it's really me?

---

### Post by hermanvanharen on 2015-02-24
it seems to be working. i had to use the sudo command prior to the commands slickymaster mentioned
Now the terminal is quite active. I suppose it's ready when the terminal is at ease?

---

### Post by hermanvanharen on 2015-02-24
Incredible!
Devolo is installed and it's working.
Thank's a lot

---

