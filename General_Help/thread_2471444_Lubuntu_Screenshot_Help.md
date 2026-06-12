---
title: "Lubuntu Screenshot Help"
date: 2022-01-30
forum: General Help
---

### Post by arius88 on 2022-01-30
Hello!  I recently switched from Ubuntu 20.04 to Lubuntu 20.04. I'm mostly pretty satisfied with how light-weight and fast it is.   However, in Ubuntu, when I wanted to take a screenshot, I just pressed the "printscreen" button and that was that. It would automatically save the file to my pictures folder where I could deal with it later. Now when I press the printscreen button this annoying "ScreenGrab" utility pops up, like "hey are you sure you wanted a picture of this?" to which the answer is always YES, THAT'S WHY I PRESSED THE BUTTON, and then I have to go through a whole thing where I name the file, tell it where to save it, etc. Then a useless message pops up on the screen for a while, telling me what I just did. Meanwhile, the ScreenGrab interface lingers about for no reason, waiting for me to manually close it. I don't want any of that. I just want to press PrintScreen and have my screenshot saved automatically like it used to do. Is there a way to make this happen?  I installed a couple other screenshot programs, but I have two problems:  1. None of them seem as simple as what I want, although the Gnome one at least seemed to have less steps. 2. I can't figure out how to change the default screenshot program. I thought to uninstall ScreenGrab but it's not listed among my installed programs for some reason.  Thoughts?

---

### Post by GhX6GZMB on 2022-01-30
Take a deep breath. :)
Been there, done that, annoyed the heck out of me as well. But I'm slowly getting to be an old hand at Lubuntu 20.04.

You need to do the following (apart from deinstalling the debile ScreenGrab):

Start Muon and make certain that scrot and xclip are installed on your machine. If not, install them.

Go to: Preferences -> LXQt Settings -> Shortcut Keys
and remove any existing PrtScr entries.

Add the following new keys with the following commands:

_PrtScr_: ```
[COLOR=#000000]sh -c 'scrot -o /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''[/COLOR]
```
[COLOR=#000000](full screen)

_Alt+PrtScr_: [/COLOR]```
[COLOR=#000000]sh -c 'scrot -o -u /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''[/COLOR]
```[COLOR=#000000]
(active window)

Now, when using PrtScr or Alt+PrtScr, your copied screen or window will be available in all programs under Edit -> Paste

Cheers.


[/COLOR]

---

### Post by guiverc on 2022-01-30
Well answered and thank you @ml9104

(I sort of wish the answer had been made on [Lubuntu's discourse]("https://discourse.lubuntu.me/") so I had the option of grabbing and making it a howto in our [*documentation *]("https://discourse.lubuntu.me/c/documentation/20")section!  :P)

Yes [scrot]("https://packages.ubuntu.com/jammy/scrot") looks pretty efficient, but [screengrab]("https://packages.ubuntu.com/jammy/screengrab") at least is Qt5 based which makes sense on LXQt (*somewhat* *limited I'll admit given it's designed for Qt5/KF5*). Prior Lubuntu releases used *lighter* [lximage-qt]("https://packages.ubuntu.com/jammy/lximage-qt") (using the `-s` option) but we had complaints there too.  We'll never please everyone I suspect with whatever is chosen (`*screengrab` is more flexible; still missing some things we could achieve with the native & flexible`lximage-qt`but better in other ways & the added features does increase complexity*).

---

### Post by GhX6GZMB on 2022-01-30
> **guiverc said:**
> 
(I sort of wish the answer had been made on [Lubuntu's discourse]("https://discourse.lubuntu.me/") so I had the option of grabbing and making it a howto in our [*documentation *]("https://discourse.lubuntu.me/c/documentation/20")section!  :P)

Yes [scrot]("https://packages.ubuntu.com/jammy/scrot") looks pretty efficient, but [screengrab]("https://packages.ubuntu.com/jammy/screengrab") at least is Qt5 based which makes sense on LXQt (*somewhat* *limited I'll admit given it's designed for Qt5/KF5*). Prior Lubuntu releases used *lighter* [lximage-qt]("https://packages.ubuntu.com/jammy/lximage-qt") (using the `-s` option) but we had complaints there too.  We'll never please everyone I suspect with whatever is chosen (`*screengrab` is more flexible; still missing some things we could achieve with the native & flexible`lximage-qt`but better in other ways & the added features does increase complexity*).

Don't get me started on Lubuntu Discourse. I used to have an account there, but was constantly attacked by trolls living in the cellar under their mother's house. I deleted my account after that.

The solution I presented is just a Ctlr+C, Ctrl+V variation for screen/windowshots using PrtScr.
It emulates the Windows screenshot functionality (not everything about Windows is bad), nothing else.

Some people need more functionality than that, and can then use ScreenGrab.

Scrot and xclip are basic Linux utilities and are not related to (?)ubuntu as such.

BTW: you're welcome to post my suggestion anywhere you want.

---

### Post by guiverc on 2022-01-30
> **ml9104 said:**
> Don't get me started on Lubuntu Discourse. I used to have an account there

Yeah I recall; I was hesitant to mention discourse, but in the end I hoped the reason for my mention of it would make you feel good (*understanding how useful I though the post was*) as I see like questions now & again (*once  per non-LTS cycle probably & a few times for a LTS*)

> **ml9104 said:**
> 
BTW: you're welcome to post my suggestion anywhere you want.

Thanks, I may, but if I do I'll credit you of course (*at the start, or possibly at the end, somewhat like we do at Ubuntu News*)

---

### Post by GhX6GZMB on 2022-02-04
> **barbaraturner said:**
> Screenshot the entire screen and save it to the clipboard: Ctrl + Print Screen.
Copy the screenshot of a specific region to the clipboard: Shift + Ctrl + Print Screen.
Save the screenshot of the current window to the clipboard: Ctrl + Alt + Print Screen.

Only true for old versions. On LXQt environments it won't work (18.10 and newer).

---

### Post by dragonfly41 on 2022-02-04
Try Flameshot .. although I am not on Lubuntu.

---

### Post by GhX6GZMB on 2022-02-04
> **dragonfly41 said:**
> Try Flameshot .. although I am not on Lubuntu.
I think you should read the whole thread first...

---

### Post by #&amp;thj^% on 2022-02-04
> **guiverc said:**
> Well answered and thank you @ml9104

(I sort of wish the answer had been made on [Lubuntu's discourse]("https://discourse.lubuntu.me/") so I had the option of grabbing and making it a howto in our [*documentation *]("https://discourse.lubuntu.me/c/documentation/20")section!  :P)

Yes [scrot]("https://packages.ubuntu.com/jammy/scrot") looks pretty efficient, but [screengrab]("https://packages.ubuntu.com/jammy/screengrab") at least is Qt5 based which makes sense on LXQt (*somewhat* *limited I'll admit given it's designed for Qt5/KF5*). Prior Lubuntu releases used *lighter* [lximage-qt]("https://packages.ubuntu.com/jammy/lximage-qt") (using the `-s` option) but we had complaints there too.  We'll never please everyone I suspect with whatever is chosen (`*screengrab` is more flexible; still missing some things we could achieve with the native & flexible`lximage-qt`but better in other ways & the added features does increase complexity*).

Just to let you know ad nothing else: Flameshot &#8212; Qt5 based software for interactive screenshot taking. Select the desired area, draw with different tools and enjoy the customization capabilities. [https://wiki.archlinux.org/title/Screen_capture](https://wiki.archlinux.org/title/Screen_capture)
I find it very useful for how to's.
@ml9104 other suggestions may be welcome as well, good answer though.

---

### Post by GhX6GZMB on 2022-02-04
It's just a question of how you like to work:
Some people like GUI tools for for this kind of thing, others (like myself) prefer shortcut keys for maximum efficiency.
I'm sure Flameshot is great, but that's not what the OP wanted/asked for.

---

### Post by guiverc on 2022-02-04
> **1fallen said:**
> Just to let you know ad nothing else: Flameshot — Qt5 based software for interactive screenshot taking. Select the desired area, draw with different tools and enjoy the customization capabilities. [https://wiki.archlinux.org/title/Screen_capture](https://wiki.archlinux.org/title/Screen_capture)
I find it very useful for how to's.


Thanks

I won't write anything currently, but if/when we get another question asking for help, that's when I usually do it  (*point the user here [source], with a local ~howto on our local site).  We get one query like this probably each release/cycle, but next cycle is LTS so it's 3-4 usually...  I'm still waiting for LXQt 1.0.0 to drop into jammy (thru Debian sid this time :P) so as to know what it'll be like next release** first*). 

Thank you; yes the requirements of `flameshot` look good. :P

---

### Post by #&amp;thj^% on 2022-02-04
> **ml9104 said:**
> It's just a question of how you like to work:
Some people like GUI tools for for this kind of thing, others (like myself) prefer shortcut keys for maximum efficiency.
I'm sure Flameshot is great, but that's not what the OP wanted/asked for.

I sense a disturbance in the force here ;) It's all good, your among friends.
```
CLI configuration

You can use the graphical menu to configure Flameshot, but alternatively you can use your terminal or scripts to do so.

    Open the configuration menu:

    flameshot config

    Show the initial help message in the capture mode:

    flameshot config --showhelp true

    For more information about the available options use the help flag:

    flameshot config -h

Config file

You can also edit some of the settings (like overriding the default colors) in the configuration file.
Linux path : ~/.config/flameshot/flameshot.ini.
Windows path : C:\Users\{YOURNAME}\AppData\Roaming\flameshot\flameshot.ini.

When copying over the config file from Linux to Windows or vice versa, make sure to correct the savePath variable,
so that the screenshots save in the right directory on your desired file system.
Keyboard shortcuts

```
Source: [https://github.com/flameshot-org/flameshot](https://github.com/flameshot-org/flameshot)

---

### Post by GhX6GZMB on 2022-02-04
I'm confused about this reply. I only answered the OP's question. And suddenly I'm in the middle of configuring Flameshot?
I only showed a way to configure a shortcut key, nothing else. I'm totally in over my head here. Sorry.
I have a feeling that this has been taken over by developers discussing internal issues.

Sorry, but I'm just a user.
Over and out. (I feel propelled back to the Lubuntu Discourse time) :(

---

### Post by dragonfly41 on 2022-02-04
> [COLOR=#000000]I'm sure Flameshot is great, but that's not what the OP wanted/asked for.[/COLOR][COLOR=#000000]

Just to add some context to my pennyworth, I selected Flameshot since I can grab a batch of multiple regions of screens with single clicks per grab. Buttons, menus etc.
No gui.
I need such a tool to build up many targets on desktop apps and browser screens.
The game plan (in my usage) is desktop automation.[/COLOR]

---

### Post by GhX6GZMB on 2022-02-04
Still not an answer to what the OP asked...
I'm sure your use/application is super-interesting, but...

---

### Post by dragonfly41 on 2022-02-04
This is what OP wrote.  "[COLOR=#000000]Thoughts?"
Now are you the OP or just speaking *your* views?
One click operation is quite feasible.[/COLOR]

---

### Post by #&amp;thj^% on 2022-02-04
> **dragonfly41 said:**
> This is what OP wrote.  "[COLOR=#000000]Thoughts?"
Now are you the OP or just speaking *your* views?
One click operation is quite feasible.[/COLOR]

+1  Me thinks he doth protest to much :)

---

### Post by GhX6GZMB on 2022-02-05
> **dragonfly41 said:**
> [COLOR=#000000]
One click operation is quite feasible.[/COLOR]

Seems to be more like "two-click" (call up program plus Enter). And how do you capture an active window? That's unclear to me.
I installed Flameshot just for fun and tried it. Nice, but somehow a bit deficient. Mind you, that might be because my PrtScr key is already reserved for my own use. Flameshot does not install any shortcut keys by itself, it seems.
The file configuration menu allows me to select a myriad of date formats for file names, I'm unsure why. Additionally, I can select a number of graphic tools that belong more in a drawing editor.
Why they're included in a screen grabber? No idea.

I've removed it again, it brought nothing additional to me. But it's better than ScreenGrab.

---

### Post by dragonfly41 on 2022-02-05
At least you explored it.
I guess that much depends on what you plan to do with screenshots once you have them.
My own interest is in automation and capturing images from regions of the screen. This is required for applications such as machine learning to cite one example. Where we try to match an image with parts of a larger image base.

Taking your questions one by one.

I'm not sure what deficiencies you see.

How ro capture an active window?

Launch the downloaded executable AppImage.

A small Flameshot icon appears in Ubuntu top bar (launchers).

You might wish to setup Configuration before general use.

A bunch of features is displayed offering the more exotic features. 

In **Interface tab**

I only enable

Move
Undo
Redo
Copy
Save
Exit
Accept

This minimises the number of function buttons you will later see.

In Filename **Editor tab** I just use Time. I agree that there are too many options here. Later I change these names and they are chosen to help indexing.

I also suggest setting opacity slider to about 25%.

In **General Tab**

I create the Save Path which in my case is just

~/_FLAMESHOT

The prefix &#8220;**_**&#8221; is a notation I use to bring important folders to the top of the file index.

In **Shortcuts Tab**

Chose the best shortcut for taking screenshots saved to folder (or clipboard if you prefer).

In your case you seem to take just total screenshot.
So look at &#8220;Save screenshot to a file&#8221; which has a default setting of Ctrl+S. If one click operation is required change this setting to suit. But this might conflict with other apps.

So some trial and error is needed.

I try the NumEnter key which is to the far right of the keyboard.

I stay with default **Ctrl+S**..

Now the workflow is 

Select dialog from top tray
Select &#8220;Take Screenshot&#8221;


At this point  floating menu appears on screen:

Mouse
Ctrl+S
Ctrl+C
Mouse Wheel
Right Click
Space
Exit

The one you are interested in is &#8220;Ctrl+S&#8221; and hitting the assigned sjhortcut grabs a screenshot and places in designated folder ~/_FLAMESHOT

 For other scenarios where regions are selected we choose - Mouse and when we left click on mouse, hold down key and drag as a **region selection tool.**
 
 The buttons surrounding the region are a mirror of selections in Configuration > Interface (which you consider to be too numerous).

Really Flameshot excels in rapidly capturing regions.
You can get by without using it if all you are interested in is taking screenshots to put into say YouTube. I am trying to break way from that well worn model of displaying screenshots in tutorials.  Instead I target real desktop applications by clicking on button areas .. in real time. An "autopilot" looking over the user's shoulder.

As we explore more desktop automation this becomes important.   

If you reaaly insist on having a one click operation I can add to the above workflow.

For example I assign just the NumEnter key to launching Albert (another useful tool).

[P.S.] I use gThumb to inspect screenshot image gallery.

---

### Post by GhX6GZMB on 2022-02-05
@dragonfly41:
Wow!
You put a lot of effort into answering here, and I appreciate and respect that. Thank You.

But you and I have completely different workflows, which probably has to do with our work environments.

I just need:
1: a _screen_ shot that I can directly paste into the document I'm currently working on. Or:
2: an _active window_ shot where I can do the same.

I do that with my shortcut keys (PrtScr or Alt+PrtScr) followed by Ctrl+V into Writer, Draw, Impress, whatever. If I need a certain screen cutout, I paste a full screen shot into Kolourpaint and crop it there and then use it. Done.

It saves me a lot of time and effort. Downside is that you need use the keyboard in between.

Cheers.

---

### Post by arius88 on 2022-02-06
Most of this discussion is also over my head, but your initial response was exactly what I needed, ml9104. Thank you.  Only issue is that I don't need it copied to clipboard - I just want the image saved directly into my Pictures folder where I can sort it later.  Is there a way to modify your code to make that happen?

---

### Post by GhX6GZMB on 2022-02-06
Yep.
Actually much simpler from a command point of view (no need for the clipboard).
Commands:

PrtScr:
```
sh -c 'scrot $HOME/Pictures/clip_%Y_%m_%d_%H_%M_%S.png'

```Alt-PrtScr:
```
sh -c 'scrot -u $HOME/Pictures/clip_%Y_%m_%d_%H_%M_%S.png'

```

---

