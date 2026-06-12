---
title: "E: couldn`t find package"
date: 2006-11-16
forum: General Help
---

### Post by jessewryan on 2006-11-16
Hey sorry everyone for posting like crazy but im having ALOT of difficulty with this. Im looking to get my dialup modem up and running. I am on my other computer right now with my UBUNTU laptop infront of me. I am trying to install my modem and so far I have downloaded: sl-modem-daemon to my jump drive.

I then opened the terminal and typed:
sudo apt-get install sl-modem-daemon 
which ended up saying
Reading package lists... Done.
Building dependency tree... Done.
E: Couldn`t find package sl-modem-daemon

Im really struggling here guys ! If someone can help it would be greatly appreciated. Thanks in advance you all are awsome.

---

### Post by WalmartSniperLX on 2006-11-16
Do you have all the repositories open?

(sorry It's best to start with the basic/noob questions :P)

If not enable them in Software Properties by checking all the boxes

---

### Post by jessewryan on 2006-11-16
Im not too sure how to open all the repositories. haha. Its taken me at least 4 straight hours to find out where im at now. LOL. Can u give me a clue as to where I go or how I open all the repositories ? Thanks for the reply though. At least it pointed me in the right direction.

---

### Post by reclusivemonkey on 2006-11-17
> **jessewryan said:**
> Hey sorry everyone for posting like crazy but im having ALOT of difficulty with this. Im looking to get my dialup modem up and running. I am on my other computer right now with my UBUNTU laptop infront of me. I am trying to install my modem and so far I have downloaded: sl-modem-daemon to my jump drive.

I then opened the terminal and typed:
sudo apt-get install sl-modem-daemon 
which ended up saying
Reading package lists... Done.
Building dependency tree... Done.
E: Couldn`t find package sl-modem-daemon

Im really struggling here guys ! If someone can help it would be greatly appreciated. Thanks in advance you all are awsome.

Using apt-get tries to connect to the repos online. As I understand from your post, you are not connected yet. If you have downloaded a .deb to your laptop, just open the folder where you have saved and double click on it. You should get up a little window where you can install it from. If it mentions any dependencies you will have to copy those over too.

---

