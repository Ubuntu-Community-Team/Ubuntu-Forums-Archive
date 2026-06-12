---
title: "Why Can't I View Any Data In Text Files As Root?"
date: 2012-11-21
forum: General Help
---

### Post by NoSalt on 2012-11-21
Hello All

    I have a weird issue that I just cannot figure out. The problem started "out of the blue", but probably after some past update, I'm just not sure which one.

First my specs:
    Dell T110
    XUbuntu 12.04

Now the issue. When I Vi a system file (e.g., all files in /etc) as myself, they look normal. However, if I "sudo Vi" that same file so that I can make changes, one of two things happen:

1) All the text in the file is this horrible yellow color.

    -or-

2) I cannot see any of the text in the file, at all, unless my cursor is directly on top of a character, at which point I can see only that one character.

Typically, it is option #2. It is the darndest thing I have ever seen. This happens if I am sitting at the machine on a terminal, or if I am secure shelled into the machine from a remote location. Anyway, If anybody can help out, I would appreciate it.

Thank you for taking the time to read, and have a great day!    :)

---

### Post by JKyleOKC on 2012-11-21
When you do the "sudo vi" you temporarily switch into the super-user account, and its configuration files are different from your own. It sounds as if in your system, "root" is set up for yellow text, or possibly for foreground and background to be the same color. This isn't normal but I have no idea how things got that way.

A quick and simple fix would be to try "sudo nano" instead of vi; I've found that the "simplification" applied to vi in this distribution makes my past knowledge of it rather useless -- for instance the arrow keys don't work in "insert" mode, nor do backspace or delete. Using nano instead might let you do the needed editing.

To get vi back into working order, take a look at the directory /etc/vim and especially the two configuration files it contains. In my 10.04.4 system, "vi" is actually a symlink to "vim.tiny" and that probably accounts for part of the problems I have had with it; you may be able to tweak these files to make the editor behave, if it's your editor of choice. Myself, I simply switched to using "mousepad" in the GUI instead, and "gksudo mousepad" as the command to launch it as root...

---

### Post by Impavidus on 2012-11-22
On my 12.04 with default configuration vi is a symlink to vim.basic, just as vim, so 't is the same program.

Per user configuration of vi(m) is in .vimrc in the home directory, system wide configuration in /etc/vim/vimrc or /etc/vim/vim.tiny. Something could be wrong here.

Which colours  are used by vim depends on whether you have a dark or a light background in your terminal. Vim typically guesses the background (don't ask me how) and then selects either light or dark letters. The problem might be that when you use sudo vim has trouble guessing the background. It can be set manually with```
:set background=dark
:set background=light
```

---

