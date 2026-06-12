---
title: "Keyboard hell -- my forward slash isn't working"
date: 2013-06-28
forum: General Help
---

### Post by RangerK on 2013-06-28
My forward slash doesn't work on Ubuntu.  (Everything works fine when I connect the keyboard to my old XP laptop.)

Here's a photo of the keyboard on my new Xubuntu 12.04 box:

[IMG]http://i.imgur.com/d4ESYn6s.jpg[/IMG]

Please ignore the Cyrillic letters.  The keyboard is a logitech k120.  It's a British layout ([http://en.wikipedia.org/wiki/File:KB_United_Kingdom.svg](http://en.wikipedia.org/wiki/File:KB_United_Kingdom.svg)), but I set it to English US so that the double quote -- " -- is in the usual place.

Everything works fine except for the forward slash.  They key labelled with the forward slash which you can see in the photo gives the characters "<" or with the shift key ">".

Those characters already exist in their usualy places above the comma and period and work fine.

Can anyone recommend how I might troubleshoot / work around?  It's super annoying to have to cut and paste forward slashes.

---

### Post by HermanAB on 2013-06-28
Howdy,

Years ago, my T key stopped working.  It has something to do with the configuration of X going bad.  A temporary fix is to copy and paste the missing letter, while a permanent fix is to define the key again, using xmodmap:
[https://www.google.ae/search?q=xmodmap&rlz=1C5CHFA_enAE535AE537&oq=xmodmap&aqs=chrome.0.57j0l3.4614j0&sourceid=chrome&ie=UTF-8](https://www.google.ae/search?q=xmodmap&rlz=1C5CHFA_enAE535AE537&oq=xmodmap&aqs=chrome.0.57j0l3.4614j0&sourceid=chrome&ie=UTF-8)

---

### Post by Bronie12345 on 2013-06-28
Perhaps putting your keyboard layout to us:int might help (it did for me when I had the problem)
Other than that: until you have found a solution or different keyboard, while using bash you can use tab to cheat using auto-complete.

---

### Post by HermanAB on 2013-06-28
Removing duplicate. Something wrong with this bulletin board.

---

### Post by Impavidus on 2013-06-28
The source of the the problem is of course that the US english layout doesn't have a key at that location, but has the \| key above the enter, where your keyboard has an enlarged enter key. This causes confusion. I never tried this, but with xev you may be able to find the key code of your \| key and with xmodmap you may be able to reconfigure it as the key you really want there. Ask google about xmodmap.

---

### Post by RangerK on 2013-06-29
Thanks for pointing me in the right direction with xmodmap.  I found the  clearest directions here:  [http://www.ehow.com/how_2180748_command-linux-swap-keyboard-keys.html](http://www.ehow.com/how_2180748_command-linux-swap-keyboard-keys.html)

Basically,  you use either the command 'xev' or 'xmodmap -pke' to figure out the  keycode of the key you want to change.  Then you either create or edit a  .xmodmaprc file with a line 'keycode [#] = [desired key] [desired  shift-key].

It says to put the .xmodmaprc in your home directory and then re-login.

To  test, I made a file called .xmodmaprc with the single line: 'keycode 94 = a A'.

It didn't seem to work.   I tried a 'chmod 777' on the .xmodmaprc file.  That didn't seem to  work either.  Any ideas?

---

### Post by Impavidus on 2013-06-29
The chmod 777 is not necessary, you can change that back to the default permissions.

I don't know whether your .xmodmaprc should be loaded automatically. You may have to load your .xmodmaprc explicitly by running the command ```
xmodmap .xmodmaprc
``` You can put that in a login script.

---

### Post by Zill on 2013-06-29
RangerK:  PC keyboards are so cheap that, personally, I would not mess about trying to get one with a non-standard configuration working.  A new keyboard can be bought for around £6 (UK) with free shipping!  That's around $10 for those of you in the USA. ;-)

[Black USB Wired Stylish Slim QWERTY KeyBoard UK EU Layout For PC Computer Laptop]("http://www.ebay.co.uk/itm/Black-USB-Wired-Stylish-Slim-QWERTY-KeyBoard-UK-EU-Layout-For-PC-Computer-Laptop-/310394005415?pt=UK_Computing_ComputerComponents_KeyboardsMice&hash=item4844eca7a7")

---

### Post by JKyleOKC on 2013-06-29
> **RangerK said:**
> To  test, I made a file called .xmodmaprc with the single line: 'keycode 94 = a A'.

It didn't seem to work.   I tried a 'chmod 777' on the .xmodmaprc file.  That didn't seem to  work either.  Any ideas?In a terminal window, type "man xmodmap" which will get you the "man(ual) page" describing the command in detail. Unlike many man pages, the one for xmodmap is pretty clear and not overly burdened with tech jargon.

I believe the step that you missed on your test was to execute the "xmodmap" command from the command line, once you had created the .xmodmaprc file. Doing this should cause the system to modify the existing keyboard map, using the rule you had stored in the file. If this works, you can then add that xmodmap command to your login startup sequence. Since I use Xubuntu rather than Unity, I can't tell you exactly how to do so, but I'm sure that others can provide this information. While you are testing, just remember to execute the command after each change you make to the file.

Hope this helps; you're definitely making progress!

---

### Post by RangerK on 2013-06-29
Okay.  So there's a few ways to do this from the command line.

1) xmodmap -e "keycode 94 = slash"

If I wanted the key to be to represent something different, say, 'B' when Shift is pressed, I'd use

xmodmap -e "keycode 94 = slash B"

2) make a file with the single line

keycode 94 = slash

I called the file .xmodmap, and to make the change, I used the command

xmodmap .xmodmap

3) make a script (my first script! ) with the following content:
#!/bit/bash
xmodmap -e "keycode 94 = slash"

Call the file, say, myawesomescript.sh, and execute it with ./myawesomescript.sh

The most readable & comprehensive guide I found to xmodmap was here:  [http://offend.me.uk/blog/14/](http://offend.me.uk/blog/14/)

My problem has now become how to get a script to run at startup.  I really, really, really wanted to solve it myself, but I'm throwing in the towel.  But this is a different topic --------->[http://ubuntuforums.org/showthread.php?t=2158599&p=12711317#post12711317](http://ubuntuforums.org/showthread.php?t=2158599&p=12711317#post12711317)

---

