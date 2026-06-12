---
title: "Problems after upgrade"
date: 2016-08-22
forum: General Help
---

### Post by cerasus on 2016-08-22
My previously installed version (I think 12.10, hope I'm not wrong) wasn't supported anymore for a good while and I decided to upgrade. I was already having problems since I switched from 12.04 to 12.10 as that "update center" thing appeared twice in my sidebar. I upgraded to 13 then to 14 but after restarting I get the reboot options screen. Here's what I get when choosing "Ubuntu":

[[IMG]http://imagizer.imageshack.us/v2/640x480q90/922/ASH8oU.jpg[/IMG]]("https://imageshack.com/i/pmASH8oUj")[URL="http://imageshack.com/i/pmASH8oUj"]
[/URL]
And here's what I get when choosing any other previously installed version (including the recovery mode):

[[IMG]http://imagizer.imageshack.us/v2/640x480q90/921/9vC0Aj.jpg[/IMG] ]("https://imageshack.com/i/pl9vC0Ajj")

How can I at least start the 12.10 and get some things on a stick or smth and format and install the newest version from scratch cause I see no other way of getting rid of these problems which I've been having for a while now.

---

### Post by banceu_sergiu_ione on 2016-08-22
If you have a Live Ubuntu installer, plug it in an boot from it. Select ' Run Ubuntu without installing ' and let it load. Once load you can get all files you want from your /home. You also can run a [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and fix the one you already have installed. But a new install is always better.
If you do not have a LiveUbuntu yet, ask for someone's pc to let you make one. You can use [UNetBootin]("https://unetbootin.github.io/") to download and create an USB live installer, it run on windows/mac too. I recommend you go with 14.04.5 version 1st.

---

### Post by cerasus on 2016-08-22
> **banceu_sergiu_ione said:**
> If you have a Live Ubuntu installer, plug it in an boot from it. Select ' Run Ubuntu without installing ' and let it load. Once load you can get all files you want from your /home. You also can run a [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") and fix the one you already have installed. But a new install is always better.
If you do not have a LiveUbuntu yet, ask for someone's pc to let you make one. You can use [UNetBootin]("https://unetbootin.github.io/") to download and create an USB live installer, it run on windows/mac too. I recommend you go with 14.04.5 version 1st.

Is the boot repair the same thing as live ubuntu installer? I mean do I need 2 cds or usbs or it's all about 2 different options you can select from the same cd?

---

### Post by banceu_sergiu_ione on 2016-08-22
You only need 1 CD or 1 USB pen. Use it to make a live ubuntu installer. 
Once you have the live installer, you can boot from it. You will get same options such as ' run ubuntu with out install' / install ubuntu / mem tes.... 
If you chose to run ubuntu with out install it will log you in a live ubuntu  desktop session. It look like as near to your ubuntu desktop. From it you can easily access your /home folder and backup your data. Also, if you connect to network, and go to this link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) you can see how to run boot-repair. Its easier to use the 2nd option, open a terminal ( CTRL+ALT+T ) and then run the commands you see at 2nd option.

---

### Post by cerasus on 2016-08-26
> **banceu_sergiu_ione said:**
> You only need 1 CD or 1 USB pen. Use it to make a live ubuntu installer. 
Once you have the live installer, you can boot from it. You will get same options such as ' run ubuntu with out install' / install ubuntu / mem tes.... 
If you chose to run ubuntu with out install it will log you in a live ubuntu  desktop session. It look like as near to your ubuntu desktop. From it you can easily access your /home folder and backup your data. Also, if you connect to network, and go to this link [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) you can see how to run boot-repair. Its easier to use the 2nd option, open a terminal ( CTRL+ALT+T ) and then run the commands you see at 2nd option.

I see. Is the boot kit bigger than a regular cd....so over 650...700 mb?  And yes.....one more thing....is the repair option some kind of  reinstall? Or is it something completely different? Is it better to wipe  out all of my data after backing up and install from scratch?

---

