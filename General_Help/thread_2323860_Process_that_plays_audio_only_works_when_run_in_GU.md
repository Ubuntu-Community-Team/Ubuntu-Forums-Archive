---
title: "Process that plays audio only works when run in GUI terminal"
date: 2016-05-09
forum: General Help
---

### Post by davetempleton on 2016-05-09
I'm running 16.04 on an Intel NUC NUC5CPYH that's outputting audio through HDMI.

I'm setting up an AirPlay server using [these]("https://www.raywenderlich.com/44918/raspberry-pi-airplay-tutorial") instructions as a general guide. I realize most of that is about RPi; mostly I'm just cloning these two repos ([1]("https://github.com/njh/perl-net-sdp"), [2]("https://github.com/hendrikw82/shairport")) and running an executable. You don't need to dive into the weeds of these projects; what matters is that everything works well when I'm running the .pl executable from within the Terminal application in the Ubuntu GUI, but it doesn't work if I run the executable via an SSH session from another computer (logged in as the GUI user), or as a daemon of either the logged-in user or root.

I'll repeat that in case I'm not making any sense. If I run the ./program.pl file in my terminal in the GUI, it works ouputting audio. If I try running the process any other way, including as an init.d daemon as either root or the logged-in user, it acts like it works but the audio isn't actually output. If I try running it in a remote ssh session of the logged-in user, it acts like it's working but doesn't actually output audio.

When I say "act's like it's working", I mean the process is running happily and reports successful connections and looks like it should be playing sound.

It seems like the internal "mixer" of the OS is not connecting this process to the HDMI audio output unless I'm running it right on the machine in the GUI.

How might I get this to work as an init.d daemon run as the logged-in user (not root)? Thank you.

---

