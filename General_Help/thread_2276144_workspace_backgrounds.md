---
title: "workspace backgrounds"
date: 2015-04-30
forum: General Help
---

### Post by bobardu on 2015-04-30
I have been using Ubuntu 14.04 desktop and I just installed Ubuntu 15.04 MATE. How do I use different backgrounds on each of my workspaces? I was able to do so in Xubuntu 14.04, but it's not obvious how to do it in either of the others.
Thanks...

---

### Post by Dennis N on 2015-04-30
> **bobardu said:**
> I have been using Ubuntu 14.04 desktop and I just installed Ubuntu 15.04 MATE. How do I use different backgrounds on each of my workspaces? I was able to do so in Xubuntu 14.04, but it's not obvious how to do it in either of the others.
Thanks...

You can do it by switching the window manager to Compiz in MATE Tweak. Then activate the wallpaper plugin (it's already installed in 15.04). I believe you then would use that plugin's settings dialog and make your wallpaper choices.

Sometimes there are stability problems with these plugins, so proceed with that in mind.

---

### Post by bobardu on 2015-05-01
Thanks Dennis, one more question...how to activate that wallpaper plugin? I tried using CCSM, which I downloaded, and turned on the wallpaper option, but that produced problems when changing workspaces (resulted in totally black screen - requiring reboot).

---

### Post by Dennis N on 2015-05-01
> **bobardu said:**
> Thanks Dennis, one more question...how to activate that wallpaper plugin? I tried using CCSM, which I downloaded, and turned on the wallpaper option, but that produced problems when changing workspaces (resulted in totally black screen - requiring reboot).

To activate, you just check the box next to the plugin in the settings manager. That's all I did. It works immediately. I did get the wallpaper plugin to work with four desktops, each with a different background - but the regular desktop switcher on the panel stops working. Don't know if that is supposed to happen. I used Ctrl+Alt+Up and it went into expo mode where I could arrow to the desktop I wanted, then enter. 

My CCSM was installed by default in 15.04. Yours wasn't?

---

### Post by Dennis N on 2015-05-01
If you get a chance, I wonder if you would please test the Alt-Tab (and Ctrl+Alt+Tab) switcher under Compiz. I can switch between windows as long as they are both on the same workspace. Ctrl+Alt+Tab should switch between windows in ALL workspaces, and in fact I can see the windows from other workspaces, and even move the one I want to the front, but it is impossible to select it for use. As soon as I release a key, the switcher jumps back to the workspace I am on instead of selecting the window from another workspace. Maybe I am doing something wrong here.

---

### Post by bobardu on 2015-05-02
I did not see CCSM as "installed" in the Ubuntu Software Center and so I installed it. 
I've been playing around with the Ctrl+Alt combinations and I see the same behavior as you describe.

I am still unable to get different backgrounds on the workspaces. If I change background on one workspace, it is changed on all of them.

---

### Post by bobardu on 2015-05-02
I have found that each press of [COLOR=#000000]Ctrl+Alt+Tab cycles through each of the windows. When I release the key-combo, the one on top is now the active window, regardless of the workspace where it is located.

[/COLOR]

---

### Post by Dennis N on 2015-05-02
Here's the plugins I have enabled. Maybe you are missing one that's needed for separate wallpapers? In experimenting, I may have enabled or disabled a couple of the plugins, but what I list here works with multiple wallpapers. 

General: Commands, Composite, Gnome Compatability, Open GL, Copy to Texture.
Accessibility: Dim Inactive, Show Mouse, Enhanced Zoom Desktop
Desktop: Expo, Show Desktop
Effects: Animations, Window Decoration
Extras: Thumbnail Window Previews
Image Loading: JPEG, Text, PNG
Utility: Compiz Library Toolbox, Regex Matching, Crash Handler, Mouse Position Poling, Wallpaper, Workarounds
Window Management: Maximumize (sp), Put, Scale, Snapping Windows, Move Window, Resize Window, Grid, Place Windows, Shift Switcher

> **bobardu said:**
> I have found that each press of [COLOR=#000000]Ctrl+Alt+Tab cycles through each of the windows. When I release the key-combo, the one on top is now the active window, regardless of the workspace where it is located.
[/COLOR]

Ctrl+Alt+Tab just not working here. It works if the window I choose is on the current workspace, but won't change to a window on another workspace. I can bring the window I want forward by holding Ctrl and Alt down and hitting Tab a few times, but releasing either Ctrl or Alt or both returns to the current workspace and window.

Attached Image: Four desktops, four backgrounds

---

### Post by Dennis N on 2015-05-03
@bobardu
Hope you got your wallpaper problem sorted out.

I've switched from Compiz back to Marco. Although all the effects are very cool, two things were show stoppers: (1) Failure to get the Ctrl+Alt+Tab switcher working with multiple workspaces, and (2) the inability to have icons on the Desktop. I want both of these features working for me.

---

