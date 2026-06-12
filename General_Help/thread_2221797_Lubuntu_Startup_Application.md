---
title: "Lubuntu Startup Application"
date: 2014-05-03
forum: General Help
---

### Post by Kevin_Verax on 2014-05-03
I am currently running Lubuntu and I am needing this:

```
xinput --set-prop "Cypress APA Trackpad (cyapa)" "Synaptics Finger" 10 10 240
```[B][COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR][/B][COLOR=#222222][FONT=Verdana]to run whenever the computer starts up. This is what allows my trackpad on the laptop to function properly. I downloaded "Default applications for LXSession" which did not work. How would I go about achieving this?[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-05-03
Well, run-this-at-boot is pretty much what Upstart does: [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/)

Do you want it to run at boot (before login), or do you want it to run upon login?
Big difference.

---

### Post by vasa1 on 2014-05-03
> **Kevin_Verax said:**
> ... I downloaded "Default applications for LXSession" which did not work. ...
What do you mean by "*I downloaded "Default applications for LXSession"*"? Why did you need to download it? Where did you download it from? IMO, it's part of a default Lubuntu installation and there's no need to download it.

[LIST]
[*]Normally, you just need to click on the Menu, then expand Preferences, and select "Default Applications for LXsession". Again, this is there by default; there's no need to "download" it at all! 
[*]You'll get a screen (after a small popup notice of updating or something). 
[*]Click on the Autostart tab on the left.
[*]Paste in your code in the box next to "Add".
[*]Click on "Add".
[*]Make sure "Disable Autostarted Appplications" is set to "No"
[*]Close the window.
[*]Look at ~/.config/lxsession/lubuntu/autostart. That should be a plain text file with just one line in it and that line should be the code you added through the "Default applications for LXSession" GUI.
[*]Log out. 
[*]Log in. The code should run by itself and your laptop's trackpad should function normally.
[/LIST]

---

### Post by Kevin_Verax on 2014-05-03
I apologize, it was already installed. But, I tried exactly what you said, and it does not work. Though, I may be doing something wrong. I am relatively new to Lubuntu and Linux operating systems in general.

Here is a screenshot of what I did:

[ATTACH=CONFIG]252817[/ATTACH]

---

### Post by vasa1 on 2014-05-04
I will ask people on the Lubuntu mailing list about your problem.
Please confirm that the code you use works perfectly when you enter it from a terminal.
Also, why do you have "Zeitgeist Datahub"? How did you get that? It isn't part of Lubuntu.

I've linked to your problem here: [https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007426.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007426.html) and on a Facebook page where several Lubuntu users hangout. Let's hope :)

---

### Post by vasa1 on 2014-05-04
There's been one response which looks very promising. You can read it here: [https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007427.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007427.html) and I'm quoting it below as well:
> From my previous experience with other command-line tools for various X11 configurations there is a chance they do not work when specified in ~/.config/lxsession/lubuntu/autostart. I guess they are run too early and their settings get overwritten by the system after that point.

So if the command you are interested in works if you run it manually after login, but it seems not to work when put in ~/.config/lxsession/lubuntu/autostart, then what works for me in such cases is to make a small bash script with a sleep someseconds and then the command. Then I call the script from ~/.config/lxsession/lubuntu/autostart, rather than the command directly. Like this I can experiment with the sleep timeout, until I find a value that works. In my computers that have SSD the sleep time is as small as 1 or up to 3 seconds to be really sure. In HDD computers, you may need to experiment with much longer sleep values sometimes, if in doubt use 60 seconds or higher.

I have a strong feeling this should solve your problem.

If you don't know how to make the script just ask!

Edit: actually, it's quite easy.

Make a new folder in your home folder (in case you haven't already) and call it **bin**.
Use Leafpad to open a new text file.
Paste in the following:
```
#!/usr/bin/env bash
(sleep 10s &&
xinput --set-prop "Cypress APA Trackpad (cyapa)" "Synaptics Finger" 10 10 240) &

```
Save that file as **touchpad** in the **bin** folder you created in earlier. You could call it anything else and add the **.sh** suffix but no suffix is really needed.
Open your file manager (PCManFM).
Open the **bin** folder. You should see the file called **touchpad** (or whatever).
Right-click on it.
Select **Properties**.
Then select **Permissions**. And, in **Access Control**, click in the space to the right of **Execute**. 
Click on **Only Owner**.
Click on **Okay**.

Now, go back to the Autostart screen (Default Applications for LXSession).
Delete the entry you made earlier.
Just paste in the full path of the script you created earlier so that Lubuntu will autostart that script. So, you'll be pasting in something like */home/vasa1/bin/touchpad* (with your own username instead of *vasa1*).

Now, log out and log back in. If all is well, you should be good to go.
I've used 10s but you can reduce it once you know things are working.
All the best!

(*You could use the terminal to create the script and make it executable but you said you're new to Linux so I didn't go that route.*)

---

### Post by Kevin_Verax on 2014-05-04
> **vasa1 said:**
> There's been one response which looks very promising. You can read it here: [https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007427.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-May/007427.html) and I'm quoting it below as well:


I have a strong feeling this should solve your problem.

If you don't know how to make the script just ask!

Edit: actually, it's quite easy.

Make a new folder in your home folder (in case you haven't already) and call it **bin**.
Use Leafpad to open a new text file.
Paste in the following:
```
#!/usr/bin/env bash
(sleep 10s &&
xinput --set-prop "Cypress APA Trackpad (cyapa)" "Synaptics Finger" 10 10 240) &

```
Save that file as **touchpad** in the **bin** folder you created in earlier. You could call it anything else and add the **.sh** suffix but no suffix is really needed.
Open your file manager (PCManFM).
Open the **bin** folder. You should see the file called **touchpad** (or whatever).
Right-click on it.
Select **Properties**.
Then select **Permissions**. And, in **Access Control**, click in the space to the right of **Execute**. 
Click on **Only Owner**.
Click on **Okay**.

Now, go back to the Autostart screen (Default Applications for LXSession).
Delete the entry you made earlier.
Just paste in the full path of the script you created earlier so that Lubuntu will autostart that script. So, you'll be pasting in something like */home/vasa1/bin/touchpad* (with your own username instead of *vasa1*).

Now, log out and log back in. If all is well, you should be good to go.
I've used 10s but you can reduce it once you know things are working.
All the best!

(*You could use the terminal to create the script and make it executable but you said you're new to Linux so I didn't go that route.*)


I followed all of these steps, but it still did not work. If I execute the touchpad.sh it fixes the touchpad, but it never executes via the autostart.

---

### Post by vasa1 on 2014-05-04
> **Kevin_Verax said:**
> I followed all of these steps, but it still did not work. If I execute the touchpad.sh it fixes the touchpad, but it never executes via the autostart.
Sorry to hear that. I'm out of ideas.

---

### Post by Elastic_Potential on 2014-05-04
I would try to make it executable in the terminal before digging any further: "chmod +x /path/to/touchpad_script"

The terminal might be intimidating at first, but as you get used to it, you'll find it incredibly useful.

EDIT: also, would you be able to send another screenshot of your current Startup Applications window?

---

### Post by sysmatck on 2014-05-04
This is how I create manual update shortcut:

1- Create a text file (e.g. with leafpad) named: manual-update.desktop
2- Insert the following content:

[COLOR=#000080]*[Desktop Entry]*[/COLOR]
[COLOR=#000080]*Encoding=UTF-8*[/COLOR]
[COLOR=#000080]*Type=Application*[/COLOR]
[COLOR=#000080]*Name=Manual Update*[/COLOR]
[COLOR=#000080]*Icon=ibus-engine*[/COLOR]
[COLOR=#000080]*Exec=xterm -e 'sudo apt-get upgrade'*[/COLOR]
[COLOR=#000080]*Terminal=false*[/COLOR]

3- Save the file and double click on it to test if works...

You can do the same to run your command, you only need to replace ***[COLOR=#000000]Exec=xterm -e '[/COLOR][COLOR=#000080]sudo apt-get upgrade[/COLOR][COLOR=#000000]'[/COLOR]*** with your command. It might be something like this:[I] [B]Exec=xterm -e '[COLOR=#000080][FONT=Ubuntu Mono]xinput --set-prop "Cypress APA Trackpad (cyapa)" "Synaptics Finger" 10 10 240[/FONT][/COLOR]'

[/B][/I]Final step - Once you've done, place the shortcut (.desktop file) on [COLOR=#ff0000]~/.config/autostart/[/COLOR] or [COLOR=#ff0000]/home/USER_NAME/[/COLOR][COLOR=#FF0000].config/autostart/

[/COLOR]Log off and log in again to test if works...

---

### Post by Kevin_Verax on 2014-05-04
> **sysmatck said:**
> This is how I create manual update shortcut:

1- Create a text file (e.g. with leafpad) named: manual-update.desktop
2- Insert the following content:

[COLOR=#000080]*[Desktop Entry]*[/COLOR]
[COLOR=#000080]*Encoding=UTF-8*[/COLOR]
[COLOR=#000080]*Type=Application*[/COLOR]
[COLOR=#000080]*Name=Manual Update*[/COLOR]
[COLOR=#000080]*Icon=ibus-engine*[/COLOR]
[COLOR=#000080]*Exec=xterm -e 'sudo apt-get upgrade'*[/COLOR]
[COLOR=#000080]*Terminal=false*[/COLOR]

3- Save the file and double click on it to test if works...

You can do the same to run your command, you only need to replace ***[COLOR=#000000]Exec=xterm -e '[/COLOR][COLOR=#000080]sudo apt-get upgrade[/COLOR][COLOR=#000000]'[/COLOR]*** with your command. It might be something like this:[I] [B]Exec=xterm -e '[COLOR=#000080][FONT=Ubuntu Mono]xinput --set-prop "Cypress APA Trackpad (cyapa)" "Synaptics Finger" 10 10 240[/FONT][/COLOR]'

[/B][/I]Final step - Once you've done, place the shortcut (.desktop file) on [COLOR=#ff0000]~/.config/autostart/[/COLOR] or [COLOR=#ff0000]/home/USER_NAME/[/COLOR][COLOR=#FF0000].config/autostart/

[/COLOR]Log off and log in again to test if works...

Still didn't work.

---

### Post by vasa1 on 2014-05-04
> **Kevin_Verax said:**
> Still didn't work.
Could I humbly suggest you get a bit more verbose :)
You haven't yet explained what Zeitgeist Datahub is doing on your machine.
Is your Lubuntu a standard install or have you modified it somehow?
Really, if you need help, you need to provide more information even if people don't ask for it. See if this helps: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by Kevin_Verax on 2014-05-05
> **vasa1 said:**
> Could I humbly suggest you get a bit more verbose :)
You haven't yet explained what Zeitgeist Datahub is doing on your machine.
Is your Lubuntu a standard install or have you modified it somehow?
Really, if you need help, you need to provide more information even if people don't ask for it. See if this helps: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)


Sorry, this is the first time I have had a chance to sit down and properly reply. As far as I know, this is a standard install of Lubuntu. I have installed some other applications on the computer, if that could effect anything. I am not exactly sure what Zeitgeist Datahub is, but I know I have not installed that, at least not that I know of.

I have made a completely transparent desktop shortcut to the command and placed it right where the mouse is placed on startup. This allows me to just double click to get the mouse working on startup, but I still would like to get this working properly. I am just not sure what the problem with the autostart is. :\

---

