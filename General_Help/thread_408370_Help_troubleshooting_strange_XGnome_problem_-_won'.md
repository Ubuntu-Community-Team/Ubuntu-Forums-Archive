---
title: "Help troubleshooting strange X/Gnome problem - won't open applications"
date: 2007-04-13
forum: General Help
---

### Post by m0nstr42 on 2007-04-13
I'm looking for some help troubleshooting this strange problem that my wife's laptop has been intermittently experiencing:

Occaisionally she is unable to open any applications in X.  I'm not sure how to even qualify the problem... When you double click any icon on the desktop or click any App/Places/System menu item it displays a "thinking" cursor but ultimately fails to display the app.  However if you, for example, right click on the panel at the top of the screen and click "add item" it allows you to go through the motions and adds the item.  I was even able to add system monitor to see that the processor was not being hogged and there was no massive amount of writing to the hard drive going on, and was furthermore able to access the settings for system monitor.  TomBoy was able to give me a new note.  But if you tried to open a terminal from the app menu or double click on an openoffice document on the desktop you get nothing.  I'm able to go to ctrl+alt+F1 and access a terminal that way and it switches back to ctrl+alt+F7 for X normally.  I was able to make the problem go away by restarting X with a ctrl+alt+backspace, but I'd rather find the root of the problem and fix it.

I'm at a loss... I'm not even sure what program to suspect.  Maybe Nautilus?  It seems that gnome and X are doing their things normally and that it's just the act of creating a new application UI that fails?  Would it be posting log messages?  to what logs?  I've only been around once when it's happened to even be able to check it out but it happens to her once every few days I guess.

The laptop is a Gateway M210 or M410 I think.  It uses 955-resolution and hibernates fairly well.  I'm not sure how closely this problem does or does not correllate with waking up from a hibernate.

Any suggestions would be greatly appreciated.

---

### Post by m.musashi on 2007-04-13
Try to launch the application in a terminal. That way you will get some error output that might help narrow down the problem. I've seen this behavior before. I can't remember all the cases but I remember one had to do with a needed file having the wrong permissions. One way to check that is to run the app with sudo (or gksudo if it's a GUI - which most are) but be careful what you run that way. I wouldn't do anything except to see if it starts. Although running it normally in a terminal (i.e. without sudo) should be enough to see if it's a permission problem since you will get an error about permissions. If it's something else, post the output and we can try and narrow down the problem.

EDIT: one more thought. Try rebooting next time it happens. If there are problems coming out of hibernate that might solve it. Although then you have a problem coming out of hibernate. I've never had much luck with that though.

---

### Post by fanatik on 2007-04-13
Hmm, I had a similar problem a while back when I used to use Mandrake... I think it was to do with DNS and the hostname of the box. Have you changed the hostname at all? Perhaps to a fully qualified name?

I am struggling to remember the problem, and how I fixed it to be honest.

Post the output of the hostname command and see if anyone else has any thoughts.

Regards,
James.

---

### Post by m0nstr42 on 2007-04-13
> **m.musashi said:**
> Try to launch the application in a terminal. That way you will get some error output that might help narrow down the problem. 

My wife's not a normal terminal user, so when this happens it's not likely I'll have a terminal open.  Will I get useful error messages if I try to start from the F1 console, or just error messages telling me that I'm trying to start an X program outside X?  I also can't do this until the problem presents again while I'm right there to see it happen.

I was just looking at her logs and didn't see any obvious red flags, but I'm not 100% qualified to know what a red flag would be.

> **fanatik said:**
> Post the output of the hostname command and see if anyone else has any thoughts.

Haven't changed the hostname since install, it's just "maximus" (which hostname confirms).

---

### Post by m.musashi on 2007-04-13
Having a terminal open wouldn't help. However, when it happens, open a terminal and try to run the application by typing the proper command in the terminal - often just the name of the application. For example, if firefox is the app that won't start, open a terminal and type
```
firefox
```
It will tell you what it's doing and out put any errors. Those errors should help to pinpoint the problem. Running in VT probably won't help. I've never tried to start a GUI app in a VT, but it might also give you the error output. I think a terminal would be easier - at least as a place to start troubleshooting.

Sorry, I don't know much about error logs or which ones to check. There is one command that will give you error log output but I don't remember it. I'll try and find it.

---

### Post by m0nstr42 on 2007-04-13
> **m.musashi said:**
> Having a terminal open wouldn't help. However, when it happens, open a terminal and try to run the application by typing the proper command in the terminal

Therein lies the problem - when this happens I don't have any methods available to open a terminal that I know of (it horks just like every other prog I try to start).  I can't run it from the menus or a desktop shortcut.  Is there another way I could try?  I can try adding a launcher to the panel but I suspect this will suffer the same problems.  That's why I was in VT - it was the only command line I could get to.

---

### Post by m.musashi on 2007-04-13
Ah, now I understand better. If you can't run any applications then it sounds like a system wide problem (dare I say crash?). Since you mentioned this problem with a possible connection to hibernate I would try and rule that out first. My laptop doesn't do sleep or hibernate well and is often frozen on wake up. If possible, avoid using hibernate for a while and see if that help. Also, see if you can determine if the problem manifests after hibernating or if there is a sequence of events that seems to trigger it.

---

### Post by m0nstr42 on 2007-04-13
> **m.musashi said:**
> Ah, now I understand better. If you can't run any applications then it sounds like a system wide problem (dare I say crash?). Since you mentioned this problem with a possible connection to hibernate I would try and rule that out first. My laptop doesn't do sleep or hibernate well and is often frozen on wake up. If possible, avoid using hibernate for a while and see if that help. Also, see if you can determine if the problem manifests after hibernating or if there is a sequence of events that seems to trigger it.

That's the weirdness of the problem.  It's not that no problems can open at all, it's that no problems open when I try to open them from the menu or the desktop.  I can highlight and click and all the normal stuff, they just won't actually open.  It gets the "thinking" mouse cursor then nothing.  Other things, like adding to the gnome panel or opening a new TomBoy note *do* work.  Things operate normally in VT as well.

It could be a problem associated with coming out of hibernate, but it doesn't happen every time.  The infrequency of it happening and the fact that it's not me doing it makes it hard to find a pattern.  She says that there doesn't seem to be a pattern, but she's not a computer person so probably doesn't know what to look for.

---

### Post by fanatik on 2007-04-13
have a look in the file:

/home/user/.xsession-errors

and see if there are any obvious messages in there.

---

### Post by m0nstr42 on 2007-04-13
> **fanatik said:**
> have a look in the file:

/home/user/.xsession-errors

and see if there are any obvious messages in there.

Thanks.  What's the lifetime of this file?  Is there any way to get timestamps on the errors?  I feel like what's in there might be stuff that's only been added since I restarted X to fix the problem last night.  If it happens again I will definitely look at the file.

There's a bunch of errors in there, which I expect is more or less common, none of them look catastrophic.  There are a couple that are repeated pretty frequently though:

```
LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
```
and
```
** (nm-applet:9826): WARNING **: <WARNING>	 nma_dbus_net_properties_cb (): dbus returned an error.
  (org.freedesktop.NetworkManager.NetworkNotFound) The requested network does not exist for this device.
```

The second one sounds fairly innoculous, but the first one could be fishy - involving XtCalloc.  She does have nppdf.so and it has the same permissions as mine (which works and doesn't give me .xsession-errors entries), but it has a different size.

---

### Post by BomanAJeff on 2007-04-15
I just tried to load Tomboy in a terminal window. Here's the output:

Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. Done.
Tomboy remote control disabled: Name 'com.beatniksoftware.Tomboy' does not exist.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:6883): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

(Tomboy:6883): libtomboy-WARNING **: Binding '<Alt>F11' failed!

---

### Post by H.E. Pennypacker on 2007-04-16
Having the very same problem here.  Sometimes, killing X (ctrl-space-backspace) won't help either.  It may be worth noting that I was not hibernating or suspending, but I did close the laptop lid (with processes on going).

Sometimes the problem is only with certain applications.  Sometimes it is with everything.

---

