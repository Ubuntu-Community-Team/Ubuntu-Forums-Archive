---
title: "Restart to update?"
date: 2021-07-16
forum: General Help
---

### Post by monkeybrain20122 on 2021-07-16
In Ubuntu 21.04 if update through the gnome software store by clicking its popup it restarts your computer just like Windows update even for small updates like Firefox. I disabled automatic update and automatic update notification from the gnome software store and just set my preferences in good old Software&updates and no more annoying restarting. But not sure what happens to snap apps (I don't have any) This is very annoying behaviour for new users, seems like yet another brilliant idea from the gnome crew.

---

### Post by TheFu on 2021-07-17
Don't allow automatic patching and use the CLI to patch if you want control.  I patch once a week, Saturday mornings. Don't want any updates at any other time, unless I manually install them.  

The only way I've found to prevent snap package updates is to blacklist the snap servers on the network so that snapd can't auto-update whenever it feels like it.

Gnome has been dumbing down their software for a long time.

---

### Post by monkeybrain20122 on 2021-07-21
So it asks me to restart in order to upgrade libruby today. Ubuntu 21.04, no such idiocy in 20.04.

                                                                                                                                           > Don't allow automatic patching and use the CLI to patch if you  want control.  I patch once a week, Saturday mornings. Don't want any  updates at any other time, unless I manually install them.  

Yes, that is what I usually do but this is really bad a 'feature' for new users who can't tell the difference between apt, packagekit, synaptic and the gnome-software-store. They will have their computers restart a few times a day to 'update' just like Windows.

---

### Post by TheFu on 2021-07-21
I think snaps should be opt-in, not the default.  For many users, it can be a good thing.
I haven't used a GUI for package management in many years, though I have used a TUI - aptitude - in the last 10 yrs. Aptitude has a smarter dependency selection capability, IMHO, but not enough to use it more than about 1% of the time.

---

### Post by monkeybrain20122 on 2021-07-21
> **TheFu said:**
> I think snaps should be opt-in, not the default.  For many users, it can be a good thing.


There is no snap, it has been purged. This is a gnome-software store (packagekit) thing, it exhibits the same behaviour in Fedora 34 where you won't find any snap. In fact I first noticed this when I was playing with a Fedora VM. So I made a Ubuntu 21.04 VM too to see if it happens there as well.

---

### Post by Dennis N on 2021-07-23
In Ubuntu 21.04, there should be a checkbox you can uncheck in the "Power Off" confirmation and it will bypass the updates. I don't know if "restart" will have the same option. But if it does, you can do them your way the next session.

Edit: It does the same with restart (attached).
Using Gnome Software to update, it did show a "restart and update" button, but I just closed the window. 
Since they weren't finished, I got the "update and restart" when I restarted (or the other one if shutting down). Then next session, I finished them up with software updater. So no need to interrupt the session with a restart when prompted by Software.
I keep Gnome Software since it notifies me of Flatpak updates. Nothing else does that.

---

### Post by monkeybrain20122 on 2021-07-23
> **Dennis N said:**
> In Ubuntu 21.04, there should be a checkbox you can uncheck in the "Power Off" confirmation and it will bypass the updates. I don't know if "restart" will have the same option. But if it does, you can do them your way the next session.

Edit: It does the same with restart (attached).
Using Gnome Software to update, it did show a "restart and update" button, but I just closed the window. 
Since they weren't finished, I got the "update and restart" when I restarted (or the other one if shutting down). Then next session, I finished them up with software updater. So no need to interrupt the session with a restart when prompted by Software.
I keep Gnome Software since it notifies me of Flatpak updates. Nothing else does that.

I know, but new users would not know these options. I think Windows (only pro and above) has some options to delay or schedule updates too but most people don't know it, but then I can be wrong since I haven't touched Windows since Win7. At least gnome asks you first unlike MS but let's wait for gnome 5.

---

### Post by ajgreeny on 2021-07-23
If you use terminal commands to update do you still get the automatic reboot?

My only instance of a gnome system is a VM of 21.10 which is running fine but I use it only to check progress and have a tendency to shutdown very quickly after using it.
However, always using terminal to update the system has so far never shown me any indication that I need to reboot, and an automatic reboot has definitely never happened.

---

### Post by monkeybrain20122 on 2021-07-23
> **ajgreeny said:**
> If you use terminal commands to update do you still get the automatic reboot?

My only instance of a gnome system is a VM of 21.10 which is running fine but I use it only to check progress and have a tendency to shutdown very quickly after using it.
However, always using terminal to update the system has so far never shown me any indication that I need to reboot, and an automatic reboot has definitely never happened.

No, that is a gnome-software thing. Update never followed by mandatory reboot if you use apt or one of its frontends (synaptic, muon) to update. On Fedora it is same, no mandatory reboot if use dnf or dragora.

But new users are not aware of the other more obscure options, the software store with its default settings are all the new users see.

---

### Post by Dennis N on 2021-07-23
@monkeybrain20122

In practice, I don't use Gnome Software to perform the actual updates. It gives update notifications, but I just ignore those and they go away. Software Updater will autolaunch a short while later with the same set of updates (but apt packages only). I suppose that's what you are doing too. 

Gnome software's Flatpak plugin will automatically update Flatpaks and notify that it did so.

I leave the unattended-upgrades on. I think they are a good thing.

Software Updater is now checking and updating snaps every time it installs updates.

---

### Post by ajgreeny on 2021-07-24
Gnome seems to be moving more and more away from what I think of as one of the big advantages of Linux, choice.  It appears to be moving towards a "this is the way we think it should be done, and there is no way to move away from this".
I have never used Gnome-Software or software-store or any of those means of installing or upgrading in my 16 years of using Ubuntu family OSs so I did not even realise that Gnome-Software was rebooting the system in this manner.

I did use synaptic for a long time but seldom use that any more except when searching for packages as its search function is second to none, and I now always use terminal for updating and upgrading; it is so much quicker and simpler.

---

