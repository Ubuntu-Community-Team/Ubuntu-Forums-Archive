---
title: "Can't figure out how to disable power button shut down."
date: 2017-05-12
forum: General Help
---

### Post by thedeathclox on 2017-05-12
Hey folks, I've been having an aggravating issue lately. My cats keep jumping onto the top of my computer where my power button is located, and keep triggering a shutdown while I'm gone. I would like to figure out how to have Ubuntu (I am running Ubuntu vanilla 16.04 LTS) essentially ignore that the power button is being pressed (although I am aware that after 10 seconds, the motherboard will power-off the machine anyways). In Windows, I know you can change it in the power settings to 'Do Nothing' when the power button is pressed. I know there must be a way to do that, either through GUI or Terminal, but so far forum searches and extensive google searches haven't yielded anything that worked for me.

Any suggestions are appreciated. If I don't respond within a couple hours of this post, I'm probably sleeping (it's almost 11:00pm here now), but I will get back to you as soon as I can. Thanks folks!

---

### Post by SuperFreak on 2017-05-12
I have Mint 18.1 which is Ubuntu based and Power Management gives me that option

---

### Post by thedeathclox on 2017-05-12
Interesting. I don't know why, but my Power Management preferences omit that option all together. It's rather thin, actually.

---

### Post by wildmanne39 on 2017-05-12
Go to all settings > power > when power button is pressed > click on the tab and choose nothing.

If you are running unity type in the dash power and it should show you the settings before you are done typing.

---

### Post by thedeathclox on 2017-05-12
That is where I was going to my power settings from (shown in a screenshot from my response above). I am using Unity as you suggested (I just have a flat theme enabled, but this is vanilla 16.04 through-and-through). This is all that I get in my power options.

---

### Post by thedeathclox on 2017-05-12
I finally managed to solve the problem using dconf-editor, followed the following guide:

[https://askubuntu.com/questions/66723/how-do-i-modify-the-options-for-the-power-button](https://askubuntu.com/questions/66723/how-do-i-modify-the-options-for-the-power-button)

Hopefully this serves as a reference for anybody else having this issue. Thanks guys!

---

