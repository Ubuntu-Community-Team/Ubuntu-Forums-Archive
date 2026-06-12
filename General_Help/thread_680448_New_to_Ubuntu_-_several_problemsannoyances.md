---
title: "New to Ubuntu - several problems/annoyances"
date: 2008-01-27
forum: General Help
---

### Post by Agent ME on 2008-01-27
I've recently installed Ubuntu 7.10 (Gutsy) on my laptop, and I managed to update ALSA to 1.0.15 so I could get sound working, and now it works pretty good.

**------- Things I need help on**

**1.** Whenever I'm playing certain full screen games like quake3, the volume controls on my laptop don't do anything. Pressing mute won't mute, etc. If I exit the game, they'll work immediately afterward, but not while I'm in the game. Can I fix this? (I've only had this problem with q3-based games, and ioquake3. Some other games, I have the problem that the volume control makes the game lose focus and I have to click to make it come back up.)

**4.** I've been using ThunderbirdPortable with Enigmail plugin for my email on windows, so when I got linux, I figured out if I put the standard linux version of thunderbird on my flashdrive, and managed to set it up to use the same profile directory as the windows portable version on the flashdrive. It loaded all my email and the enigmail plugin.
But the enigmail plugin is still set up to try to use the windows version of gpg. I can change it, but then it will want to use the linux version when I try to use it on windows. Is there a way around this?

**10.** If I switch users (leaving first profile logged in), then log out of the second one, it goes back to the enter password window because its locked, but the screen is completely blank except for a mouse. I have to move the mouse until it becomes the symbol when its being held over a text box, click, and enter my password, press enter, and then log back in, which things work fine afterward. This is pretty annoying as I'd like to be able to use this feature without blanking the screen. Anyone have some ideas to fix this?

In case it helps for anything, my system is an HP Pavilion dv9543cl system, with 2 hard drives (first is Vista, second has ext3 and swap partitions for linux), a core2 duo 2ghz processor, and an Nvidia 8600M GS video card.

**------- Closed (More or Less)**

**2.** When I use one of the buttons, the graphic on the screen showing this is huge -
[http://img253.imageshack.us/my.php?image=volumenh0.png](http://img253.imageshack.us/my.php?image=volumenh0.png)

But I noticed that sometimes it shows a little tiny, non-transparent graphic, such as if I change the volume after I log in and before the desktop has fully loaded. Is there a way I can make it use that one always?
**- Explained.**

**3.** This is probably the biggest thing I miss from windows vista - a media player that can either play media from a upnp-sharing source, or properly play a playlist file properly from an ftp server and automatically find the media on the ftp source.
I have my music and videos on my other computer, a windows xp, both being hosted through WMP11's upnp sharing feature and on a filezilla ftp server.
I've tried using the Totem Movie Player, Rhythmbox music player, and VLC to try to load the playlist file on the ftp server - didn't work. I saw Rhythmbox had upnp support, so I checked that plugin in the plugins window of it (after getting the needed python dependency), restarted it, but nothing seemed to change in Rhythmbox.
Anyway I could get this to work?
**- Gave up.** Tried about 6 different media players, and none could do this. So I just copied my music collection to this comp and using Amarok for now. Though I'd be interested if anyone knows of a program that can share music to a linux client, including playlists.

**5.** I'm able to use the pre-installed linux gpg on this system with my flashdrive's keys by using the --homedir option pointing to the directory on my flashdrive. I wanted to see if there was a way to make it do this by default for my account, and in the manual page for gpg it mentions the GNUPGHOME environment variable.
I tested that this would do what I wanted by trying out trying out GPG with a modified env with my GNUPGHOME variable using the 'env' command, and it does.
But how do I make the system remember the environment variable for my account? (I want it to stay persistent, and only on my account login.)
**- SOLVED.** I just added "export MYVAR=/value" to the end of my ~/.bashrc file.
**- NOPE NOT REALLY.** This only sets the environment variable in the terminal - if I run a program not in a terminal it won't see the variable. What gives?!
**- FOR REAL NOW.** I moved the line of code from ~/.bashrc to ~/.profile and it works now.

**6.** My system uses the grub bootloader that was auto-installed by the live cd. If I boot up with a flashdrive in my system, it stops with "Error 17" and the only button combo that will do anything to get me out of there is Ctrl+Alt+Del, which reboots (and runs into the same error again if I haven't removed my flashdrive). Is there a way around this?
**- Explained.**

**7.** When I log in, or log out, the screen flashes out of the GUI to a console temporarily, with code running by. Is there a way to fix it so this doesn't happen, and it seamlessly stays in the GUI? Obviously not a big problem but I figured if I'm posting everything else I might as well add this on.
**- Explained.**

**8.** When I play Quake 3 (ID build, not the ioquake3 port or other games based on it) there is no sound unless sometime before starting quake3 I used the command **echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss** as root in a terminal by using the su command. (And if I reboot, I need to do it again.) How can I set this up so it's done automatically or saved? I already thought of making a script so when I started quake3, it would run that first, then quake3, but I'd need to be root, and I want a solution that doesn't require me to be root, so that way other users without the password can play quake3 without me.
**- Solved.** See [http://www.frihost.com/forums/vt-87999.html#736199](http://www.frihost.com/forums/vt-87999.html#736199).

**9.** My computer has a mousepad near the keyboard with a button that toggles it being on/off. That works correctly, but whenever I turn it on, a window opens up too, "Ubuntu Help Center". I can close it, but wtf? Why does this happen?
**- Figured it out.** My stupid keyboard has a button for help - FN + F1, but toggling on the keypad sends the same keycode. I just disabled this in the Keyboard shortcuts menu.

---

### Post by dcstar on 2008-01-28
> **Agent ME said:**
> 
..........
**6.** My system uses the grub bootloader that was auto-installed by the live cd. If I boot up with a flashdrive in my system, it stops with "Error 17" and the only button combo that will do anything to get me out of there is Ctrl+Alt+Del, which reboots (and runs into the same error again if I haven't removed my flashdrive). Is there a way around this?
.........

Your BIOS is probably changing the order (and designation) that the drives are presented to Grub when the USB drive is plugged in at boot time, since Grub relies on this not changing there is little you can do about it.

---

### Post by Agent ME on 2008-01-28
I've checked my BIOS settings for anything obvious, so I guess that isn't fixable.

I added a #9 to the list.

---

### Post by nick_h on 2008-01-29
2. The transparent dialog is used when Visual Effects is enabled.

3. Try another music player such as exaile or banshee.

7. I also get this problem. It seems to be a bug that has been introduced in releases after Dapper.  I haven't found a solution yet.

---

### Post by Agent ME on 2008-01-29
Thanks for explaining some things - I didn't manage to find a media player that did what I wanted, but I found one that I liked (Amarok) and decided just to copy my music to this computer.

Added a #10, and resorted it so it doesn't look so daunting to someone trying to read the post.

Surely #5 is a simple thing someone can help me with.

---

### Post by Agent ME on 2008-01-31
Bump.

I solved 5, and the answer is there for anyone curious.

---

### Post by jivabill on 2008-02-01
I have a flash drive plugged into my Ubuntu 7.10 system as we speak. Works fine, loads up looking like another disk drive.  No problem at all with that.
Bill

---

### Post by Agent ME on 2008-02-02
I'm guessing that was supposed to be a reply to a different topic and got mixed in here.

#5 isn't really solved - this has to be really simple. Any help? This is the thing that is annoying me the most now... EDIT: Solved it for real now...

---

