---
title: "Can't boot from CD"
date: 2007-10-08
forum: General Help
---

### Post by crowhereuat on 2007-10-08
I downloaded and burned the iso image from ubuntu.com file ubuntu-7.04-desktop-amd64.iso when i tried to boot it in my laptop it says there is a graphic problem. And asks if I want to veiw the report. After I view it and hit enter it then just goes to a command line. I tried booting it in graphical safe mode and the same thing happend.

So, I thought I'd try booting it on my desktop pc. Once I make an option to boot ubuntu a few seconds later my monitor turns off. the cd is still spining but i cant see anything. Tried in graphical safe mode and the same thing happens.

My laptop is a dell intel core 2 duo. with a  ATI Radeon x1300 graphic card.

My desktop is a AMD Athlon 64. with an ATI Radeon grapic card

Here are some of the error msgs:
Failed to start X server. It is likely it is not set up correctly.

when i view the problem, it says:
Fatal server error: no screens found

when i get returned to the text interface the last line reads:
[ 166.539345] bcm43xx: Error: Microcode "bmc43xx_microcode s.fu" not available or load failed

Any ideas on whats going on? Thanks for the help guys.

---

### Post by strabes on 2007-10-08
Please search the forums before asking a question. This is a known bug with feisty and the question has been asked many times. The page I will link to below is a sticky thread in the "Absolute Beginners Talk" section.

Anyway, you have two options. The one I recommend is to simply download, burn, & install the gutsy beta. The bug has been fixed in gutsy.
 
Your other option is to follow the instructions located [here](http://ubuntuforums.org/showthread.php?t=414194). Notice that it instructs you to install using the **alternate** CD.

---

### Post by crowhereuat on 2007-10-08
Thanks, the only problem is I just want to try ubuntu before im ready to commit to it...so a live CD is kind of my best bet. Does anyone know if the 6.06LTS version has the ATI problem resolved. Perhaps I should just try that? Thanks for ur help so far.

---

### Post by bodhi.zazen on 2007-10-09
> **crowhereuat said:**
> Thanks, the only problem is I just want to try ubuntu before im ready to commit to it...so a live CD is kind of my best bet. Does anyone know if the 6.06LTS version has the ATI problem resolved. Perhaps I should just try that? Thanks for ur help so far.

No. Gutsy is your best bet.

You can also see here : [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

FYI the "problem" is ATI does not open source their drivers, so you should ask them to support Linux as you bought their card :)

---

