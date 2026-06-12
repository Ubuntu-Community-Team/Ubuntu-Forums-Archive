---
title: "Please help I don't want to re-install gutsy again"
date: 2008-03-21
forum: General Help
---

### Post by jvh100 on 2008-03-21
I just installed a fresh gutsy on my laptop and I am getting errors when I click anything in add/remove. It just says packages are not installable. I think this is due to the fact that I didn't have an internet connection during my install and I got a message saying that :
> 
AbiWord Word Processor cannot be installed on your computer type (i386)
?
Either the application requires special hardware features or the vendor decided to not support your computer type.

I have previously installed ubuntu on this computer with the same problem and had to do another complete install when I got this message because things were just goofy. What is wrong? during th install I got a message saying some security things couldnt be updated. I try running update manager but it just says that my system is up to date. I DONT WANT TO INSTALL AGAIN this is just a pain.. how can I run an update to get the security stuff I need so I can install stuff off the medibuntu rep to get this computer actually functional. Yeah Im new to linux and all of this is extremely frustrating to me as this is the OS im stuck with and the only thing I do in terminal is sudo stuff and use apt-get.. other than that I am COMPLETELY illiterate. 

This is a message I get in synaptic when I try to install something : 

> acroread:
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
 Depends: libstdc++5  but it is not installable


anyways Im thankful this forum is here but it does me no good if one of those experienced linux users can help me ... never happened before. 
anyways here goes before I decide to put the live cd back in and do another fresh install (read: pain in the ***) 

thanks for the help if anyone can

---

### Post by ibuclaw on 2008-03-21
Enter ```
 lspci 
``` in the terminal, then copy & paste the output in your next message.

Gives me a good look at what machine your using. Then I'll do my best to interpret what's going on and why.

Regards
Iain

---

### Post by bwang on 2008-03-21
Post the contents of /etc/apt/sources.list

---

### Post by forrestcupp on 2008-03-21
It looks like you need to enable your Universe and Multiverse repos to get libstdc++5.

Open Synaptic and click Settings->Repositories.  In the front tab called 'Ubuntu Software' make sure all of the boxes are checked *except* the CD box.  Then close the Repositories window and click the 'Reload' button and try again.  It should work after you do that.

---

### Post by jvh100 on 2008-03-21
thanks for the help, I believe it was the fact that I didn't have the repos checked. for another question, I'm new to these forums as well, how do I formally thank you guys for the help?

---

### Post by Oldsoldier2003 on 2008-03-21
> **jvh100 said:**
> thanks for the help, I believe it was the fact that I didn't have the repos checked. for another question, I'm new to these forums as well, how do I formally thank you guys for the help?

click the little star in the bottom right corner of their post in order to give a thank you. (its right next to the "quote" button.)

---

