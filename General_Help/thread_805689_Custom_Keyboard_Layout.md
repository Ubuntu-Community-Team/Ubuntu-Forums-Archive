---
title: "Custom Keyboard Layout"
date: 2008-05-24
forum: General Help
---

### Post by frogitts on 2008-05-24
I created a custom keyboard layout that uses the third level chooser to type ä,ö,ü,Ä,Ö,Ü, and ß, since I often type in German but have an English keyboard. However, sometimes with some applications (like Firefox, for instance) the third level chooser will stop working. To fix it, I have to go to System->Preferences->Keyboard->Layouts, open Layout Options, deselect the third level chooser (I use Right Alt), close Layout Options, open Layout Options again, reselect Right Alt, and then close it all. This fixes it every time.

I have two possible layouts, this and Greek, with this one being the default. "Separate Layout for Each Window" is unchecked.

Anyone know why this is happening and what I can do to keep the third level chooser on all the time?

---

### Post by frogitts on 2008-05-29
Well, it's still happening, and it's really bugging the crap out of me. I have, however, found that all I have to do to fix the problem (whether it's in Pidgin, Firefox, Terminal, or whatever) is open the keyboard preferences (which I have on my panel, since this happens at least twice a day), Layouts->Layout Options->Third Level Choosers, then uncheck and recheck the "Press Right Alt Key to choose third level" box, close out of the two windows, and it works. No restarting of the app or anything. I guess my next step is to submit this as a bug, but I just wanted to see if anyone knew if it's just some rogue setting I have or an actual bug in Ubuntu before I head that direction.

---

### Post by frogitts on 2008-06-05
Tried another solution. I used the SCIM Input Method Setup and checked "Share the same input method across all applications" under the FrontEnd section and disabled the English/European option under the IMEngine setup. No dice - it held for a while, but I just tried to reply to an email in Gmail and it didn't recognize the third level chooser. Incidentally, during this time that it had been working, no third level chooser was specified in System > Preferences > Keyboard > Layouts > Layout Options. Specifying one was enough to fix it back to the way it should be. Still annoying.

Anyone know how to specify a third level chooser AND HAVE IT STICK?!?

---

### Post by unutbu on 2008-06-05
I have an idea, which *if* it works, would preserve your custom keyboard layout throughout your X session. The problem is, it is a hack, not a clean solution.

Essentially, it is this:

Step 1) Find a command to monitor your current layout.

Step 2) Find a command to change your current layout.

Step 3) Write a script that will periodically monitor your current layout. If it changes to something you don't want, change the layout back to what you want. 

Step 4a) Enter the script as a cron job so it will run every 5 seconds.

Step 4b) Alternatively, if you know the layout only gets messed up when you launch certain applications, then you could write wrapper scripts so that the script in Step 3 is run immediately after the problem application is run, thus correcting the layout.

I think I know how to do each of these steps, but I'd rather not explain it all unless you find the "solution" acceptable.

---

### Post by frogitts on 2008-06-06
Well, that's definitely a hack, but a couple parts of my setup are already supported by hacks, so I'm not opposed to it! :)

Besides, I'd really like to know, if you know, a command to monitor my current layout and change the current third level chooser.

---

### Post by unutbu on 2008-06-06
Copy the following script to a file. Let's call it 'probe-kbd'.

```
#!/bin/sh
echo "% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/general"
gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/general
echo
echo "% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd"
gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd
echo
echo "% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd.sysbackup"
gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd.sysbackup
echo
echo "% xprop -root | grep XKB"
xprop -root | grep XKB
```

Make it executable:
```
chmod 755 probe-kbd
```

Set up your keyboard as you like it, then run

```
probe-kbd > probe-kbd-good
```

Now wait for or induce your machine to change the layout. Then run
```
probe-kbd > probe-kbd-bad
```

Post probe-kbd-good and probe-kbd-bad here.
This hopefully, will move us close to an answer to Step 1.

For Step 2, I think something like

```
gconftool-2 -t list -s /desktop/gnome/peripherals/keyboard/kbd/layouts <something>
```
will work. But I haven't tried it yet myself, so it might take some mucking about to make it work.

---

### Post by frogitts on 2008-06-07
Well, that's a lot of cool information from that script. I just noticed that my keyboard's messed up again, so I got the information from that state as well as the normal one. Unfortunately, they're exactly the same (I looked over them and ran a diff)

```
% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/general
 groupPerWindow = false
 layoutNamesAsGroupNames = true
 handleIndicators = false
 known_file_list = []
 disable_sysconfig_changed_warning = false
 defaultGroup = -1
 update_handlers = []

% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd
 layouts = [us	us_de]
 model = 
 options = [lv3	lv3:ralt_switch]
 overrideSettings = true

% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd.sysbackup
 layouts = [us]
 model = pc105

% xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us", "", ""
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us", "us_de", "lv3:ralt_switch"
```

us_de is the name of my custom layout, which includes the us layout plus additional options.

---

### Post by unutbu on 2008-06-07
Hm. If they are the same, that's bad. I'm not sure I'll be able to help you. 

Here is a complete different idea: 

My /etc/X11/xorg.conf contains

```
Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,us"
    Option         "XkbVariant" "**dvorak,basic**"
    Option         "XkbOptions" "ctrl:nocaps,**grp:shift_toggle**,grp_led:scroll"
EndSection

```

Notice that I have two layout/variants. The grp:shift_toggle option allows me to switch between the two kbd layouts by pressing both shift keys simultaneously. I wonder what would happen if we set your xorg.conf up to have the same custom keyboard layout twice. If Firefox messes up your keyboard, perhaps you can just press both shifts and it will "swap" you to your original layout...

If you want to try it, first make a backup of your current xorg.conf
```

cd /etc/X11
sudo cp xorg.conf xorg.conf.20080607
```

Then edit your xorg.conf. If you have any questions how to do it, post your xorg.conf.

---

### Post by unutbu on 2008-06-07
After you change your keyboard layout using xorg.conf, you'll have to logout of your X session, get back to the (orange/brown?) gdm login window and press Ctrl-Alt-Backspace to restart the X server. 

When you log back in, GNOME will throw up a dialog box complaining that your keyboard layout does not match the keyboard layout it remembers you used to use. It will ask if you want to use the layout defined by xorg.conf, or if you want to use the one GNOME remembers. Pick the xorg.conf config (of course).

I wonder if that choice alone might be enough to preserve your custom keyboard layout. If so, you don't have to double up your keyboard layout and use the double-shift toggle trick. You could just define the layout in xorg.conf and maybe, hopefully, GNOME will leave it alone. Just a thought. Maybe wishful thinking.

---

### Post by frogitts on 2008-06-08
Well so far, just changing my xorg.conf file to us_de allowed my computer to start up with the right layout. We'll see if it keeps it. At any rate, thanks!

---

### Post by frogitts on 2008-06-09
The change to us_de didn't do the trick, it reverted after a reboot. Trying the double listing/shift change.

---

### Post by unutbu on 2008-06-09
Looking at my probe-kbd output, I notice that my backup strings are the same as my current keyboard setting: 
```

% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd # I don't know why this one is empty, but it is.					     
 layouts = []							                                                                                          
 model = 							                                                                                          
 overrideSettings = true					    # Hm. Maybe this should be false? Something else to explore if the below doesn't work.
 options = []

% gconftool-2 -a --all-dirs /desktop/gnome/peripherals/keyboard/kbd.sysbackup
 **layouts = [us	dvorak,us	basic]**
 model = pc105
 options = [ctrl	ctrl:nocaps,grp	grp:shift_toggle,grp_led	grp_led:scroll]

% xprop -root | grep XKB
_XKB_RULES_NAMES_BACKUP(STRING) = **"xorg", "pc105", "us,us", "dvorak,basic", "ctrl:nocaps,grp:shift_toggle,grp_led:scroll"**
_XKB_RULES_NAMES(STRING) = **"xorg", "pc105", "us,us", "dvorak,basic", "ctrl:nocaps,grp:shift_toggle,grp_led:scroll"**

```

Perhaps if you can make the backup strings the same as the current keyboard string, then the computer will have no choice but to use us_de after a reboot.

So instead of trying the double shift trick just yet, I would try re-editing xorg.conf back to pure us_de. Then set us_de using the GNOME System>Preferences>Keyboard. Reboot and reconfigure xorg.conf and System>Preferences>Keyboard again. Run probe-kbd to see if the backup strings are correct. Then reboot and see if the setting sticks.

HTH.

---

### Post by frogitts on 2008-06-16
I'm sorry it's taken so long for me to reply to this, but I figured it out!

First off, I changed /etc/X11/xorg.conf so that

```
  	Option         "XkbLayout" "us,us_de"
  	Option         "XkbVariant" "us,us_de"

```

Before I didn't even have the Variant option in my xorg.conf, I don't know if this actually even matters, if it's the default layout.

That, however, only loaded the correct layout - it didn't load the third level chooser. For this, I needed

```
  	Option          "XkbOptions"    "lv3:ralt_switch"

```

Now it works. So I guess I just needed to have the third level chooser defined in xorg.conf, even though I thought I defined it in my custom layout.

---

### Post by frogitts on 2008-06-16
So I did even more research, and realized where the main problem was: I wrote a faulty custom keyboard section. Go figure - operator error!

I looked back at my /usr/share/X11/xkb/symbols/us file just to prove to myself that I had actually told it to use Ralt as the default modifier, but I hadn't!

That said, simply adding ```
include "level3(ralt_switch)"
``` fixed the problem. After doing that, I reset xorg.conf to "XkbLayout" "us" and erased the XkbVariant line, and then used Keyboard preferences to reset to defaults so that there was no trace of my preference for us_de. I restarted the computer, and the layout was the default, as expected. I then used the keyboard preferences menu to select us_de (With German keys), restarted X, and all was well, including the third level modifier.

That said, here is my final, working, custom keyboard for German umlauts, etc.

In /usr/share/X11/xkb/symbols/us, after "classmate-altgr-intl":

```
partial alphanumeric_keys
xkb_symbols "us_de" {

    name[Group1]= "USA - With German Keys";

    include "us(basic)"

    key <AD07> { [ u,	U,	udiaeresis,	Udiaeresis	] };

    key <AD09> { [ o,	O,	odiaeresis,	Odiaeresis	] };

    key <AC01> { [ a,	A,	adiaeresis,	Adiaeresis	] };

    key <AC02> { [ s,	S,	ssharp,	ssharp	] };

    key <AD03> { [ e,	E,	eacute,	Eacute	] };

    include "level3(ralt_switch)"
};
```

In /usr/share/X11/xkb/rules/xorg.lst, after "us: Group toggle on multiply/divide key":
```

  us_de		  us: With German Keys
```

And in /usr/share/X11/xkb/rules/xorg.xml, after the "us: Group toggle on multiply/divide key" entry:

```
        <variant>
          <configItem>
            <name>us_de</name>
            <description>With German Keys</description>
          </configItem>
        </variant>
```

With those put in place, I believe that changing the default keyboard to USA > With German Keys in System > Preferences > Keyboard will be enough to make it the permanent default.

---

### Post by unutbu on 2008-06-16
Congratulations, froggits!

Can you point me toward any resources or documentation on how to make custom keyboard layouts? Where do the 
"key <AD07>" codes come from? where is the a list of possible symbols, (e.g. Udiaeresis)? and does the list include arrow keys?

---

### Post by frogitts on 2008-06-17
Agh, posted too early.

As it turns out, the third level chooser would work just fine after simply setting my custom layout as the default using the keyboard preferences. It would even stick through logging out and logging back in, as well as restarting X through Ctrl+Alt+Backspace.

However, as soon as I restart the computer, the setting goes away. So I'm back to square one - after restarting, I still have to deselect and reselect the third level chooser in the layout options under keyboard preferences. I've tried changing the settings in gconf manager under desktop>gnome>peripherals, and that didn't help either. I'm going to now experiment with other keyboard layouts included by default to see if they will allow the RAlt 3rd level chooser to be switched on after a reboot.

Edit: I've experimented with the USA > With Eurosign on 5 setting. This one will stick after a reboot, and I can't find any major difference between its setup and my setup, except for the way in which it defines its settings. It uses an include setting to include the Eurosign on 5 option, whereas I explicitly define my keys. Maybe this is somehow making a difference?

I guess the question now is what exactly is causing this break in functionality in my layout. My layout remains as posted above, and something's wrong with it, specifically with the way I define keys - either that, or I'm not defining a setting somewhere that I should be defining a setting.

Edit again: I reformatted my layout, defining a new keyboard set in /symbols called "us_de" with a layout called "1". I then called this layout in the "us" file in a similar manner to the "With Eurosign on 5" layout. It did not stick after a reboot. It had the exact same effect as before. My layout, however, now looks like this:

```
partial alphanumeric_keys
xkb_symbols "us_de" {

    name[Group1]= "USA - With German Keys";

    include "us(basic)"

    include "us_de(1)"

    include "level3(ralt_switch)"
};
```

with a new file in /usr/share/X11/xkb/symbols called "us_de" with these contents:
```

partial alphanumeric_keys
xkb_symbols "1" {

    key <AD07> { [ u,	U,	udiaeresis,	Udiaeresis	] };

    key <AD09> { [ o,	O,	odiaeresis,	Odiaeresis	] };

    key <AC01> { [ a,	A,	adiaeresis,	Adiaeresis	] };

    key <AC02> { [ s,	S,	ssharp,	ssharp	] };

    key <AD03> { [ e,	E,	eacute,	Eacute	] };

};
```

As I said, making this change has made absolutely no difference in functionality. The problem, as far as I can tell, must lie in a misplaced setting in the us_de file above, or I must not be defining the RAlt switch somewhere where I should be defining it.

It seems like this could be a problem of more than one thing trying to control the keyboard layout. In gconf, I can change the keyboard layout through the desktop > gnome > peripherals > keyboard > kbd > layouts setting. However, setting this as "us	us_de" breaks things. Setting it as "us" gives it the default USA layout. Setting it as "us	euro" gives it the "euro" layout under "us". Setting it to "us", with Xorg.conf's default layout as "us	us_de" and then choosing "Reset to Defaults" in System > Preferences > Keyboard sets desktop > gnome > peripherals > keyboard > kbd > layouts to an empty list, but everything works fine. This just seems weird to me.

---

### Post by frogitts on 2008-06-17
To answer your post, unutbu, I found a few resource through forum searching, such as this one:
[http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11](http://people.uleth.ca/~daniel.odonnell/Blog/custom-keyboard-in-linuxx11)
[http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)
[http://www.charvolant.org/~doug/xkb/html/index.html](http://www.charvolant.org/~doug/xkb/html/index.html)

The last one is particularly detailed and helpful.

As for your other questions:

1)<AD07> is the physical address of a key. A = Alphanumeric (as opposed to function keys, numpad), D = 4th row from the bottom, and 07 = the seventh key from the left, not including special keys like Tab.

2) I can't figure out where it was that I found the codes, but you can get them from a well-notated keyboard layout like the "fr" one. I'll post when I remember where it was that I found these.

3) As for arrow keys, I'm not sure. These are special keys, like Tab, Shift, Ctrl, etc. However, I do know that it's possible to switch the caps lock key and the LAlt key, as is done on some European keyboard layout (Norwegian? I forget). I just don't know how it's done, or if you could reassign the arrow keys and give them additional levels or not. I also don't know what the output code for an arrow key is, so I don't know if you could assign a random key to function as an arrow key. I could look, but it's a beautiful day outside and I've spent way too much time on this today :)

---

### Post by rajan on 2008-11-14
gnome is the problem to your answer. gconftool is the answer to that problem. i'm having a similar problem (yours is much more complicated, but still, similar) in that when start my computer up, the "p" key doesn't work. whatever. simple fix in that i just need to go through the same System > Preferences > Keyboard > then I actually need to select a different keyboard layout, then delete it so that i can select the layout that was there in the first place. Very roundabout way to get my keyboard working. 

Here's a few details:
when i restarted my computer after changing my keyboard layout in xorg.conf, it asked me which one of the conflicting layouts i wanted to go with (gnome or x11, same as posted above). this seems to confirm your suspicion that there are two things trying to get at your layout.
Also, i can type "p" all i want before i actually log into the computer. My login name/password could have all the "p" letters it wanted. It's just when the real gnome applications start that it changes the settings. 

like i said, i'm gonna take a look at gconftool because the gui for changing gnome just doesn't work that great. if you've discovered something in the past months, i'd be glad to hear it. thanks.

---

### Post by rajan on 2008-11-14
gconf-editor is the more user-friendly way to change the settings. i guess it's bad to do it this way, but it looks like i'm gonna find out the hard way. 

this site says that when gnome is going to override the x defaults, it's bad. 

[http://linuxtidbits.wordpress.com/2007/12/19/gconf-and-keyboard-warnings/](http://linuxtidbits.wordpress.com/2007/12/19/gconf-and-keyboard-warnings/)

EDIT: ok changing the overrideSettings to false with gconf-editor didn't work. the settings were saved, but they didn't do anything. i don't know why there is a problem with gnome. according to the site above, some people were deleting all their gnome settings and it helped out. i'm hesitant to use the sledgehammer method now. i just want my "p" key to work!

---

### Post by rajan on 2008-12-10
since gnome is the problem, i fixed my no "p" character by adding a startup script into gnome's startup manager. i'm using 6.06 so this may be different for you, but i go to System > Preferences > Sessions then I click on the Startup Programs tab, where I add the following command:

```

setxkbmap -model pc105 -layout us 

```

and that did it for me. it's a shame that gnome works so poorly in this respect because by and large this is the only large problem i've had with it. anyway, it's fixed, hope this helps.

rajan

---

### Post by julio prada on 2009-04-14
I would love to have the @ sign as a simple key instead of a shift key.
I never use first hand keys like []\ or the "Windows" key.
Would it be possible to assign one of them to @?
Thanks,
Julio

---

