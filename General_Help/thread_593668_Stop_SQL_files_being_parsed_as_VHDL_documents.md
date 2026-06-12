---
title: "Stop SQL files being parsed as VHDL documents?"
date: 2007-10-27
forum: General Help
---

### Post by svivian on 2007-10-27
When I click on some SQL files in nautilus, the type changes to "VHDL Document". I'd never heard of this and from a Google search it looks like some obsure file type that I will never ever use. It means that I can't double click the files to open them, I get an error messgae about conflicting extension and type.

Is there a way to stop Ubuntu/Nautilus parsing these files as VHDL? They are definitely SQL code, I think it's the comments at the beginning of the file that confuse the parser, but I don't wanna remove them for every file...

---

### Post by svivian on 2007-10-28
[bump]

Done some more searching around but can't find anything. Can I remove the VHDL type from a list somewhere? How much of a file does it linux read before deciding on the type?

---

### Post by mcox1982 on 2007-11-01
I'm not sure about the automatic VHDL typing of .sql files. If anybody has some insight I would love to hear that.

However, to allow your .sql files to be opened you can edit your settings using gconf-editor. Type alt-f2 to bring up a command runner and then type gconf-editor navigate to apps->nautilus->preferences and uncheck "display_mimetype_warning". This will allow you to open your .sql files on double-click. It will however also not catch any other mime-type/file extension issues, so be careful.

---

### Post by svivian on 2007-11-01
OK thanks, that's gotten rid of one annoyance. The most annoying this though is documents in Nautilus moving when I click on them - I prefer to order things by type, but when I click on documents, types often change and so the document moves to another place in the list.

Is there perhaps a way to turn OFF this file type recognition, and just use the file extension?

---

