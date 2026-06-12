---
title: "After installing Eclipse, Ubuntu won't boot"
date: 2005-04-28
forum: General Help
---

### Post by angryfix on 2005-04-28
Actually, it wasn't so much Eclipse screwing up Ubuntu, it's the dumb thing I did after I installed it that screwed everything up.

Hoary was working perfectly for me and was quickly replacing Windows XP as my primary OS. Needing only a few things to complete the switch, I installed Java (which worked fine) and then installed Eclipse (which installed and ran fine). Well after I installed Eclipse on my desktop, I realized I wanted the Eclipse folder not on my desktop but with the rest of the programs in /usr/share (Sorry if this is a dumb idea, but I'm new to Linux and used to having programs in a directory, like C:\Program Files). I tried to simply copy the Eclipse folder into usr/share, but access was denied. Being the Linux novice that I am, I tried to $sudo chmod user/share to a level where I had write permissions so that I could drag and drop Eclipse into usr/share. The command executed successfully but then something weird happened right after. Every icon turned to the same blank page thingy, so I couldn't tell files apart from folders. Thinking this was a stupid glitch, I restarted my computer hoping to boot back into Ubuntu and have everything be back to normal....no go on that. When I restarted my computer, it started to load Ubuntu (doing all the unpacking and "blahblah .... [ok]" stuff) but then at the end, the screen just flickered.

Well that's about as far as I can go in Ubuntu. Either I get the flickering screen or it just sits still and does nothing. So experts, what in the hell did I manage to do?

*NOTE: Go easy. I already had a friend scold me for not trying $sudo cp.

---

### Post by shakin on 2005-04-29
Try booting in recovery mode or if that doesn't work use the Ubuntu Live CD to boot your computer. That should give you access to your Ubuntu root directory.

While I don't know how to help you properly change your permissions back, I suspect the problem is that no files there are executable anymore. From the console, run something like 'chmod -R 777 /usr/share/' (I assume you  used the -R option when changing permissions the first time, thus affecting all files and directories under /usr/share/).

Doing this will compromise security because it leaves your /usr/share/ wide open, but by removing all restrictions on those files and directories it should let you get back in. chmodding 776 might work as well and would be more secure... I just don't know and I don't really want to test it on my system :)

---

### Post by shakin on 2005-04-29
Here's slightly better advice. It appears as though the permissions for /usr/share and its subfiles and directories is rwxr_x_r_x or lower (many aren't executable). So, I suggest you run two commands:
```

$ chmod -R 766 /usr/share
$ chmod -R +x /usr/share

```

And I bet that will work :)

I'm sure there is a one-command version of this, but this is what I know without testing. Also, this will make everything executable even though not all files should be. They'll still work, but security will be compromised.

---

### Post by bigzak on 2005-04-29
[QUOTE=angryfix]I tried to $sudo chmod user/share to a level where I had write permissions[/QUOTE]

What was the exact command you typed? Open a terminal and type

less .bash_history

and hit <shift>+G to get to the bottom and you can scroll back with the up arrow if you can't remember.

Depending on what you did, it may be easy or not to recover completely. Either way, there should be a working solution even if it's not perfect.

---

