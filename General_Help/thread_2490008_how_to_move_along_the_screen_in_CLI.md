---
title: "how to move along the screen in CLI"
date: 2023-08-18
forum: General Help
---

### Post by grafeno30 on 2023-08-18
Hi Geeks,

How I could move through a full screen in CLI mode without using the mouse?

For example not using the mouse to select something

One solution is to capture but in TEXT MODE the screen, writing a file and  after view it with a text editor . I´d like be able to navigate directly

Thanks in advance

---

### Post by MAFoElffen on 2023-08-18
It depends in what you are doing and what you are in...

For example, you can always use redirection or tee to put output in different places.

Or in an editor like vi, marking text to cut or copy...

I'm going to show my age when I say I came from emacs on a terminal, and DOS on a PC... I was over joyed using XWindows and a mouse. Graphical terminal sessions are a step above. there is a difference between being a purist, and just torturing yourself when you don't need to be. You can do it, but why? 

Borrowed from a friend: 
"Because something is possible, doesn't make it a good idea."

---

### Post by dragonfly41 on 2023-08-18
You might use [xdotool]("https://manpages.ubuntu.com/manpages/trusty/man1/xdotool.1.html") in CLI.

Or pyautogui.

Or Albert.

Or Actiona.

All for UI emulation.

---

### Post by Holger_Gehrke on 2023-08-18
I can't offer you cut and paste without using the mouse, but you can move in most terminals using shift-PgUp and shift-PgDn. Sadly the virtual terminals have lost this ability, mostly thanks to the move to a frame buffer instead of real text-mode. Alternatively you can use a pager ('more' or 'less'; no that's not a joke, those are the names of the two most well-known pagers and 'less' is more (powerful) than 'more' ...) either directly with a file name or at the end of a pipe to view a file or scroll through the output of a command that produces more than one screenful of text. 

There's also 'screen' and 'tmux' which are called 'terminal multiplexers'. They allow you to have multiple command line sessions in one terminal - either taking the whole of the terminal or splitting the terminal into regions - and allow quite a few of the things you'd expect of a windowing system, including cut and paste - but only inside the terminal sessions under the control of the multiplexer. They also give you a backscroll buffer even in a virtual terminal, configurable through either a command line option or in an initialization file.

And cut and paste on the command line itself is possible through the readline library that the bash and quite a few other programs use. ctrl-k kills text from the cursor to the end of the line, ctrl-u kills text from the cursor to the beginning of the line, and ctrl-w kills the word before the cursor (if you hit ctrl-w multiple times, you kill multiple words, but for the purpose of pasting killed stuff back they are concatenated into one kill). To bring back the last text you killed, you use ctrl-y. To replace the text you just brought back with an earlier kill, you use alt-y. There might be a limit to the size of the kill-ring in which killed text is stored (either regarding the maximum size of a single kill or the number of kills stored on the ring), but in all my years of using the shell I've never reached it. Combine this with moving through command history (cursor up, cursor down, alt-<,alt->) and incrementally searching command history (ctrl-r) and you can assemble new commands from bits and pieces of older commands.

Holger

---

