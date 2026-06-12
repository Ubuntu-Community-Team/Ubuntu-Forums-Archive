---
title: "VNC access breaks with 12.04"
date: 2012-10-22
forum: General Help
---

### Post by rh10023 on 2012-10-22
I just completed an upgrade from Ubuntu 10.04 LTS to Ubuntu 12.04 LTS.  All of my services are pretty much broken and I need to go in and fix all of them.  But first to tackle is my VNC access.  I had resumable sessions for use with Chicken of the VNC, so that I can do whatever admin work anywhere in my home.  (My linux server is located in the basement, utility room.)  Everytime I bring up Chicken of the VNC up and connect to my Ubuntu box, I just get a grey screen, not the Gnome desktop that I used to get.  I have a suspicion that my Gnome sessions are all messed up and probably missing a dot file configuration but I cannot figure out what is missing.  I found a 12.04 VNC setup on the web, but I am still not able to get things working.  Anyone have a clear step by step guide on getting VNC and 12.04 working again?

---

### Post by Cheesehead on 2012-10-22
Well, my VNC has upgraded perfectly for the last four or five years, so it may or may not be a VNC upgrade issue.

Can you ssh into the server? Does the server respond to ssh's -X command? Are the Gnome processes working? Do those processes respond to commands? (For example, if you use SSH command-line to start Firefox, does it start? does it crash?) Is a gdm/lightdm process live? If you kill gdm (or lightdm), does the session restart?


If you really think it's a Gnome issue, looking for a missing file can eat a lot of time. If your Gnome is not heavily customized, it may be worth simply using apt-get's --reinstall feature.

---

### Post by steeldriver on 2012-10-23
Which ~/.vnc/xstartup file did you find on the web? this one worked for me

[https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)

It is important to specify the 2d session I think - compiz still doesn't play nice with vnc afaik

```
gnome-session --session=ubuntu-2d &
```

---

### Post by rh10023 on 2012-10-25
I probably should clarify.  I was using ubuntu-desktop through a resumable vnc session on 10.04 LTS.  Now I only get an X-Window Grey Screen.  I tried the code in xstartup that was in the .vnc directory.  But I still get the X-Window Grey Screen.  Any suggestions would appreciated.  I tried to run a sudo apt-get --reinstall ubuntu-desktop.  I kept getting some weird "unrecognized command ubuntu-desktop" as a result.

ubuntu desktop is working on the computer.  I just can't get it to work through the vnc resumable session.

---

### Post by rh10023 on 2012-10-25
As I search the internet for a solution for my problem.  I realize that most of the solutions are either using vncserver, vino.  I have been using Xvnc4 using some forum threads on how to setup resumable sessions.  So I believe that my resumable sessions setup is still working.  I just need to figure out how to get ubuntu desktop to appear instead of a Grey X-Window.  Some how the ubuntu desktop works differently in 12.04?

---

