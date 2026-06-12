---
title: "acroread ssl error"
date: 2015-09-22
forum: General Help
---

### Post by nishantpa2 on 2015-09-22
Hi, everyone who can see this, I am new to Ubuntu, but I manage to work around. My work involves to fill forms for the candidates who want driving licence . The web site for this is : [www.sarathi.nic.in]("http://www.sarathi.nic.in")  When I open to fill form in Ubuntu 15.04 using built in Fire Fox and Adobe reader 9.5.5-1 Debian package, Installed . The box appear say ssl error please install certificate. I choose to install the certificate using second method which is as follows : acroread -installCertificate sarathi.nic.in:8443 , every thing went good then prompt me to install certificate I chose yes , terminal said the certificate successfully installed . I reboot and start , but the same error , I want to add that when I visit some other website that have some PDF file , can easily displayed pdf in browser no problem with then but when I tried the above website problem persist . I have Googling a lot so i can find similar problem but every problem seems different solution as they have slightly different problem I came to know that this problem is exist from adobe 8.0 . Is there any solution for this or has any work around for this? I can not use Evince because the website clearly indicate the form can only be fill with Adobe 9.0 and onward. So if any one want to help ,please do it, thanks in advance.

---

### Post by kc1di on 2015-09-22
Hello nishantpa2 and Welcome to Ubuntu,

This is a real problem - unfortunately adobe stopped supporting linux at version 8.xx   but their is a 9.5.5 package available from this sight.
I have not tried it myself , but worth a try.  

[http://www.omgubuntu.co.uk/2014/10/adobe-reader-linux-download-pulled-website]("http://www.omgubuntu.co.uk/2014/10/adobe-reader-linux-download-pulled-website")

---

### Post by nishantpa2 on 2015-09-23
hi. Kc1di, Thanks for your pointing out, but I have already use 9.5.5 tar package with slacko puppy with the same disappointing result. I don't know what to do now should I stick to Windows 7 for only that I have to do some work that requires Adobe Reader and use Ubuntu for some other work ? As I want to totally move from Windows to Ubuntu but Alas! my work include that form to be filled every day in quantity , if it is for time being I defiantly use windows , but every time I need to fill that form I switch to Ubuntu to Windows this is discouraging isn't it ? Can any one have solution or try the same situation , I mean to install Adobe in 15.04 and go to web site and try to fill that form with Adobe being the default , and have install the certificate correctly , then tell me about it. If this could be possible I will be very glad that finally I have find the solution . There must be some one who has this solution for acroread ssl error . Can any one help me ?

---

### Post by kc1di on 2015-09-23
There is another option: You could run windows 7 in a virtual Machine on your Ubuntu Machine. 
Virtual Box is in the repositories and can easily be install, they you install windows 7 in that and it's like opening anyother program in ubuntu no need to reboot each time. 

here are a couple pages that may be of help to you:

[http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html]("http://www.junauza.com/2010/01/how-to-install-windows-7-on-ubuntu.html") Old but step by step. 

[http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box]("http://askubuntu.com/questions/187424/install-windows-7-through-virtual-box")

Good Luck ;)

---

### Post by nishantpa2 on 2015-09-24
HI,kc1di, Thanks for your post, I came across the very same idea but would not it be killing the joy of using Ubuntu ? I totally shift from Windows to Linux , but this problem would not let me do that . People prefer Linux because it is alternative of Windows , but people like me can not utilities its full potential this is a bit disappointing isn't, it ? Well any way I keep searching for my problem and find some solution , thanks once again.

---

### Post by kc1di on 2015-09-25
Yes it's a shame that Adobe stopped supporting Linux.  But that was their choice.  There will be and are alternatives to their software. But not every webpage understands that yet. so guess your stuck using windows for that function for now.

---

