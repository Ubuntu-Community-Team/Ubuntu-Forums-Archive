---
title: "Virtual Box Seamless Integration in Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by nickdr on 2007-10-20
I have installed VirtualBox in Ubuntu Gutsy 64 bit. I am looking to have seamless integration. I installed the guest additions, but how do I get my windows apps to come out of virtual box? I  tried the Seamless mode (Ctrl+L) but often my screen becomes distorted. I tried reading the guide here:
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
But the first part seemed confusing so I skipped over. It now seems that VMWare would've been a better choice. Will I have better luck with it? Also since I can't get my TV tuner configured in Ubuntu will I be able to install it in Windows?

Thanks!

---

### Post by UK-Wobbie on 2007-10-20
> **nickdr said:**
> I have installed VirtualBox in Ubuntu Gutsy 64 bit. I am looking to have seamless integration. I installed the guest additions, but how do I get my windows apps to come out of virtual box? I  tried the Seamless mode (Ctrl+L) but often my screen becomes distorted. I tried reading the guide here:
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
But the first part seemed confusing so I skipped over. It now seems that VMWare would've been a better choice. Will I have better luck with it? Also since I can't get my TV tuner configured in Ubuntu will I be able to install it in Windows?

Thanks!

Your TV Card will not work in vbox! As when installing Windows in vbox it's not getting the full system.. Like your Ubuntu is doing..

I know lot of people are having allot of problems with TV Cards on Ubuntu. Have you got your TV Card pluggings right? :)

---

### Post by nickdr on 2007-10-20
i have a leadtek tv2000xp expert. i have read that it should work in ubunut i just cant figure out how. i am a noob and much of the technological mumbo jumbo that goes along with it makes it too difficult to follow. i thought that it ubuntu detected it, windows would detect it.

---

### Post by UK-Wobbie on 2007-10-20
> **nickdr said:**
> i have a leadtek tv2000xp expert. i have read that it should work in ubunut i just cant figure out how. i am a noob and much of the technological mumbo jumbo that goes along with it makes it too difficult to follow. i thought that it ubuntu detected it, windows would detect it.

Am looking for plugings for you... And i seen this! [http://www.mythtv.org/wiki/index.php/Leadtek_WinFast](http://www.mythtv.org/wiki/index.php/Leadtek_WinFast)

Right down at the bottom of the page! 


Here are some sites what tells you about your leadtek tv2000xp exper!

[http://ruel.net/pc/tv.tuner.winfast2000xp.htm](http://ruel.net/pc/tv.tuner.winfast2000xp.htm)

[http://www.pcstats.com/articleview.cfm?articleID=1574](http://www.pcstats.com/articleview.cfm?articleID=1574)

[http://www.videohelp.com/capturecards/leadtek-winfast-tv2000-xp-expert/322](http://www.videohelp.com/capturecards/leadtek-winfast-tv2000-xp-expert/322)

[http://www.hardwarecentral.com/hardwarecentral/reviews/article.php/3343921](http://www.hardwarecentral.com/hardwarecentral/reviews/article.php/3343921)

[http://www.bjorn3d.com/read.php?cID=636&pageID=789](http://www.bjorn3d.com/read.php?cID=636&pageID=789)

[http://www.tv-cards.com/messageboard/viewtopic.php?id=14390](http://www.tv-cards.com/messageboard/viewtopic.php?id=14390) 


Have a look at this one! It may get your TV Card working :-D
[http://web.missouri.edu/~datcnc/htpc_single.html](http://web.missouri.edu/~datcnc/htpc_single.html)
Everthing about your TV Card and how to Instill it...

 If your TV Card is in your pc!
Can you get anything at all? Have you had a go opening your pc up and push your card in more? 
It may not be pushed in right or somthing... Give the Instill a go and if that do not work! Give pushing your card in a bit more see if it's not out or somthing... 
It's easy done! :)

---

### Post by UK-Wobbie on 2007-10-20
> **nickdr said:**
> i have a leadtek tv2000xp expert. i have read that it should work in ubunut i just cant figure out how. i am a noob and much of the technological mumbo jumbo that goes along with it makes it too difficult to follow. i thought that it ubuntu detected it, windows would detect it.

I see why it's not working now! It's got the wrong" drivers:
sudo rmmod bt878
sudo rmmod tuner
sudo rmmod bttv

You have to instill the new drivers! 
[http://web.missouri.edu/~datcnc/htpc_single.html](http://web.missouri.edu/~datcnc/htpc_single.html) <-- Look there for more info!

And i hope for the best for you. :)

---

