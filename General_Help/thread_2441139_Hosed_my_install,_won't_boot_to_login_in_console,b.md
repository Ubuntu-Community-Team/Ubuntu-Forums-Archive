---
title: "Hosed my install, won't boot to login in console,but I can SSH in (boot.log provided)"
date: 2020-04-19
forum: General Help
---

### Post by alexdodd on 2020-04-19
Hey everyone, i've been a silly boy.

Background: I installed Ubuntu 20.04 beta, with the intent on just playing around a bit on an old laptop, but I got "carried away" with a project.

Here's the timeline:
[LIST=1]
[*] I installed the server components using **tasksel**
[*]Installed docker and docker-compose and have hass.io and some other containers all working great
[*]At this point I thought I should lose the GUI on boot, so run systemctl set-default multi-user.target.  Boots to console. So far so good.
[*]Turns out Ubuntu doesn't have anything to blank the console or powersave anymore, probably since the move to systemd?
[*]This is where things probably take a turn for the worse [this askubuntu]("https://askubuntu.com/questions/1228271/how-do-i-enable-a-timed-laptop-screen-power-off-from-the-console") is what I did, which is create a service using **setterm --blank 30 --powerdown 2**, that actually seemed to work because once i enabled it, started it and checked status it seemed good *and* the screen was powering off in the console like i hoped.
[*]The next restart thing get worse, essentially it hangs at the boot splash, or if i press f1 on boot, at a blank screen. Like the login for console can't be involked due to something holding everything up.  No keyboard inputs work.
[/LIST]

Good news howeve: the laptop actually boots fine, all other services, includingimportant ones and less so like docker and hass.io run, SSH runs, and I can SSH in like its 1999.  So it's not all lost yet! But I'd quite like some help in fixing my lack of login prompt on boot.

So far I've tried stopping and disabling the service I created in the hope that would undo the boot problem, but alas that would have been too simple.

I SSH'ed in and took the last boot log here: [https://paste.ee/p/oiDxG](https://paste.ee/p/oiDxG)

But i'm way out my depth, and in the spirit of 'keeping digging', i'd prefer to have a go at fixing this and hopefully learn something along the way.


Worst case is a nuke it and start a fresh, with the final release server edition instead and not fanny about in the future!

---

### Post by Tadaen_Sylvermane on 2020-04-20
[https://askubuntu.com/questions/788323/how-do-i-change-the-runlevel-on-systemd](https://askubuntu.com/questions/788323/how-do-i-change-the-runlevel-on-systemd)

[COLOR=#242729][FONT=Consolas]```
sudo systemctl set-default graphical.target
```

This would be my first place to start.

 *edit* could save trouble by just installing the server version from the start. then you wouldn't have to mess with this stuff. i'd also suggest getting virtual box and doing everything inside of that first. saves headaches on bare metal screw ups. snapshot is a wonderful thing.[/FONT][/COLOR]

---

### Post by alexdodd on 2020-04-20
The edit is a fair assesment.  I wasn't planning on experimenting, but one thing lead to another....

I'll backup my dockers i've made and just put a fresh install of the final server LTS release, and stop messing around when I don't know what I'm doing =/

---

### Post by Tadaen_Sylvermane on 2020-04-20
I still consider myself a freshman so to speak in Linux. But most everything I've managed to learn involved both Virtualbox, and forums like this. Saved many a headache.

---

