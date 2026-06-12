---
title: "Ubuntu server login"
date: 2012-10-17
forum: General Help
---

### Post by Naeemdal on 2012-10-17
I have download and burnt iso to my USB and installed ubuntu-12.04.1-server-amd64 in my machines. Installation went successfully when I hit Ubuntu from the boot it ask for Login and password, login successfully but it is stuck on:

mypc@MIS-IRD:^$

Can someone please tell me how to login ubuntu? I am just stuck here.

---

### Post by drmrgd on 2012-10-17
What you typed (assuming you didn't make any typos) looks like you've successfully logged in and are now seeing the command prompt.  What is the system not doing that you expected it to do?

---

### Post by Naeemdal on 2012-10-17
I entered user id and password then a login msg is appearing and in the bottom i am seeing this

mypc@MIS-IRD:^$

I am logged in but i dont know how to see my desktop? I just want to see the GUI desktop. Istead of this msg mypc@MIS-IRD:^$ after login

---

### Post by Naeemdal on 2012-10-17
I am just seeing console however i logged in with user id and password and this is appearing after login mypc@MIS-IRD:^$

how can i proceed further step to view the gui desktop?

---

### Post by steeldriver on 2012-10-17
You installed ubuntu-12.04.1-**server**-amd64 - there **is** no GUI desktop

If you want a GUI then your easiest option at this point is probably to go back and install the regular desktop iso - else you will need to add the whole ubuntu-desktop package + dependencies on top of what you have

---

### Post by Naeemdal on 2012-10-17
Thank you so much for the kind help, I am windows server user. I have decided to install windows server along with cloud computing, we are having small office. The main purpose of server will be controlling internet traffic and file sharing in real time as cloud computing do. Can you please help me which server package should i download for the gui? I am totally newbie on ubuntu. I just googled and figure out that ubuntu is good one for server along with gui. Kindly help me .... 

Thanks in advance.

---

### Post by drmrgd on 2012-10-17
If you prefer the GUI, then as Steeldriver says, you should install Ubuntu 12.04 Desktop version.  You'll might have to add some extra packages to it, as I'm not exactly sure what's in server that's not in Desktop.  It's really easy to add packages if you need, though.  

If you don't mind not having a GUI (which I think is nice as it reduces OS bulk and speeds things up), then stick with what you have.

---

### Post by PowerBarry43 on 2012-10-17
Hi

as has already been mentioned Ubuntu server comes without any  GUI whatsoever in order to boost performance but you can install unity  by running

```
sudo apt-get install ubuntu-desktop
startx
```

or you could just install the desktop version of ubuntu which will come with a GUI

Hope this helps!

Barry

---

### Post by steeldriver on 2012-10-17
IS there still a way for the OP to install the basic GUI without all the additional desktop components? something like

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```maybe?

---

### Post by PowerBarry43 on 2012-10-17
If you want a basic desktop I'd recommend trying lxde, it's very lightweight but if you only need basic functionality it should do the job.

```
sudo apt-get install lubuntu-desktop
```

Barry

---

