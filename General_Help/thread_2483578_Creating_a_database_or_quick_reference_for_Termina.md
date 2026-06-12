---
title: "Creating a database or quick reference for Terminal Commands??"
date: 2023-02-03
forum: General Help
---

### Post by DVD-R on 2023-02-03
Hello All,
I'm wondering what people are using as a utility for recording and rapidly pulling up terminal commands which you use for various processes?

One can record ALL Terminal Commands within a one single text file
And then search that file - when one needs to find a Terminal Command for a given purpose.

Or one could perhaps record them in one single document for rapid searching
Or one could put them into several text files named by categories "File Commands", "Network Commands"... etc

Or one could even build a tiny personal database for Terminal Commands for rapid searching

For those of you who use Terminal Commands and don't have perfect memory of every command - what do you use or suggest to record them for rapid search and usage?
Sincere thanks!

---

### Post by coley9225 on 2023-02-03
DVD-R, hello.
All the commands you run are saved in  /home/<user>/.bash_history. This is a simple text file. It can be set to save as many commands as you want(setting in preferences in you terminal), and I believe the default is to save the lastt 1000 or 2000 commands. I have a script that appends the date to the file at midnight daily,and it reads the number of lines in the file. When it gets to 1500 lines, it copies the file whith a new name, clears the default file(~/.bash_history), and the process starts over. I can open ./bash_history with a text editor and search for a partial command, say 'chmod', and view the entire command if I need to. It should be quite easy to append the existing .bash_history to the new file, rather that have multiple files, based on when I reach 1500 lines, and search all of your past commandss that way.

Another, slightly more time consuming idea, is to simply go through the ./bash_history file and copy any commands you struggle to remember to a new text file.

Hope this helps give you ideas on how to go back and search through your previous commands. I'll be happy to share the script if you would like to take a look, and modify to your needs.

---

### Post by DVD-R on 2023-02-03
Thank you very much coley9225

What do you do in the event - you have a command syntax in your log which will produce an error - and another instance of it which is correct?
How do you know which one is the correct one?

---

### Post by oldfred on 2023-02-03
I am a regular here in forums. Notices many times issues are the same, so started saving links & commands to text file.
Links then had to be copied.
Imported files to Zim which can have links directly work. So have multiple text files with links & commands. zim has both a find on a page & a search for all pages. And you can turn on various plugins like Table of contents. If you set any heading, then it is in toc, so you can jump directly to that section on that page.

---

### Post by Holger_Gehrke on 2023-02-03
I simply use 'apropos' from the package man-db - should be installed by default - to find commands. It uses an index of every relevant word in the first paragraph of the manual page of every command which by convention contains an abstract of the page. Add the history function of the shell and the keyboard shortcut for incrementally searching the history (ctrl-r reverse search) and the problem is solved as far as I'm concerned ...

Holger

PS: @coley9225 - are you aware of HISTTIMEFORMAT ? If this variable is set to a time specification like the one used for strftime() a time / date is put as a comment into the historyfile for each and every command. I have this set to '%F %T ' - iso date and 24 hour time.

---

### Post by DVD-R on 2023-02-03
Thank you OldFred!
I'll take a look at Zim!

My first introduction to it!  :-]

---

### Post by DVD-R on 2023-02-03
Thank you Holger_Gehrke!
I'll look at that also!

My thanks!  :-]

---

### Post by MAFoElffen on 2023-02-04
Could also be used for command history, if so desired...
> 
**Gnome Clipboard History**  is a Gnome extension that saves what you've copied into an easily  accessible, searchable history panel. The extension is a rewrite of  Clipboard Indicator with vastly improved performance, new features, and  bug fixes.

[https://extensions.gnome.org/extension/4839/clipboard-history/](https://extensions.gnome.org/extension/4839/clipboard-history/)

---

### Post by SeijiSensei on 2023-02-04
I usually just hit the up arrow key enough times to get back the command I want.

If I don't remember exact syntax I just use man or apropos.

---

