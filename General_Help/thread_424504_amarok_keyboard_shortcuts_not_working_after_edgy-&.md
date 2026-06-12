---
title: "amarok keyboard shortcuts not working after edgy-&gt;fiesty upgrade"
date: 2007-04-26
forum: General Help
---

### Post by Jorenko on 2007-04-26
I was using amarok with my keyboard's media buttons in edgy. In order to get it to work, I had to go into its Settings/Configure Global Shortcuts dialog and set each function myself. However, after doing this, it worked perfectly. After upgrading to fiesty, this stopped working. I've reset the settings, but they still don't work. They're currently set to:

Play/Pause: XF86AudioPause
Stop: XF86AudioStop
Next Track: XF86AudioNext
Previous Track: XF86AudioPrev

The media keys still work with rythymbox, which is okay, but I'd rather use amarok. The windows key shortcuts still seem to work, but I had the media keys down to muscle memory and I'd really appreciate it if someone knew how to fix this.

Thanks.

---

### Post by stylishpants on 2007-04-26
The DBUS bindings that handle XF86Audio keys have changed in feisty.  Audio players that depended on them now need to be updated.

Quodlibet has the same problem: [https://bugs.launchpad.net/ubuntu/+source/quodlibet/+bug/43464](https://bugs.launchpad.net/ubuntu/+source/quodlibet/+bug/43464)


I don't see a bug filed for Amarok for this though.  [https://bugs.launchpad.net/amarok](https://bugs.launchpad.net/amarok)

I can't confirm that this is actually the problem you're experiencing.  I can confirm that Amarok is ignoring those keys on my system as well (also using Gnome.)

---

### Post by rocktorrentz on 2007-04-28
I have the same problem. Is there a workaround?

---

### Post by stylishpants on 2007-04-28
I'm only aware of one ugly workaround.

Unmap your Xf86Audio keys in the Keyboard Shortcuts dialog box.  You can use "Backspace" to clear the key instead of remapping it.  Remember what keycode each one was set to.  

Define some new Gnome keyboard shortcuts using this method:
    [http://ubuntuforums.org/showthread.php?t=42404](http://ubuntuforums.org/showthread.php?t=42404)

Map each key to the equivalent amarok command (or any other player that provides command-line flags that control it's functionality.)  

For example, my "Stop Playback" key was mapped to 0xa4.  After clearing that mapping, I would run 'gconf-editor' and follow the instructions in the howto above to map that key as follows:  Define 'command_1' under keybinding_commands as 'amarok --stop', and 'run_command_1' under 'global_keybindings' as 0xa4.   

You find out what commands to use by running your music player from the terminal with it's "--help" flag, which shows all the command-line options.

```
fraser@ged:/tmp/A$ amarok --help
Usage: amarokapp [Qt-options] [KDE-options] [URL(s)] 

The audio player for KDE

Generic options:
  --help                    Show help about options
  --help-qt                 Show Qt specific options
  --help-kde                Show KDE specific options
  --help-all                Show all options
  --author                  Show author information
  -v, --version             Show version information
  --license                 Show license information
  --                        End of options

Arguments:
  URL(s)                    Files/URLs to open

Options:
  -r, --previous            Skip backwards in playlist
  -p, --play                Start playing current playlist
  -t, --play-pause          Play if stopped, pause if playing
  --pause                   Pause playback
  -s, --stop                Stop playback
  -f, --next                Skip forwards in playlist

Additional options:
  -a, --append              Append files/URLs to playlist
  -e, --enqueue             See append, available for backwards compatability
  --queue                   Queue URLs after the currently playing track
  -l, --load                Load URLs, replacing current playlist
  -m, --toggle-playlist-window Toggle the Playlist-window
  --wizard                  Run first-run wizard
  --engine <name>           Use the <name> engine
  --cwd <directory>         Base for relative filenames/URLs
  --cdplay <device>         Play an AudioCD from <device>

```

---

### Post by overmetal61 on 2007-05-01
I just upgraded and am having the same issues!

This is disappointing... I use my media keys all the time to control my music.

---

### Post by mkw87 on 2007-05-06
> **overmetal61 said:**
> I just upgraded and am having the same issues!

This is disappointing... I use my media keys all the time to control my music.

Same here, has anyone filed a bug yet?

---

### Post by scotty32 on 2007-05-06
I use Gnome and i love Amarok, so i use it.

i also had the same problems you lot are facing about a week or 2 ago when i upgraded. 

have you set the shortcuts in the Keyboard Shortcuts (of gnome, if your using it) or even any other programs?

is i had to disable the gnome ones and then reset it in amarok for it to work, and it works ok now

---

### Post by rocktorrentz on 2007-05-06
Worked a treat, thanks :D

---

### Post by mkw87 on 2007-05-07
> **scotty32 said:**
> I use Gnome and i love Amarok, so i use it.

i also had the same problems you lot are facing about a week or 2 ago when i upgraded. 

have you set the shortcuts in the Keyboard Shortcuts (of gnome, if your using it) or even any other programs?

is i had to disable the gnome ones and then reset it in amarok for it to work, and it works ok now

Worked for me as well - thanks.  For those wondering:

1. Close amarok, then go to System > Preferences > Keyboard Shortcuts in GNOME.  

2.  Then, scroll down to the media keys, and select Play, Stop, Next, and Prev and press the backspace key to disable them.  

3.  Open Amarok and reset the controls in Global Shortcuts - viola!

---

### Post by Jorenko on 2007-05-09
Disabling gnome's bindings and redoing amarok's worked for me as well. Thanks a lot all!

---

### Post by joeashcraft on 2007-05-18
+1 scotty32 and mkw87

It works for me on my Inspiron 6400/E1505.
I'm glad I finally found a fix.

---

### Post by maxwellcom on 2007-05-19
> **mkw87 said:**
> 3.  Open Amarok and reset the controls in Global Shortcuts - viola!

I can follow you up to this point.  When I try to change the shortcut (in the global configuration or otherwise), the configuration window simply flickers-- nothing changes.

No doubt I'm overlooking something really, really simple.  Any suggestions?

Thanks

---

### Post by bstock on 2007-05-30
Simply unbinding the keys and trying to bind them in Amarok didn't work for me in Fiesty. I used to have to do that in Edgy.

I ended up using stylishpants' method by giving commands to the shortcut keys and that worked great. Basically I did the following:

1) Determine keybindings to your playback keys by setting them in the Keyboard Shortcuts window. I then copied the key codes into a text file for each button. Make sure to disable any of them you used for testing. You want to make sure that the stop, next, previous, play, and play/pause buttons are all disabled.

2) Run gconf-editor from a terminal or through the run dialog (Alt+F2). go to Apps -> Metacity -> keybinding_commands. I set the following:

command_1: amarok --play-pause
command_2: amarok --stop
command_3: amarok --next
command_4: amarok --previous

3) Go to Apps -> Metacity -> global_keybindings. Here is where you need the keybinding codes. Double click on run_command_1 and set the value to the code for your play-pause button. Do the same for commands 2,3, and 4. Mine looked like this for a Dell multimedia keyboard:

run_command_1: 0xa2
run_command_2: 0xa4
run_command_3: 0x99
run_command_4: 0x90

Your keycodes will probably have different values, but should look similar.


That should be it. Try them out and see what happens.

---

### Post by maxwellcom on 2007-06-04
> **bstock said:**
> Simply unbinding the keys and trying to bind them in Amarok didn't work for me in Fiesty. I used to have to do that in Edgy.

I ended up using stylishpants' method by giving commands to the shortcut keys and that worked great. Basically I did the following:

1) Determine keybindings to your playback keys by setting them in the Keyboard Shortcuts window. I then copied the key codes into a text file for each button. Make sure to disable any of them you used for testing. You want to make sure that the stop, next, previous, play, and play/pause buttons are all disabled.

2) Run gconf-editor from a terminal or through the run dialog (Alt+F2). go to Apps -> Metacity -> keybinding_commands. I set the following:

command_1: amarok --play-pause
command_2: amarok --stop
command_3: amarok --next
command_4: amarok --previous

3) Go to Apps -> Metacity -> global_keybindings. Here is where you need the keybinding codes. Double click on run_command_1 and set the value to the code for your play-pause button. Do the same for commands 2,3, and 4. Mine looked like this for a Dell multimedia keyboard:

run_command_1: 0xa2
run_command_2: 0xa4
run_command_3: 0x99
run_command_4: 0x90

Your keycodes will probably have different values, but should look similar.


That should be it. Try them out and see what happens.

Thanks for your post and clear directions, bstock.  I followed the above steps carefully but sadly they did not work.  Here are the details:

1. When I run the commands (amarok --stop, for example) in a terminal, they work fine.

2. My keybinding codes are exactly the same as yours (although my kb is a Logitech S 510), so I was able to literally follow your directions exactly.

3. Even when I put something other than the keybinding codes in the global keybindings (<Alt>F3 for example) the keystrokes don't work either.  In other words, the problem seems to be associated with the global keybindings.

My keyboard is not too new, not too old, fairly common I assume, and worked just fine in Dapper and Edgy.  I'm surprised it simply doesn't work out of the box any more.  Too bad.

Any suggestions?

---

### Post by Harvs on 2007-06-09
bstock - just followed your example, and it works a treat. Fantastic - thanks!

---

### Post by Ench on 2007-06-11
I tried both methods but they are not working... :/ any other suggestions?

---

### Post by akshayas1986 on 2007-06-11
Disable all the multimedia keys on System > Preferences > Keyboard shortcuts.  Install xbindkeys.. I think it is > sudo apt-get install xbindkeys (Figure it out if I am missing the information on repositories). xbindkeys comes with a multi-key utility.. Type > xbindkeys -mk. It should open a blank window. When you press the multimedia key say play button, you would see a response like this on shell > m:0x0 + c:24
. Copy it. now type > sudo nano ~/.xbindkeysrc. And add the following line

> 
# Amarok controls
"amarok --play"
     m:0x0 + c:24


'#' is only for adding comments for readability.

Repeat the above the above steps for the other keys.
Save the file and restart xbindkeys by typiing > xbindkeys and Eureka!!!:popcorn:

---

### Post by BrowneR on 2007-06-22
I have written an Amarok script to allow the use of multimedia keys in fiesty (and other gnome 2.18 distros).

There is no fuss at all - just load the script into amarok's script manager and configure the keys in 
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)

or install it directly from the amarok script manager - its called "gnome multimedia keys".

this way you can leave the keys assigned in gnome keyboard shortcuts and have them work in other apps too rather than disable them as per above instructions.

any problems just send me a pm.

hope this helps. would love your feedback and bug reports.

---

### Post by erra on 2007-07-14
> **BrowneR said:**
> 
There is no fuss at all - just load the script into amarok's script manager and configure the keys in 
system-->preferences-->keyboard shortcuts

done.

get it here [http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910](http://kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910)

or install it directly from the amarok script manager - its called "gnome multimedia keys".

hope this helps. would love your feedback and bug reports.

Worked like a charm for me. 

Thanks!!

---

### Post by bford16 on 2007-07-21
Thank you.  This is one thing I like about Ubuntu.  When something doesn't work as planned, there is usually someone who has been there, done that, and brought back fire...

---

### Post by jolla on 2007-08-01
Well if nothing else works try [ReMoot]("http://kde-apps.org/content/show.php/ReMoot?content=63140&PHPSESSID=68a62ff7ee397398b5dacb31a92d5658"). It makes your multimedia keyboard keys work as they should with most multimedia apps. If you have a palm pilot, or any other web enabled gadget ReMoot+Rewww00t turns it into a remote control.

works very well!  :-)

---

