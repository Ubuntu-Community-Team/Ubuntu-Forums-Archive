---
title: "How do I change a custom keyboard shortcut from the command line?"
date: 2024-09-02
forum: General Help
---

### Post by Paddy Landau on 2024-09-02
In Ubuntu, I can go to Settings > Keyboard > View and Customise Shortcuts > Custom Shortcuts. There, I can add, delete or change custom keyboard shortcuts.

What I'd like to know is how to do this on the command line (so that I can use it in a script)? I know BASH, but no other language.

I've searched online for the solution but found nothing.

Thank you

---

### Post by him610 on 2024-09-04
Hello Paddy,

Have you considered an *alias* defined in .bash_aliases to implement your desired shortcut?

---

### Post by Paddy Landau on 2024-09-05
> **him610 said:**
> Have you considered an *alias* defined in .bash_aliases to implement your desired shortcut?
Thanks, but keyboard shortcuts are for the GUI, not for the terminal. It's those keyboard shortcuts that I wish to change, but using a script instead of using the GUI.

---

### Post by dragonfly41 on 2024-09-05
Would it be acceptable to have a UI automation script to flash through this process via Settings in a blink of an eye?

---

### Post by Paddy Landau on 2024-09-05
> **dragonfly41 said:**
> Would it be acceptable to have a UI automation script to flash through this process via Settings in a blink of an eye?
Um… Sorry, I don't understand what you're saying?

To clarify with an example:

Suppose that I have a keyboard shortcut Super+F11 to open VirtualBox. Now, I want Super+F11 to open GIMP instead. I can manually make this change by going to Settings > Keyboard > View and Customise Shortcuts > Custom Shortcuts, and making the change there. But, what I really want is a script to do make that change. In other words, how can I change the shortcut using a CLI command?

---

### Post by dragonfly41 on 2024-09-05
I was attempting to suggest that you can "drive" *established processes* using commands ..
> [COLOR=#000000]Settings > Keyboard > View and Customise Shortcuts > Custom Shortcuts, and making the change there. But, what I really want is a script to do make that change.

That is leverage proven tools to automate such actions.  I know that CLI is the holy grail* but if there are UI tools around I use them to speed up proven workflows rather than replacing them with Bash scripts*.

I will give one example. Install Albert, ensure it is in tool bar, then hit Ctrl+Space (I don't know why but it is required twice on my desktop). You are presented with a  popup query field and that can be your sole portal into the Ubuntu galaxy rather than the usual launch terminal and run bash script. Just saying ...[/COLOR]

---

### Post by Holger_Gehrke on 2024-09-05
I can't really speak about main-line Ubuntu and Gnome, but in XUbuntu / XFCE keyboard shortcuts are stored in xfconf and can be viewed and changed with xfconf-query. 
```

xfconf-query -c xfce4-keyboard-shortcuts -p /commands/custom/'<Primary><Alt>e' -n -s xeyes -t string

```
This assigns Ctrl-Alt-e to starting xeyes. XFCE monitors xfconf and reacts to changes made to it's properties. I'd think that there's something similar in Gnome, probably gsettings.

Holger

---

### Post by Paddy Landau on 2024-09-05
> **Holger_Gehrke said:**
> probably gsettings
Thank you — you might be onto something here. I'll have to search to find out how to specify key bindings with gsettings. (I don't have xfconf, nor is it in the standard repositories. It's obviously only for XFCE and LXDE.)

---

### Post by dragonfly41 on 2024-09-05
Gnome Tweaks?

[https://askubuntu.com/questions/1289077/make-additional-layout-options-in-gnome-tweaks-apply-to-specific-keyboard](https://askubuntu.com/questions/1289077/make-additional-layout-options-in-gnome-tweaks-apply-to-specific-keyboard)

---

### Post by Paddy Landau on 2024-09-05
> **dragonfly41 said:**
> Gnome Tweaks?
[https://askubuntu.com/questions/1289077/make-additional-layout-options-in-gnome-tweaks-apply-to-specific-keyboard](https://askubuntu.com/questions/1289077/make-additional-layout-options-in-gnome-tweaks-apply-to-specific-keyboard)
Thanks for the link. Gnome Tweaks is a GUI. The answer given is about changing keys at a hardware level, which is not what I'm after.

---

### Post by Holger_Gehrke on 2024-09-05
xfconf is exclusively part of XFCE, AFAIK. If I were in your situation I'd take a good hard look at 'gsettings list-recursively', probably piping it through less and searching for the word 'key'. Since XFCE is GTK-based and I have quite a few applications running that are meant for a Gnome environment, doing that shows me things like key-bindings for the window-manager ("org.gnome.desktop.wm.keybindings activate-window-menu ['<Alt>space']" and so on ...) and I expect that on a Gnome system the kind of setting you're looking for is somewhere in there.

Holger

---

### Post by Paddy Landau on 2024-09-05
> **Holger_Gehrke said:**
> gsettings list-recursively
Alas, no luck. I searched for some strings that I know are in the custom keyboard settings (case insensitive), and nothing appears.

Back to the drawing board!

---

### Post by tea for one on 2024-09-05
> **Paddy Landau said:**
> Back to the drawing board!
Try the following text in your favourite drawing board - whoops, internet search engine
> /org/gnome/settings-daemon/plugins/media-keys/custom-keybindings
It may lead you to a command line answer...............?

---

### Post by Paddy Landau on 2024-09-05
> **tea for one said:**
> It may lead you to a command line answer
Thank you. I have that entry, but it seems to contain nothing of value:

[FONT=courier new]['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom1/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom2/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom3/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom4/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom5/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom6/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom8/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom9/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom10/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom11/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom12/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom13/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom14/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom15/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom16/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom17/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom18/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom19/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom20/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom23/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom22/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom7/', '/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom21/'][/FONT]

Certainly, none of my existing custom keyboard shortcuts is there. In fairness, this does seem to specifically be for media keys, not for anything else.

Gnome must be storing the custom keyboard shortcuts somewhere else!

---

### Post by tea for one on 2024-09-05
> To perform the same process via command line do the following.  These steps assume that there are no other custom key bindings assigned.  If there are, or could be, then an additional step should be taken to list the current custom key binding entries and then add this one with the appropriate number assigned.  Further explanation below.
[https://www.suse.com/support/kb/doc/?id=000019319](https://www.suse.com/support/kb/doc/?id=000019319)
Is this link any help in your quest?

---

### Post by Paddy Landau on 2024-09-05
> **tea for one said:**
> [https://www.suse.com/support/kb/doc/?id=000019319](https://www.suse.com/support/kb/doc/?id=000019319)
Is this link any help in your quest?
Thank you for the link. It also points to gsettings, but there is nothing in my gsettings that matches what I have in my custom keyboard shortcuts.

I wonder if Ubuntu is using a non-standard method to set custom keyboard shortcuts?

---

### Post by 1fallen on 2024-09-05
Hi Paddy, I'm fairly certain this may fit your needs, but will take some thought on your end to manage to your liking.
I actually created a new account to help here. :)
xbindkeys.. is pretty handy

```
sudo apt-get install xbindkeys
```

Xbindkeys is a very versatile program that lets you remap keys very easily. It uses a config file, my default located in your home directory, to change key bindings into certain commands.

To create a default config file you use the command:

```
xbindkeys --defaults
```

Which prints the default config file. So if you want to create the file containing the default values you would use:

```
xbindkeys --defaults > $HOME/.xbindkeysrc
```

Which prints the default values into a hidden file named .xbindkeysrc located in home (~).

Now to actually change the bindings of keys we first need to know what the name or keysym of those keys is. xbindkeys allows us to use the -k handle to find the name of a key or key combination. Run:

```
xbindkeys -k
```

And press a key or key combination. Your output will look something similar to this (when pressing space):

```
"NoCommand"
m:0x10 + c:65
Mod2 + space

```
"No Command" tells us that currently no command is associated with the Space key.
```

m:0x10 + c:65
Mod2 + space  

```
Is the name of the key/key combination.
the config file..

Lets open up the config file you made earlier:

```
gedit .xbindkeysrc  

```
Here is an excerpt from the default config file:

```
#
# A list of keys is in /usr/include/X11/keysym.h and in
# /usr/include/X11/keysymdef.h
# The XK_ is not needed.
#
# List of modifier:
#   Release, Control, Shift, Mod1 (Alt), Mod2 (NumLock),
#   Mod3 (CapsLock), Mod4, Mod5 (Scroll). 
#

# The release modifier is not a standard X modifier, but you can  
# use it if you want to catch release events instead of press events

# By defaults, xbindkeys does not pay attention with the modifiers
# NumLock, CapsLock and ScrollLock.
# Uncomment the lines above if you want to pay attention to them.

#keystate_numlock = enable
#keystate_capslock = enable
#keystate_scrolllock= enable

# Examples of commands:

"xbindkeys_show" 
 control+shift + q  

```
Every line beginning with # is a comment and won't be read or run by xbindkeys.

So far the only line that isn't commented out is:

```
"xbindkeys_show" 
 control+shift + q  

```
This excerpt shows the basic syntax of xbindkeys commands:

"Command to run (in quotes)"
key to associate with command (no quotes)  

So as you can see:

```
"xbindkeys_show" 
 control+shift + q  
```

Runs the command xbindkeys_show when you press Ctrl+Shift+q.
bind keys to commands..

Now lets try binding a few keys. I recommend clearing the entire default file so that it's blank. It contains preset key bindings you probably don't want.

Now lets say you want to use Ctrl+b to open your browser. First you need to know what the name or keysym of Ctrl+b is. As mentioned earlier you can use xbindkeys -k to find the name of a key or keys, but there is an easier way. For simple combinations like Ctrl+b you can just use:

```
Control+b
```

A lot easier isn't it!

Now find the command for your favorite browser:

    For Firefox: firefox

    For Chromium: chromium-browser

    For Opera: opera

Remember the syntax from earlier? The xbindkeys command to launch Firefox (or your other favorite browser) when you press Ctrl+b is:
```

"firefox"
Control+b

```
Now put that in your config file and save it. Now you might notice your command doesn't work yet, that's because xbindkeys isn't running. To start it just run xbindkeys from a terminal. Your Ctrl+b should now start your browser!
bind keys to other keys..

If you want a key on your keyboard to call a different key on your keyboard, you will need an extra piece of software as xbindkeys does not support this on it's own. I know of two programs which we can use, xdotool and xte. I prefer xte so I'm going to use that.

Install it:
```

sudo apt-get install xautomation
```

The syntax for xte is like this:
```

xte 'command key/mousebutton/xyCoordinates'
```

Examples:
[LIST]
[*]To call a single key press: xte 'key keyName' 
[*]To call a key combination: xte 'keydown keyName' 'keydown secondKeyName' 'keyup keyName' 'keyup secondKeyName 
[*]To call a mouse button: xte 'mouseclick buttonNumber' (We'll discuss finding button numbers a little latter) 
[*]To move the mouse: xte 'mousemove xCoordinate yCoordinate' 
[*]And more! Read man xte 
[/LIST]


Now that you know the command for simulating key presses you can call it from your xbindkeys script, like this:
```

"xte 'key b'"
Control+b 
``` 

As you might guess, this calls xte 'key b' when we press Ctrl+b, which would enter a b into any document you might be currently working on.

I think to note however is that xbindkeys and xte don't always work very well together. Sometimes you have to press the keys exactly at the same time to get output, other times it works just fine. This may or may not have to do with system configuration and/or hardware.. I'm not sure. 

You can also use xbindkeys to bind mouse buttons to commands (and thence keyboard shortcuts, see above). The basic format for mouse buttons should be familiar to you now:
```

" [command to run]  "
b:n
```

Where [command to run] is the command you want to run and n the number of the mouse button you want to use for that command.

If you don't know the number of your mouse button you can use xev to find out what it is:
```

xev | grep button
```

The output will be something like this:
```

user@host:~$ xev | grep button
    state 0x10, button 1, same_screen YES
    state 0x110, button 1, same_screen YES
    state 0x10, button 2, same_screen YES
    state 0x210, button 2, same_screen YES
    state 0x10, button 3, same_screen YES
    state 0x410, button 3, same_screen YES
```

When I press each of my mouse buttons.

For example:
```
]
" firefox "
b:2
```
Launches firefox when I press my middle mouse button.

---

### Post by Paddy Landau on 2024-09-06
> **1fallen2 said:**
> I actually created a new account to help here.
Thank you!

I'll have a good look at this later or maybe over the weekend. Thank you for such a comprehensive reply.

---

### Post by tea for one on 2024-09-06
> **Paddy Landau said:**
> 
Now, I want Super+F11 to open GIMP instead.
First of all, please note that I have zero keyboard shortcuts, therefore my first one is called custom0
Via the terminal, I created a shortcut to open GIMP with Super F11
Then I changed it to Super F10
Here we go:-

Command to create the 'custom0' key binding:
```
$ gsettings set  org.gnome.settings-daemon.plugins.media-keys custom-keybindings "['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/']"
```
Command to enter the name of the binding:
```
$ gsettings set  org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ name 'GIMP'
```
Command to enter the command to run:
```
$ gsettings set  org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ command 'gimp'
```
Command to enter the key combination that will run the command:
```
$ gsettings set  org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ binding '<Super>F11'
```
If this is being scripted and there is a possibility that a custom key binding already exists then the script should check the value of the first command above:
```
$ gsettings get org.gnome.settings-daemon.plugins.media-keys custom-keybindings
['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/']
```
Command to enter/change the key combination that will run the command:
```
$ gsettings set  org.gnome.settings-daemon.plugins.media-keys.custom-keybinding:/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/ binding '<Super>F10'
```

All these commands were shamelessly copied from the site I linked previously [https://www.suse.com/support/kb/doc/?id=000019319](https://www.suse.com/support/kb/doc/?id=000019319)
All tested and functioned as expected (Ubuntu 24.04 and Gnome 46)

By the way, dconf-editor (universe repo), is a useful utility for gsettings

Edit: If you have more than one shortcut using these commands, it appears to create a "custom-keybindings" folder.
Multiple shortcuts are stored but I haven't figured out exactly how multiple shortcuts are activated yet.
Paddy, apologies if this isn't what you need (but it was a bit of fun for me)

---

### Post by Paddy Landau on 2024-09-06
[QUOTE=tea for one;14204128]```
$ gsettings get org.gnome.settings-daemon.plugins.media-keys custom-keybindings
['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/custom0/']
```
Yes, I've seen that, not only on the command line but also using dconf-editor.

It seems that gsettings simply doesn't store the custom keyboard shortcuts that Ubuntu creates. None of my custom keyboard shortcuts is shown there.

Thank you for taking the time to document this.

---

### Post by Paddy Landau on 2024-09-06
> **1fallen2 said:**
> xbindkeys…
I've noted your post in my documentation, because it's an extensive and helpful description. Thank you again.

xbindkeys works at a low level, I see. It fits nicely with commands such as xev, xmodmap and showkey.

It's not quite what I'm after, though, because I'm trying to access the custom keyboard shortcuts that Ubuntu saves. There must be an answer somewhere, but despite extensive searching, I simply cannot find it!

Although this isn't the end of the world for me, I am finding this most interesting.

---

### Post by tea for one on 2024-09-06
> **Paddy Landau said:**
> 
It's not quite what I'm after, though, because I'm trying to access the custom keyboard shortcuts that Ubuntu saves. There must be an answer somewhere, but despite extensive searching, I simply cannot find it!
Although this isn't the end of the world for me, I am finding this most interesting.
Yes, interesting indeed.
Now, if you return to post 19 and create a shortcut (4 commands for custom0), this shortcut will appear in the GUI
Settings > Keyboard > View and Customise Shortcuts > Custom Shortcuts

Then, create another shortcut (4 commands for custom1)
Check via dconf-editor that you have /org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/ folder containing custom0 and custom1

Open a terminal and enter
```
gsettings set  org.gnome.settings-daemon.plugins.media-keys custom-keybindings "['/org/gnome/settings-daemon/plugins/media-keys/custom-keybindings/[COLOR="#0000FF"]custom1[/COLOR]/']"

```
This new shortcut will now appear in the GUI settings

It seems that you can have multiple shortcuts created via the terminal but only one can have priority in Custom Shortcuts GUI.

Useful info - I'm not sure but it is addictive on a rainy day ;)

---

