---
title: "Chrome/Chromium media keys in Unity, Gnome-Shell and Cinnamon"
date: 2014-08-27
forum: General Help
---

### Post by Kimm on 2014-08-27
Hello guys!

This is mainly an annoyance, but since I am a Google play music user, it becomes a bit of a hindrance. The issue is simply this, when I use the Google play music player in my web-browser with the Google play music extension (or Sway.fm Unified Music Media Keys, or Key Socket Media Keys), my desktop will not recognize that Chrome has bindings for these keys. The issue persists in Unity, Gnome-Shell (from standard repos 14.04) and Cinnamon, but not in KDE. Whenever I press any media key a large "stop" icon will appear on my screen, indicating that no player is running (I assume).

My media keys work with all other players I have tried, including VLC, Rhythmbox, Clementine and Nuvola, but will not work with chrome for some reason. Since the issue persists only in desktop environments that are somehow derived from Gnome (or perhaps I should say GTK based environments, but have not tried XFCE), I can only assume that it is some issue with global settings relating to media keys, but I have been unable to find them. It works fine in KDE, but I prefer not to switch desktop environment just to fix this issue.

Interestingly, Chrome will accept any key-bindings other than the media keys for controlling playback. For example, I can use Ctrl+P to pause the music or Ctrl+right key to skip ahead without any issues. But I would very much prefer to use the media keys, since it feels more intuitive.

I also know that Nuvola exists and has a plugin for Google music, but I would prefer to run the player in my main browser since it means fewer windows to manage and fewer applications running. I also suspect that others may run into this issue and find every bit as annoying as I have.

Any help would be much appreciated! :)

---

### Post by Kimm on 2014-08-28
I solved it myself!

It was as simple as deactivating the key bindings for media keys in the system settings for Gnome (I believe Cinnamon and Ubuntu use the same application, or at least the same configurations).

Keyboard -> Keyboard Shortcuts -> Sound and Media -> <<Select the keybinding of interest, double click on the assigned key and press backspace to unassign>>

---

### Post by KillEmAllx on 2014-11-11
> **Kimm said:**
> I solved it myself!

It was as simple as deactivating the key bindings for media keys in the system settings for Gnome (I believe Cinnamon and Ubuntu use the same application, or at least the same configurations).

Keyboard -> Keyboard Shortcuts -> Sound and Media -> <<Select the keybinding of interest, double click on the assigned key and press backspace to unassign>>

Have you found a "real" solution? I'm using Media Keys by sway.fm + Chrome, but I use Spotify so I need the keys to work with it too...

---

