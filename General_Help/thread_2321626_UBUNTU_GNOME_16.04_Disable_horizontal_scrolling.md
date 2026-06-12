---
title: "UBUNTU GNOME 16.04: Disable horizontal scrolling"
date: 2016-04-23
forum: General Help
---

### Post by PhilGil on 2016-04-23
Hello, all. Just installed Ubuntu Gnome on a Dell Inspiron 11 3162. Everything works remarkably well, but there's one thing that's driving me crazy: I'm can't disable horizontal scrolling on the trackpad in either the Gnome 3 settings or in dconf manager. The option does not exist, although an Internet search seems to indicate that it should (or at least that it existed in previous versions of Gnome 3).

I have tried a synaptics.conf file and it appears Gnome settings supersede it. Any help would be greatly appreciated, the track pad is already fiddly and adding horizontal scrolling to the mix makes it very frustrating to use.

Edited: to make the title more descriptive

---

### Post by vasa1 on 2016-04-23
Do you get any output when running the *synclient* command in a terminal?

```
09:06 PM ~ $ synclient | grep -i horiz
    HorizScrollDelta        = 25
    HorizEdgeScroll         = 0
    HorizTwoFingerScroll    = 0
    HorizHysteresis         = 6
09:08 PM ~ $ 
```

---

### Post by PhilGil on 2016-04-23
Thank you for your reply, vasa1.

So I ran the command the first time and got the following output:
```
~$ synclient | grep -i horiz
    HorizScrollDelta        = 114
    HorizEdgeScroll         = 0
    HorizTwoFingerScroll    = 1
    HorizHysteresis         = 28

```

So, at this point horizontal scroll is enabled. Thinking you were on to something I ran the following command...
```
$ synclient HorizTwoFingerScroll = 0
```

After running the command again the output is...
```
synclient | grep -i horiz
    HorizScrollDelta        = 114
    HorizEdgeScroll         = 0
    HorizTwoFingerScroll    = 0
    HorizHysteresis         = 28
```

So synclient thinks that horizontal scrolling is disabled, but that's not the case as side scrolling still works. I re-started shell to see if that would  have any effect, but nothing changed.

---

### Post by vasa1 on 2016-04-23
> **PhilGil said:**
> ...
So synclient thinks that horizontal scrolling is disabled, but that's not the case as side scrolling still works. I re-started shell to see if that would  have any effect, but nothing changed.
If it was going to work, it would have. I don't think there's need for a restart or log-out, etc.

I'm not sure this will help any, but what's the output of *xinput -list*?

---

### Post by PhilGil on 2016-04-23
> **vasa1 said:**
> If it was going to work, it would have. I don't think there's need for a restart or log-out, etc.

I'm not sure this will help any, but what's the output of *xinput -list*?

```
~$ xinput -list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; DLL0725:01 06CB:7D47                        id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Integrated Webcam                           id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                            id=14    [slave  keyboard (3)]
    &#8627; DELL Wireless hotkeys                       id=15    [slave  keyboard (3)]


```

Is it strange to have two different touchpads listed?

---

### Post by PhilGil on 2016-04-23
Okay, just took a trip down the rabbit hole and found the answer to my own question (as well as discovering why synclient doesn't work). The short answer is that horizontal scrolling can't be disabled.

What I pieced together was that you cannot configure your touchpad in Gnome 3.18 using the traditional tools (synclient and a synaptics.conf file) because input device configuration is now handled by libinput. Unfortunately, libinput does not expose a method for toggling horizontal scrolling on or off. In my particular case libinput was not installed at all (possibly because I installed Ubuntu Gnome on top of a Xubuntu install), so I was unable to configure my touchpad at all.

WARNING - KIDS DON'T TRY THIS AT HOME UNLESS YOU ARE *ABSOLUTELY, POSITIVELY SURE* YOU ONLY WANT GNOME ON YOUR MACHINE: After removing the xserver-xorg-input-synaptics and xserver-xorg-input-evdev packages and installing xserver-xorg-input-libinput and libinput-tools I have a much smoother and less wonky mouse (bug report here: [https://bugs.launchpad.net/ubuntu-gnome/+bug/1552558](https://bugs.launchpad.net/ubuntu-gnome/+bug/1552558)). So even though I wasn't able to turn off side scrolling my touchpad is far less frustrating to use, so I'm marking this thread solved.

Thank you again for your help, vasa1!

---

### Post by vasa1 on 2016-04-23
Hi,

Two points: 

you can change the title of the first post in your own thread by clicking on "go advanced" when in edit mode. I don't think you can change the titles in subsequent posts in the the thread if they're already posted. Anyway, I've done what I think you want. You can change it further. It's good to have descriptive titles!

I'm not sure about your conclusion that h scrolling can't be disabled because of gtk 3.18. I too am on gtk 3.18. I'll change my OS specs in the forum settings ASAP. Before I posted I checked that the synclient settings worked. Not all of them, especially the multitouch ones, work, but some do. Just to be sure, I'll check again later today.

---

### Post by PhilGil on 2016-04-23
> **vasa1 said:**
> Hi,

Two points: 

you can change the title of the first post in your own thread by clicking on "go advanced" when in edit mode. I don't think you can change the titles in subsequent posts in the the thread if they're already posted. Anyway, I've done what I think you want. You can change it further. It's good to have descriptive titles!

I'm not sure about your conclusion that h scrolling can't be disabled because of gtk 3.18. I too am on gtk 3.18. I'll change my OS specs in the forum settings ASAP. Before I posted I checked that the synclient settings worked. Not all of them, especially the multitouch ones, work, but some do. Just to be sure, I'll check again later today.

Thank you for changing the title, that's what I wanted. I did not see a way of doing it from the advanced editing page, I'll look more carefully next time now that I know it's possible.

I don't think the problem is related to GTK 3.18, it's specific to Gnome. I already thought my post was long-winded so I didn't go into more detail, but from what I could gather the Gnome project has moved input device control to libinput in preparation for the transition to wayland. The Ubuntu Gnome team chose to leave the synaptics and evdev bits intact so that users could run multiple DE's/Window Managers, but none of it actually works in Gnome any more. Here is a Fedora bug that describes the same issue: [https://bugzilla.redhat.com/show_bug.cgi?id=1206961](https://bugzilla.redhat.com/show_bug.cgi?id=1206961)

It may also be a combination of factors such as installing Ubuntu Gnome on top of a Xubuntu install and also that the laptop is a very new model.

I'd like to be proven wrong, because not being able to control your touchpad settings seems like a pretty big bug in an LTS release of a popular Ubuntu flavor.

---

### Post by vasa1 on 2016-04-23
I have to attend a rather nasty meeting. I'll read your post more carefully later on :)

---

### Post by moteprime on 2016-04-24
I'm having this ridiculously annoying  problem to.
In october i upgraded to 15.10 and the 'Horizontal Scrolling' has gotten greyed out in Unity Tweak, there are bugs on launchpad, but the answer is:

 »The backend option to disable horizontal scrolling was removed and merged with the two-finger scroll option. You can no longer change them independently. This isn't a change we have control over«

This scrolling feature ended up being so unbearable for me that i switched to Mint with Cinnamon for 4½ months (There's no problem disabling it in Cinnamon), but now i'm giving Ubuntu another try, it must be possible to disable this horizontal scrolling.

Is it everybody or just a few people that are affected by the removing of the backend?

Ubuntu 16.04 (64) Thinkpad L450 (Intel core i5)

---

### Post by vasa1 on 2016-04-26
@PhilGil, please take a look at [http://ubuntuforums.org/showthread.php?t=2322086&p=13477856#post13477856](http://ubuntuforums.org/showthread.php?t=2322086&p=13477856#post13477856)

---

### Post by PhilGil on 2016-04-26
> **vasa1 said:**
> @PhilGil, please take a look at [http://ubuntuforums.org/showthread.php?t=2322086&p=13477856#post13477856](http://ubuntuforums.org/showthread.php?t=2322086&p=13477856#post13477856)
Thank you. I've switched to Mate, but I'll try out the solution in the linked thread if I decide to go back to Gnome. My laptop only has 2GB of RAM so I'm trying out lighter DEs (even though Gnome is still my favorite).

---

### Post by clam2 on 2016-07-27
Now this option is available!
Type
```
$ xinput list
```
for getting the *device-number* of your touchpad and the* option-number*.
You'll see something like: 
```
 libinput Horizontal Scroll Enable (*option-number*):   1 
```
Change it for 0 and you'll enable it
```
$ xinput set-prop *device-number* *option-number* 0
```

:)

---

### Post by techguy348 on 2016-11-11
> **clam2 said:**
> Now this option is available!
Type
```
$ xinput list
```
for getting the *device-number* of your touchpad and the* option-number*.
You'll see something like: 
```
 libinput Horizontal Scroll Enable (*option-number*):   1 
```
Change it for 0 and you'll enable it
```
$ xinput set-prop *device-number* *option-number* 0
```

:)

While that does work, it doesn't set the value on startup. You can use this script to disable the horizontal scrolling on startup
```
 Section "InputClass"
     Identifier "touchpad"
     Driver "libinput"
     MatchIsTouchpad "on"
     MatchDevicePath "/dev/input/event*"
     Option "HorizontalScrolling" "off"
 EndSection
```

You can type this in gedit, and then save it to /usr/share/X11/xorg.conf.d
I also have another script in there to disable mouse acceleration so I edited it below the script.
You could name the file 80-disable-horizontal-scrolling if you have no custom scripts
I also typed in the command
```
sudo chmod 644 80-disable-horizontal-scrolling
```
To add the necessary permissions.. Then the script will turn off horizontal mouse acceleration on startup. Hope this helps

For reference here are some other values you can set in libinput [https://www.mankier.com/4/libinput](https://www.mankier.com/4/libinput)

---

### Post by oswaldpp on 2016-12-09
An other possibility is to use:
```
 synclient HorizTwoFingerScroll=0
```

It can be added to the app at boot.

Cheers.

O-p

---

### Post by hanafey on 2017-03-03
I have this problem as well, and it is a huge problem that should be fixed. This case should not have been marked resolved!!! I found it with Google, saw the word resolved in the hit, eagerly clicked hoping to end the misery, but what a disappointment...

Two finger up down scroll is extremely nice. Two finger horizontal scroll is a pain in the neck.

---

