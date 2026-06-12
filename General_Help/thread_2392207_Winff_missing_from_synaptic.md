---
title: "Winff missing from synaptic"
date: 2018-05-17
forum: General Help
---

### Post by Robbyx on 2018-05-17
I have the universe  repository ticked. When I search on winff nothing is found.  At the base it says 5 packages listed, 2631 installed, 0 to install, 0 to remove. I have tried to find other packages and they also do not show in synaptic. What should I change?

---

### Post by Autodave on 2018-05-17
Have you made sure that the system is up to date?  If not, in a terminal:

sudo apt-get update
sudo apt-get upgrade

---

### Post by oldos2er on 2018-05-17
Which version of Ubuntu are you using?

---

### Post by PaulW2U on 2018-05-18
> **Robbyx said:**
> When I search on winff nothing is found.  At the base it says 5 packages listed, 2631 installed, 0 to install, 0 to remove. I have tried to find other packages and they also do not show in synaptic. What should I change?
If the number of winff packages is being displayed on the bottom bar then they **are** being found but for some reason they are **not** being displayed. You say that other packages are not being "found" either. When you first open synaptic, "All" in the left hand window should be selected. Do you see a full package listing in the upper right hand pane? If not then you might have changed something that is inhibiting the **display** of packages although at this time I can't think what that might be.

For info I'm attaching my screenshot of synaptic after searching for winff.

[ATTACH=CONFIG]279737[/ATTACH]

---

### Post by ajgreeny on 2018-05-18
It may also be worth checking that you have the **universe** repos enabled as that is where the winff package resides.

---

### Post by mc4man on 2018-05-18
If you disabled enough stuff in synaptic > Settings > Preferences > Columns & Fonts I guess searches would return results with nothing shown.
(seems unlikely anyone would do that..
You could try resetting synaptic.conf back to default, can be deleted (rm) or move to a .bak to keep option to restore, with synaptic not running, - 
```
sudo mv /root/.synaptic/synaptic.conf /root/.synaptic/synaptic.conf.bak
```

---

### Post by Robbyx on 2018-05-20
> **Autodave said:**
> Have you made sure that the system is up to date?  If not, in a terminal:

sudo apt-get update
sudo apt-get upgrade



Will upgrade replace my current version (16.04)  of ubuntu-gnome with a later one?

---

### Post by Robbyx on 2018-05-20
> **oldos2er said:**
> Which version of Ubuntu are you using?

Ubuntu gnome 16.04

---

### Post by Robbyx on 2018-05-20
> **PaulW2U said:**
> If the number of winff packages is being displayed on the bottom bar then they **are** being found but for some reason they are **not** being displayed. You say that other packages are not being "found" either. When you first open synaptic, "All" in the left hand window should be selected. Do you see a full package listing in the upper right hand pane? If not then you might have changed something that is inhibiting the **display** of packages although at this time I can't think what that might be.

For info I'm attaching my screenshot of synaptic after searching for winff.

[ATTACH=CONFIG]279737[/ATTACH]

When I start synaptic I see "all" and below it various categories of files, which are the same as clicking on the sections button.

---

### Post by Robbyx on 2018-05-20
> **mc4man said:**
> If you disabled enough stuff in synaptic > Settings > Preferences > Columns & Fonts I guess searches would return results with nothing shown.
(seems unlikely anyone would do that..
You could try resetting synaptic.conf back to default, can be deleted (rm) or move to a .bak to keep option to restore, with synaptic not running, - 
```
sudo mv /root/.synaptic/synaptic.conf /root/.synaptic/synaptic.conf.bak
```

I have just run the code and it has restored Synaptic to finding my searches. 

Thank you all for your help.

---

