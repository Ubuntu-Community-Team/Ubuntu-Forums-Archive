---
title: "Help - please tell me if I did anything here that hurt my gutsy install. . ."
date: 2007-10-20
forum: General Help
---

### Post by episodic on 2007-10-20
I entered the following commands below into the terminal.

It did not work. It did not give me any warnings, etc.

The wiki was for Feisty. I'm using gutsy - I was hoping it would work. it did not. By entering these commands did I hurt something? Can someone tell me if I need to undo these commands some sort of way.

The goal was to have "control - alt - delete" open the gnome system monitor - anyone tell me how to accomplish this and what I may have done to bork the system if anything at all?



How to enable Ctrl+Alt+Del to open System Monitor in GNOME

gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

---

### Post by Dr. Nick on 2007-10-20
that really wont hurt anything. It just created a few keybinds which shouldnt have any negative effect

Why it didnt work I dont know, Are you using compiz or emerald? Maybe it isnt working is you dont use metacity?

---

### Post by g2g591 on 2007-10-20
thats one reason why I like KDE, to do the same thing there all you have to do is use kmenu editor (just right click on the button and select menu editor). (posting this for the benefit of  any Kubuntu users out there reading this)

---

### Post by episodic on 2007-10-20
No, I don't use compiz at all - even removed it. 

If it created keybinds why don't they work?

Are the keybinds stored in your home folder?

---

### Post by Dr. Nick on 2007-10-20
> **episodic said:**
> No, I don't use compiz at all - even removed it. 

If it created keybinds why don't they work?

Are the keybinds stored in your home folder?

[COLOR=DarkRed] EDIT
I played with gconf-editor, Its similar to regedit in windows, Go here /apps/metacity/global_keybindings/
You should see things that resemble the structure of the commands you posted in post 1.  I would play around with the <> around the word delete. control and alt need the <> around them, not sure about delete. ctrl+alt+delete brings up the shutdown menu for me and i cant figure out how to override it to test it out or you.

I did however set the keybinding to <Control><Alt>1 and it worked like you want it too. post back your results
END EDIT[/COLOR] 


OK.. That helps some. Ill try and figure it out for you real fast.

keybinds are stored in the gconf folder which is hidden in your /home. I am not sure if they are in a real readable format or not, however try this program to set them, It does the same things the commands do, but graphically.


[B]gconf-editor

[/B]

---

### Post by episodic on 2007-10-20
Hi, 

Thanks.

I had found the folder in my home directory after learning to use the 'locate' command.

I had found the xml files I created with the commands by date stamps (cross referencing them with my bash history). 

I deleted them. I used your trick about the editor and went and mapped them to control alt 1 - it worked. Funny how you can't map to control alt delete anymore. It worked fine in feisty.

Thanks (amazing how much you can learn with a tiny problem)

---

### Post by Dr. Nick on 2007-10-21
yeah, i guess they locked control alt delete at a lower level and reserved it. Glad ctrl+alt+1 worked good

---

### Post by tombott on 2007-10-24
Anybody got any ideas on how to remove this Ctrl-Alt-Del binding?

I connect to a lot of Windows servers & workstations via VNC and need to be able to send a Ctrl-Alt-Del to unlock / login users.

Cheers

Tom

---

### Post by tombott on 2007-10-24
Ok found it.
Use Configuration Editor and browse to 

/apps/gnome_settings_daemon/keybindings/power

You can change the binging there.

---

