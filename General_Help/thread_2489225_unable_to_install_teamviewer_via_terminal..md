---
title: "unable to install teamviewer via terminal."
date: 2023-07-22
forum: General Help
---

### Post by josephchrzempiec on 2023-07-22
hello, I'm learning linux more and more however I'm having a hard time installing teamviewer within terminal. I really need help. I downloaded the deb file from the site. I went into my downloads folder on the terminal and put the command sudo apt install ./teamviewer_amd64.debI got these errors in return.

jjc@jjc-HP-Pavilion-Desktop-590-p0xxx:~/Downloads$ sudo apt install ./teamviewer_amd64.deb
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 anydesk : Depends: libgtkglext1 but it is not installed
 mongodb-compass : Depends: libgconf-2-4 but it is not installed or
                            libgconf2-4 but it is not installable
                   Depends: libgconf-2-4 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

I'm unsure what to do next I tried googling got mixed results I haved tried a couple of things and no luck. Can someone please help me to fix this?

Joseph

---

### Post by TheFu on 2023-07-22
Would you be interested in alternative solutions that don't depend on some 3rd party that you probably aren't paying, but still trusting?

Linux admins use ssh to manage servers around the world.
If I'm outside my home and need a remote desktop, say the place I am in the world isn't to be trusted, so having zero data with me is a priority, then I'd use x2go.
x2go works within the same LAN, but remote X11 over ssh tunnels is seamless, easier, and provides an integrated view with my current desktop, so this is what I use 99% of the time at home.  In fact, I'm using it for this browser window, which is running on a different system, just being displayed onto the system I happen to be sitting behind at this instance.

You'll note that pretty much all of these use ssh, since x2go is based on the NX protocol which leverages ssh for network and system authentication.  ssh is secure enough, if you use ssh-keys for authentication, to be used over the internet from untrustworthy locations.

Anyway, thought I'd throw out the options that don't require trusting some 3rd party.

---

### Post by josephchrzempiec on 2023-08-05
Hello sorry for the late update. I never got TeamViewer installed. I did manage to get realvnc server setup and I&#8217;m now able to remote desktop.

joseph

---

### Post by TheFu on 2023-08-05
> **josephchrzempiec said:**
> Hello sorry for the late update. I never got TeamViewer installed. I did manage to get realvnc server setup and I’m now able to remote desktop.

joseph

I hope you are using an ssh tunnel to connect to VNC.  None of the VNC-based tools are secure.
[https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/](https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/) is a guide.  Be careful out there.

---

