---
title: "unknown files"
date: 2007-11-21
forum: General Help
---

### Post by go_beep_yourself on 2007-11-21
These files appeared in my home directory one day, and I have no idea how they got there, or where they are from. Can anyone tell me? My guess is that it is a automatic backup of some sort, but of what?

untitled1_MAS.bak
untitled2_MAS.bak
untitled3_MAS.bak
untitled4_MAS.bak
untitled5_MAS.bak

The file command says that each of them are XML files. The files will not open in Firefox. When I open them up in a text editor, It shows a bunch of random looking characters, so it might be something encrypted.

---

### Post by goldencako on 2008-02-17
I have a bunch of those files myself. I managed to open a few. I think thay have something to do with Maple. I didn't fret too much because they are backup files. anyways, i think they are harmless.

---

### Post by grogger13 on 2008-02-27
wow, thats probly it.  I just started getting these files this semester and i had installed maple on my computer for school work.  i wish they didn't do that but if thats all it is then fine for me

---

### Post by go_beep_yourself on 2008-02-27
You guys are right. I've also been using Maple. So it's safe to delete those files because I have not done anything important with it. I was only playing around, and I'm at the Calculus 2 level which is everything about integration mostly.

---

### Post by gcranston on 2008-04-07
They're Maple autosave files. I have no idea how to get them to go somewhere else without mucking about through source code and hidden prefs.  But yes, you're completely safe to delete them.

If you tel Maple not to autosave (tools->options->general) they won't pop up anymore.

---

### Post by gcranston on 2008-04-07
After a little more digging, this may be a bug.  From the maple help files:

AutoSave saves a copy of the worksheet in the same directory as the worksheet file. The filename is the worksheet's filename with _MAS appended to it. When the worksheet is manually saved, the _MAS file is deleted.
When you open a _MAS worksheet that has been automatically saved, the worksheet is read-only. Therefore, you must use Save As to save the _MAS worksheet as a Maple worksheet.
AutoSave does not save the worksheet under the following conditions.
The worksheet does not have a filename associated with it.
The worksheet has not been changed.
The worksheet was loaded using the HTTP protocol.

So these autosave files appear to be going to the home directory because they're from unnamed worksheets, which means they shouldn't have been autosaved. Autosaves for worksheets with names go to the same directory as the saved sheet.  I may submit this to MapleSoft.

By the way, I'm using maple 10, so this may have been fixed in 11, or the upcoming 12, due out in June.

---

