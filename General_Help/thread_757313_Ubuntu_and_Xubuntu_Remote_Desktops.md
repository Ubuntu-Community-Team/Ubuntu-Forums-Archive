---
title: "Ubuntu and Xubuntu Remote Desktops"
date: 2008-04-16
forum: General Help
---

### Post by dugonline on 2008-04-16
Ok, before I get into my question, if I may be allowed to go over my very short history with Ubuntu and Linux.  If you would rather skip all that, just pass over the next paragraph.

In January I downloaded the Ubuntu Live CD.  I threw it in and was impressed, intrigued and had to see more.  So I set up for the dual boot.  I couldn't have been any happier about that decision.  I have been a fan of Open Source for a long time and over the years have been growing sicker and sicker of Microsoft and their BS tactics.   I have in the last year become money minded which is good cause I don't make a lot of money and the current economy certainly calls for it.  So having heard more about Open Source OS's (I like to call them and OS OS's) I wanted to look into them.  This lead me here.  The more I played with Ubuntu the more I was in love.  The learning curve was simple and finding support didn't require a log in, only a google search and I had an answer in minutes.  I had made the decision to get more comfortable and start finding alternative software for the things I still needed windows fore.  I set a deadline to be Microsoft free by June of 08.  This past March my computer died.  I think it might have been a power spike, but I can't be sure.  I lost my mother board, my AGP Vid Card and a Hard Drive.  Luckily for me, I started fresh with my dual boot and had recently backed my PC up.  So not much was lost and none of it was important.  I am back up and running again by mix and matching parts from a used PC I purchased.  I was ready to throw Ubuntu on but with just over 2 weeks until the next release I decided to wait for that instead.  I couldn't wait for the next release to play with it again so I converted my file server over to Ubuntu.  Again, I couldn't believe how easy it was to make it a network device for files and such.  Now onto the question. . . .


My file Server is a 1ghz box with 512 RAM.  It has onboard video, which suits its purpose quite well.  I have been reading more and more about Ubuntu and Linux lately and that lead to reading about Xubuntu.  I understand the basic differences, and it sounds like a better fit for the File PC.  I would like to be rid of the monitor/keyboard/mouse that accompany it, so I am preparing for Remote Desktop access to the File PC, but when I get Ubuntu back on this machine (8 more days) I was wondering how compatible  will Ubuntu and Xubuntu be for remote desktop access?  Or as I learn more about terminal commands, will it work with remote access period?  I am sure a simple search could find an answer for me, but seeing as I have yet to post in the forums I thought this would be a great ice breaker.

So. . . .  any and all help would be greatly appreciated

I look forward to the new experiences that still await me and I can't wait to be able to read through the forums and help others who are making the switch!

---

### Post by stephan0h on 2008-04-17
don't worry, there shouldn't be any compatibility issues. x-windows on both sides - i don't see a problem. even accessing a windows-box remotely would be no problem.

good luck!
stephan

---

### Post by bodhi.zazen on 2008-04-17
You can manage the box remotely with ssh

[uwiki]SSHHowto[/uwiki]
[uwiki]AdvancedOpenSSH[/uwiki]

ssh is command line only. If you want X you can 

ssh -X

or use VNC.

[uwiki]VNCOverSSH[/uwiki]

If you are only using the box as a file server, go for a server install + Samba.

[uwiki]SettingUpSamba[/uwiki]

---

