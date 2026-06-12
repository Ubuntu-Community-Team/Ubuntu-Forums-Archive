---
title: "How Do I Make Ubuntu 14.04 Go To Sleep"
date: 2015-12-23
forum: General Help
---

### Post by Rocky_Bennett on 2015-12-23
Hello All,
I am new to Ubuntu, so I just installed Ubuntu Studio 14.04 because I wanted the LTS version. My problem is the sleep setting. The way that I use my computer is as a triple boot with Linux Mint 17.3 and Windows 10 Redstone Preview. With the other two operating systems, I have them dialed in so that when I am done with my session I can just get up and walk away from the computer and the computer will go to sleep automatically in approx. 5 minutes. I see the setting in my Ubuntu, but the setting is greyed out, I can not set it to go to sleep. Is there anything that I need to do to unlock this setting (ungray it)? I might be having other issues and questions, but after I deal with this I will start other threads for each specific question. So far I really like my Ubuntu experience. Installation was smooth with no issues.

I'm sorry, I should mention that this computer is a standard desktop computer, it is not a laptop.

---

### Post by deadflowr on 2015-12-23
I've added the ubuntu studio prefix so others might know better.
i believe Ubuntu studio uses the xfce desktop environment, but I'm really not clear.
Hopefully someone who does know can help.
Sorry I can't help with more than that.

---

### Post by Rocky_Bennett on 2015-12-23
Thank you. I did not add the prefix "Ubuntu Studio" because I was not aware that there might be a difference in environments and commands between the different flavors of Ubuntu. Also, at the end of my session I can hit the "suspend" button and it does put my PC to sleep, I just like it when it is done automatically.

I have done a lot of Google searches, and tried various fixes, but nothing has seemed to work. Any suggestions?

---

### Post by pfeiffep on 2015-12-24
Is it possible Win 10 is in a mode that prevents Ubuntu from sleeping?

---

### Post by Rocky_Bennett on 2015-12-24
Of course that is a possibility, and I don't know for sure because I am new to all this Ubuntu stuff, but I am triple booting with Linux Mint Cinnamon 17.3 and that falls to sleep very obediently. So I really think that there is a feature or setting within Ubuntu that needs to be activated in order to enable the sleep mode.

---

### Post by pfeiffep on 2015-12-25
I suggest looking at 2 system settings: 
1) brightness and lock
2) power

---

### Post by Rocky_Bennett on 2016-01-01
I finally found a way to fix this;

[http://askubuntu.com/questions/453372/suspend-is-not-working-after-updating-to-ubuntu-14-04-from-13-10](http://askubuntu.com/questions/453372/suspend-is-not-working-after-updating-to-ubuntu-14-04-from-13-10)

---

### Post by pfeiffep on 2016-01-01
Please mark your thread solved. Also to help others indicate which portion of the link solved your issue

---

### Post by Rocky_Bennett on 2016-01-02
I think that all I did in order to fix my problem was to use a command line and enter

 sudo pm-suspend

I believe that is what fixed my problem, I was doing so much to my computer that day that I am not 100% sure if that is the key.

---

