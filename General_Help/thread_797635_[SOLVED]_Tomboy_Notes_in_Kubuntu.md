---
title: "[SOLVED] Tomboy Notes in Kubuntu?"
date: 2008-05-17
forum: General Help
---

### Post by zachthejones on 2008-05-17
I've recently gotten massively addicted to using Tomboy Notes. I just installed Kubuntu on my Ubuntu desktop (via "sudo apt-get install kubuntu-desktop) with no problems.

But I can't get tomboy notes to run!!!!

I NEED this program to work....and I'm really enjoying kubuntu.

here's the output I get in Terminal when I run "tomboy":
```
[DEBUG]: NoteManager created with note path "/home/zach/.tomboy".
[INFO]: Initializing Mono.Addins
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.Tomboy
[DEBUG]: 	       Name: Tomboy.Tomboy,0.10
[DEBUG]: 	Description: 
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/Tomboy.exe
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.ExportToHtmlAddin
[DEBUG]: 	       Name: Export to HTML
[DEBUG]: 	Description: Exports individual notes to HTML.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/ExportToHtml.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.PrintNotesAddin
[DEBUG]: 	       Name: Printing Support
[DEBUG]: 	Description: Allows you to print a note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/PrintNotes.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.BacklinksAddin
[DEBUG]: 	       Name: Backlinks
[DEBUG]: 	Description: See which notes link to the one you're currently viewing.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Backlinks.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.EvolutionAddin
[DEBUG]: 	       Name: Evolution Mail Integration
[DEBUG]: 	Description: Allows you to drag an email from Evolution into a tomboy note.  The message subject is added as a link in the note.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/Evolution.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FixedWidthAddin
[DEBUG]: 	       Name: Fixed Width
[DEBUG]: 	Description: Adds fixed-width font style.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FixedWidth.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.StickyNoteImportAddin
[DEBUG]: 	       Name: Sticky Notes Importer
[DEBUG]: 	Description: Import your notes from the Sticky Notes applet.
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/StickyNoteImport.dll
[DEBUG]: StickyNoteImporter: Sticky Notes XML file does not exist or is invalid!
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.WebDavSyncServiceAddin
[DEBUG]: 	       Name: WebDav Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a WebDav URL
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/WebDavSyncService.dll
[DEBUG]: AddinManager.OnAddinLoaded: Tomboy.FileSystemSyncServiceAddin
[DEBUG]: 	       Name: Local Directory Sync Service Add-in
[DEBUG]: 	Description: Synchronize Tomboy Notes to a local file system path
[DEBUG]: 	  Namespace: Tomboy
[DEBUG]: 	    Enabled: True
[DEBUG]: 	       File: /usr/lib/tomboy/addins/FileSystemSyncService.dll
[DEBUG]: Unable to locate 'gnomesu' in your PATH
[DEBUG]: Using '/usr/bin/gksu' as GUI 'su' tool
[DEBUG]: Successfully found all system tools
[DEBUG]: Unable to locate 'wdfs' in your PATH
[DEBUG]: Tomboy remote control disabled (DBus exception): Unable to open the session message bus.
[DEBUG]: EnableDisable Called: enabling... True
[DEBUG]: Binding key '<Alt>F12' for '/apps/tomboy/global_keybindings/show_note_menu'
[DEBUG]: Binding key '<Alt>F11' for '/apps/tomboy/global_keybindings/open_start_here'

```

---

### Post by ajgreeny on 2008-05-17
A google search of tomboy on kde brings up masses of items which may help you.  I have not spent time looking at them all but there are many who had problems and then managed to get it running without too many difficulties.  Have a look and you may find the answer.

PS  Tomboy is strictly a gtk app, though I agree that doesn't usually stop them running if all the correct libraries are installed, which they will be if you still have ubuntu desktop, ie gnome, installed.

---

### Post by zachthejones on 2008-05-18
I ended up going to Kubuntu forums and starting a [thread]("http://kubuntuforums.net/forums/index.php?topic=3094579.0") there to see if anyone on that end knew what was going on. check it out to see what we worked through.

In the end, I think the version that was installed with Ubuntu (my original installation) worked fine. I did try removing and reinstalling it, but it behaved the same.  What I did realize, though, was that when I ran Tomboy in Terminal (or Konsole, for Kubuntu) that, though there were a couple of error messages, the tomboy icon showed up in the KDE tray at the bottom.

It worked fine there as long as I kept the Terminal session open. But, when I logged out with that terminal session open, when I logged back in, the icon was still in the tray and would run Tomboy notes. I then closed out the terminal session which had opened automatically when I logged in and I had my Tomboy notes running as they had been in Ubuntu.

Not so much a solution as a workaround...I think...

---

### Post by AcidicChip on 2009-04-25
Your best bet is to go to KMenu->System Settings->Advanced->Autostart and add /usr/bin/tomboy and it'll start up (and remain) as expected.

---

