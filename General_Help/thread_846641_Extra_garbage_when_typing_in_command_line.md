---
title: "Extra garbage when typing in command line"
date: 2008-07-01
forum: General Help
---

### Post by Aterian on 2008-07-01
I'm currently running an Ubuntu 7.10 (gutsy) server, and I have the following problem when using the local command line.

When I enter commands, everything works fine.  However, when I go back and edit a command, extra garbage is added at the end.  This is a display issue (commands still work as typed, but display incorrectly).  An example:

Type a command:

$cp file file.copy
Works fine

Bring back previous command (hit up)

$cp file file.copy
Works fine

Edit the command (now I want to copy file to file2.copy)
CLI displays -> $cp file file2.copy.copy
Actual command -> $cp file file2.copy
An extra garbage ".copy" has been added to the end of the displayed command (though not the actual executed command).

Edit the command further (I actually want to copy file2 to fil2.copy)
CLI displays -> $cp file2 fil2.copy file2.copy.copy
Actualy command -> $cp file2 file2.copy
Now the entire string " file2.copy.copy" has been added to the end "garbage" section and the correct command is displayed in front of it.

Final example edit: I had a typo and want to copy "2file" not "file2"
Delete the extra "2" -> $cp file file2.copy file2.copy file2.copy.copy
Add the leading "2" -> $cp 2 file file2.copy file2.copy file2.copy.copy
Actual command -> $cp 2file file2.copy
As you can see, when typing at the beginning of a word/argument, it will often add extra displayed spaces.  Deleting characters in the middle of a command also causes problems.

Similar formatting problems occur at least in vim, and probably other command-line text editors (haven't checked).

I had a problem like this once before (where strange formatting issues caused the CLI to display the wrong thing), but it was because the shopt -s checkwinsize command was missing from my .bashrc and that is not the case this time (the problem is also slightly different).  Any help/insight would be appreciated.

---

### Post by sdennie on 2008-07-01
I haven't looked very closely at the exact details but, I've seen similar sorts of behavior when $PS1 (the prompt) is set to something really odd.  Have you changed the prompt at all?

---

### Post by Aterian on 2008-07-01
Someone else did the early server setup, but as far as I know they didn't change anything in .bashrc, and I haven't changed anything since I started using it.

Currently getting

$ echo $PS1
${debian_chroot:+($debain_chroot)}\u@\h:\w\$

(hopefully I typed that right) which doesn't seem too far off.

---

### Post by sdennie on 2008-07-01
That looks like the default Ubuntu prompt.  Not sure what the problem could be.

---

### Post by VMC on 2008-07-01
This happens in both Terminal and VIM?  I'm assuming your using bash. Maybe something in .bashrc has been altered, or did this just start happening?

Does the same thing happen using xterm?

---

### Post by Aterian on 2008-07-01
Yes, I'm using bash as the shell, and I agree that it sounds like something weird in .bashrc, although I'm not aware of any changes to it since Ubuntu was installed.  As far as I know this has been happening for a while.  We don't have ssh connections open (and I'm no longer near the server) so I can't test other shells/terminals at the moment.

---

### Post by Aterian on 2008-07-07
A quick bump and update.
When using vim, the behavior is as follows (Underlined/Bolded = cursor position):
_**S**_ome line of text

Moving the cursor right makes it look like this
Some lin_**S**_ome line of text
Some line of t_**S**_ome line of text

Moving left has no issues, so moving back after the above
_**S**_ome line of tSome line of text

Deleting anything causes the line to reset, so
_**o**_me line of text

and various other weird garbage similar to what happens at the terminal prompt.

---

