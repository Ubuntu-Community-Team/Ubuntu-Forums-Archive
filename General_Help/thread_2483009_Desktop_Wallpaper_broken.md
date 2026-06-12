---
title: "Desktop Wallpaper broken"
date: 2023-01-17
forum: General Help
---

### Post by josefranw on 2023-01-17
Hello. I'm having a little issue with the desktop wallpaper: it's not changing. No matter how many times I select one from the settings, it won't load or show in the desktop. I notice it does show in the login screen but not once the session is loaded.

I used to have Variety installed it was working fine, changing the wallpaper every so often and loading the quotes and showing the date and time but now it's only the default wallpaper and it's impossible to change. How can I fix this, please?

Thanks.

---

### Post by Impavidus on 2023-01-17
You tagged this thread as Xubuntu, so I assume you run some release of Xubuntu.

The utility you use to select the wallpaper must match the utility that draws the wallpaper. On Xubuntu, the former is normally xfce4-settings-manager and the latter is xfce4-session. If your system isn't pure Xubuntu, you may have a mismatch. You can start those tools from command line to make sure you run the right tool.

Just checking my wallpaper switching script on Xubuntu 22.04.
First the script extracts the DBUS_SESSION_BUS_ADDRESS environment variable from the xfce4-session using the /proc pseudofilesystem. This isn't needed if you run things from the command line, but only when running it from cron, as that comes without the environment.
Then it runs```
xfconf-query -c xfce4-desktop -p /backdrop/screen0/monitorLVDS-1/workspace0/last-image -s /path/to/file
```to set the file as background. I've noticed that the part after the -p varies from one version of Xubuntu to another. xfce4-settings-manager is simply a front-end to the xfconf-query tool. You can also access the settings through xfce4-settings-editor, where you may be able to find the bit after the -p in the above command.

---

### Post by josefranw on 2023-01-26
Hello. Can anybody give me a hand? The wallpaper seems to be broken. It won't fit the screen properly and it won't change if I select a different wallpaper. But this all occurs only when I log in. In the log-in screen, the wallpaper is ok, it's the one I had selected but when the session starts, the wallpaper that is shown is Xubuntu default's but it won't match the screen neither can it be changed.

How can I fix this issue?

I used to used Variety to automatically and periodically load different wallpapers and I was working OK until one day when it stopped working (in the session) I repeat, in the log-in screen everything seems normal.

[https://ubuntuforums.org/attachment.php?attachmentid=291635&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=291635&stc=1)

[https://ubuntuforums.org/attachment.php?attachmentid=291636&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=291636&stc=1)
[https://ibb.co/YW51Z4J](https://ibb.co/YW51Z4J)

---

### Post by Impavidus on 2023-01-27
You already told so in post #1. Have you read post #2? The second paragraph shouldn't be too hard to understand. The last part of that post gives some internals of wallpaper switching, which you may be able to use to troubleshoot this.

---

### Post by josefranw on 2023-01-27
I did read post #2, I thank you for answering but I don't understand much about technical terms like "[COLOR=#000000]extracts the DBUS_SESSION_BUS_ADDRESS environment variable from the xfce4-session using the /proc pseudofilesystem" and such.

The problem persists...

The setting-manager also shows the correct wallpaper but it won't "load" or "show" on the desktop.[/COLOR]

---

### Post by Impavidus on 2023-01-29
That looks like the xfce4-settings-manager. Do you actually run an xfce4 session?```
ps -x | grep xfce4-session
```
Can you look around in xfce4-settings-editor, use the xfce4-desktop channel, and find the selected wallpaper and the actual wallpaper? That may give a lead about what's going wrong.

I've never used variety. I prefer to write my own wallpaper switcher. Then I know exactly what's happening.

You haven't mentioned the release of Xubuntu you use.

---

### Post by josefranw on 2023-01-29
```
ps -x | grep xfce4-session
 109678 ?        Ssl    0:13 xfce4-session
 173916 pts/0    S+     0:00 grep --color=auto xfce4-session

```

> [COLOR=#000000]Do you actually run an xfce4 session?[/COLOR][COLOR=#000000][/COLOR]


Yes, I do.

> [COLOR=#000000]You haven't mentioned the release of Xubuntu you use.[/COLOR]


[COLOR=#000000]
[/COLOR]```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.10
Release:	22.10
Codename:	kinetic

```

> [COLOR=#000000]I've never used variety. I prefer to write my own wallpaper switcher. Then I know exactly what's happening.[/COLOR]




I don't know how to do that.

PS: I just noticed when I login with another user, the desktop wallpaper works just fine. So, it just seems to be broken in my session. If it works in others, then I don't think there's something wrong with anything, but there must be something wrong with my session, like a misconfiguration or something. Isn't there a way to "reset" the wallpaper configuration or something like that? 

Thanks in advance.

---

### Post by #&amp;thj^% on 2023-01-29
change solid color to Horizontal gradient in Desktop Settings
EDIT: I do the same as Impavidus, but I'll set mine in "/usr/share/backgrounds"  
Also I saw variety so if no longer using it and gain your control back use:
```
 sudo apt-get purge --auto-remove variety
```
That ought to reset your configuration.

---

### Post by ajgreeny on 2023-01-29
> **1fallen said:**
> change solid color to Horizontal gradient in Desktop Settings
Why or how does a gradient make any difference to any chosen images which is what the question is about?
..

---

### Post by #&amp;thj^% on 2023-01-29
> **ajgreeny said:**
> Why or how does a gradient make any difference to any chosen images which is what the question is about?
..
Relax already, LOL it was a bug on another distro, I edited my post to reflect the change. :P

---

### Post by josefranw on 2023-01-29
> [COLOR=#000000]I saw variety so if no longer using it and gain your control back use:[/COLOR]
[COLOR=#000000]Code:
 sudo apt-get purge --auto-remove variety

[/COLOR]
[COLOR=#000000][/COLOR]

I just did, rebooted and nothing changed (apart from the app being removed). The desktop continues to be broken.

When I enter the configuration settings, this is what I get (see attachment) but no change I make will reflect in the desktop... during the session. If I log out, I would see any wallpaper or solid color or gradient I had selected... in the log-in screen.

---

### Post by ajgreeny on 2023-01-30
Have you tried all the different available styles, ie, where you have set zoomed?
Mine is set to **stretched** i think and always seems to fit whatever display I'm using.

I'm not on my Xubuntu machine at the moment. I'll check again later and report back

---

### Post by josefranw on 2023-01-30
No change I make in the configuration settings will reflect in the desktop.

---

### Post by ajgreeny on 2023-01-30
A last thought from me; is this a laptop or a desktop, and if a desktop machine, how is the monitor connected, VGA, DVI or HDMI?

Going back many years I remember having a similar problem to you when my monitor was using a VGA connection with the desktop display being offset to one side a bit like you show us.

---

### Post by #&amp;thj^% on 2023-01-30
> **josefranw said:**
> I just did, rebooted and nothing changed (apart from the app being removed). The desktop continues to be broken.


Look here:
```
ls .config | grep variety
variety

```
if there use:
```
rm -rf '/home/<youruser>/.config/variety'
```
EDIT: I did have problems on my end with variety, but after a clean up and a re-login back to normal.

---

### Post by josefranw on 2023-01-31
Hello, @[COLOR=#000000]ajgreeny. It's a laptop but I'm using an external monitor connected via VGA. But I don't think this is the problem because the screen wallpaper is OK in the login screen and when I login with a different username. I mean, I have two users configured.... only mine has the wallpaper broken.

I did what you recommended, @1fallen, but it's still broken.


[/COLOR]

---

### Post by ajgreeny on 2023-01-31
You say it's not VGA related but my old monitor, when connected by VGA had a setting to shift the whole display on the screen up/down and left/right; if I didn't set that correctly I had the problem you're seeing.

---

### Post by #&amp;thj^% on 2023-01-31
> **josefranw said:**
> Hello, @[COLOR=#000000]ajgreeny. It's a laptop but I'm using an external monitor connected via VGA. But I don't think this is the problem because the screen wallpaper is OK in the login screen and when I login with a different username. I mean, I have two users configured.... only mine has the wallpaper broken.

I did what you recommended, @1fallen, but it's still broken.


[/COLOR]

Can you copy your .config from the working user to replace in the broken DE.
Back them up first, or just copy both to a different drive, USB, HDD, SSD, or even a CD/DVD drive.
Trying to drill down on the culprit here.

---

### Post by josefranw on 2023-02-01
> [COLOR=#000000]Can you copy your .config from the working user to replace in the broken DE.[/COLOR]

Where do I find that .config file?

---

### Post by #&amp;thj^% on 2023-02-01
In your file browser /home/<yourusername>/.config
Easier to open your file-manger in your home user directory and use key combo <Ctrl + h> it's ".file" so it's hidden until uncovered.

---

### Post by josefranw on 2023-02-01
I fear that would make more harm than good. I noticed it includes many folders with the apps and programs I use, so I assume it has all their configurations so if I copy that file into another user, wouldn't that change (or even brake) the apps because their configurations won't match?

---

### Post by MAFoElffen on 2023-02-02
I'm spinning up an Xubuntu 22.04 LTS instance now...

I know that deleting $HOME/.config is overkill. Besides, that is not a file. It's a folder that holds ***all user settings***. (Or at least a big collection of them.) In Ubuntu, $HOME/.config/dconf/user 'is' the file that is the dconf "user settings" file that stores the gnome background setting at org.gnome.desktop.backround picture-uri... 

At least in Ubuntu... If you delete that file, on first login after that, a new, fresh file is created in it's place, with default settings. I'm not sure if that is necessary "yet.' I need to do some testing on that. Maybe just resettting that one setting within whatever is equivalent in Xubuntu. Not sure yet.

I'm hoping to find out what is equivalent in Xubuntu. Will reply soon...

---

### Post by MAFoElffen on 2023-02-02
Xubuntu XFCE stores its background image setting for User in file $HOME/. config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop. To reset's desktop type settings to default:
```

cp /etc/skel/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop

```
Or change the path of $HOME to the user's Home Folder...

Post #2 are the xfce4 tools that edit that XML file.

---

### Post by josefranw on 2023-02-02
```
cp /etc/skel/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktopcp: cannot stat '/etc/skel/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop': No such file or directory

```

> [COLOR=#000000]Xubuntu XFCE stores its background image setting for User in file $HOME/. config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop. To reset's desktop type settings to default:[/COLOR]

I deleted that file hoping it would reset to default, after rebooting. In a way, it did but even though I have all the options back in the configuration settings, it continues to be broken... (See attachment)

---

### Post by MAFoElffen on 2023-02-03
I wonder if there is somethng in the cache that has it locked up? What happenes if you try
```

rm -R ~/.cache/sessions/* 
xfdesktop --reload
sudo reboot

```

---

### Post by josefranw on 2023-02-03
> [COLOR=#000000]I wonder if there is somethng in the cache that has it locked up? What happenes if you try[/COLOR]
[COLOR=#000000]Code:
rm -R ~/.cache/sessions/* 
xfdesktop --reload [/COLOR]
[COLOR=#000000][FONT=&amp]sudo reboot[/FONT][/COLOR]

We,, I just did and guess what? It worked!

I always knew there was a command line to reset everything back to normal, but I just didn't know which one it was...

Thanks god, there's always someone ready to help.

Thank you!

PS: I did not have to reboot the system.

---

### Post by MAFoElffen on 2023-02-03
You are welcome. Happy I could help.

Please mark this thread as "Solved" so that others can find your solution.

---

### Post by #&amp;thj^% on 2023-02-03
> **MAFoElffen said:**
> You are welcome. Happy I could help.

Please mark this thread as "Solved" so that others can find your solution.

Good Job ;)

---

