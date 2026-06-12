---
title: "Some problems with the Ubuntu on Wubi"
date: 2008-03-29
forum: General Help
---

### Post by JoshuaMaximilian on 2008-03-29
err.. hi?
i installed wubi with ubuntu 8.04.. and is having some problems with it

after installation, it notified me whether i want to reboot and i allowed it.
so it rebooted.. i selected Ubuntu, and they will start up ubuntu with the scrolling thing [loading?]

then there is this installation window, at step 6 of 7, they asked me to import documents.
Problem #1: the forward button is not working.. so the option available is only close, so i closed it, they asked me if i want to quit the installation process, so i clicked quit..

they forwarded me to the Live CD user? everything is working fine..
i can connect to the internet, use any applications, after i finished, i end the session by clicking Shut Down

Problem #2: After the screen kind of logged out, it just blanked out and then it doesn't shut down.. as the light of my computer is working I have to shut it down 'the hard way' by pressing the power button for a few seconds..

After shutting down 'the hard way', i switched on the computer and selected ubuntu and the same thing happen again..

I use a laptop, running on Windows XP Professional Edition, with 1GB RAM, 1.60GHz and I got 6GB fee space.

I installed Ubuntu when with the option 4GB, under C:\ drive
Problem #3: When I go back to Ubuntu, I cannot see the second partition D:\ because it contained all of my documents, so i can't really work. Can't I make it appear under the explorer or file manager?

and Problem #4: What happened? my settings [desktop background, fonts, installation, etc] also isn't saved. Is it because of the LiveCD user?

Need help A.S.A.P
Thanks ^__________^

---

### Post by ago on 2008-03-29
Yes installation failed and you are back to live desktop

That is a known bug: [https://wiki.ubuntu.com/WubiGuide#head-e4dd73d03cc565bdbdcec46e799f8f73a7b726e0](https://wiki.ubuntu.com/WubiGuide#head-e4dd73d03cc565bdbdcec46e799f8f73a7b726e0)

---

### Post by JoshuaMaximilian on 2008-03-29
> Migration assistant page with forward button disabled
During installation sometimes you may get stacked seeing a migration assistant page with the forward button disabled ( [https://bugs.launchpad.net/wubi/+bug/195905](https://bugs.launchpad.net/wubi/+bug/195905)). In this case press cancel, at the desktop open a terminal (Applications > Accessories > Terminal) and run 

[QUOTE]ubiquity --automatic[/QUOTE]

[COLOR="DarkRed"]hmmmm.. so i open the terminal and type ubiquity --automatic  ?
and it will solve the problem?
sry, because i don't understand linux command prompt language

EDIT: 00ps.. now after a few times i reboot the computer, and when i click quit, it did not direct me to the LiveCD user anymore, instead, the screen just blanked.. what happened?[/COLOR]

---

