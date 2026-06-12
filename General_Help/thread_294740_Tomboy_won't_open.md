---
title: "Tomboy won't open?"
date: 2006-11-07
forum: General Help
---

### Post by sktfeelsdapper on 2006-11-07
So, I downloaded the "awesome program" Tomboy.
And I used it once, to take some notes, sent the notes to html and now they are in firefox.

EXCEPT:

Now I can't open tomboy, I click on the launcher, I changed the path (which tomboy) and still can't open it up.

What's going on?>

---

### Post by Najand on 2006-11-07
Try to run it in the terminal and write errors you got here, please.

---

### Post by qiemem on 2006-11-10
experienced same problem. Check your system monitor, it might be already open (it runs in the background). press alt+f12 (default) to use it. Threw me off too.

---

### Post by DJiNN on 2006-11-15
> **sktfeelsdapper said:**
> So, I downloaded the "awesome program" Tomboy.
And I used it once, to take some notes, sent the notes to html and now they are in firefox.

EXCEPT:

Now I can't open tomboy, I click on the launcher, I changed the path (which tomboy) and still can't open it up.

What's going on?>

Are you running "Edgy"?  It could be a bug in Tomboy (When running under Edgy) because i have the same problem here (Just upgraded to Edgy) and can only access Tomboy (Once it's running) by pressing ALT-F12. 

Apparently others have also noticed this..... :)

---

### Post by qiemem on 2006-11-15
> Are you running "Edgy"? It could be a bug in Tomboy (When running under Edgy) because i have the same problem here (Just upgraded to Edgy) and can only access Tomboy (Once it's running) by pressing ALT-F12.]
I am running edgy. Though, it doesn't bug me at all to be honest. I added an icon for it to one of my panels (just a little dock-like thing I made) and I can also access it from that. 

I'm using it all the time now though.

---

### Post by eg-maverick on 2006-11-16
Here are the error messages I get ( used Synaptic to completely remove and reload - still no good):

laptop:/usr/bin$ tomboy
NoteManager created with note path "/home/forbescw/.tomboy".
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. Done.
Tomboy remote control disabled: Name 'com.beatniksoftware.Tomboy' does not exist.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:8267): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

(Tomboy:8267): libtomboy-WARNING **: Binding '<Alt>F11' failed!

---

### Post by dsanderson on 2006-11-23
I get the same:

davidanderson@apollonia:~/Desktop/tomboy-0.4.1/tomboy-0.4.1$ tomboy
NoteManager created with note path "/home/davidanderson/.tomboy".
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. Done.
Tomboy remote control disabled: Name 'com.beatniksoftware.Tomboy' does not exist.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:9382): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

(Tomboy:9382): libtomboy-WARNING **: Binding '<Alt>F11' failed!

---

### Post by baslow on 2006-11-24
In what may or may not be a related problem I am finding that though I get Tomboy to run Alt-F12 does not work and the icon is invisible on the systray.  I have to hover my cursor over the empty space where I think Tomboy MIGHT be to try to find it.  When I've found it all is well and left-clicking brings up the "Create New Notes" menu, etc.

I'm running under Kubuntu if that makes a difference and I've tried changing  icons but this happens with all that I've tried. 

When I've run Tomboy on the command line error messages are similar to others reported:

tomboy --tray-icon
NoteManager created with note path "/home/baslow/.tomboy".
Trying Plugin: Evolution.dll ... EvolutionPlugin. Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. Done.
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Tomboy remote control disabled: Name 'com.beatniksoftware.Tomboy' does not exist.
EnableDisable Called: enabling... True
Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'

(Tomboy:6028): libtomboy-WARNING **: Binding '<Alt>F12' failed!

Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'
/bin/sh: /usr/bin/esd: not found

---

### Post by dsanderson on 2006-11-24
Still no luck, I did a reinstall from Synaptics, and tried the alt f-12 trick, nothing works. Ksysguard says it is running, but no luck. If I try to uninstall and reinstall with Synaptics, it tells me that it has to uninstall Ubuntu Desktop as well. I have installed K desktop and know longer use gnome. Maybe its okay to let it uninstall Ubuntu desktop? I am at a loss here. I too am runny edgy.

---

