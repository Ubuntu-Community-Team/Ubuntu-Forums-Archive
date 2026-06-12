---
title: "Ubuntu creating new txt file when I copy/paste?"
date: 2021-11-18
forum: General Help
---

### Post by Friggs on 2021-11-18
Ubuntu 20.04.3 LTS


I am using Google Chrome to learn some business courses on Udemy.com


Part of my workflow is that I copy/paste from the transcription section of Udemy.com into a a notes file (built-in Ubuntu "Text Editor" application).


Sometimes, not always, when I copy and paste to this notes file, Ubuntu will create a new text file for me with with that text snippet that I have just copied and pasted.


Even stranger, this new file that is created gets created in the Music folder that I have open in a completely different workspace.


So in workspace 1: I have VLC media player and my music folder open


In workspace 2 below, I have my Chrome open with my notes file.


So I copy and paste in Workspace 2 to an existing notes file in same workspace and then Ubuntu creates an entirely new txt file with what I just copied/pasted in Workspace 2 in Workspace 1's Music folder.


I have been using Ubuntu for a very long time now following the same work flow and have never seen this.


Any insight is greatly appreciated.

---

### Post by TheFu on 2021-11-18
I use X/Windows and it supports select --> paste.  The act of selecting any text almost anywhere places that text (without formatting) into the x-buffer.  Then the middle mouse button pastes the contents into the widget under the mouse.  This is the expected behavior and has worked this way since at least 1990 in all X/Windows workstations.

GUI programs have to go out of their way to prevent the select-paste from working. I know this because I was an X/Windows programmer for a few years.  Sadly, some programs  ... some webapps ... do exactly this.  Usually it is their attempt to prevent content from being stolen and they implement it by using javascript to capture the select and paste actions. The fix is to disable javascript, but that may prevent the webapp from displaying the desired information or break it completely.  I've never used any paid training online, so I don't know what those do. Sorry.

There are many note-taking programs.  If you want to just create a new text file from the x-buffer paste, then you can use
```
$ cat > tmp-file
```
and paste into that terminal window. After the paste completes, press <cntl>-d to end the input stream.  The 'tmp-file' will have the contents pasted using the middle mouse button.

Not sure I understand the underlying issue or what the goal is to be achieved.  I use vimwiki for my notes after trying to use about 15 other programs first. Each is full of compromises ... the most universal for my needs so far is vim with some wiki-like markdown macros. The wiki can be dumped to html, though I don't really do that.  The only trick with vimwiki when pasting is to be in INSERT MODE. Vim users understand what that means.

---

### Post by vanadium on 2021-11-21
Difficult to imagine what happens. Pasting text from the clipboard will never automatically create a file. When pasting in a file manager, a file may be created because a pathname of a file is in the clipboard, which was put there by copying or cutting a file in the file manager.

---

