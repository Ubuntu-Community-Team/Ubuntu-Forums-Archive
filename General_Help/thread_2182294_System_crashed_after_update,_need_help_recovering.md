---
title: "System crashed after update, need help recovering"
date: 2013-10-20
forum: General Help
---

### Post by Xenoverse on 2013-10-20
Hi all, I've got quite a problem on my hands and no idea how to fix it. I'm running 64-bit dual-boot 13.04, and last night I decided I'd update to 13.10. I started the update before I went to sleep (bad idea I know) and figured it'd be fine. I totally forgot that I had my system set to suspend after 30 minutes and that I'd had an issue with it getting locked up after waking from suspend. So when I came back to it in the morning I found that the update had progressed about a third of the way through downloading the new packages before it went to sleep and that my desktop had locked up again, so I had to hard reboot it. Once it restarted it told me to do a partial upgrade in order to recover/fix anything that needed it, so I did and it did its thing just fine and I restarted it from the system menu. Now what happens is I choose Ubuntu from the start-up menu, it loads for a second and then comes up with a window that says something like "System is running in low graphics mode, cannot properly detect hardware, please configure manually", I click OK on that window and it asks me whether I want to run in low graphics, reconfigure, troubleshoot, or exit to login console. The first and last options do the same thing from what I can tell, it says to wait while the display resets, then it goes to a black screen where I can type and that's it, and because I don't know any console commands off the top of my head I have to hard reboot. I tried the reconfigure option, but all that does is pop up with the same window I had just clicked OK on. I looked at troubleshooting but it seemed way over my head, the options for that being to review different system logs and such.

What should I do from here? I would really like to recover the system as it was before but if I have to wipe Ubuntu and reinstall I will. Any help is very much appreciated.

---

### Post by crazymonkey05 on 2013-10-20
+1 with this.

same problem here.

---

### Post by Praveen_Thankappan on 2013-10-21
Same problem for me as well.

---

### Post by mörgæs on 2013-10-21
An upgrade is about the most dangerous one can do in Buntu and I don't recommend it. Always a fresh install - more in the link in my signature.

Chances for a recovery are small, but if you get to a command line please run 
```
sudo apt-get update 
sudo apt-get upgrade
```

and post the results in CODE tags.

---

### Post by Xenoverse on 2013-10-21
Thanks for the replies. I decided to remove Ubuntu completely and attempt to recover from backup, will post results soon.

---

### Post by Praveen_Thankappan on 2013-10-23
Remove the existing installations and installed Kubunutu 13.10. It worked ..

---

### Post by Praveen_Thankappan on 2013-10-24
Was too addicted to ubuntu. freshly installed ubuntu 13.10 again and now things are fine. 
Had to install and re-configure things, but now it is happy end to the story

---

