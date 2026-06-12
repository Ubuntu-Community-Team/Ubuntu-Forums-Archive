---
title: "xscreensaver unlock dialogue, possible to get fonts large enough to see?"
date: 2013-11-21
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-11-21
As things stand, when unlocking from xscreensaver's lock I'm typing blind on faith because the characters (dots, stars, who knows?) are so tiny I can't even tell whether a key press registered once, twice, or not at all.  Using a wireless (ok, a CHEAP wireless) keyboard that's not something that can be taken for granted. Frequently I have to try 3 or 4 times before I get it. I've been searching and reading on this off an on for months and more intensively for the past 48 hours or so.

What I read is, in a word, strange. Seems like it has been a problem for a fair number of people for quite a while, but others seem to have no problem changing their font size. This thread
 [http://ubuntuforums.org/showthread.php?t=2032776&highlight=xscreensaver+missing+fonts](http://ubuntuforums.org/showthread.php?t=2032776&highlight=xscreensaver+missing+fonts)
while actually about changing fonts in the "hacks" (i.e., individual screensavers) may be relevant. It seems to be more technically astute than anything else I've read touching on the subject. But the last post is a year and a half old, it doesn't really address quite the same issue, and anyway I tried the font that was mentioned in there without success. I've tried a lot of different font lines found reccomended in varilus fora  in the .xresources file. All but the last were in exactly the same format. Just now I tried the line in the thread I just referenced, which is a little longer. Still no change. Nothing I put in .xresources or whether I even HAVE an .xresources file makes any difference.

There are a lot of threads about making the unlock dialogue "prettier". I don't give a hoot about how pretty it is. I just want to be able to see the darned thing. 

At this point I can only think of 2 options I haven't tried yet that have a reasonalbe chance of working:

1 - Use a script to call xscreensaver and lower the rez with xrandr before the lock command and raise it after unlocking. I tried that manually and it did work but it was rather slow.
    -- or --
2 - Get the source, see if I can figure out how to edit it so it points to some font known in the civilised world and compile it. I've never done that but perhaps now is the time to learn it.

Any suggestions would be appreciated.

---

### Post by Toz on 2013-11-21
Xscreensaver can be "skinned" by editing the ~/.Xdefaults file (in your home folder). If it is the font size that you want to change, the lines of interest are:
> !font settings
xscreensaver.Dialog.headingFont:        -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-dina-bold-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-dina-medium-r-*-*-10-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-dina-bold-r-*-*-20-*-*-*-*-*-*-*
On my system, I don't have the dina font installed so making changes to those lines won't make a difference. However, I do have the "georgia" font installed, so lets give it a try. (The "xfontsel" program can be used to see which fonts are installed on your system.)

1. Kill the xscreensaver process (it stores the resource information at each startup and we need to have this refreshed):
```
kill -9 $(pidof xscreensaver)
```

2. Edit the .Xdefaults file in your home directory, delete the lines above and replace them with:
```
!font settings
xscreensaver.Dialog.headingFont:        -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
```
...note that I have set the font size to 36.

3. Save the file.

4. Merge the changes in:
```
xrdb -merge ~/.Xdefaults
```

5. Restart the xscreensaver process:
```
xscreensaver -no-splash
```

6. Test. You should get larger font sizes in the xscreensaver unlock screen. Make any other font changes as required following the same process as above. Note that the ~/.Xdefaults file is sourced on every login so you don't have to run "xrdb -merge" every time, only when we are testing (so we don't have to log out and back in again).

---

### Post by Dreamer Fithp Apprentice on 2013-11-23
Thanks, Toz. It's very strange. I distinctly remember composing, previewing, and POSTING (I could have sworn) a reply to this about an hour after your kind response. But it's not here. I must be losing my marbles.

Anyway, we are at least on what is new ground for me here as all the other things I've read on this talk about similar code being put in .Xresources rather than .Xdefaults. I had no .Xdefaults so I made one and tried it 2 ways, first with an exact copy of your code, on the strength of the probability that if you had that font installed and didn't mention having installed it, probably I did too. That didn't cause any change in the font size in the unlock dialogue. So then I used xfontsel, clicked on the pxlsz heading, got a drop down menu of numbers and clicked on the highest one which was 32 and one of the middle asterixes was changed to 32. Then I clicked and chose something for all the other headings until I had a line where all asterixes were replaced with something. If I understand xfontsel correctly to this degree, that line should have fully specified some font that I have installed. I replaced all the corresponding strings in .Xdefaults with with that string and tried again. Both times I rebooted. No change. One point, seemingly odd to me, about xfontsel. The fonts listed don't seem to correspond all that well to the choices I typically get in some application with adjustable fonts, like gedit for instance. It's a much shorter list and only a couple of the entries sound familiar. I'm not sure what to make of that.

Anyway, thanks for the ideas. So far though, I haven't gotten it to work. Now let's see if I can make this post successfully this time.

---

### Post by Toz on 2013-11-23
I think I may have made the .Xdefaults file a while ago myself and have kept recycling it. It shouldn't matter which file you put it in during the testing as long as you merge it in (using "xrdb -merge <file>"). The important thing is to make sure that the file you use is sourced during login. I believe both .Xdefaults and .Xresources are if they exist in the home directory.

As for the fonts, I find you have to find the correct font for rendering or it doesn't work. I just tried a number of different ones displayed in xfontsel, and couldn't get some to work. The georgia font that I used is in the **ttf-mscorefonts-installer** package - make sure it is installed if you want to try the this font. You can check if the font itself is installed via:
```
fc-list  | grep georgia
```

Using this process changes the fonts on the xscreensaver lock screen for me. I am using Xubuntu 13.10.

One final thing - make sure you test using the process I identified above (no rebooting). Once you get that to work, then you can try rebooting to see if it becomes persistent.

---

### Post by Dreamer Fithp Apprentice on 2013-11-23
Thank you again, Toz. I followed your instructions EXACTLY this time, varying nothing. ```
fc-list  | grep georgia
```returned only a new prompt. I installed [B]ttf-mscorefonts-installer, did it again and it showed up this time. I deleted everything in .Xdefaults and copied your code in in it's entirety. Followed the rest of your procedure precisely. Still no change. So I rebooted for good measure. Still no change. 

I find it interesting that you observe some fonts work and others don't. That suggests trying fonts at random or systematically trying all I have may be worthwhile. I'll try that for a while.
[/B]

---

### Post by Toz on 2013-11-24
Not sure if it matters, but that was only a snippet from my .Xdefaults file. Here is the complete listing:
```
! xscreensaver ---------------------------------------------------------------

!font settings
xscreensaver.Dialog.headingFont:        -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
!general dialog box (affects main hostname, username, password text)
xscreensaver.Dialog.foreground:         #EDEDED
xscreensaver.Dialog.background:         #202020
xscreensaver.Dialog.topShadowColor:     #202024
xscreensaver.Dialog.bottomShadowColor:  #202024
xscreensaver.Dialog.Button.foreground:  #EDEDFF
xscreensaver.Dialog.Button.background:  #444
!username/password input box and date text colour
xscreensaver.Dialog.text.foreground:    #EDEDFF
xscreensaver.Dialog.text.background:    #444
xscreensaver.Dialog.internalBorderWidth:24
xscreensaver.Dialog.borderWidth:        0
xscreensaver.Dialog.shadowThickness:    2
!timeout bar (background is actually determined by Dialog.text.background)
xscreensaver.passwd.thermometer.foreground:  #A9B7C4
xscreensaver.passwd.thermometer.background:  #202020
xscreensaver.passwd.thermometer.width:       8
!datestamp format--see the strftime(3) manual page for details
xscreensaver.dateFormat:    %I:%M%P %a %b %d, %Y

```

---

### Post by Toz on 2013-11-24
Do you have a ~/.xscreensaver or a ~/.Xresources file? If so, can you post back the contents?

---

### Post by Dreamer Fithp Apprentice on 2013-11-24
> **Toz said:**
> Do you have a ~/.xscreensaver or a ~/.Xresources file? If so, can you post back the contents?
Thanks again, Toz. I've attached those files and 2 others that might concievably be relevant.  I had to add the extension ".txt" not on the originals to some of them to get them to attach.

---

### Post by Toz on 2013-11-24
Okay, lets try this (using my ~/.Xdefaults config files with the georgia font):

```
sudo bash
cd /usr/share/fonts/truetype/msttcorefonts;mkfontdir
exit
```
...then:
```
xset +fp /usr/share/fonts/truetype/msttcorefonts/
xset fp rehash
```
...then check that georgia appears with:
```
xlsfonts  | grep -i georgia
```

If it does, then merge in the .Xdefaults file:
```
xrdb -merge ~/.Xdefaults
```
...and check to see if the georgia font is merged into your resource file:
```
xrdb -query | grep georgia
```
...if its not, you need to run:
```
xrdb -merge ~/.Xdefaults"
```
...first.

Then lets restart xsscreensaver:
```
xscreensaver-command -restart
```
...and test.

---

### Post by Dreamer Fithp Apprentice on 2013-11-25
Thanks much, Toz. You're taking a lot of time with this and I do appreciate it. Interesting stuff. You're coming up with commands I never heard of and it'll take a bit of studying man pages and such before I can see where you're heading. But I won't hold up for comprehension. For the moment, I follow blindly, which is why I'm unsure whether you really meant that lone unpaired " mark. :) So:

I deleted everything in my .Xdefaults and replaced it with the exact and ENTIRE contents of yours.

Then in lxterminal:```
me@ubuntu:~$ sudo bash
[sudo] password for me: 
root@ubuntu:~# cd /usr/share/fonts/truetype/msttcorefonts;mkfontdir
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# exit
exit
me@ubuntu:~$ xset +fp /usr/share/fonts/truetype/msttcorefonts/
me@ubuntu:~$ xset fp rehash
me@ubuntu:~$ xlsfonts  | grep -i georgia
me@ubuntu:~$ xrdb -merge ~/.Xdefaults"
> ^C
```
At that point I saw the arrow and looked more closely at what I'd copied and pasted and decided the " mark was a typo. So I entered the Cntrl-C [enter] for a new prompt and reentered that line without the " mark and continued:
```
me@ubuntu:~$ xrdb -merge ~/.Xdefaults
me@ubuntu:~$ xscreensaver-command -restart
xscreensaver-command: restarting.

```Then I tested it. The color stuff in the .Xdefaults file was picked up but the font size was unchanged. That, btw, is consistent with the response I've gotten from stuff I've put in .Xresources in the past. I have no problem changing color (except for one of the white areas in the logo I haven't been able to change yet) but nothing I've done affects font size. I can't say I've seen any evidence that the font style has ever been affected either but that's hard to be sure of, since they border on microscopic. So anyway, I thought, what if you really DID mean to have that unpaired " mark? So I did this:```
me@ubuntu:~$ xrdb -merge ~/.Xdefaults"
> xrdb -merge ~/.Xdefaults
> xscreensaver-command -restart
> 
```and concluded it really was a typo.

Then I studied what I'd done to see if maybe I'd left out something unstated but logically implied since I'd been kind of in the copy/paste automaton mode and this part seems odd to me:> **Toz said:**
> ...then check that georgia appears with:
```
xlsfonts  | grep -i georgia
```

If it does, then merge in the .Xdefaults file:
```
xrdb -merge ~/.Xdefaults
```
...and check to see if the georgia font is merged into your resource file:
```
xrdb -query | grep georgia
```
...if its not, you need to run:
```
xrdb -merge ~/.Xdefaults"
```
...first.

Then lets restart xsscreensaver: . . . 

So I check to see if it worked and if it didn't I just do the same thing again? Am I missing something? [see next post - I figured this part out, mea culpa]

---

### Post by Dreamer Fithp Apprentice on 2013-11-25
OK, I kept mulling that and I think I see where I misunderstood. It's the pronoun "it's" in this sentence> **Toz said:**
> ...if its not, you need to run:that I misinterpreted.

Since the response I got to```
xlsfonts  | grep -i georgia
```was just a new prompt, nothing after> **Toz said:**
> ...then check that georgia appears with:
```
xlsfonts  | grep -i georgia
```

If it does, thenapplied, right?

Jeez, I can see why bash needs fi and indents. I'm human and even I can't always read plain english.:)

---

### Post by Toz on 2013-11-25
> **Dreamer Fithp Apprentice said:**
> OK, I kept mulling that and I think I see where I misunderstood. It's the pronoun "it's" in this sentencethat I misinterpreted.

Since the response I got to```
xlsfonts  | grep -i georgia
```was just a new prompt, nothing afterapplied, right?

Jeez, I can see why bash needs fi and indents. I'm human and even I can't always read plain english.:)

Yes, something wrong here, you should have gotten a positive reply. Try the following and post back the results:
1. This will locate the files physically exist on your system:
```
locate -i georgia | grep font | grep truetype
```
...output from my system:
> $ locate -i georgia | grep font | grep truetype
/usr/share/fonts/truetype/droid/DroidSansGeorgian.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf
/usr/share/fonts/truetype/msttcorefonts/georgia.ttf
/usr/share/fonts/truetype/msttcorefonts/georgiab.ttf
/usr/share/fonts/truetype/msttcorefonts/georgiai.ttf
/usr/share/fonts/truetype/msttcorefonts/georgiaz.ttf


2. This will show what fonts are available to your system:
```
fc-list : file | grep -i georgia
```
...output from my system:
> fc-list : file | grep -i georgia
/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiab.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiai.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiaz.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: 
/usr/share/fonts/truetype/droid/DroidSansGeorgian.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: 


If, you don't get the second reply, you need to, as root, run "mkfontdir" in the directory that the font exists (in this case, /usr/share/fonts/truetype/msttcorefonts) which you already did, and it will create a fonts.dir file in that directory. So lets check that it exists:
```
cat fonts.dir | grep "\-georgia\-"
```
...my output:
> # cat fonts.dir | grep "\-georgia\-"
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-adobe-standard
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-ascii-0
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso10646-1
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-1
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-10
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-13
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-15
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-2
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-3
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-4
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-5
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-9
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-e
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-r
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-ru
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-u
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-uni
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-microsoft-cp1252
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-adobe-standard
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-ascii-0
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso10646-1
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-1
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-10
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-13
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-15
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-2
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-3
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-4
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-5
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-9
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-e
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-r
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-ru
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-u
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-uni
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-microsoft-cp1252
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-adobe-standard
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-ascii-0
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso10646-1
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-1
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-10
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-13
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-15
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-2
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-3
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-4
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-5
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-9
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-e
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-r
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-ru
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-u
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-uni
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-microsoft-cp1252
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-adobe-standard
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-ascii-0
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso10646-1
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-1
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-10
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-13
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-15
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-2
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-3
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-4
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-5
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-9
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-e
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-r
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-ru
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-u
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-uni
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-microsoft-cp1252


The above should only need to be done once.

The following two commands make the X server aware of the fonts by adding the path to the fonts to the X server font path:
```
xset +fp /usr/share/fonts/truetype/msttcorefonts/
xset fp rehash
```
...there is no output to the commands but you can check if it worked via:
```
xset q | grep -i font
```
...output from my system:
> $ xset q | grep -i font
Font Path:
  /usr/share/consolefonts/,/usr/share/fonts/truetype/msttcorefonts,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins

...note: this will need to be automated when we get it working by manually adding this path to a config file but more on this later.

Then it should show up using xlsfonts:
```
xlsfonts  | grep -i georgia
```
...the output is similar to the one when you cat'd the fonts.dir file.

Now, if you've made it this far, the next step is to merge the .Xdefaults file into your resource list:
```
xrdb -merge ~/.Xdefaults
```
...and you can check with:
```
xrdb -query
```
...to see that the georgia font is listed. My output:
> $ xrdb -query | grep -i georgia
xscreensaver.Dialog.bodyFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:	-*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.headingFont:	-*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:	-*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*


If it is, restart the xscreensaver:
```
xscreensaver-command -restart
```
...and check the X resources to see that georgia is still listed:
```
xrdb -query
```
...and test again. My output:
> $ xrdb -query | grep -i georgia
xscreensaver.Dialog.bodyFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:	-*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.headingFont:	-*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:	-*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:	-*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*


Can you go through these steps again and post back what results you get so that we can compare?

One final question: what version and flavour of Ubuntu are you using? I'm using Xubuntu 13.10.

---

### Post by Dreamer Fithp Apprentice on 2013-11-25
OK, here is my lxterminal contents verbatim including comments I inserted (with some bumbling) via echo:
```
me@ubuntu:~$ locate -i georgia | grep font | grep truetype
me@ubuntu:~$ fc-list : file | grep -i georgia
/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiab.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiai.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiaz.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: 
me@ubuntu:~$ cat fonts.dir | grep "\-georgia\-"
cat: fonts.dir: No such file or directory
me@ubuntu:~$ cd  /usr/share/fonts/truetype/msttcorefonts
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ mkfontdir
./fonts.dir: fopen(w): Permission denied
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ sudo mkfontdir
[sudo] password for me: 
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ cat fonts.dir | grep "\-georgia\-"
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ fc-list : file | grep -i georgia
/usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiab.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiai.ttf: 
/usr/share/fonts/truetype/msttcorefonts/georgiaz.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: 
/usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: 
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ cat fonts.dir | grep "\-georgia\-"
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ cat /usr/share/fonts/truetype/msttcorefonts/fonts.dir
0
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "
> Ahaa! There is the problem!!!"
bash: !": event not found
> ^C
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "Ahaaa! There is A, maybe THE problem!!!"
bash: !": event not found
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "I thought bash passed everything in the quotes after echo through without trying to interpret it."
I thought bash passed everything in the quotes after echo through without trying to interpret it.
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "I thought bash passed everything in the quotes after echo through without trying to interpret it!"
bash: !": event not found
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "I thought bash passed everything in the quotes after echo through without trying to interpret it\!"
I thought bash passed everything in the quotes after echo through without trying to interpret it\!
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "No more exclamation points are to be echoed. I guess bash likes not the excitement."
No more exclamation points are to be echoed. I guess bash likes not the excitement.
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ echo "Ok. Nothing but a plain zero in fonts.dir, so I'll copy Toz's content in manually with gedit."
Ok. Nothing but a plain zero in fonts.dir, so I'll copy Toz's content in manually with gedit.
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ cat fonts.dir | grep "\-georgia\-"
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-adobe-standard
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-ascii-0
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso10646-1
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-1
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-10
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-13
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-15
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-2
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-3
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-4
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-5
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-iso8859-9
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-e
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-r
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-ru
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-u
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-koi8-uni
Georgia.ttf -microsoft-georgia-medium-r-normal--0-0-0-0-p-0-microsoft-cp1252
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-adobe-standard
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-ascii-0
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso10646-1
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-1
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-10
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-13
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-15
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-2
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-3
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-4
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-5
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-iso8859-9
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-e
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-r
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-ru
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-u
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-koi8-uni
Georgia_Bold.ttf -microsoft-georgia-bold-r-normal--0-0-0-0-p-0-microsoft-cp1252
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-adobe-standard
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-ascii-0
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso10646-1
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-1
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-10
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-13
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-15
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-2
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-3
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-4
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-5
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-iso8859-9
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-e
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-r
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-ru
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-u
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-koi8-uni
Georgia_Italic.ttf -microsoft-georgia-medium-i-normal--0-0-0-0-p-0-microsoft-cp1252
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-adobe-standard
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-ascii-0
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso10646-1
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-1
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-10
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-13
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-15
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-2
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-3
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-4
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-5
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-iso8859-9
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-e
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-r
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-ru
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-u
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-koi8-uni
georgiaz.ttf -microsoft-georgia-bold-i-normal--0-0-0-0-p-0-microsoft-cp1252 
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ xset +fp /usr/share/fonts/truetype/msttcorefonts/
xset:  bad font path element (#0), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ sudo xset +fp /usr/share/fonts/truetype/msttcorefonts/
[sudo] password for me: 
xset:  bad font path element (#0), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ 

```The directory owner is root. Everybody but root is read only. But sudo should have taken care of that. (I even cheated later and tried it after su'ing. Same result.) The file is there. That leaves "Incorrect font server address or syntax". That's an odd error message when I think about it. "or bad syntax"? Uh . . . doesn't xset KNOW whether the syntax is sound or not? If the syntax is bad most commands don't hedge about it, they just say it's bad and give you some example or a generic model. They don't say "Maybe that's wrong". So it must not be referring to a possibility of bad syntax in the command. Maybe in the file content? That leaves "Incorrect font server address". I have to be away for a few hours. I'll startpage.com that phrase when I get back unless you've posted some more suggestions in the meantime. You'll also note that at one point font.dir didn't contain the expected content but only a single character "0", that is a zero without quote marks. So I copied your contents in manually. That may have been a mistake. I'll look closely at that when I get back also.

Thanks a million.

---

### Post by Toz on 2013-11-25
Yes, you shouldn't have copied my content in (sorry I was a little unclear there). Can you please delete /usr/share/fonts/truetype/msttcorefonts/fonts.dir:
```
sudo rm /usr/share/fonts/truetype/msttcorefonts/fonts.dir
```
...and lets start again.

First, what are the contents of /usr/share/fonts/truetype/msttcorefonts:
```
ls /usr/share/fonts/truetype/msttcorefonts
```
...you should see the georgia font listed there (meaning its installed).

Here are the commands in order to be run without any commenting (again post back your results):
```

sudo bash
cd /usr/share/fonts/truetype/msttcorefonts
mkfontdir
cat fonts.dir | grep "\-georgia\-"
exit
xset +fp /usr/share/fonts/truetype/msttcorefonts/
xset fp rehash
xset q | grep -i font
cat ~/.Xdefaults
xrdb -merge ~/.Xdefaults
xrdb -query
xscreensaver-command -restart
xrdb -query
```
...and test.

---

### Post by Dreamer Fithp Apprentice on 2013-11-26
ok.```
me@ubuntu:~$ sudo rm /usr/share/fonts/truetype/msttcorefonts/fonts.dir
[sudo] password for me: 
me@ubuntu:~$ ls /usr/share/fonts/truetype/msttcorefonts
Andale_Mono.ttf              Georgia.ttf
andalemo.ttf                 georgiaz.ttf
arialbd.ttf                  impact.ttf
arialbi.ttf                  Impact.ttf
Arial_Black.ttf              timesbd.ttf
Arial_Bold_Italic.ttf        timesbi.ttf
Arial_Bold.ttf               timesi.ttf
Arial_Italic.ttf             Times_New_Roman_Bold_Italic.ttf
ariali.ttf                   Times_New_Roman_Bold.ttf
arial.ttf                    Times_New_Roman_Italic.ttf
Arial.ttf                    Times_New_Roman.ttf
ariblk.ttf                   times.ttf
comicbd.ttf                  trebucbd.ttf
Comic_Sans_MS_Bold.ttf       trebucbi.ttf
Comic_Sans_MS.ttf            Trebuchet_MS_Bold_Italic.ttf
comic.ttf                    Trebuchet_MS_Bold.ttf
courbd.ttf                   Trebuchet_MS_Italic.ttf
courbi.ttf                   Trebuchet_MS.ttf
Courier_New_Bold_Italic.ttf  trebucit.ttf
Courier_New_Bold.ttf         trebuc.ttf
Courier_New_Italic.ttf       Verdana_Bold_Italic.ttf
Courier_New.ttf              Verdana_Bold.ttf
couri.ttf                    verdanab.ttf
cour.ttf                     Verdana_Italic.ttf
fonts.dir~                   verdanai.ttf
Georgia_Bold_Italic.ttf      verdana.ttf
Georgia_Bold.ttf             Verdana.ttf
georgiab.ttf                 verdanaz.ttf
Georgia_Italic.ttf           webdings.ttf
georgiai.ttf                 Webdings.ttf
georgia.ttf
me@ubuntu:~$ sudo bash
root@ubuntu:~# cd /usr/share/fonts/truetype/msttcorefonts
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# mkfontdir
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# cat fonts.dir | grep "\-georgia\-"
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# exit
exit
me@ubuntu:~$ xset +fp /usr/share/fonts/truetype/msttcorefonts/
me@ubuntu:~$ xset fp rehash
me@ubuntu:~$ xset q | grep -i font
Font Path:
  /usr/share/fonts/truetype/msttcorefonts/,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
me@ubuntu:~$ cat ~/.Xdefaults
! xscreensaver ---------------------------------------------------------------

!font settings
xscreensaver.Dialog.headingFont:        -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.bodyFont:           -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.labelFont:          -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.unameFont:          -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.buttonFont:         -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:           -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.passwdFont:         -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
!general dialog box (affects main hostname, username, password text)
xscreensaver.Dialog.foreground:         #EDEDED
xscreensaver.Dialog.background:         #202020
xscreensaver.Dialog.topShadowColor:     #202024
xscreensaver.Dialog.bottomShadowColor:  #202024
xscreensaver.Dialog.Button.foreground:  #EDEDFF
xscreensaver.Dialog.Button.background:  #444
!username/password input box and date text colour
xscreensaver.Dialog.text.foreground:    #EDEDFF
xscreensaver.Dialog.text.background:    #444
xscreensaver.Dialog.internalBorderWidth:24
xscreensaver.Dialog.borderWidth:        0
xscreensaver.Dialog.shadowThickness:    2
!timeout bar (background is actually determined by Dialog.text.background)
xscreensaver.passwd.thermometer.foreground:  #A9B7C4
xscreensaver.passwd.thermometer.background:  #202020
xscreensaver.passwd.thermometer.width:       8
!datestamp format--see the strftime(3) manual page for details
xscreensaver.dateFormat:    %I:%M%P %a %b %d, %Y
me@ubuntu:~$ xrdb -merge ~/.Xdefaults
me@ubuntu:~$ xrdb -query
*customization:    -color
Xft.lcdfilter:    lcddefault
xscreensaver.Dialog.Button.background:    #444
xscreensaver.Dialog.Button.foreground:    #EDEDFF
xscreensaver.Dialog.background:    #202020
xscreensaver.Dialog.bodyFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.borderWidth:    0
xscreensaver.Dialog.bottomShadowColor:    #202024
xscreensaver.Dialog.buttonFont:    -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.foreground:    #EDEDED
xscreensaver.Dialog.headingFont:    -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.internalBorderWidth:    24
xscreensaver.Dialog.labelFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.shadowThickness:    2
xscreensaver.Dialog.text.background:    #444
xscreensaver.Dialog.text.foreground:    #EDEDFF
xscreensaver.Dialog.topShadowColor:    #202024
xscreensaver.Dialog.unameFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.dateFormat:    %I:%M%P %a %b %d, %Y
xscreensaver.passwd.passwdFont:    -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.thermometer.background:    #202020
xscreensaver.passwd.thermometer.foreground:    #A9B7C4
xscreensaver.passwd.thermometer.width:    8
me@ubuntu:~$ xscreensaver-command -restart
xscreensaver-command: no screensaver is running on display :0
me@ubuntu:~$ xrdb -query
*customization:    -color
Xft.lcdfilter:    lcddefault
xscreensaver.Dialog.Button.background:    #444
xscreensaver.Dialog.Button.foreground:    #EDEDFF
xscreensaver.Dialog.background:    #202020
xscreensaver.Dialog.bodyFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.borderWidth:    0
xscreensaver.Dialog.bottomShadowColor:    #202024
xscreensaver.Dialog.buttonFont:    -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.dateFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.foreground:    #EDEDED
xscreensaver.Dialog.headingFont:    -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.internalBorderWidth:    24
xscreensaver.Dialog.labelFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.Dialog.shadowThickness:    2
xscreensaver.Dialog.text.background:    #444
xscreensaver.Dialog.text.foreground:    #EDEDFF
xscreensaver.Dialog.topShadowColor:    #202024
xscreensaver.Dialog.unameFont:    -*-georgia-medium-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.dateFormat:    %I:%M%P %a %b %d, %Y
xscreensaver.passwd.passwdFont:    -*-georgia-bold-r-*-*-36-*-*-*-*-*-*-*
xscreensaver.passwd.thermometer.background:    #202020
xscreensaver.passwd.thermometer.foreground:    #A9B7C4
xscreensaver.passwd.thermometer.width:    8
me@ubuntu:~$ 

```Tested, no change in font size.

To that I"d add```
me@ubuntu:~$ cat /usr/share/fonts/truetype/msttcorefonts/fonts.dir
0
me@ubuntu:~$ 
```Thanks again. Must sleep. Later.

---

### Post by Toz on 2013-11-26
There are two things that I notice:

1. mkfontdir isn't working. Not exactly sure why. Its not creating the proper fonts.dir file. I also notice that there is a **fonts.dir~**  (tilde after the file name) in your /usr/share/fonts/truetype/msttcorefonts directory. I wonder if this may be some sort of leftover temporary file that is preventing mkfontdir from writing. Can you please delete that file and try to run mkfontdir (as root) in that directory again. Successful completion of that command should result in a fonts.dir file that lists all of your fonts out that exist in that directory.

2. "xscreensaver-command  -restart" errored out saying it wasn't running. Did you have it disabled at that time? What does the following command return:
```
ps -ef | grep screensaver
```

Everything else looks good.

---

### Post by Dreamer Fithp Apprentice on 2013-11-26
> **Toz said:**
> I also notice that there is a **fonts.dir~**  (tilde after the file name) in your /usr/share/fonts/truetype/msttcorefonts directory.Gedit made that when I manually edited the file earlier.> **Toz said:**
> Can you please delete that file and try to run  mkfontdir (as root) in that directory again. Successful completion of  that command should result in a fonts.dir file that lists all of your  fonts out that exist in that directory.```
me@ubuntu:~$ cd /usr/share/fonts/truetype/msttcorefonts/
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ sudo rm ./fonts.dir~
[sudo] password for me: 
rm: cannot remove ‘./fonts.dir~’: No such file or directory
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ 
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$  echo "That's because I'd already done it. I followed all your instructions and was going to paste the results into this post, but I accidentally closed the terminal before I got it pasted in so I'm doing it again to make a record."
That's because I'd already done it. I followed all your instructions and was going to paste the results into this post, but I accidentally closed the terminal before I got it pasted in so I'm doing it again to make a record.
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ sudo mkfontdir
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ ls ./fon*
./fonts.dir
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ cat ./fonts.dir
0
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ 
```

> **Toz said:**
>  "xscreensaver-command  -restart" errored out saying  it wasn't running. Did you have it disabled at that time?Not disabled. Probably unstarted. I don't start it automatically. My lock script starts it and issues the lock command. So it isn't running until after the first time I need it.

> **Toz said:**
> What does the following command return:
```
ps -ef | grep screensaver
``````
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ ps -ef | grep screensaver
me         2403  2402  0 13:36 ?        00:00:00 xscreensaver
me         2414     1  0 13:36 ?        00:00:00 conky -o -c .conkyrc-clock.screensaver
me         2701  2590  0 14:05 pts/2    00:00:00 grep --color=auto screensaver
me@ubuntu:/usr/share/fonts/truetype/msttcorefonts$ 

```Now THAT'S interesting. I wonder what autoscreensaver is.

Be that as it may, looking back at some of the output I posted earlier I notice this:```
xset:  bad font path element (#0), possible causes are:     Directory does not exist or has wrong permissions     Directory missing fonts.dir     Incorrect font server address or syntax
```So:
```
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# xfsinfo
xfsinfo: no font server defined
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# xfs
_FontTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_FontTransMakeAllCOTSServerListeners: server already running

```Notice it doesn't return a prompt. I haven't figured out what to do about this, but it's hard not to believe it is near the root of the problem.

Thanks much, Toz. I'll ponder and startpage.com this for a bit.

---

### Post by Toz on 2013-11-26
> **Dreamer Fithp Apprentice said:**
> Now THAT'S interesting. I wonder what autoscreensaver is.
Don't worry about that, its just the process running your grep command that is colouring the output.

> Be that as it may, looking back at some of the output I posted earlier I notice this:```
xset:  bad font path element (#0), possible causes are:     Directory does not exist or has wrong permissions     Directory missing fonts.dir     
```
This is the problem, its not creating the fonts.dir file for you. The question is why?

> Incorrect font server address or syntax[/CODE]So:
```
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# xfsinfo
xfsinfo: no font server defined
root@ubuntu:/usr/share/fonts/truetype/msttcorefonts# xfs
_FontTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_FontTransMakeAllCOTSServerListeners: server already running

```Notice it doesn't return a prompt. I haven't figured out what to do about this, but it's hard not to believe it is near the root of the problem.
I get this same message on my system when I run xfsinfo or xfs - I don't think its related.

> Thanks much, Toz. I'll ponder and startpage.com this for a bit.
I just installed a new Xubuntu 13.10 system for a test project - I'm going to try these commands from scratch and see what I get.

You're using Ubuntu right? Not the xubuntu flavour. What version?

---

### Post by Toz on 2013-11-26
Okay, it didn't work for me either initially - I had to run mkfontscale to get it to catch. So lets try again.

First get root and get to the msttcorefonts directory:
```
sudo bash
cd /usr/share/fonts/truetype/msttcorefonts
```

Let's delete the cruft in there:
```
rm fonts.*
```

Then create the fonts.dir file (and fonts.scale):
```
mkfontscale
mkfontdir
exit
```
...you should now have a /usr/share/fonts/truetype/msttcorefonts/fonts.dir file that contains font info.

Then lets setup your environment:
```
xset +fp /usr/share/fonts/truetype/msttcorefonts/
xset fp rehash
xrdb -merge ~/.Xdefaults
```
...assuming that my georgia fonts code is in ~/.Xdefaults.

And finally restart xscreensaver and test:
```
xscreensaver-command -restart
```

Fingers crossed.

---

### Post by Dreamer Fithp Apprentice on 2013-11-26
> **Toz said:**
> I get this same message on my system when I run xfsinfo or xfs - I don't think its related.You are absolutely correct, sir; and I'd have beat my head against that for weeks without your help. It seemed so OBVIOUSLY a likely culprit.> **Toz said:**
> I just installed a new Xubuntu 13.10 system for a test project - I'm going to try these commands from scratch and see what I get. . . . Okay, it didn't work for me either initiallyThanks. It is gratifying to know the difficultywas there right out of the box rather than produced by my fiddling.But the big news is - THAT WORKED!!!!! 
ADDED BY EDIT: But it hasn't survived reboot. It's back to small fonts now. So I must retract my "solved", but clearly this is progress. More - I can reinstate the large fonts by entering the last 4 commands again. If nothing else I could put them in an autostart script.

Thanks very much, Toz. Truly above and beyond. I owe you one.

---

### Post by Dreamer Fithp Apprentice on 2013-11-27
Update: I renamed .Xdefaults .Xdefaults-bak-Toz-version, made a similar copy of my .Xresources, and copied the font statements from .Xdefaults into .Xresources. It still reverts to small fonts upon reboot. However the one file seems to work just as well as both. 

I found I don't need all of the last 4 commands to reset font size of the unlock dialogue after rebooting reverts it to small fonts, just the 2 xset commands:```
xset +fp /usr/share/fonts/truetype/msttcorefonts/
xset fp rehash
```I'm going to read up on xset a bit. Probably I'll put these 2 commands in an autostart script.

I'll post back and mark this solved when I have this fixed so it survives reboot.

---

### Post by Toz on 2013-11-27
If you have an /etc/X11/xorg.conf file, then add the new directory to the Files Section as a new Fontpath. For example (something like):
```

Section "Files"
    FontPath    "/usr/share/fonts/100dpi"
    FontPath    "/usr/share/fonts/75dpi"
    FontPath    "/usr/share/fonts/cantarell"
    FontPath    "/usr/share/fonts/cyrillic"
    FontPath    "/usr/share/fonts/encodings"
    FontPath    "/usr/share/fonts/local"
    FontPath    "/usr/share/fonts/misc"
    FontPath    "/usr/share/fonts/truetype"
    FontPath    "/usr/share/fonts/TTF"
    FontPath    "/usr/share/fonts/util"
**[COLOR="#FF0000"]    FontPath   "/usr/share/fonts/truetype/msttcorefonts/"[/COLOR]**
EndSection
```
...NOTE: don't use the contents in their entirety - just add the the msttcorefonts line to your existing FontPaths.

If you don't have an /etc/X11/xorg.conf file, try creating **/usr/share/X11/xorg.conf.d/50-fonts.conf** will the following content:
```
Section "Files"
    FontPath   "/usr/share/fonts/truetype/msttcorefonts/"
EndSection
```

It should survive the reboot by having X automatically set the fontpaths for you.

---

### Post by Dreamer Fithp Apprentice on 2013-11-29
> **Toz said:**
> If you have an /etc/X11/xorg.conf file, then add the new directory to the Files Section as a new Fontpath. For example (something like):
```

Section "Files"
    FontPath    "/usr/share/fonts/100dpi"
    FontPath    "/usr/share/fonts/75dpi"
    FontPath    "/usr/share/fonts/cantarell"
    FontPath    "/usr/share/fonts/cyrillic"
    FontPath    "/usr/share/fonts/encodings"
    FontPath    "/usr/share/fonts/local"
    FontPath    "/usr/share/fonts/misc"
    FontPath    "/usr/share/fonts/truetype"
    FontPath    "/usr/share/fonts/TTF"
    FontPath    "/usr/share/fonts/util"
**[COLOR=#FF0000]    FontPath   "/usr/share/fonts/truetype/msttcorefonts/"[/COLOR]**
EndSection
```
...NOTE: don't use the contents in their entirety - just add the the msttcorefonts line to your existing FontPaths.That works for me. Thanks a million, Toz. A matter of curiosity - my xorg.conf had nothing between the 'Section "Files"' line and the 'EndSection' line. Now it has just the one line. Does that account for the fact the fonts listed by xfontsel don't seem to include more than small fraction of those that a font-settable app like gedit for instance has available to it? Does that mean gedit has a different mechanism for finding the fonts or does it mean something isn't quite right somewhere? Should those other fonts be showing up in that file and be visible to xfontsel? This isn't an important matter - you solved the important thing - I'm just curious

---

### Post by Toz on 2013-11-29
> **Dreamer Fithp Apprentice said:**
> That works for me. Thanks a million, Toz. A matter of curiosity - my xorg.conf had nothing between the 'Section "Files"' line and the 'EndSection' line. Now it has just the one line.
Alot of stuff is done automatically by X now, you don't really need to specify an xorg file (or conf files in /usr/share/X11/xorg.conf.d) unless you need to do something specific - like what we did above. To see what X does automatically, have a look at your /var/log/Xorg.0.log file to see, in this case fonts, are being set.
> Does that account for the fact the fonts listed by xfontsel don't seem to include more than small fraction of those that a font-settable app like gedit for instance has available to it? Does that mean gedit has a different mechanism for finding the fonts or does it mean something isn't quite right somewhere? Should those other fonts be showing up in that file and be visible to xfontsel? This isn't an important matter - you solved the important thing - I'm just curious
I haven't played with fonts for a while so I'm not exactly sure. I don't have access to a linux computer right now to check, but find the font on your system, make sure that a fonts.scale and fonts.dir files exist and check /var/log/Xorg.0.log to see if the font path is being recognized. If not, create the files (mkfontscale & mkfontdir) and add the path to the file you created for this font. See if that makes xfontsel recognize them.

---

### Post by Dreamer Fithp Apprentice on 2013-12-01
Thanks again, Toz. I'll mess with this a bit and if I find anything interesting I'll post back here. Have a Super Solticial Season!

---

