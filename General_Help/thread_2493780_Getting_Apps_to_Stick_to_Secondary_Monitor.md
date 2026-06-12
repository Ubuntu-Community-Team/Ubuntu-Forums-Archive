---
title: "Getting Apps to Stick to Secondary Monitor"
date: 2023-12-24
forum: General Help
---

### Post by sdsurfer on 2023-12-24
***Sorry, getting APPS to stick . . . can't edit title. :-\***

MSI B560M Pro-VDH
Intel 17-11700K
64GB T-Force 3200 mhz RAM
Unity 23.10 (yes I know it's not an LTS)
XFX 580RX GPU

**The issue: I have specific apps I want to "stay" on the secondary monitor. On screen lock they move to the first monitor. Is there a reasonable way to keep them on the secondary monitor?**

I've installed 22.04 using the default Gnome shell, issue is observed here as well. Updated to Unity 7.7, issue persists. I know this used to work in 20.04 with the Unity theme, which is no longer an option. In short, this used to work this way, now it doesn't.

I'm going to use the Evolution mail client as an example, that's the main one that is annoying me. :-D

I ***know*** it's "the responsibility" of the app to "remember" it's last screen position. In fact if I close the program, restart the program OR the computer, on re-opening the program Evolution indeed launches on the second monitor. But if the screen locks, on unlocking Evolution has moved back to the primary monitor.

My conclusion is that something is resetting it when it goes into lock mode. Aside, I just recently put the XFX card in, the issue was present before that (even when running on integrated graphics.)

I've fiddled about with settings in both Gnome and Unity as well as Tweaks and dconf editor in both, not seeing anything helpful. Most unity searches lead to the Unity game editor, not the desktop. There is one suggestion of a script that records a "snapshot" of the window positions, I could try that but I don't think I should have to - ***this used to work this way.***


I also searched my system for everything "evolution," found a bunch of config files, the most relevant of which is org.gnome.gschema.xml (also in dconf-editor.) Under org.gnome.evolution.window there are default coordinate values, all set to 0, and in dconf-editor it says "no schema found."

That's all I have folks, any idea what I can do to restore this functionality?

---

### Post by sdsurfer on 2023-12-24
**Additional info:**

I have the secondary monitor attached to HDMI, primary to display port, wondering if that's where it's broken. 

Tried the approach in #4 of[ this 13 year old post]("https://askubuntu.com/questions/9921/dual-monitor-applications-opening-on-wrong-monitor"), shifting the secondary monitor down or up in relation to the primary monitor doesn't work. When I manually lock the screen, it works, if I allow system to go into screen lock, Evolution is still moved to the primary monitor.

---

### Post by MAFoElffen on 2023-12-24
> **sdsurfer said:**
> **Additional info:**

I have the secondary monitor attached to HDMI, primary to display port, wondering if that's where it's broken. 

[COLOR=#ff0000]Tried the approach in #6 of this 13 year old post[/COLOR], shifting the secondary monitor down or up in relation to the primary monitor doesn't work. When I manually lock the screen, it works, if I allow system to go into screen lock, Evolution is still moved to the primary monitor.
You lost me with a lost reference to Post #13 of "something" you never linked to anywhere that I can see(???)

Then you lost me on your DE customizations you said you did... Ubuntu (xorg & wayland) is not gnome-session... Though that can be installed. The Ubuntu DE is Unity-like, but support for hat was Unity ended... So where are you at with that?

IDK from what you described, but... I do i3 as a DE, where I do application pinning... In my app launcher, I pin applications to open in certain workspaces. So to get to those applications, I only have to toggle to that workspace...

Like this:
```

# Workspace Variables
set $ws1 "1: "
#set $ws2 "2: "
set $ws2 "2: "
set $ws3 "3: "
set $ws4 "4: "
...
# Bind App to workspace
# Check class by using xprop command
assign [class="chromium"] $ws2
assign [class="Firefox"] $ws2
assign [class="Atom"] $ws3
assign [class="Foxit Reader"] $ws3
assign [class="Pcmanfm"] $ws4
assign [class="VirtualBox"] $ws5
assign [class="Virt-manager"] $ws5
...

```
And to autostart apps to a workspace doing things like:
```

exec --no-startup-id i3-msg 'workspace 1:Web; exec /usr/bin/firefox'

```
The hooks are there...

EDIT: Is this (the dual monitors) on one workspace or different workspaces? If on one, then single workspace, with it just shifting within that same workspace... Is that what you are describing?

---

### Post by sdsurfer on 2023-12-24
> **MAFoElffen said:**
> You lost me with a lost reference to Post #13 of "something" you never linked to anywhere that I can see(???)

Sorry, fixed, it's the ***4th*** answer in which he offsets the top alignment of the monitors and it fixed it. No matter, didn't work.

> Then you lost me on your DE customizations you said you did...

Really haven't customized anything system wise, just in settings assigned the primary monitor and location of dock/launcher.

> Is this (the dual monitors) on one workspace or different workspaces?

Single workspace. Log in, drag Evolution to second monitor, maximize, all good. Screen locks, it moves Evolution back to the primary monitor. If I exit before lock, when I unlock and re-launch it maintains the second monitor position.

Just trying to regain functionality that used to be there.

**Edit:** it's notable to mention that Unity desktop allows shell selection on login, just like the old days. I've launched the GUI of other shells (Gnome Classic, Wayland, etc.) and the issue remains.

---

### Post by MAFoElffen on 2023-12-24
Your link is from 2010 for Ubuntu 8.04? That was posted before the release of 10.04... Over 13 years ago. That was prior to Unity, and Wayland even being an idea.

"Unity" was abandoned 6 years ago, and end of life for it was back in 2021... [https://www.omgubuntu.co.uk/2017/10/why-did-ubuntu-drop-unity-mark-shuttleworth-explains](https://www.omgubuntu.co.uk/2017/10/why-did-ubuntu-drop-unity-mark-shuttleworth-explains)

I'm having troubles understanding what you are referring to, so I'll let someone else try to figure out what you are trying to do... Or what you are saying. 

Sorry.

---

### Post by sdsurfer on 2023-12-24
> **MAFoElffen said:**
> Your link is from 2010 for Ubuntu 8.04? That was posted before the release of 10.04... Over 13 years ago.

That's what I*** said.*** When you've tried everything you can find, you try other things. Desperate times call for desperate measures (will try ANYTHING LOL)

> "Unity" was abandoned 6 years ago, and end of life for it was back in 2021..

It is an integrated "flavor" of Ubuntu now, it is 22.04.3 underneath but the GUI is "like" the old Unity shell. ***But this isn't about Unity,*** as mentioned above, the problem persists in Gnome, Wayland, and others (for me.)

```
sudo apt install ubuntu-unity-desktop -y
```

> I'm having troubles understanding what you are referring to

1. You have two monitors.

2. A and B

3. A is primary. B is secondary.

4. I launch a program, using Evolution as an example. Drag Evolution to monitor B. Maximize.

5. Screen goes into lock. 

6. Unlock screen, Evolution has been **MOVED** to monitor A. 

I am trying to make it STOP doing that, it never used to, it used to stay where I put it. That is all.

---

### Post by MAFoElffen on 2023-12-24
The application "is" in a single workspace, which the workspace resides in a virtual display (the overall combined display space of the screen), extended across two displays, which each just displays a portion of that virtual displays..

What you are trying to describe is no that it is not in that (virtual) displayed workspace, but that the position of that application has moved...

To have the position stay in a certain place within that virtual display, you need to know the details of the geometry of where you want it, then use something that will keep it there as a property...

Look for that section in the Ubuntu Help Page ([https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)) for Devilspie, and create a script for that. Devilspie is still current and actively maintained.

---

### Post by sdsurfer on 2023-12-24
> **MAFoElffen said:**
> Look for that section in the Ubuntu Help Page ([https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)) for Devilspie 

Thank you, I have come across Devilspie and have not installed it. I just never had to before 22.04.

---

### Post by sdsurfer on 2023-12-30
**To anyone else coming to this thread:** There is a workaround, not marking as solved because I still haven't gotten to the root of the problem.

**The workaround: *do not maximize apps on the secondary monitor.* **I  happened to notice a terminal window I'd moved to the secondary monitor  survived the screen lock. As a test I enlarged Evolution to ***almost***  maximized but did not maximize it. Tested the screen lock via  xscreensaver, let it shut off the monitor signal, on unlock Evolution  remains on the secondary monitor.

I haven't installed devilspie because I don't believe this should require user intervention, it used to work and now does not. I've spent the last week trying all sorts of things, going into Gnome and Wayland, back into unity, fiddling about with settings, unity tweaks and gnome tweaks, all the same. Uninstalled and re-installed the amdgpu drivers. In Display settings, I set "scale all windows contents to match" to the secondary monitor. Didn't matter, and makes sense it wouldn't. monitors are identical. Disabled sticky edges, Workspace set to 1 workspace, multitude of other things, nothing worked.

I suspect it **may** have something to do with my environment. The only options for multi monitor in the MSI bios are for integrated graphics, I am using PEG to enable the XFX 580RX so this option is not available.. I also have one monitor connected to HDMI (primary)  the other DP (secondary,) I have another DP cable coming to see if possibly that is the issue - maybe the system is shutting off DP first and moving everything to the HDMI port on the primary monitor. I don't think it is, as mentioned this issue was present before I installed the XFX 580RX (but only had one HDMI port then as well, so, maybe.)

I have both power and screen lock set to never suspend/shut off monitors, and have installed xscreensaver to see if it handles it differently. It doesn't. As soon as xscreensaver shuts off, on unlock, any apps maximized on the secondary monitor are moved to the primary monitor.

I'm still fiddling with it, I'm down to ***apps only move from secondary monitor on lock if they are in a maximized state.***

---

### Post by sdsurfer on 2024-05-25
ER. MI. GIRD. @TheFu to the rescue, again.

I have struggled with this since December 2023, no apps would "stick" to the secondary monitor. Typical behavior would be screen lock comes on, apps on the second monitor would disappear into some no-man's land but still be on the launcher. I'd have to quit them from there and re-launch. I resigned myself to my fate, Ubuntu was broken . . . there were tons of other problems as well I won't describe. It was a nightmare, I could barely get anything done.

Took the plunge yesterday and upgraded from 22.04->23.10->24.04 (despite claims it wasn't ready.) Lots of difficulties I won't describe, but again[ this post got me through a full update]("https://ubuntuforums.org/showthread.php?t=2486668&p=14142160#post14142160"). Thanks again @TheFu.

Problem is gone, after lock apps stay where I put them, Unity updated to 7.7, OS 24.04.

---

### Post by TheFu on 2024-05-25
Uh .... 

I came here to suggest using a better DE or not even a DE at all, but a good Window Manager that isn't dumbed down so much like Gnome.  Applications aren't supposed to know their size or location. That's the job of the WM and has been for 40 years.  If Gnome apps are trying to change that, they are breaking a standard for Window Managers.   ICCCM2 is the standard.

Skimming through ... gee - I helped someone?  No way!  Whatever. Thread **SOLVED**?   ;)  Thread Tool near the top to mark it that way.

Leaving now.

---

