---
title: "Shift+Del doesn't work in tty"
date: 2019-09-29
forum: General Help
---

### Post by &amp;KyT$0P# on 2019-09-29
Xubuntu 18.04 in a VirtualBox VM.  I have this code in my .bashrc to make Shift+Del clear the current command input -
```
bind '"\e[3;2~": kill-whole-line'
```

In GUI terminal apps, it works well.  But if I switch to a tty with Ctrl-Alt-F1 (well, Host key + F1), it doesn't work.

I wasn't able to find anything about this through searching the Internet, but I did turn up that running [FONT=Courier New]read[/FONT] and pressing keys could give useful diagnostic info.  In GUI terminals, this is what's produced for Shift+Del -
```
$ read
^[[3;2~

```

In the tty, I get this instead -
```
^[[3~
```

Which is as if I had just pressed Del by itself.

How to fix the tty to get it to recognise Shift+Del?

---

### Post by Skaperen on 2019-10-01
what is your ultimate goal?  to have some key that clears the line, or a specific key?

the console tty, which that switches to, is about as direct as you can get.  the kernel is emulating the tty device.  it's very simplistic.

does ^U do what you want?  (before you change anything)

---

### Post by &amp;KyT$0P# on 2019-10-03
> **Skaperen said:**
> what is your ultimate goal?  to have some key that clears the line, or a specific key?

My ultimate goal is to have Shift+Del clear the line in the tty, same as it does in GUI terminals.  And I would like to achieve that without also making plain Del (without modifiers) clear the whole line.

> does ^U do what you want?  (before you change anything)

No, it only clears the portion of the line before the cursor, it doesn't clear the whole line.

---

### Post by &amp;KyT$0P# on 2019-10-14
bump

---

### Post by #&amp;thj^% on 2019-10-14
With just my plain .bashrc mine follows this:
[list]

    [*]Clean up the line: You can use Ctrl+U to clear up to the beginning.
    [*]Clean up the line: Ctrl+E Ctrl+U to wipe the current line in the terminal
    [*]Clean up the line: Ctrl+A Ctrl+K to wipe the current line in the terminal
    [*]Cancel the current command/line: Ctrl+C.
    [*]Recall the deleted command: Ctrl+Y (then Alt+Y)
    [*]Go to beginning of the line: Ctrl+A
    [*]Go to end of the line: Ctrl+E
    [*]Remove the forward words for example, if you are middle of the command: Ctrl+K
    [*]Remove characters on the left, until the beginning of the word: Ctrl+W
    [*]To clear your entire command prompt: Ctrl + L
    [*]Toggle between the start of line and current cursor position: Ctrl + XX[/list]
BTW  ctrl-k deletes everything between the cursor and the end of the line on my system.
Just tried your addition in .bashrc and seems to create havoc here In a regular GUI Terminal and a TTY. :(
One more note: You can enable vi mode by echo 'set editing-mode vi' >> ~/.inputrc. Also works in places like python interpreter prompts if needed.
```
me on Mon Oct 14 at 10:06 AM in ~ branch: (HEAD) 
>> echo 'set editing-mode vi'
set editing-mode vi

```

---

### Post by &amp;KyT$0P# on 2019-10-15
> **1fallen said:**
> Clean up the line: Ctrl+E Ctrl+U to wipe the current line in the terminal

Thanks 1fallen, I can use this for now until we figure a way to get Shift+Del working.

---

### Post by Holger_Gehrke on 2019-10-15
I think I solved it. In a virtual terminal you're using the kernels keyboard translation table. On ubuntu these are generated and loaded on the fly from the X keyboard description, AFAIK, so there are no tables stored in the system. You're going to need 'showkey' (in the package kbd) to get the keycode and 'loadkeys' (same package) to load an additional keyboard translation table into the kernel. loadkeys works cumulative, so we only have to write a small table defining one key and a string.
Run 'showkey -k' in a VT to get the keycode for the delete key (mine comes up as 111, YMMV). showkey stops automatically if you don't hit a key for 10 seconds. Now use your favourite editor and write a file named ~/keytable with these contents:
```

shift keycode 111 = F246
string F246="\033[3;2~"

```
Replace the '111' with the keycode for your delete-key.  You might want to check that F246 (the very last Fnnn Macro-String) isn't already used by something. Use 'dumpkeys -f|less' in a console to do so. Now load the table with 'sudo loadkeys ~/keytable', execute your 'bind' and be happy.

Holger

---

### Post by #&amp;thj^% on 2019-10-15
> **Holger_Gehrke said:**
> I think I solved it. In a virtual terminal you're using the kernels keyboard translation table. On ubuntu these are generated and loaded on the fly from the X keyboard description, AFAIK, so there are no tables stored in the system. You're going to need 'showkey' (in the package kbd) to get the keycode and loadkeys to load an additional keyboard translation table into the kernel. loadkeys works cumulative, so we only have to write a small table defining one key and a string.
Run 'showkey -k' to get the keycode for the delete key (mine comes up as 111, YMMV). showkey stops automatically if you don't hit a key for 10 seconds. Now use your favourite editor and write a file named ~/keytable with these contents:
```

shift keycode 111 = F246
string F246="\033[3;2~"

```
Replace the '111' with the keycode for your delete-key.  You might want to check that F246 (the very last Fnnn Macro-String) isn't already used by something. Use 'dumpkeys -f|less' in a console to do so. Now load the table with 'sudo loadkeys ~/keytable', execute your 'bind' and be happy.

Holger
Nicely Done! Works here also. Now if it works on OP's Mac Book.

---

### Post by &amp;KyT$0P# on 2019-10-15
> **Holger_Gehrke said:**
> I think I solved it. In a virtual terminal you're using the kernels keyboard translation table. On ubuntu these are generated and loaded on the fly from the X keyboard description, AFAIK, so there are no tables stored in the system. You're going to need 'showkey' (in the package kbd) to get the keycode and 'loadkeys' (same package) to load an additional keyboard translation table into the kernel. loadkeys works cumulative, so we only have to write a small table defining one key and a string.
Run 'showkey -k' in a VT to get the keycode for the delete key (mine comes up as 111, YMMV). showkey stops automatically if you don't hit a key for 10 seconds. Now use your favourite editor and write a file named ~/keytable with these contents:
```

shift keycode 111 = F246
string F246="\033[3;2~"

```
Replace the '111' with the keycode for your delete-key.  You might want to check that F246 (the very last Fnnn Macro-String) isn't already used by something. Use 'dumpkeys -f|less' in a console to do so. Now load the table with 'sudo loadkeys ~/keytable', execute your 'bind' and be happy.

Holger

Works.  Thanks Holger! :D

---

### Post by &amp;KyT$0P# on 2019-10-31
To get this to persist, I made a systemd service -
```
[Unit]
Description=Make Shift+Del work in tty

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=bash -c "echo -e 'shift keycode 111 = F246\nstring F246=\"\\\\033[3;2~\"' | loadkeys -"

[Install]
WantedBy=multi-user.target

```

---

