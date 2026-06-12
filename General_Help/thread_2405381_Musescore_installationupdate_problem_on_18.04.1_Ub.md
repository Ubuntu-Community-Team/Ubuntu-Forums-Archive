---
title: "Musescore installation/update problem on 18.04.1 Ubuntu"
date: 2018-11-05
forum: General Help
---

### Post by Richard_York on 2018-11-05
[SIZE=2]I've newly installed Ubuntu 18.04.1 to dual boot with Windows 10, computer details at the foot of this post. It's a new-to-me desktop machine built in 2011.

I loaded Musescore from the software centre, realised it was only version 2, so tried to update it using [http://omgfoss.com/how-to-install-musescore-in-ubuntu-18-04-lts/](http://omgfoss.com/how-to-install-musescore-in-ubuntu-18-04-lts/)  copying and pasting the lines for the terminal given in the PPA section. It seems this was the wrong thing to do.

Where Musescore had worked fine, it now fails: the Start Centre comes up but no workspace, and nothing clicks open from the desktop, but what's there won't close either. Clicking on Quit on the drop-down menu from the top bar has no effect, it only clears when I restart the computer.

I work at the level of following simple instruction steps but with little understanding of why, so now I'm stuck. 

One option would be to remove and re-install the whole Ubuntu, a frustrating thing but I'd do it if it's the easiest way.
Alternatively, is there a way I can get rid of the mess I've made?
And if so, how can I safely update to the more useful version of Musescore? - is it better to simply stick with the older version from the Software centre, or use those PPA method instructions in the first place?

Thanks.

Intel i5-2400
Asus P8Z68-V LX Mainboard
8GB Kingston HyperX DDR3
Graphics card,  NVIDIA GT 710/REV 1.0
320GB Hard Disk
[/SIZE]

---

### Post by dragonfly41 on 2018-11-05
I can advise that Musescore 2.3.2 installs on Ubuntu 16.04.  I have just installed it afresh.

I suggest that you install Y PPA Manager which is a tool to tidy up PPA installations.
You can do this manually but using a GUI might help you.
Also use Synaptic to purge any old installation of Musecore.
Then try again to install Musecore.

I am not a musician but supported another user who was working with lilypond.org (which also works from the command line).

---

### Post by Richard_York on 2018-11-05
Thanks. 
While Y PPA Manager isn't on the Software centre, I found this: [https://y-ppa-manager.en.uptodown.com/ubuntu](https://y-ppa-manager.en.uptodown.com/ubuntu)
Having already messed up by under-informed enthusiasm I'm being cautious: is this the one?

I have Synaptic, though use it with some trepidation as I don't understand it well and don't want to do more damage. Should I use that to clean up before installing  the Y PPA manager?

I've heard good things about Lilypond. Without wanting to get off topic, I like Musescore because I can customise it to notate music for Wire strung harp.

---

### Post by dragonfly41 on 2018-11-05
The answer is yes.

Here is one article explaining how to remove/purge (make sure that you first backup any developed Musecore scripts you might have).

[https://www.howtoinstall.co/en/ubuntu/xenial/musescore?action=remove](https://www.howtoinstall.co/en/ubuntu/xenial/musescore?action=remove)

The Y PPA link you quote is the correct one.  Install this after purging Musecore.

Then launch Y PPA gui and remove the PPA which you earlier tried unsuccessfully.

These steps should purge all references to Musecore (apt installed and ppa listed).

Now you can start afresh and  add the correct PPA information.

I can't comment on music notations - it is all double Dutch to me.  
I just regard the notations as patterns.
While experimenting I have been playing around rendering the lilypond glyphs as SVG in Inkscape.
The snippets repository is here ...

[http://lsr.di.unimi.it/LSR/Search](http://lsr.di.unimi.it/LSR/Search)

---

### Post by Richard_York on 2018-11-05
Thanks.
This is where your comment on music as Double Dutch is relevant... I think I did what the pattern of the words said, but with little understanding, and now am lost again!

I followed the instructions on your link to remove & purge Musescore using the terminal. This seemed to work fine.

I went to the Y PPA site and downloaded/installed from there. At least, I thought I had.
 - I clicked on "Download", clicked the option which was suggested of opening it with the installer, which brought up the Software centre page.
I clicked on "install" there. The orange progress line whipped across to 100%, vanished, and the "install" box stayed unchanged and didn't register it as installed.
It's not appearing in the grid of apps at the bottom of the Dash. Typing Y PPA into the Activities search at the top of the screen offers other things, but not that.

Should I have asked it to Save instead?

So I hope I'm not wasting your time here, but will be grateful for the next step, please.

Maybe "launch Y PPA gui" will then also become clear. I get stuck on the "gui" bit. I'm used to working on Ubuntu14, and  the 18 interface is still very new for me. But we're making progress!

---

### Post by mc4man on 2018-11-05
If musescore upgraded after adding the ppa then nothing done wrong there.

if you still have the ppa version installed try running this command, then open musescore from a terminal, see if any errors are reported.
```
rm .config/MuseScore/MuseScore2.ini
```
Then just 
```
musescore
```
Normally it would just show this on opening
> $ musescore
initScoreFonts 0x563e5387ebe0
libpng warning: iCCP: known incorrect sRGB profile
Creating interface for ScoreView object
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile


---

### Post by Richard_York on 2018-11-05
Having done the steps described already, it's evidently taken most of it it away, though I see the folder's still in "Documents"

Here's what the terminal gives: [ATTACH=CONFIG]281553[/ATTACH]

---

### Post by dragonfly41 on 2018-11-05
I'm sorry if I threw in this extra step to install Y PPA Manager (gui is short for "Graphical User Interface" .. or window ..  as distinct from command line operations) but it should help once you get it installed. In fact I have opened Synaptic Package Manager, searched for "PPA" and I see that it can be installed from Software Centre.

So just try command ..

sudo apt install y-ppa-manager

Then when installed launch it to inspect your PPA installation(s).

---

### Post by mc4man on 2018-11-05
> **Richard_York said:**
> Having done the steps described already, it's evidently taken most of it it away, though I see the folder's still in "Documents"

Here's what the terminal gives: [ATTACH=CONFIG]281553[/ATTACH]
Trying the ppa version it seems to work ok here in 18.04.1, to try again go 
```

sudo add-apt-repository ppa:mscore-ubuntu/mscore-stable
```
```
sudo apt update
```
```
sudo apt install musescore
```
```
musescore
```

---

### Post by Richard_York on 2018-11-06
Thanks both.

Dragonfly, I just tried that and the terminal shows:

E: Unable to locate package y-ppa-manager


So I tried copying mc4man's code into the terminal. And I'm back to where I started: Musescore comes up, gives me the Start Centre, but while it shows previews of the working space when I click on the icon screen left on the Dash, it won't come up, nor will it respond to instructions to Quit.
This behaviour only applies to Musescore - I just tried opening windows on Libre Office and Text editor and they behaved as they should. Meanwhile the terminal comes up with:

richard@LizardsDesktop:~$ musescore
initScoreFonts 0x56114be68410
libpng warning: iCCP: known incorrect sRGB profile
Creating interface for ScoreView object
libpng warning: iCCP: known incorrect sRGB profile
libpng warning: iCCP: known incorrect sRGB profile


I guess I need to purge the whole thing and start again. I do now have Synaptic Manager installed. I'm wary of it, but willing to follow instructions if that's a more reliable way of getting this working. But I'll not try anything until further guidance here, in case I make things worse.

Thanks for your patience.

---

### Post by mc4man on 2018-11-06
When you open it do you get 2 windows, MuseScore2: Title & Start Center?

Edit: something like the screenshot?

---

### Post by Richard_York on 2018-11-06
The screen shot is what I'd expect. But I only get one window, the Start Center. If I press on "New score" it then shows a page of music staves in the preview window, but not the main screen.

---

### Post by dragonfly41 on 2018-11-06
I am able to create that scenario by minimising musescore window which leaves only Start Center showing.
Is it possible that you have minimised Musescore window?

In command terminal run .. musescore --help

There are some options you might try

In my desktop I have docky installed and I can just click on Musescore button (in Docky bar at bottom of page)  to maximise/minimise Musescore window.

---

### Post by Richard_York on 2018-11-06
(Written from different computer) I don't think I've minimised it, or would expect it to appear when I click on it from the preview... . Maybe I'm making a new-to-Ubuntu18 error here?
 I have to be out this evening now, but will try tomorrow. Thanks again.

---

### Post by Richard_York on 2018-11-07
In response to these suggestions - this query has suddenly changed shape. Does it need to become a new thread?
 
I was going to upload two screenshots, one showing the result of  asking the terminal for musescore help, ( it's a list of letters with what they relate to, and at the bottom,
"Arguments:   scorefiles   The files to open"), and the other showing what I get when I ask the Start Centre to open a score.

For some reason the attachments refuse to upload. I've uploaded others before from here, but now pressing the "upload" button after having chosen my file gets no response. That's maybe not the important issue, however.

Screen size - when I viewed the reduced scale screenshot of Musescore, I realised it was two screens wide. The image shows the orange Bionic Beaver screen with a preview panel on the left, showing the score page I can't get to open, but then there's another whole screen to the right of this in the picture, with a rather greyed image of just that score page, like a ghost of a second screen which I can't see in reality. 

I'm now well out of my depth!

When my local computer shop had to update the graphics card recently, because the installed one wouldn't work with Windows 10's latest updates, the guy had problems, which he told me weren't unusual, of Windows insisting there were three display screens, when he had to persuade it to show only the one which existed. The behaviour is somewhat the same - in Windows it appeared to open, but wasn't apparently responding to commands, but was actually responding on a non-existent screen which it believed existed.

You may see from my thread here, [https://ubuntuforums.org/showthread.php?t=2405207](https://ubuntuforums.org/showthread.php?t=2405207), which in turn links to a previous thread, that I needed guidance to get the right screen driver to work with the NVIDIA card now in the machine when loading Ubuntu18 on.

Is this new issue possibly in some way related to that?

Thanks.

I should add - this problem seems to be special to Musescore. I can have a preview of two things open from Files, can click either of them, and have either opening or closing as they should. I find this a bit reassuring.

---

### Post by mc4man on 2018-11-07
Any difference if you go 
```
musescore -R
```
or
```
musescore -F
```

---

### Post by dragonfly41 on 2018-11-07
> *When my local computer shop had to update the graphics card recently, because the installed one wouldn't work with Windows 10's latest updates, the guy had problems, which he told me weren't unusual, of Windows insisting there were three display screens, when he had to persuade it to show only the one which existed. The behaviour is somewhat the same - in Windows it appeared to open, but wasn't apparently responding to commands, but was actually responding on a non-existent screen which it believed existed.*

I smell a rat here.

Bear in mind that I am on Ubuntu 16.04, not 18.04.  I too have had issues with offscreen windows.
You might experiment with hitting the SuperKey (the windows icon) plus P Key to cycle through any multiple window views you might have.

I would first launch System Settings (click on the top bar, far right, cog icon and System Settings is in dropdown menu).

First check point:

Go to Personal > Appearance > Behaviour
check that you do not have Enable workspaces ticked (your Musescore window might be hidden in a workspace).

Second check point:

Go to Hardware > Screen display
what do you see .. multiple displays?

Third check point:

When you move the cursor on screen does the cursor disappear at edge of screen or does it stop when hitting screen borders?

...

Regarding my earlier suggestion to install docky you can use a simpler approach.

Hold down Alt key and then hit Tab key to toggle through application windows? Do you see Musescore window?

...

---

### Post by Richard_York on 2018-11-08
Thanks both. I'll take them in order.
 Musescore -R produced
"libpng warning: iCCP: known incorrect sRGB profile
unknown file suffix <>, name <R>"  
 and Musescore - F   gets me the same warning. 
Musescore opened, clicking on asking it to open a score produced
"Creating interface for ScoreView object" on the terminal - sorry, I'm still not able to upload images for some reason - but just the same behaviour on the screen I can see as I had before.

But.. I then moved onto dragonfly41's post: I think your smelt rat was the right rat! And the off-screen behaviour of the cursor was indeed a clue.

I started with Super+P, moved from there into settings... they're under different headings on 18, but I found screen display, and without troubling you with all the various experiments, I've ended up with a working Musescore, and apparently other things functioning too. I had to switch to "single display" and alter the screen size. I haven't yet found out how to detect the number of px's on this screen (a freebie pass-on) but rather at random tried one or two until it looked about right. 

So I believe this problem is now solved, and thank you very much.

Because Life Outside the Screen means I now have to be away from this set until Monday, I'll not mark it as solved until I've had time to test more, but all appears well. Thanks again all who've helped get me there.

---

