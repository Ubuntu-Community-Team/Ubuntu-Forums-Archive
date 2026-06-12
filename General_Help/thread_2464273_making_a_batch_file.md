---
title: "making a batch file"
date: 2021-06-28
forum: General Help
---

### Post by thaddeus2 on 2021-06-28
Hi All,

I have a VPN client installed. 

everytime i need to run it i need to type a long command. 

I wanted to know if i can run this long command quickly by just adding it to a batch file. 

My command is as under

[COLOR=#202124][FONT=Roboto]sudo ./[/FONT][/COLOR][cclient.sh]("http://cclient.sh/")[COLOR=#202124][FONT=Roboto] start --user [email]abc@mycompany.com[/email] [/FONT][/COLOR][COLOR=#202124][FONT=Roboto] --account mycompanyname

I would like to add this to some batch file so i can just execute the batch file and the command executes without me typing the long line. 

Please advise. 
-thads

[/FONT][/COLOR]

---

### Post by scorp123 on 2021-06-28
> **thaddeus2 said:**
> 
I wanted to know if i can run this long command quickly by just adding it to a batch file. 


They are called **"shell script"** here.
[https://medium.com/tech-tajawal/writing-shell-scripts-the-beginners-guide-4778e2c4f609]("https://medium.com/tech-tajawal/writing-shell-scripts-the-beginners-guide-4778e2c4f609")

> **thaddeus2 said:**
>  I would like to add this to some batch file so i can just execute the batch file and the command executes without me typing the long line.

Put that line into a shell script and execute it.

```

#! /bin/bash
sudo /full/path/to/cclient.sh start --user abc@mycompany.com --account mycompanyname

```

**EDIT:**  Relative path "./" replaced with absolute path example. Depending on where you place the script and where the other "cclient.sh" shell script is located the relative path "./" might not even work correclty, as noted by others here on this page.

Make sure it has the "Execute" permissions set. Voila. Either call this script by name from a terminal (make sure you get the path correct or else you will get "Command not found" ...) or place it on your desktop and double-click it.

---

### Post by ActionParsnip on 2021-06-28
You may want to use absolute path to the binary in your script

---

### Post by vanadium on 2021-06-28
For this case, creating a shortcut for a single command, you could also set up an alias:

```
alias ccli='sudo ./cclient.sh start --user abc@mycompany.com --account mycompanyname'

```

Typing out ccli then enter will execute the full command.

To have the alias always available, put this command in a hidden file "~/.bash_aliases" in your home folder. If that file does not exist, create it.
 
As noted by ActionParsnip, your command only will work if the cclient.sh resides in the directory that is currently the default ("working directory"). To make sure the command works always, replace the relative path name './' by the full path.

---

### Post by CatKiller on 2021-06-28
You have other options, too. The shell remembers things you've typed, so you can just press up to recall what you typed. You can also type the first couple of letters and then press a button to search through the history to find entries that match; mine's been set to Page Up for years so I can't remember what the default is. You can also create an alias so that typing one (short) command will actually run another (long) command.

---

### Post by Holger_Gehrke on 2021-06-29
One more option is to create a .desktop file for the command. Then you can start it from the GUI. In doing so you should replace the 'sudo' with 'pkexec' which displays a graphical form for password entry and you should give a full absolute path to the 'cclient.sh'. The details on desktop files can be found on [freedesktop.org]("https://specifications.freedesktop.org/desktop-entry-spec/latest/").

Regarding the shell history search CatKiller mentions: the readline library - which the shell uses for command entry - offers six search commands (incremental search forward and backward (ctrl-s,ctrl-r), non-incremental search forwards and backwards (alt-p, alt-n), and search for the text between start of line and cursor - as CatKiller described - which isn't bound to a key by default. There is a bit of a problem with this approach: while the shell does keep the history across sessions in a file (~/.bash_history) there's a limit to the number of lines of history, so old commands that haven't been reused get forgotten. It also seems a bit random which history goes to the file if you've got several shells open. I wouldn't rely on the shell history for anything important.

Holger

---

### Post by CatKiller on 2021-06-29
> **Holger_Gehrke said:**
> There is a bit of a problem with this approach: while the shell does keep the history across sessions in a file (~/.bash_history) there's a limit to the number of lines of history, so old commands that haven't been reused get forgotten. 

True, but the OP is running it every time, which is why they want to script it in the first place. How many lines to keep is configurable. 

> It also seems a bit random which history goes to the file if you've got several shells open.

My understanding is that each open shell will read from the file at the start of the session, then remember its own history for the session, and then write to the file when it's closed. So you can't search through something you wrote in a different shell while that shell is still open, nor if you wrote the command in a different shell since you opened your current shell, but all the commands you'd written in prior sessions will be preserved. Just not necessarily in the order you first wrote them.

---

