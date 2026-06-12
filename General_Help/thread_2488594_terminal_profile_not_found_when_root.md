---
title: "terminal profile not found when root"
date: 2023-07-10
forum: General Help
---

### Post by ulrichmuc2 on 2023-07-10
When I do "mate-terminal --window-with-profile=root" as normal user, it works as expected.
When I do the same as root, I get no 'such profile "root"; using default profile'.
This used to work with 18.4, but not after upgrading to  Ubunto 22.04.2 LTS.

Where does root look for the terminal-profiles?

---

### Post by Holger_Gehrke on 2023-07-10
Not a user of Ubuntu Mate, but all well behaved programs look for their configuration data somewhere in $HOME, modern programs usually in $HOME/.config/program-name. For your normal user account $HOME is probably /home/$USER but for root it's '/root/'.

I don't really understand why you're trying to run the terminal as root. The terminal is just a helper which takes the input from a graphical environment (key-press / key-release events) and turns it into text for text based programs and turns the (text) output of those programs into graphics. The programs running in the terminal might on occasion need root-privileges, the terminal itself should not.

Holger

---

### Post by ulrichmuc2 on 2023-07-10
I want to open a terminal where I am immediately root. So that I don't use it unintentiously, it will have a different color.
The command (started from a panel entry) would be "sudo mate-terminal --window-with-profile=root &"

I now found the solution: I need to start the terminal as root and then create a new profile. This new profile is then later found by root.

---

### Post by Holger_Gehrke on 2023-07-10
'sudo' in a panel entry ? Where will you type in your password in absence of a terminal ? What you should do is to run the terminal as your normal user and run the shell as root. That's still a really bad idea from a security point of view unless this is a home machine and you're living alone and almost never have guests.
For that I'd do something like 'mate-terminal --window-with-profile=root -x pkexec /usr/bin/bash'. 'pkexec' will do a graphical password entry form which sudo needs a lot of help to do. Running only the shell as root stops some unintended consequences of running a graphical application as root. Additionally Wayland - which looks set to become the standard for the base of the GUI - really doesn't like graphical things running as root, so think of this as future-proofing ...

Holger

---

### Post by ulrichmuc2 on 2023-07-11
> [COLOR=#000000]'sudo' in a panel entry ? Where will you type in your password in absence of a terminal ? [/COLOR]

Well, what I really do is the following:
 [COLOR=#000000]echo <my password> | sudo -S [/COLOR][COLOR=#000000]mate-terminal --window-with-profile=root &

Yes, living alone, nobody else touching my computer. But thanks for the hint to pkexec!

ulrich[/COLOR]

---

### Post by Rubi1200 on 2023-07-11
Perhaps I am missing the point of what you are trying to do but please read the documentation here about sudo, root, and especially the part about sudo and shells:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In all honesty, you should not be running a terminal as root even if you are fully aware of the risks involved and willing to reinstall if the slightest thing goes wrong.

Make sure you have rock-solid backups either way.

---

### Post by TheFu on 2023-07-11
In 18.04, sudo didn't change the value of the HOME environment variable.  I don't recall when, but it could be 20.04 or 22.04, sudo's behavior changed to set the HOME environment variable to that of the new userid being used.  That means when a GUI program is used with and without sudo in the newer Ubuntu releases, then the HOME location is completely different.

Effectively the new behavior from **sudo** is like **sudo -H** worked in 18.04.  BTW, all sorts of problems were possible if **sudo -H** was **_NOT_** used to run GUI programs in older Ubuntu releases. I've seen users unable to login because they used sudo with gedit to modify a system file immediate post-install.  

What happened was root created settings for the GUI programs (and parent directories if they didn't exist), so the ~/.config/ could be owned by root.  Gnome freaked out over that and crashed.  Hence, why we've always said not to use sudo with any GUI programs.  

There are other reasons NOT to use sudo with GUI programs too, but some people won't listen.  One reason is that some GUI programs work fine started with sudo because they don't try to silently write config data anywhere.  Unfortunately, most GUI programs do try to silently save config information, without asking first.  Pros/cons.

So, in 20.04 and later (assuming I have the releases correct for when the sudo behavior changed in Ubuntu), sudo is safer with GUI programs than it was before. Other distros had a different default behavior for sudo setting the HOME environment variable for a long time, I believe.

---

### Post by Holger_Gehrke on 2023-07-11
> **ulrichmuc2 said:**
> 
 [COLOR=#000000]echo <my password> | sudo -S [/COLOR][COLOR=#000000]mate-terminal --window-with-profile=root &
[/COLOR]

Never ever store a password in plain text. An attacker who gains access through some service (as the user that service runs as) could then read that password and have the same access as you have. Even the passwords the system stores in /etc/shadow - which is only accessible to root - are only hashes (basically results of a complicated bit of maths that cannot be reversed; for comparison it puts your input through the same bit of maths and compares the result to the stored value). There are ways to configure 'sudo' to not ask for a password for a specific user and a specific command. Read 'man sudoers' if you really want to go this way. Remember that the question for a password serves a double purpose: it not only checks that you're authorized it also reminds you that you're about to do something potentially dangerous.

Holger

---

### Post by ulrichmuc2 on 2023-07-11
The sugested method "[COLOR=#000000]mate-terminal --window-with-profile=root -x pkexec /usr/bin/bash" works nicely for me and I don't anymore have to store the root-password in plain text.
Thanks to Holger!

ulrich

PS: is there a way to mark the thread as solved?[/COLOR]

---

### Post by Holger_Gehrke on 2023-07-11
> **ulrichmuc2 said:**
> [COLOR=#000000]
PS: is there a way to mark the thread as solved?[/COLOR]

The link 'Thread Tools' near the top of the page should offer a way to do that.

Holger

---

