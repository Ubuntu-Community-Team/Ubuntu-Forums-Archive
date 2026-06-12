---
title: "keyboard issues across the board on upcoming ubuntu 14.10"
date: 2014-10-21
forum: General Help
---

### Post by nIRV on 2014-10-21
I've recently upgraded to the upcoming Ubuntu 14.10 (64-bit) and have since then been affected by a series of (possibly related) keyboard issues on many applications. To list a few:
- In a newly opened Nautilus window, the first keyboard key press fails to open the "quick search / filter" text box
- In Filezilla, it's impossible to use the backspace key in the host, username, and password text boxes
- In XChat Gnome, keyboard input sometimes fails entirely

Is there a known launchpad issue on this that I could track and append information to?

---

### Post by grahammechanical on 2014-10-22
> [COLOR=#000000]In a newly opened Nautilus window, the first keyboard key press fails to open the "quick search / filter" text box[/COLOR]

Provided we are talking about the same thing, then it works fine for me. I have not experienced these kinds of issues.

---

### Post by VH-BIL on 2014-10-25
My keyboard stops working in Nautilus. I can reproduce this by the following actions.


I have files Named like "TV Show Name S01E01.mp4" and I press F2 to rename and press ctrl+c to copy. I drag the new file in that I want named "TV Show Name S01E02.mp4" so I press F2 to rename and press ctrl+v to copy so I just have to change the 1 to a 2. After the past action nautilus does not respond to keyboard keys but it does to keys used for navigation such as arrows, enter and backspace. Nautilus will start to work again when I kill and restart it.

---

### Post by cariboo on 2014-10-26
Seeing as we are now in the Vivid development cycle, moved to General Help.

---

### Post by nIRV on 2014-10-27
VH-BIL, exactly. 

Glad this is reproducible on other people's machine. Who now files a launchpad issue on this? :)

---

### Post by VH-BIL on 2014-10-28
> **nIRV said:**
> VH-BIL, exactly. 

Glad this is reproducible on other people's machine. Who now files a launchpad issue on this? :)

I tried to file a report with ubuntu-bug but it kept telling me nautilis was a 3rd party program and to remove the repository or something. I have since reinstalled the 14.04 LTS so if you know how to file the bug report that would be great!

---

### Post by bugcy013 on 2014-10-29
Hi Guys,

I am also facing same issue in my laptop, yesterday I upgraded 14.04 to 14.10 via update-manager, After machine reboot my laptop mouse click and keyboard button not responding properly Please guide me How to fix this.

Note :: I am able to mouse movements only left and right mouse and keyboard button's not reponding

---

### Post by nIRV on 2014-11-01
I don't think it's a Nautilus bug, as the keyboard issue occurs with other applications too. But, launchpad bug filling has become such a pain, not sure how to file a generic USB keyboard broken all around :)

---

### Post by joao-rossa on 2014-11-06
> **VH-BIL said:**
> My keyboard stops working in Nautilus. I can reproduce this by the following actions.


I have files Named like "TV Show Name S01E01.mp4" and I press F2 to rename and press ctrl+c to copy. I drag the new file in that I want named "TV Show Name S01E02.mp4" so I press F2 to rename and press ctrl+v to copy so I just have to change the 1 to a 2. After the past action nautilus does not respond to keyboard keys but it does to keys used for navigation such as arrows, enter and backspace. Nautilus will start to work again when I kill and restart it.


Yes im having the same problem with nautilus, any news on this?

---

### Post by cml.co on 2014-12-27
> **VH-BIL said:**
> My keyboard stops working in Nautilus. I can reproduce this by the following actions.


I have files Named like "TV Show Name S01E01.mp4" and I press F2 to rename and press ctrl+c to copy. I drag the new file in that I want named "TV Show Name S01E02.mp4" so I press F2 to rename and press ctrl+v to copy so I just have to change the 1 to a 2. After the past action nautilus does not respond to keyboard keys but it does to keys used for navigation such as arrows, enter and backspace. Nautilus will start to work again when I kill and restart it.

Same thing with a new installation of ubuntu 14.10 64-bit.

This seems to be an IBus issue. This workaround worked for me:

```
sudo ibus restart
```

---

### Post by ghmercado on 2015-08-11
solution here worked for me as far as filezilla was concerned [http://ubuntuforums.org/showthread.php?t=2280665&p=13296350#post13296350](http://ubuntuforums.org/showthread.php?t=2280665&p=13296350#post13296350)

---

