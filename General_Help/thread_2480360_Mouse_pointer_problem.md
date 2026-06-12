---
title: "Mouse pointer problem"
date: 2022-10-27
forum: General Help
---

### Post by satimis on 2022-10-27
Ubuntu 22.04 desktop
Firefox Browser 106.0.1

Moving the mouse pointer over Firefox Browser it changes to a very small size, almost invisible.  

This problem doesn't happen on Google Browser.  Please advise how to fix the problem?

Thanks

Regards

---

### Post by &amp;KyT$0P# on 2022-10-27
How do you have Firefox and "Google Browser" installed?  Are they .debs, or snaps, or flatpaks, or...?

---

### Post by Dennis N on 2022-10-27
What cursor theme are you using? Does the cursor theme change, or just the size?

---

### Post by satimis on 2022-10-27
> **halogen2 said:**
> How do you have Firefox and "Google Browser" installed?  Are they .debs, or snaps, or flatpaks, or...?
Sorry I can't remember.

This is an upgrade version from Ubuntu 20.04.  I just found this problem.  It worked normal before.  I haven't changed anything. 

I have another SSD on this PC also running Ubuntu 22.04, installed on ISO.  It doesn't have this mouse pointer problem.

It is very strange to me

---

### Post by satimis on 2022-10-27
> **Dennis N said:**
> What cursor theme are you using? Does the cursor theme change, or just the size?
Activities -> Tweaks

ModMyTheme

Pls see attached screenshot.  Thanks

Regards

---

### Post by Dennis N on 2022-10-27
Your Tweaks display doesn't show a Cursor theme. I suggest you pick one using the dropdown arrow and see if that makes a difference. See my screenshot.

---

### Post by satimis on 2022-10-27
> **Dennis N said:**
> Your Tweaks display doesn't show a Cursor theme. I suggest you pick one using the dropdown arrow and see if that makes a difference. See my screenshot.
Done as advised.

Still the same without improvement on mouse pointer.  Even after reboot PC

Please see screenshot.  Thanks

Edit
===
The strange thing happens only moving mouse pointer on Firefox.  This mouse point changes to very small almost invisble

---

### Post by Dennis N on 2022-10-27
I am also surprised that your Tweaks doesn't show any Applications theme or Icons theme. That's very strange. You might want to set those too.
On the cursor, you can set the cursor size of DMZ-White in **Settings > Accessibility > Cursor Size**. See if setting it there makes a difference.
Also note that my Tweaks is from Ubuntu 22.10, so the options are slightly different.

---

### Post by satimis on 2022-10-27
> **Dennis N said:**
> I am also surprised that your Tweaks doesn't show any Applications theme or Icons theme. That's very strange. You might want to set those too.
On the cursor, you can set the cursor size of DMZ-White in **Settings > Accessibility > Cursor Size**. See if setting it there makes a difference.
Also note that my Tweaks is from Ubuntu 22.10, so the options are slightly different.
Already set to largest.

Please see following article.

firefox cursor size
[https://support.mozilla.org/bm/questions/1244122](https://support.mozilla.org/bm/questions/1244122)

---

### Post by Dennis N on 2022-10-27
OK, do you have a screen resolution higher than 1920 x 1080? If so, maybe that is the cause. (I use 1920 x 1080).

---

### Post by satimis on 2022-10-27
> **Dennis N said:**
> OK, do you have a screen resolution higher than 1920 x 1080? If so, maybe that is the cause. (I use 1920 x 1080).
Yes.  This is a 4K screen
Resolution: 3840x2160.

But the strange thing is "It only happens moving on Firefox screen"

Regards

---

### Post by Dennis N on 2022-10-27
Did you look at the Bugzilla page? There are 23 bug reports under "cursor size" search. If you can't find a match to your situation, you can file a new bug report.

---

### Post by &amp;KyT$0P# on 2022-10-27
> **satimis said:**
> Sorry I can't remember.

If it's a deb package, this would show it -
```
apt-cache policy firefox
```

If flatpak,
```
flatpak list --app | grep -Fi org.mozilla.firefox
```

For other types of installation, you might remember what it is if you open Firefox, go to [FONT=Courier New]about:support[/FONT] (or, equivalently, Help > More Troubleshooting Information) and check the path shown for "Application Binary".

> **Dennis N said:**
> Your Tweaks display doesn't show a Cursor theme. 

So maybe check whether your cursor theme is set somewhere else, e.g.
[LIST]
[*][FONT=Courier New]~/.icons/default/index.theme[/FONT]
[*][FONT=Courier New]~/.config/gtk-3.0/settings.ini[/FONT]
[/LIST]

Or maybe there is an environment variable related to cursor that for some reason Firefox either isn't picking up or can't use?  You can check that by looking at output from running [FONT=Courier New]env[/FONT] in Terminal.  I use environment variable [FONT=Courier New]XCURSOR_SIZE[/FONT] to set non-default cursor size exactly because of issues like this.

---

### Post by ajgreeny on 2022-10-27
If your Firefox is the default snap version I wonder if the sandbox system that snaps have means that the cursor size set for the whole system is ignored by snaps?

I have no snaps on my system so can't test this out in any way but it might be a possibility, I think, and this non-configurable nature of snaps is one of the reasons I use none of them.

---

### Post by #&amp;thj^% on 2022-10-27
> **satimis said:**
> Yes.  This is a 4K screen
Resolution: 3840x2160.

But the strange thing is "It only happens moving on Firefox screen"

Regards
@ satimis I have had to add a file in my /home .~/.Xresources
with this added:
```
!Xcursor.theme: cursor-theme
Xcursor.size: 14
```
Adjust your size to preference. I had all different sizes, depending on the application in use by "X"
EDIT: Also important Make sure your "~/.xinitrc" looks similar to the following
```

~/.xinitrc

xrandr
...
xrdb -merge ~/.Xresources
exec wm
```
this will make sure that xrandr runs before loading ~/.Xresources. 
Just a log out and login should work.

---

### Post by Holger_Gehrke on 2022-10-27
> **ajgreeny said:**
> [snip]
I have no snaps on my system so can't test this out in any way but it might be a possibility, I think, and this non-configurable nature of snaps is one of the reasons I use none of them.

I've got the default snapped Firefox on my Xubuntu 22.04 and I can tell you that it completely ignores cursor *theme* settings but follows cursor *size* setting. I have a rather unusual animated cursor set and as soon as the pointer enters the Firefox window it goes from a large black triangle with an animated red stripe down the middle to a boring standard arrow. But that arrow honours the cursor size setting (which are useless for my animated cursor - it only exists in one size); if I set the cursor size very high (60) it goes from a small animated cursor to a big arrow when I move into the Firefox window.

Holger

---

### Post by Dennis N on 2022-10-27
On the contrary, I have been using the snap Firefox on Ubuntu 22.10 and it does use my selected cursor theme (DMZ White) and size (Large) in the Firefox window, so it's not ignoring my cursor settings. The cursor is the same everywhere as it should be. The Gnome Desktop environment could make a difference. In 22.04? I'll test the cursor on that Gnome release (if the snap is still installed).

Update:
Checked Firefox snap on Ubuntu 22.04. Same as above - no problem with the cursor.

---

### Post by satimis on 2022-10-28
> **1fallen said:**
> @ satimis I have had to add a file in my /home .~/.Xresources
with this added:
```
!Xcursor.theme: cursor-theme
Xcursor.size: 14
```
Adjust your size to preference. I had all different sizes, depending on the application in use by "X"
EDIT: Also important Make sure your "~/.xinitrc" looks similar to the following
```

~/.xinitrc

xrandr
...
xrdb -merge ~/.Xresources
exec wm
```
this will make sure that xrandr runs before loading ~/.Xresources. 
Just a log out and login should work.
Hi,

Thanks for your advice.

$ cat: /home/satimis/.xinitrc: No such file or directory
Whether create it with following content ?```

xrandr
...
xrdb -merge ~/.Xresources
exec wm
```

Regards

---

### Post by satimis on 2022-10-28
Hi all,

Thanks for your advice

$ apt-cache policy firefox```

firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 1:1snap1-0ubuntu2
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status

```

$ flatpak list --app | grep -Fi org.mozilla.firefox
no output

I suppose the Firefox is Ubuntu package

$ lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```

What shall I do?

Regards

---

### Post by Dennis N on 2022-10-28
**1:1snap1-0ubuntu2** is the apt package which links firefox to the firefox snap for installation.
Use snap list to show firefox:
```
dmn@Zotac:~$ snap list firefox
Name     Version  Rev   Tracking         Publisher  Notes
firefox  106.0-1  1969  latest/stable/&#8230;  mozilla&#10003;   -

```

---

### Post by satimis on 2022-10-28
> **Dennis N said:**
> **1:1snap1-0ubuntu2** is the apt package which links firefox to the firefox snap for installation.
Use snap list to show firefox:
```
dmn@Zotac:~$ snap list firefox
Name     Version  Rev   Tracking         Publisher  Notes
firefox  106.0-1  1969  latest/stable/…  mozilla&#10003;   -

```
Hi,

$ snap list firefox```

Name     Version    Rev   Tracking       Publisher  Notes
firefox  106.0.1-1  1993  latest/stable  mozilla&#10003;   -

```

Regards

---

### Post by Dennis N on 2022-10-28
So, is your cursor problem fixed now?

---

### Post by satimis on 2022-10-28
> **Dennis N said:**
> So, is your cursor problem fixed now?
Sorry, no.

It is very strange to me.  Moving the mouse pointer on/over Firefox screen it becomes very small, almost invisible.  Moving the mouse pointer on/over Shotcut/VLC/Shotwell screen etc it doesn't have this problem.

Regards

---

### Post by Dennis N on 2022-10-28
> **satimis said:**
> Sorry, no.

It is very strange to me.  Moving the mouse pointer on/over Firefox screen it becomes very small, almost invisible.  Moving the mouse pointer on/over Shotcut/VLC/Shotwell screen etc it doesn't have this problem.

Regards

I suspect it's a Firefox bug with the display mode. A test might be to temporarily set your monitor to 1920 x 1080, or connect a monitor with 1920 x 1080 or lower resolution and see how the cursor behaves.

---

### Post by satimis on 2022-10-28
> **Dennis N said:**
> I suspect it's a Firefox bug with the display mode. A test might be to temporarily set your monitor to 1920 x 1080, or connect a monitor with 1920 x 1080 or lower resolution and see how the cursor behaves.
Set
Resolution: 1920 x 1080

Still the mouse point is quite small

Regards

Edit-1
====
Made following test:

Start an Ubuntu 22.04 VM of VirtualBox

There is no such a problem moving the mouse pointer on Firefox the pointer becoming tiny.  Expanded the VM to full screen and still no such a problem found.

The problem only occurs on Ubuntu 22.04 host

Edit-2
====
There is another SSD on this PC running Ubuntu 22.04

Start it.  Same problem is found on Firebox.  Moving the mouse pointer on it the pointer becomes very small.

It is quite funny to me

---

### Post by Dennis N on 2022-10-28
Check that the snap is connected to use the available icon themes.

```
dmn@Zotac:~$ snap connections firefox | grep icon-themes
content[icon-themes]      firefox:icon-themes             gtk-common-themes:icon-themes    -

```

If you don't get all three columns as above, it's not connected to the socket causing some fallback cursor to be used.

---

### Post by satimis on 2022-10-28
> **Dennis N said:**
> Check that the snap is connected to use the available icon themes.

```
dmn@Zotac:~$ snap connections firefox | grep icon-themes
content[icon-themes]      firefox:icon-themes             gtk-common-themes:icon-themes    -

```

If you don't get all three columns as above, it's not connected to the socket causing some fallback cursor to be used.
$ snap connections firefox | grep icon-themes```

content[icon-themes]      firefox:icon-themes             gtk-common-themes:icon-themes    -

```
It seems connected.

Regards

---

### Post by satimis on 2022-10-29
Hi all,

I have a spare PC running Ubuntu 22.04.  I connect the Dell 4K 32" display to make another test.  There is no such funny problem moving the mouse pointer over/on Firefox.  The mouse pointer becomes tiny small.

lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy

```

$ xdpyinfo | grep 'dimensions:'```

  dimensions:    3840x2160 pixels (702x392 millimeters)
  
```

$ xdpyinfo | awk '/dimensions/ {print $2}'```

3840x2160

```

---

### Post by satimis on 2022-10-29
Hi all,

Publem solved by;
1. Delete Firefox Snap package
2. Reinstall Firefox on Ubuntu Repo

Please refer to following document
Ubuntu 22.04 and FF 104.0.2 Tiny mouse cursor
[https://www.reddit.com/r/firefox/comments/xcjxex/ubuntu_2204_and_ff_10402_tiny_mouse_cursor/](https://www.reddit.com/r/firefox/comments/xcjxex/ubuntu_2204_and_ff_10402_tiny_mouse_cursor/)

aggregatesys
·
1 mo. ago```

The issue only appears to be with Firefox packaged as a Snap. I just removed the snap package and reinstalled firefox from the official repo. You can do it with:

```

Anyway lot of thank for all folks' advice.

Regards

---

### Post by &amp;KyT$0P# on 2022-10-29
> **satimis said:**
> Publem solved by;
1. Delete Firefox Snap package
2. Reinstall Firefox on Ubuntu Repo

Thanks for posting the solution, but one correction: the referenced Reddit post instructions are for switching to the .deb Firefox from **Mozillateam PPA**, not Ubuntu repo (which don't have any .deb Firefox for 22.04).

---

