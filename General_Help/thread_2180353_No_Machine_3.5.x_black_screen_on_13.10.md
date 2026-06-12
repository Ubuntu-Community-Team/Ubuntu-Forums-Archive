---
title: "No Machine 3.5.x black screen on 13.10"
date: 2013-10-12
forum: General Help
---

### Post by bpowell2005 on 2013-10-12
Hello Gang,

I recently upgraded my desktop computer to 13.10...seemed to go well.

I installed No Machine as that has worked great for me...installed the latest (NO Machine 4.xxx) and it worked, but it was not what I was looking for...it remoted me into the open session, I wanted a new session started, so I could work on the computer while other family members were on it.

So, removed 4.xxx and reinstalled 3.5.xxx ... now, no-machine is just a black screen.

If I no-machine in and try to start a gnome session manually, I get the following:

gnome-session-is-accelerated: No composite extension.
gnome-session-check-accelerated: Helper exited with code 256
WARNING **: software acceleration check failed: Chile Process exited with code 1
CRITICAL **: We failed, but the fail whale is dead. Sorry...

I've tried the following:

/usr/bin/gnome-session --session=gnome-2d
/usr/bin/gnome-session --session=gnome-fallback
/usr/bin/gnome-session --session=gnome-flashback

Help! I really miss this functionality...I don't need Unity affects on the remote connection, I just need to be able to remote in and work on the machine without interrupting others that are physically on the machine.

Thanks!

---

### Post by QIII on 2013-10-12
Hello.  I'm on my cell right now so I can't check, but I believe NoMachine creates a folder NX (different from the .nx folder) in your home directory.

It could be that there are config files in there that have remnants of both versions.  You might try uninstalling the NX client and renaming the NX folder before reinstalling.  Just make sure you don't delete your key.

Let me know if that works.

---

### Post by bpowell2005 on 2013-10-12
Hello.

Yes, I did uninstall the 4.xx and then I went to /etc/NX and deleted everything in there....then installed 3.5.xx. Thanks for the suggestion though!

---

### Post by QIII on 2013-10-12
There should also be a folder in your home directory, too.  Did you check that one?

---

### Post by Frogs Hair on 2013-10-12
***Moved To Ubuntu +1***

---

### Post by bpowell2005 on 2013-10-12
Yeah...removed the /etc/NX and the ~/.nx directories and reinstalled. No joy.

---

### Post by QIII on 2013-10-12
:)

There should also be a ~/NX

---

### Post by bpowell2005 on 2013-10-12
Nope, no ~/NX folder...just /etc/NX and ~/.nx

---

### Post by QIII on 2013-10-12
Interesting.

I just did a clean install of Saucy again a couple of days ago and installed NoMachine 3.5 to remote to my Precise machine and it works just fine.  I'm pretty sure  /NX is in my home, but I'll have to check later.

---

### Post by bpowell2005 on 2013-10-12
So you're using NoMachine to remote FROM Saucy to another machine? I'm trying to remote INTO Saucy with NoMachine.

---

### Post by QIII on 2013-10-12
Well....   That could make a difference...

---

### Post by CrustyChris on 2013-10-19
I get the same thing as OP.
logging in from Windows 7 PC to Saucy PC via nomachine.

however, I also get the following error pop up as Im trying to log in:
> Xsession: unable to launch "gnome-session-fallback" X session --- 
"gnome-session-fallback" not found; falling back to default session.

I have gnome-session-fallback installed:
> $ sudo apt-get install gnome-session-fallback
Reading package lists... Done
Building dependency tree
Reading state information... Done
gnome-session-fallback is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

---

### Post by cariboo on 2013-10-19
Seeing as Saucy has been released, moved to General Help.

---

### Post by bpowell2005 on 2013-10-20
FYI: Still an open issue...anybody else seeing this?

---

### Post by bpowell2005 on 2013-10-20
CrustyChris:

Keep this thread updated if you find a solution...I'm still stuck.

---

### Post by CrustyChris on 2013-10-21
I have found a work-around that at least lets me log in using nomachine:

You should be able to install and use xfce (although I actually installed xfce4 and gdm, but i dont think gdm is required):
> sudo apt-get install xfce4

Then in the nomachine client on Windows (or whatever) configure the desktop setting from "gnome" to "custom" and set it to run xfce when you log in:
> Desktop: Custom
Run the following command: /usr/bin/startxfce4
Options: New virtual desktop

I have issues when I try to log out of xfce in that the screen goes black but nomachine window wont actually close - I am currently just terminating the session at this point.

I also tried installing gnome3 - I can log into it locally perfectly fine. But it broke my desktop in unity (menus etc showed up, but desktop with all the icons on it wouldnt show up at all - just black) so Ive removed it.

Interestingly theres reports of cinnamon breaking unity:
[http://askubuntu.com/questions/358988/problems-with-ubuntu-after-installing-cinnamon-unity-broken]("http://askubuntu.com/questions/358988/problems-with-ubuntu-after-installing-cinnamon-unity-broken")

So Im not really sure where to go from here. I can prove its not an issue with the nomachine server (works with xfce). Nomachine is known to not work with unity/gnome3/compositing WMs [http://www.nomachine.com/AR0500591]("http://www.nomachine.com/AR0500591") so you have to use something like xfce or cinnamon. As for why cinnamon doesnt load/start ... I not know.

---

### Post by sicco1 on 2013-10-30
I have the same problem. The procedure by CrustyChris using xfce4 worked except for one extra addition. In the nomachine client (on windows) I had to go to "Configure > Advanced" and enable "Disable DirectDraw for screen rendering", otherwise I would just see a black screen.

---

### Post by cu_ on 2013-11-27
Same problem occurs with x2go client also.  Google search tells me that it has to do with some change made to how xstartup is done and change of name of gnome-session-fallback to gnome-session-flashback.  Oneway I overcame this problem on x2go is to use specific application rather than the desktop.

---

