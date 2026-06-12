---
title: "The root  terminal and wi-fi"
date: 2005-05-12
forum: General Help
---

### Post by Kurai on 2005-05-12
I probably sound stupid but it's the price I pay.
I have installed ubuntu dual booting xp home & ubuntu on an acer travelmate 2200 w/ 258 ram, 40 GB HD, and an acer IPN2220 wifi card.  I also have two prblems when I try to go to the root terminal it asks for a passwd so i put in the root and it tells me wrong passwd.  How do I retrieve the right passwd.  Also how do i set up the wifi for my card.  Any help you can give me is appreaciated.
Thank you

---

### Post by mendicant on 2005-05-12
How are you getting a 'root terminal'?  Is it right click on the desktop and the first menu item?  Are you doing a sudo gnome-terminal?

Does iwconfig tell you anything (for your wireless card)?

---

### Post by Kurai on 2005-05-12
The root terminal is in the system tools folder in the aplications in gnome.
iwconfig doesn't tell me anything.

---

### Post by mendicant on 2005-05-12
The password is your own password.  It just runs gksudo /usr/bin/x-terminal-editor.

As for your wireless problem, google doesn't turn up much helpful.  One person did manage to get it working using the ndis wrapper at one point.

---

### Post by Kurai on 2005-05-12
Thank you I will try it, and then let you know

---

### Post by Kurai on 2005-05-12
My root passwd doesn't work for the terminal nor does the regular one how do i get the passwd

---

### Post by mendicant on 2005-05-12
If you are running as the original user (the one you entered when you installed ubuntu), then you can just use that password.  Otherwise, you must be listed in /etc/sudoers (basically, you must be in group admin, as listed in /etc/groups).

What is the output of the command:
```

% groups

```

---

### Post by Kurai on 2005-05-13
The output to the command groups from the root account is root
and i'm completely lost

---

### Post by mendicant on 2005-05-13
So you're logged in as root, or as the original user?  If you are logged in as root, then you don't need a root terminal using gksudo--you'd just have to open a terminal.  If, when you type groups, you see only 'root', you're already logged into a root terminal.

What's the output of:
```

% who | grep ":0 " # note that is colon,0,space

```

---

### Post by Kurai on 2005-05-13
I'll check that when I get home but I log in as the normal user then su over to the root in the terminal because it won't let me log in as root at the start screen.

---

### Post by poofyhairguy on 2005-05-13
[QUOTE=Kurai]I'll check that when I get home but I log in as the normal user then su over to the root in the terminal because it won't let me log in as root at the start screen.[/QUOTE]


That works too. If your wireless card doesn't work out of the box, then you probably need ndiswrapper.

Don't be offended, but I'm going to move this. The point of this area is for people who we have to explain what the terminal is!

---

### Post by Kurai on 2005-05-13
Thank you i guess....

Anyway i tried the command and got nothing so i edited the sudoers file now i have root.  Do you know about where to find the ndiswrapper modules for ubuntu?  Tell me if you do.  I apreciate the help.

---

