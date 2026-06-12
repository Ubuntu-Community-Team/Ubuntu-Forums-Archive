---
title: "tomboy is not opening(working)"
date: 2008-02-02
forum: General Help
---

### Post by thirunavukkarasu on 2008-02-02
Hi Ubuntu users,

Using tomboy in Ubuntu -7.10 i can't able to open the tomboy. when tried with pointer it remains ideal. i am ?:confused: 

when the same is tried in terminal with tomboy command:

the log message seen in terminal is below:

DEBUG]: NoteManager created with note path "/home/hcl/.tomboy".
[INFO]: Initializing Mono.Addins
WARNING: Could not scan file: /usr/lib/tomboy/Tomboy.exe
WARNING: The add-in 'Tomboy.PrintNotesAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.FixedWidthAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.BugzillaAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.StickyNoteImportAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.BacklinksAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.ExportToHtmlAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.EvolutionAddin,0.1' is trying to extend '/Tomboy/NoteAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.NoteOfTheDayAddin,0.1' is trying to extend '/Tomboy/ApplicationAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.BugzillaAddin,0.1' is trying to extend '/Tomboy/AddinPreferences', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.NoteOfTheDayAddin,0.1' is trying to extend '/Tomboy/AddinPreferences', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.WebDavSyncServiceAddin,0.1' is trying to extend '/Tomboy/SyncServiceAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.FileSystemSyncServiceAddin,0.1' is trying to extend '/Tomboy/SyncServiceAddins', but there isn't any add-in defining this extension point
WARNING: The add-in 'Tomboy.SshSyncServiceAddin,0.1' is trying to extend '/Tomboy/SyncServiceAddins', but there isn't any add-in defining this extension point


Does anybody faced the issue. Hope to resolve soon. 

the thing i have tried is removed the tomboy package and reinstalled. After this also the situation remains the same.

regards,
Thiru.S

---

### Post by AndyCooll on 2008-02-02
You could delete your .tomboy folder in your home folder. It would perhaps be worth backing it up first, for if that fixes your problem you could then try re-introducing your backed up notes again.

:cool:

---

### Post by yabu on 2008-05-08
I too was unable to start tomboy
After trying to start tomboy from the terminal I had messages relating to mono.addins
having tried the remove completely option in synaptic then installing again found this did not work and had the same messages in the terminal.
since the terminal messages mentioned mono addins I removed

tomboy
libmono-addins0.2-cil
libmono-addins-gui0.2-cil
this also removed f-spot.

after installing tomboy, all was well, the tomboy icon appeared on the toolbar 
and on opening tomboy all my notes appeared.
After installing f-spot all was well with that too.

---

