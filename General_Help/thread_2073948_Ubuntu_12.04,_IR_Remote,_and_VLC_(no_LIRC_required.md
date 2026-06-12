---
title: "Ubuntu 12.04, IR Remote, and VLC (no LIRC required)"
date: 2012-10-20
forum: General Help
---

### Post by nathandetroit on 2012-10-20
This article explains how I got my MCE type IR receiver and remote control to work with VLC on Ubuntu 12.04.  This same method should be adaptable to any other type of IR receiver and remote. I should also note that that this method no longer requires LIRC.

This method is based on information from the link below, which has the best up to date information (with respect to Ubuntu 12.04) I was able to find on IR receivers and remotes, ir-tables and LIRC. I recommend that anyone working with IR controls and Ubuntu 12.04 or later read this article to learn about significant new deveopments in this regard:

	[http://forum.xbmc.org/showthread.php?tid=104541]("http://forum.xbmc.org/showthread.php?tid=104541")

**Background:** I have a computer (running Ubuntu 12.04) connected to a TV in my living room. I use VLC on this computer to view videos from a server on my home network. An MCE type remote receiver (TSES-IR01) is USB connected to the computer; instead of using the remote that came with this, I use a "universal remote" to control both the TV and VLC on the computer. To select videos on the computer, I simply use a keyboard on the computer. The main use of the remote is to pause, skip ahead, skip back, and stop VLC, and to control volume.

This solution is certainly not the last word on using IR remotes with Ubuntu 12.04 and VLC, but I hope it will help people with similar requirements, and also serve as a good reference for people looking to do more.

If you already installed lirc, and you are not using it for anything else, you can remove it:

	```
sudo apt-get --purge remove lirc
```

Install ir-keytable:

	```
sudo apt-get install ir-keytable
```

Copy the required config file to rc_keymaps; for an MCE type remote:

    ```
sudo cp /lib/udev/rc_keymaps/rc6_mce /etc/rc_keymaps
```

Edit the config file. With ir-tables, your remote is acting like a keyboard, so you want the remote to emulate the keyboard keys that VLC is expecting:

	```
gksudo gedit /etc/rc-keymaps/rc6_mce
```

change the text on the left to the text on the right: 

	KEY_PLAY  --> KEY_SPACE
	KEY_PAUSE --> KEY_SPACE
	KEY_STOP  --> KEY_S
	KEY_REWIND --> KEY_LEFT
	KEY_FASTFORWARD --> KEY_RIGHT

You will also need to set KEY_RIGHT and KEY_LEFT in VLC hotkeys settings by editing the VLC global hotkey preferences.

Load the edited config file:

	```
sudo ir-keytable -c -p RC-6 -w /etc/rc-keymaps/rc6_mce
```

Test to make sure all is working. If everything is OK, add the following line to /etc/rc.local so that the keymap will load on boot:

	```
ir-keytable -c -p RC6,LIRC -w /etc/rc_keymaps/rc6_mce
```


Additional thoughts:

I was not able to edit the keymap to successfully send the [ or ] keys. Noe of the following worked: KEY_[, KEY_BRACKETRIGHT, KEY_RIGHTBRACKET, KEY_RIGHT_BRACKET. I was not able to find information giving the corresponding key name with a key (for example, KEY_SPACE for the SPACE key).

	Later, I found this: 

	[http://xbmc.exstatic.org/ir_keys.txt]("http://xbmc.exstatic.org/ir_keys.txt") 

	which is referenced here: 

	[http://ubuntuforums.org/showthread.php?t=1754719]("http://ubuntuforums.org/showthread.php?t=1754719")

The referenced article on ir-tables explains how more sophisticated control can be achieved using a combination of ir-tables and LIRC. However, this was not necesary for my modest requirements.

---

