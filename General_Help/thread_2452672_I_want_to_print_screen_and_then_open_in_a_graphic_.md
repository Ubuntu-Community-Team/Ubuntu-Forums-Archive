---
title: "I want to print screen and then open in a graphic viewer"
date: 2020-10-26
forum: General Help
---

### Post by victor432 on 2020-10-26
I'm interested in print screen capture and then pasting the image into a viewer. How can I do this ? I'm using Ubuntu 20.04. I'm also very new to Linux let alone Ubuntu.

Thanks in advance

---

### Post by tea for one on 2020-10-26
Show Applications > Utilities > Help > Tips & Tricks > Screenshots and Screencasts

---

### Post by victor432 on 2020-10-26
> **tea for one said:**
> Show Applications > Utilities > Help > Tips & Tricks > Screenshots and Screencasts

Great thank you.

---

### Post by TheFu on 2020-10-26
Sorry, I don't know an easy way, but I do know a way that is 3 steps using a little script and connecting a keyboard chord to make it happen.
Perhaps some other people will respond with an easier way.

I'm using imagemagick tools. You'll want to install that package. The import command only works with X11, so Wayland probably won't work. 

To grab the screen, use:
   import -display :0.0 -window root -colorspace RGB -quality 80 /tmp/screendump.png

To open that in a viewer tool:
    display /tmp/screendump.png

To hook up the script with those 2 lines, I'd use a setting in my window manager.  That is extremely specific to the WM, so you'll need to look up how to do that for the DE that you use.  "Ubuntu Desktop Guide" will have steps for stock Gnome3 DE in the default Ubuntu Desktop.

Let me test those 2 command first ... ok, that worked.  Here's my little script:
```
#!/bin/bash
FILE="/tmp/screendump.png"  # this could be timestamped or random for each run.
/usr/bin/import   -display :0.0     -window root    -quality 80    "$FILE"

# To open that in a viewer tool:
/usr/bin/display   "$FILE" &
```
I removed the colorspace option to prevent an odd color change. If you want to keep the files, you can put a time-stamp into the filename, so they are unique from run to run.  Click anywhere in the image to see a menu or press 'q' to quit and the file will be left in /tmp/.

For those using openbox, the XML config file could be ~/.config/openbox/rc.xml. There should be an existing one. The openbox process would have the --config option listed. That's the file.
```
    <keybind key="W-2">
      <action name="execute">
        <command>firejail thunderbird</command>
      </action>
    </keybind>
    <keybind key="W-3">
      <action name="execute">
        <command>firejail keepassxc</command>
      </action>
    </keybind>
  <keybind key="W-4">
      <action name="execute">
        <command>~/bin/grab-screen-and-view</command>
      </action>
    </keybind>

```

is how to setup <Super>-2 and <Super>-3 to run thunderbird or keepassxc inside a lightly constrained firejail.  The command could easily point to a script like above in your ~/bin/ directory. <Super>-4 is tied to my script. Name it whatever you like, but be consistent everywhere and make certain the file permissions are set to 700.

**import** without the -root and -display option will wait for a rectangle to be selected. Like this:
```
     /usr/bin/import    -quality 80    "$FILE"
```
I've probably left out a few details that someone new would need to handle. Sorry if I forgot something.  Hopefully someone else will point it out.

I have to do things this way in part because I don't run any DE and choose to run an older window manager. There are trade-offs with our choices. fvwm has very little bloat, uses little memory, little CPU, and is very fast on all hardware.  It has extensions for all sorts of things, including custom extensions, multiple virtual desktops, and the overall fvwm features haven't changed much the last 15+ yrs.  OTOH, it doesn't have any GUI configuration tool for tweaks and some of the configuration options are not exactly intuitive. Trade-offs.

---

### Post by SeijiSensei on 2020-10-26
On Kubuntu you can use the PrtSc key. The application it launches lets you take a variety of screenshots from full screen to specific windows to a custom rectangle. The screenshots get saved to a configurable directory. On my machine, if I take a screen shot, a notification box pops up that I can click on to open the file in the viewer program Gwenview.

Don't know if it works similarly on vanilla Ubuntu.

---

### Post by ajgreeny on 2020-10-26
On Xubuntu pressing print-screen key gives me a window with options as shown in my screenshot.

I have keyboard shortcuts set up to take screenprints of either the whole screen (Print screen), the active window (Print screen +Windows key) or a mouse selected area (Print screen + Alt).

Sorry but the attachments facility is not working at the moment; I'll try later, but the options offered are 
[LIST]
[*]Save
[*]Copy to clipboard
[*]Open with
[*]Host on imgur
[/LIST]

---

### Post by HermanAB on 2020-10-27
The Gimp photo editor has a screenshot feature - in the File menu.

---

### Post by guiverc on 2020-10-27
Modern Lubuntu uses the LXQt desktop, where the image viewer is `lximage-qt` which has a screenshot function (`lximage-qt -s`) where the default isn't to save the image, but show it in the image viewer itself (allowing save of course; lx-image-qt also has some very simple editing functions too like adding arrows, boxes etc but in no ways is it an editor).  A shortcut key is just set to run it when PrintScreen is pressed...

It's not what I'd use in a Ubuntu desktop though; it's efficient in a Qt5 base but Ubuntu is GTK3 so I'd opt for a prior alternative. 

[https://packages.ubuntu.com/focal/lximage-qt](https://packages.ubuntu.com/focal/lximage-qt)
[https://packages.ubuntu.com/focal/screengrab](https://packages.ubuntu.com/focal/screengrab)

(`screengrab` is another like program use by Lubuntu too; depending on release  it'll do the job but I'd use a GTK3 based application on main Ubuntu)

---

### Post by GhX6GZMB on 2020-10-27
Everyone has her/his favourite way of dealing with screenshots.

I prefer using the PrtScr key and automatically placing the shot on the Clipboard. From there it can be used by any program using the "Edit/Paste" menu.
 
Either as PrtScr (full screen) or Alt+PrtScr (active window).

You'll need to assign commands to the PrtScr key. ("Keyboard shortcuts"). Those are "scrot" and "xclip".

PrtScr: **sh -c 'scrot -o /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''**
Alt+PrtScr: [B]sh -c 'scrot -o -u /tmp/clip_$(id -u) -e 'xclip -selection clipboard -t image/png < $f''
[/B]
Either keystroke will store the latest screenshot on the clipboard (older will be overwritten). I don't use a "select a screen area" command, as I find this easier to do after pasting into the subsequent program.

Cheers.

PS: the quotation marks at the end of each command are two single quotes, NOT one double quote.

---

### Post by wolfzrat on 2020-10-29
An alternate solution that I can offer and may help is getting the app called Flameshot, its like snipping tool for windows. or You can also use Gnome Screenshot. Thought i'd try to assist in some way :) Good luck.

P.s. this can be downloaded in the snap store in ubuntu.

---

