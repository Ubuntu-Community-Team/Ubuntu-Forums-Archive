---
title: "Very weird problem with upstart"
date: 2014-07-12
forum: General Help
---

### Post by brickbat on 2014-07-12
Hi,

Here is my conf file.

```
description     "ncurses BitTorrent client based on LibTorrent"

console none
expect fork
kill timeout 5

start on (local-filesystems and net-device-up and runlevel [2345])
stop on runlevel [016]

script
   exec su dave -c "/usr/bin/screen -d -m -S rtorrent /usr/bin/rtorrent"
end script


pre-stop script
    exec su dave -c "killall -w -s 2 rtorrent"
end script
```

When the system boots, it doesnt work.  When I rename the file and run it manually, it starts ONCE.  Then it stops ONCE manually.  Then it hangs even after a reboot.  Also, it causes my shutdown to hang.  If I rename the file again, it will work again - Once. lol  I have no idea whats going on.

---

### Post by ian-weisser on 2014-07-12
Why do you need a pre-stop script that ends the process?

Doesn't a normal stop end the process?

---

### Post by brickbat on 2014-07-12
If you just let it stop it normally, when you restart it, it will recheck any downloads that were still going when it was shut down. When you shut it down this way, when it restarts, it continues smoothly.  Thats what the rtorrent website says and I can confirm it from personal experience.

---

### Post by brickbat on 2014-07-14
Are there any log files I can look at or post to help figure this thing out?

---

### Post by ian-weisser on 2014-07-14
You can check /var/log/syslog.

But for really troubleshooting upstart, I recommend the upstart-monitor application (provided by the upstart-monitor) package.
Then you can see both the Upstart messages and the corresponding Dbus messages, including errors.

I'm surprised that calling /usr/bin/screen works, since at that point in the startup a screen for the 'screen' application to attach to shouldn't have been assigned yet. Interesting.

I think you're trying to use rtorrent for a role it doesn't seem designed for. rtorrent in Ubuntu is not designed to run headless (which is why you need screen). You can kludge it into that role, but why bother?

Several very good, fast, easy-to-use torrent packages (like Deluge and Transmission) *are* designed to run headless, be controlled by Upstart, use the same libtorrent, and are easily customized by optional command-line, web, and application-based interfaces.

---

### Post by brickbat on 2014-07-14
I've tried them all.  rutorrent with rtorrent is simply the best for me by a mile.  It doesnt have to run headless.  I don't mind at all if it opens and runs in a terminal window.  I just want it to run at boot so I don't have to  start it manually every time.  I installed the monitor you suggested.  It doesn't show anything when I try to start the script manually and it just hangs.  I just tried running it like this in startup applications. 

```
gnome-terminal -e "rtorrent"
```

And now whats happening?  None of my startup applications are being saved. Another bug. Hmmmffff :(

---

### Post by brickbat on 2014-07-14
OMG This is so frustrating! So when I found out that Startup applications isn't saving any of my applications, I went into .config and edited autostart and inserted the line 

```
gnome-terminal -e "rtorrent"
```

What happened when I rebooted? Nothing. What the hell?  This really should not be this difficult.

---

### Post by ian-weisser on 2014-07-14
> **brickbat said:**
> I installed the monitor you suggested.  It doesn't show anything when I try to start the script manually and it just hangs.  I just tried running it like this in startup applications. 

```
gnome-terminal -e "rtorrent"
```

It's not surprising that upstart-monitor shows nothing - that method of starting rtorrent has nothing to do with Upstart.
If you used **service start rtorrent **instead, and if your Upstart .conf file is called rtorrent.conf, then upstart-monitor would show Upstart processing the request.

You seem to be mixing manual and upstart-controlled starting and stopping of the same service. That's not good.
And that service shouldn't actually be a system-level (boot) service because it requires a display. That's also not good.
So yeah, you will certainly experience plenty of unexpected behavior.

---

### Post by brickbat on 2014-07-16
When I say starting it manually, I mean starting the service manually with service start run-rtorrent and service stop run-rtorrent as opposed to it starting at boot.  I understand what you say about not being able to run it without a display so doesnt that just mean I need to have a later event level set as a prerequisite?  Also, that doesnt explain why it doesnt run when I place it in autorun.  I thought user scripts placed in autorun are run after boot is complete including initialising the display.

---

### Post by brickbat on 2014-07-16
Ok, so I think I may now understand why it isn't working with upstart.  The thing I can't figure out is what is the upstart event equivalent of runlevel 5.  ie. after display manager has loaded.  Does anyone know?

---

### Post by brickbat on 2014-07-16
ok. I've solved it.  Here are the steps I took.

1. delete ~/.config/autostarts folder
2. create new ~/.config/autostarts folder
3. copy any .desktop script from /etc/xdg/autostart
4. modify file to look like this

```
[Desktop Entry]
Type=Application
Name=rtorrent
Comment=Start rtorrent desktop at log in
Exec=gnome-terminal -e "rtorrent"
X-GNOME-Autostart-Delay=2
NoDisplay=false
Name[en_AU]=rtorrent-autostart.desktop
```

5, reboot.
6. drink beer with feet up on table.

Thanks to everyone that commented for helping me (eventually) get to a working solution.

---

