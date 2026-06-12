---
title: "I think I killed Apt"
date: 2006-12-29
forum: General Help
---

### Post by derrick1985 on 2006-12-29
Hi,

I'm having a huge problem with my system right now. I had vmware-server installed for a while, following one of the guides on the forum. Well, I wanted to go back just to the player to try and get 3D to work, and when I installed it, it would not complete the install unless it could configure the ethernet. It couldn't configure it since vmware-server was still installed. So, frantically, I remove the vmware-server directory and tried reinstalling vmware-player from the repos. That was a no go, started complaining about dpkg --configure -a and even that never got it working. So, to try and fix that I completely deleted a directory (forget which because now I can't even open up Konsole!) and tried running synaptic again and complained about libapt missing. How can I fix this?

---

### Post by bapoumba on 2006-12-29
Well, could you post the output to **cat /etc/apt/sources.list** and either ```
sudo aptitude update
``` or ```
sudo apt-get update
```.

---

### Post by derrick1985 on 2006-12-29
Well, it got worse. 

Since nothing now worked (could not even check my email through kmail, pop errors) I rebooted and went right to a text prompt. I just ended up reinstalling since everything was in a separate /home partition, it was no big deal. BUT, just to answer your post bapoumba, I could not even do an apt-get update as it gave a libapt error. So, it was meaning less. I just broke my system bit time.

---

### Post by bapoumba on 2006-12-29
Okay.
The full error message might have been useful. In addition, when you get stuck with no Xserver running, for whatever reason, there are applications working in text mode that can help you get some informations and help :
[http://bapoumba.free.fr/?p=39]("http://bapoumba.free.fr/?p=39")
I plan to develop this soon, with tips on each one of them ;)

---

