---
title: "Mouse won't respond in the majority of the work area Ubuntu 15.04 w Unity"
date: 2015-09-14
forum: General Help
---

### Post by ShinigamiKiba on 2015-09-14
Guys this is going to be a long one since I need to describe the problem and subsequent actions in case someone can help.
Keep in mind I'm an artist and not a tech guy so while I do know how to keep my computers clean and functional I may need some more casual friendly responses :)

I had quite the adventure with Ubuntu something I've never seen before that I can only blame on some sort of graphics carddriver problem judging by the behavior.

On a brand new fresh and well set up Ubuntu installation which worked fine since Saturday, today I started getting strange behavior.
After boot up everything would be fine, but as soon as I'd open any window/run any program the work area/desktop area of Unity would become unresponsive to mouse interaction but would work fine if navigated with the keyboard. 

For example opening Chromium would make it so I couldn't click on anything inside the main window and the cursor wouldn't change shape when hovering over links, text and such however if I were to click the clock area or side bar everything was fine, the desktop(actual desktop) or the active windows tho would be dead to the mouse but not the keyboard.
I could still surf the web and everything using the keyboard, tabbing from button to button and so forth.

At first this issue would go away after a minute or so but eventually it became permanent and rebooting didn't fix it, as soon as I'd run a program or open a window it would do this.

I ended up trying to disable OpenGL with the Compiz Config tool which resulted in a complete crash of Unity and Compiz, even after re-enabling OpenGL everything was dead, rebooting would take me to an empty desktop area with a single shortcut i had and every window i'd open would have no title bar no nothing, clearly i killed compiz and unity in one blow by ignoring a few warnings when trying to disable openGL.

So I hit ctrl+alt+f1 and installed gnome desktop

----------------

Gnome Desktop is up and running but I suspect the issue to be either my GTX680's drivers which Ubuntu installed on its own or a conflict with compiz of some sort that led to this, I wasn't changing any settings prior to this mind you I just installed the compiz config tool last night with no issues whatsoever.
After installing Gnome Desktop it appears even grub changed and went to its default settings and I had it edited just right lol, doesn't matter though as long as it works the way it should, what worries me now is the broken Unity installation and I feel I'm not out of the woods yet and this issue will come back as I feel a bit of a lag with Gnome too.

Gnome desktop feels very cool yet alinen at the same time, in fact it's exactly the kind of cool strange OS feel I was looking for, so it's fun for playing around, however i'd like to have the option to go back to unity for efficiency and regular computer use but that is dead and broken now.
If you guys could help me fix unity and avoid the issue I described in the OP would be great, I also fear this issue will repeat itself in gnome too.

I believe the solution would be to disable any and all visual effects, go to a 2d interface since despite the errors and everything dying after disabling open GL the mouse responded.
I'd like to know how to restore unity without breaking gnome desktop now and then running it in a completely 2d mode if possible
Also what are the chances of this happening in Gnome too and rendering my entire ubuntu install useless?

--------------
Computer Specs:

i7 3820
GTX680 2GB
16GB RAM

---

### Post by ShinigamiKiba on 2015-09-15
For the love of God people help me
I'm starting to experience the same issue with Gnome desktop, specifically the second user profile I set up
In Gnome I don't see anywhere to change the windows color/style just desktop background, the first admin profile seems to work fine the second generic user profile has the exact same problem unity did, basically the mouse is not responsive on the windows' title bars, the x button and such

it is a problem I am unable to solve myself and every single forum I posted on has not even bothered to help
I am getting very frustrated here and if the Ubuntu community wants to grow its userbase it needs to be more effective at helping casual users such as myself.

I know this isn't a user error as I did NOTHING to bring this behavior on me

Again, very similar problem with GNOME but only on one of the user accounts for now

EDIT: It appears that the graphics card drivers are the problem after all as they crash in the affected profile, once they crash the colors of course get all messed up but interacting with windows using the mouse is not an issue.

What I don't understand and what frustrates me is why this is happening on one profile but not the other, I made the now affected profile this morning and was not editing any settings much less graphics settings.

EDIT: 2 BOTH Profiles are affected apparently
I was on my Admin profile and as soon as I launched Chromium the colors got all distorted, like high contras and I guess lower bit rate like 256 colors or even 16 colors, eventually everything froze and the colors went even lower in quality, eventually the mouse pointer disappeared too.

I'm 100% certain it's the graphics card drivers but why wasn't this issue present on the live disc? WHAT can I do to safely remove whatever default drivers Ubuntu installed and use the OS in peace.
I don't need fancy windows effects and animations I just need peace and quiet and my valuable time to not be wasted at this point. I lost hours form my job because of this so in terms I lost MONEY because of this.

EDIT 3:
How do I and can I do the following so this BS ends and I use my comptuer?

1. How do I check which drivers I'm running and if the problem is indeed the drivers?
2. Is it possible to disable any and all graphics card drivers and use whatever the live USB/Disc is using, that shows all the colors and everything without any problems.

IF worse comes to worse I'm willing to delete ubuntu from this computer and never touch it again on this machine, however is that going to mess up my boot sectors and make me unable to boot into windows 8.1 further waqsting my time and taking away time form my job.

Right now I have Ubuntu, then Windows 8.1 both on different SSDs
I use grub as a boot loader, set that up myself after installing windows 8.1 it was easy to set up

my patience for computers is none, i got no patience for this stuff however i did my best to remain calm for a whole day but at this point my time is wasted and not coming back to me

so any help would be appreciated asap

---

### Post by ShinigamiKiba on 2015-09-15
I was able to somehow remove the drivers or blacklist other ones and while my screen resolution is terrible now I have no problems whatsoever, however I am unable to install new drivers.

I was following the instructions in this video:
[https://www.youtube.com/watch?v=cVTsemATIyI](https://www.youtube.com/watch?v=cVTsemATIyI)
The instructions are in the description

I get stuck on this part:

sudo chmod +x NVIDIA-Linux-x86_64-352.30.run

sudo ./NVIDIA-Linux-x86_64-352.30.run

The installation says I'm running an x server when I try to quit the server im running it says starting 2some numbers im not a numbers person, i dont memorize numbers, anyway that stays on forever but ctrl+alt+f1 lets me get further into the installation process and from there I am told something about a kernel and an error, believe me my patience is off the charts at this point so i am in no shape to remember this horse crap anymore

anyway i click yes to have nvidia attempt to edit some crappy file and that does not work

that's all

EDIT: I installed new drivers using a random command i found on google sudo apt-get install nvidia-346, let's see if this works, I mean it works now but I'm willing to bet it'll mess up again tomorrow.

I don't know if 346 is the latest or oldest or whatever driver
frankly i dont car eif it works

again any help, advice and info a regular non tech savvy person with a short fuse for computers could understand is welcome

EDIT 2: So far with these drivers and those bad ones blacklisted everything works amazingly fast and good, the way Ubuntu works on all my platforms
however I feel I'm not out of the woods yet since this very installation started working fine and messed up over time.

---

### Post by ShinigamiKiba on 2015-09-15
After it working fine for a while and a restart or two for testing the problems seem to be creeping back ever so lightly
I think imma call it quits, get rid of this half baked OS and be sure to tell people to NEVER install ubuntu if they have nVidia graphics cards if the problems come back

Edit: Clearly the problem isn't fixable on this computer and with no help or support form the Ubuntu community a non hacker programmer like me doesn't have a prayer.
I formatted the SSD Ubuntu was on, didn't even bother to do it right just deleted the volumes in anger like a madman, fixed windows' boot and now everything works fine.

thanks for all the help and support Ubuntu community
I posted on 3 different forums

THIS is why nobody wants to use your piece of crap OS, because you're not helpful

---

