---
title: "Start Kmail minimized"
date: 2007-11-19
forum: General Help
---

### Post by flip79 on 2007-11-19
Hello, I'd like to have Kmail start minimized. I added it to Autostart apps, but it starts in a normal window... I can't find the option :/

---

### Post by Thyme on 2007-11-19
Hi flip79,

I found the following from the sabayon forum:

```

ksystraycmd --hidden --title 'kmail' kmail

```

I've never ever tried this nor seen it before, It worked for the dude at that forum so I though I'd just give you an option :)

---

### Post by flip79 on 2007-11-19
Thank you very much, Thyme! Unfortunately it doesn't work... Kmail starts normally after a bunch of strange errors in the terminal:

```
ricky@ricky:~$ ksystraycmd --hidden --title 'kmail' kmail
WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "move_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "copy_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "jump_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "jump_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "cancel"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "inc_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "dec_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "select_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "inc_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "dec_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "select_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "delete"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "edit"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "use_template"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x8172d30 ): KAccel object already contains an action name "display_message"
```

---

### Post by flip79 on 2007-11-22
Bumping :/

---

### Post by JabberWokky on 2007-12-02
Easy.  Use:

kmail ; dcop kmail kmail-mainwindow#1 close

Alas, there's no easy commandline option to do this, so the window will flash up before closing (it has to load before the dcop command is run and it closes the main window so it just runs in the tray).

The "errors" you see in a console aren't errors, just the normal information about what it is doing.  If you run most KDE apps from a console, they will display similar information.  You'll probably want to just add the above command as a menu command.

(And I just registered to tell you this).

---

### Post by Tari Narmolanya on 2008-01-23
Did you try "alltray" ? works perfectly for me.

---

