---
title: "Terminator: how to Prevent new terminal from being opened in the same directory?"
date: 2021-01-26
forum: General Help
---

### Post by ranjith19 on 2021-01-26
I have installed the following on Ubuntu 20.10

- zsh
- Oh my zsh
- terminator

When I open a new tab or split window in the terminator, I find that the current working directory is copied from the previous session. I want to instead be in the home directory whenever I open a new terminal.

This is what is happening for example

- I have an open terminal in directory /home/user/folder1
- I open a new terminal
- New terminal is in /home/user/folder1
- How can I prevent this from happening?

Currently I have added this line in .zshrc

cd $HOME

But I do not really like this solution as it prevents me from using open in terminal from context menu from nautilus.

Please help me figure out how I can always open a new terminal to go to home dir.

PS: clone of my unanswered question [https://askubuntu.com/questions/1310610/prevent-new-terminal-from-being-opened-in-the-same-directory](https://askubuntu.com/questions/1310610/prevent-new-terminal-from-being-opened-in-the-same-directory)

---

### Post by ranjith19 on 2021-01-26
I did the following and solved my problem within terminator

- Go to[FONT=Courier New] preferences -> profiles [default] -> Command[/FONT]
- Check **Run a custom command** instead of my shell
- Set the custom command as [FONT=Courier New]cd /home/mydir; exec /usr/bin/zsh[/FONT]


Now a new terminal opens in the home dir instead of the current working directory of the previous terminal

---

### Post by ranjith19 on 2021-01-26
I did the following and solved my problem within terminator

- Go to[FONT=Courier New] preferences -> profiles [default] -> Command[/FONT]
- Check **Run a custom command** instead of my shell
- Set the custom command as [FONT=Courier New]cd /home/mydir; exec /usr/bin/zsh[/FONT]


Now a new terminal opens in the home dir instead of the current working directory of the previous terminal

---

