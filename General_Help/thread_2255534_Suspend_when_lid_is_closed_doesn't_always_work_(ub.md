---
title: "Suspend when lid is closed doesn't always work (ubuntu 14.10, lenovo ideapad y410p)"
date: 2014-12-05
forum: General Help
---

### Post by I.Bun.Tu on 2014-12-05
I have a Lenovo Ideapad y410p running Ubuntu 14.10. Everything seems to work pretty well. One issue I've had since I got the laptop (from Ubuntu 13.10 to 14.04 and still in 14.10 the problem has always persisted exactly the same) is that sometimes it doesn't suspend when I close the lid. I don't know how to recreate the issue, just sometimes I go to open my laptop after it has been closed for a few hours and it is completely dead. I would normally leave it with more than 50% battery and only for 4-8 hours. 

When it successfully suspends I've left it at less than 20% battery for more than 24 hours and not had it die. Whenever I close the lid and open the laptop back up a couple minutes later, just to check if it suspended, it always seems to wake from suspend. I've never gone to open the lid and seen it still on my desktop, it always goes to the log in screen after the lid has been closed and I open it back up again... maybe once or twice it was still on the desktop and I witnessed it fail to suspend, There were no errors from what I recall.

I'm not really sure how to recreate the problem or troubleshoot this issue. I've tried searching online and it seems that quite a number of people have this issue on different laptops. I have a Dell Inspiron 15R that does not have this issue as far as I can see. I've left it unplugged with the lid closed for days, even weeks and opened it up right back to the log in screen with almost all of the batter still there. Both the Dell and Lenovo use the same versions of Ubuntu. Of the people having this issue, some have fixed it and all in various different ways. I'm going to try one at a time and report back on my progress, but without being able to definitively re-create the issue it will be difficult to discern when/if a solution has worked.

Any help anyone can offer will be appreciated.

First attempted sol'n: removing the crunch (#) sign in front of HandleLidSwitch=suspend in /etc/systemd/logind.conf

I will let you guys know if this works... which I probably won't know for certain until my battery doesn't die for a few days/weeks; sooner if it doesn't. Any help or suggestions anyone can offer is still greatly appreciated. Thanks for reading!

---

### Post by I.Bun.Tu on 2014-12-18
I am not sure if this worked for me, but I have since discovered that the laptop dies or shuts down even when it still has battery.

So the laptop will have a good amount of battery life and I close the lid to suspend the laptop.

I open my laptop and it is off (or, I am not 100% sure of this, because the back light on the keyboard flashes like it is going to resume from suspend and the whole thing dies). I have to push the power button to get a response from the computer and it boots fresh. 

When the computer boots and logs in, none have my programs have been saved as in hibernation (I have hibernation enabled, but have not yet configured the computer to hibernate automatically after being suspended for an hour, this is something I have intended to do and found instructions for, but have just not gotten around to yet). It has 2-3 apport errors, which I send to Canonical, but when I check the details it says that apportcheckresume is the program that has failed. I get this error all the time and not sure what it means. As I am writing this, I am starting to theorize that the laptop failed to resume and I see people talking about this online all the time, so I am going to do some research.

I was particularly confused by the apportcheckresume error because I used to see it all the time on different laptops and I have never had an issue resuming. I am starting to wonder if this is an error during resume but in the past has never been a fatal enough error to cause a system shut down. I had always assumed it was an error with the error reporting service as I understood that to be called apport.

Any information people can provide will be helpful, in terms of confirming this to be a suspend resume issue or, if not, how to troubleshoot further to attempt to determine the nature of the issue. I will post back if I am able to resolve the issue through some of the suspend resume research.

---

### Post by Bucky Ball on 2014-12-18
How have you got it setup in Lightlocker, if you are using it?

---

