---
title: "How to stop highlighting in terminal"
date: 2020-07-20
forum: General Help
---

### Post by PopsTheSailor on 2020-07-20
I'm using Lubuntu 20.04 and xfce terminal (although the all do it). I want to stop it from highlighting the folders when using the ls command. I've found a few posts about editing the .bashrc file but they didn't work. How do I stop the highlighting permanently?

---

### Post by GhX6GZMB on 2020-07-20
My first instinctive question is: why would you use Xfce terminal with Lubuntu? It's born with Qterminal.

Apart from that, what exactly do you mean by "highlighting"? Bold? Inverse? Coloring? Blinking?
Clarity is king when asking questions.

---

### Post by PopsTheSailor on 2020-07-20
Well, as I mentioned all the terminal emulators I've tried do it. I am using it because Geany has it listed as one of the options to open the folder of the file you are editing and Qterm wasn't one of them. But that's off point. They all do it. 

What do I mean by highlighting. Well all my folders are a blue font that are then highlighted in a lime-ish green. It's horrible and both distracting and hard to read. So I want to issue an ls command and just get a list of files and folders with no highlighting.

---

### Post by GhX6GZMB on 2020-07-20
Just use the default QTerminal in Lubuntu.
Open it and right-click somewhere. Choose "Preferences". Select a different Color scheme. "WhiteOnBlack" still has blue folders, but with no backlighting. Try some of the others until it's OK.

Done.

---

### Post by Holger_Gehrke on 2020-07-20
It's not a function of the terminal program, it's the 'ls'-command itself. Some bash configuration file executes "alias ls='ls --color=auto' ". Putting an "alias ls='ls --color=never' " into your ~/.bashrc should put an end to all colouring. If you want to use colours but change them to something you like better, read 'man dircolors' and take a look at the environment variable LS_COLORS.

Holger

---

### Post by PopsTheSailor on 2020-07-20
Doing some more investigating, it appears it only does this when I'm listing files / folders on my data drive. Here's an attempt to add a screenshot of what I'm faced with. It's pretty ugly, wouldn't you say? 

[IMG]https://pasteboard.co/Jiz80jH.jpg[/IMG]

---

### Post by raleigh3 on 2020-07-20
There is no screenshot.

---

### Post by PopsTheSailor on 2020-07-20
Yes I know. I have not often had luck adding screenshots to my posts. How do I do it? It asked for a URL so I put my picture up on pasteboard, got the URL and used that. But obviously it didn't work.

---

### Post by raleigh3 on 2020-07-20
Like yourself, the colorization was irritating.

In .bashrc, notice the 2 aliases that are commented out.

```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'
```

---

### Post by GhX6GZMB on 2020-07-20
Here's a screenshot of my QTerminal with the default "linux" color scheme.
Files are light gray, directories are blue, symbolic links are pale green. Personally I think it looks OK.

---

### Post by PopsTheSailor on 2020-07-20
Mine were commented out too. Do I take the # off so they are not commented out? I also tried changing to color=mono (something I think I saw in a different post). Neither worked. And again, to make sure folks see this, the highlighting is only happening ls commands on a separate data partition where I store my files. On my Lubuntu partition, I don't get the highlighting.

---

### Post by GhX6GZMB on 2020-07-20
It's not the terminal playing up, it's your "Geany". Can't help there,sorry.

---

### Post by PopsTheSailor on 2020-07-20
Hum, I'm not sure why you think it's Geany. It's not. This happens if I reboot, don't start Geany and just issue the ls command in both QTerminal and XFCE terminal. How do I include a screenshot and I can show you / everyone?

---

### Post by GhX6GZMB on 2020-07-20
Click on "Go Advanced" here, then upload your file.

---

### Post by Holger_Gehrke on 2020-07-20
Try 'ls --color=never' in any of your terminals. The color-option to ls tells the program when to color; values for the option are always, never and auto (put color-controlcodes in the output if it goes to a terminal, don't put color-controlcodes in the output if it goes to a file or into a pipe). The colours used are set according to the variable $LS_COLORS which can be set using the program 'dircolors'. In the standard ~/bashrc there's a line before the two commented lines with aliases for 'dir' and 'vdir' but after the line beginning with 'test' which should read "alias ls='ls --color=auto' ". Change the 'auto' to 'never'. The shell does **not** watch that file for changes, so you should log out and back in to get the shell to read it.

Holger

---

### Post by PopsTheSailor on 2020-07-20
Here is the results of "ls" on my data partition


[ATTACH=CONFIG]286498[/ATTACH]

---

### Post by GhX6GZMB on 2020-07-20
> **PopsTheSailor said:**
> Here is the results of "ls" on my data partition


[ATTACH=CONFIG]286498[/ATTACH]

I have to agree. Uncommonly ugly.
I've never had that before and have run Lubuntu 19.04, 19.10 and now 20.04LTS using the preinstalled QTerminal (I showed a screenshot earlier).

My feeling is that you've messed around with your system to an extent that you're past the point of no return.
I suggest a new bare metal install to get out of this loop.

---

### Post by sudodus on 2020-07-20
I suspect that you are looking at a Microsoft file system, when it is that ugly. And the execute bit might be set for the files and directories?

What happens when you try the tips by Holger Gehrke in post #15?

---

### Post by Impavidus on 2020-07-21
Using the default settings, this blue text on a green background means it's a directory that's writeable by others and has the sticky bit not set. This is typical for Windows file systems mounted on your Linux system. Ways to change this:
- Use different mount options for your Windows partitions.
- Change colours used by ls. It's controlled by the LS_COLORS environment variable. Read the man page for dircolors.
- Disable colors for ls altogether.

---

### Post by PopsTheSailor on 2020-07-21
Ah, things are starting to make sense now. I didn't get the "windows file system" until Impavidus' post. Yes, my data partition is an NTFS partition because I dual boot to Win10 sometimes. The command 'ls --color=never' worked but that's just issuing the command. A couple of questions:

1. Since I dual into Win 10 sometimes, is there a different partition type other than NTFS I can use that will get rid of the colors?
2. I read the man page on dircolors. It mostly makes sense but it doesn't say what to put into my .dircolors file and what the format is for that file. I did the --print-database and what's interesting is it doesn't list either XFCE or QTerminal as ones it works with. Maybe my first question is the way to go, if there's a way to do it.

---

### Post by PopsTheSailor on 2020-07-21
One more thing. I'm making changes to my .bashrc file and saving them but nothing ever happens. Do I need to: 1) shut down my terminal and reopen, 2) Log out and back in, 3) Shutdown and reboot?

---

### Post by sudodus on 2020-07-21
- You can use [UDF](https://askubuntu.com/questions/952673/how-do-i-copy-a-file-larger-than-4gb-to-a-usb-flash-drive/952706#952706), but there is no tool to repair such a file system.

- With a Microsoft file system you can [mount the partition with other mount options](https://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition/956072#956072) (for example turn off execute for 'others', and get rid of the worst problem.

- It is possible to use the same mount options in /etc/fstab as in a plain mount command line.

---

### Post by sudodus on 2020-07-21
> **PopsTheSailor said:**
> One more thing. I'm making changes to my .bashrc file and saving them but nothing ever happens. Do I need to: 1) shut down my terminal and reopen, 2) Log out and back in, 3) Shutdown and reboot?

Run

```

source ~/.bashrc

```

or log out and log in or shutdown or reboot.

---

### Post by Dennis N on 2020-07-21
the .bashrc file is read and settings applied when you start terminal. So you need to close and restart to see the changes.

---

### Post by TheFu on 2020-07-21
To get the changes in .bashrc, run
**source ~/.bashrc**
[LIST]
[*]inside every already open terminal or
[*]open new terminals or
[*]logoff and login again
[/LIST]


No need to reboot when only one user's settings are involved.

---

### Post by PopsTheSailor on 2020-07-21
OK I'm getting the changes now in my .bashrc file. Back to the highlighting issue. After reading about mounting the NTFS as a different type, I'm going to attempt to figure out dircolors first. I really don't want to mess with my data partition. Dircolors seems confusing but if I muck it up, at least I just have bad or no colors. A much better disaster!

---

### Post by TheFu on 2020-07-21
I'd just remove all colors by replacing the alias with 
```
alias 'ls=ls -F'
```
Put that above all other aliases that reference 'ls' and ensure that any other alias lines with 'ls' on the left hand side are commended out.  That will end colors, but add characters for some important types of file system objects.

To see how those work, run **\ls -F** .... yes, including the leading \ character. That prevents any alias from being used.

---

### Post by sudodus on 2020-07-21
*No colours* is a good alternative :-)

---

### Post by PopsTheSailor on 2020-07-21
Thanks everyone for your help and patience

SUCCESS!!! OK. I'm marking this as solved. For anyone else that stumbles across this thread, what I did was to add the following 2 lines to the very bottom of my .bashrc file. I then saved .bashrc, closed the terminal (all of them if you have multiple one's open) and restart your terminal. The highlighting is gone.

Add these at the bottom of .bashrc

LS_COLORS='ow=01;36;40'
export LS_COLORS

I'm not going to try and explain what ow=01:36:40 does but it worked for me.

---

### Post by TheFu on 2020-07-21
```
export LS_COLORS='ow=01;36;40'
``` is functionally the same as those 2 lines above.

---

### Post by PopsTheSailor on 2020-07-21
I've confirmed that placing 

export LS_COLORS='ow=01;36;40'

at the end of my .bashrc file does the exact same thing so you can do it in 2 lines or 1. Your choice.

---

