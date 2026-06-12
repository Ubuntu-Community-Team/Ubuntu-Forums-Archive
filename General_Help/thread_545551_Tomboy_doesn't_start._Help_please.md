---
title: "Tomboy doesn't start. Help please"
date: 2007-09-07
forum: General Help
---

### Post by Croaker on 2007-09-07
Hi 2all, i'm new here.

Being a windows user for many years now i'm running Feisty for a couple months. One day i've done something (don't ask me what) with Tomboy and after that it fails to start. Running it from terminal brings this:

...@HOME1:~$ tomboy
[DEBUG]: NoteManager created with note path "/home/andrew/.tomboy".
Trying Plugin: Backlinks.dll ... BacklinksPlugin. [DEBUG]: Done.
Trying Plugin: Bugzilla.dll ... BugzillaPlugin. [DEBUG]: Done.
Trying Plugin: Evolution.dll ... EvolutionPlugin. [DEBUG]: Done.
Trying Plugin: ExportToHTML.dll ... ExportToHTMLPlugin. [DEBUG]: Done.
Trying Plugin: FixedWidth.dll ... FixedWidthPlugin. [DEBUG]: Done.
Trying Plugin: NoteOfTheDay.dll ... NoteOfTheDayPlugin. [DEBUG]: Done.
Trying Plugin: PrintNotes.dll ... PrintPlugin. [DEBUG]: Done.
Trying Plugin: StickyNoteImport.dll ... StickyNoteImporter. [DEBUG]: Done.
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: Tomboy remote control active.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

Unhandled Exception: System.ArgumentOutOfRangeException: Argument is out of range.
Parameter name: startIndex
at System.String.Substring (int) <0x000cb>
at NoteOfTheDay.GetContentWithoutTitle (string) <0x0002a>
at NoteOfTheDay.HasChanged (Tomboy.Note) <0x00071>
at NoteOfTheDay.CleanupOld (Tomboy.NoteManager) <0x00286>
at NoteOfTheDayPlugin.CheckNewDay (object,System.EventArgs) <0x00075>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_void_object_EventArgs (object,System.EventArgs) <0x0003e>
at Tomboy.InterruptableTimeout.TimeoutExpired () <0x00019>
at (wrapper delegate-invoke) System.MulticastDelegate.invoke_bool () <0x0002c>
at TimeoutProxy.Handler () <0x0002a>
at (wrapper native-to-managed) TimeoutProxy.Handler () <0x00036>
in (unmanaged) 0xb7f123c5
at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
at Gtk.Application.Run () <0x00007>
at Gnome.Program.Run () <0x00007>
at Tomboy.Application.StartMainLoop () <0x00014>
at Tomboy.Tomboy.StartTrayIcon () <0x000b2>
at Tomboy.Tomboy.Main (string[]) <0x001bc>

Reinstalling and adding Tomboy applet to the deskbar results with nothing. Could anyone here help?

Thanks in advance.

---

### Post by K.Mandla on 2007-09-07
That looks like an error in the code somewhere. Did you check Launchpad for any bug reports? It's possible that there's something wrong with the package itself.

---

### Post by Croaker on 2007-09-08
Checked. Seem that i'm unique with this bug...

---

### Post by Marc Hoffman on 2007-09-20
I am having the same problem- it has started the same time as I added Flock to my system.  Did you find a way round the problem?

---

