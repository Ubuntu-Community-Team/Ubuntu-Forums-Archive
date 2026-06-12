---
title: "Chrome Won't Start"
date: 2014-05-22
forum: General Help
---

### Post by Ayal_Kellman on 2014-05-22
Hi,

I'm new to Ubuntu but I've found these forums extremely helpful so far. 
I downloaded the "google-chrome-stable_current_amd64.deb" file from the Chrome website and installed it using the Software Center. However, I cannot open the program from the Unity Launcher. 
When I try to open via the terminal using the command "google-chrome-stable" I get the following and I cannot close the terminal without also closing Chrome:

ayalkellman@ubuntu:~$ google-chrome-stable
[9557:9557:0522/060915:ERROR:component_loader.cc(138)] Failed to parse extension manifest.
ATTENTION: default value of option force_s3tc_enable overridden by environment.
[9557:9557:0522/060917:ERROR:desktop_window_tree_host_x11.cc(1289)] Not implemented reached in void views::DesktopWindowTreeHostX11::MapWindow(ui::WindowShowState)

Thanks in advance!

---

### Post by sudodus on 2014-05-22
It is common to get warnings to the terminal when you start a GUI program from it.

If you want to start a GUI program, you can start it with nohup. Then it should survive even if you close the calling terminal window. Test with this example before you try with ***google-chrome-stable***

```
nohup xterm &
```

---

### Post by Ayal_Kellman on 2014-05-22
OK. So this is what happened

[1] 10250
ayalkellman@ubuntu:~$ nohup: ignoring input and appending output to &#8216;nohup.out&#8217;

and it opened the XTerm. What would be the exact command to open Chrome with nohup?
Also, why won't it open from the launcher? Other programs I installed (Skype, VLC) seem to work fine...

Thanks!

---

### Post by sudodus on 2014-05-22
```
nuhup google-chrome-stable &
```

I don't know why that version of Chrome does not create an entry in your menu in your particular version of Ubuntu.

- Which version of Ubuntu are you running?

---

### Post by Ayal_Kellman on 2014-05-22
14.04 downloaded from Wubi running (replacing) alongside XP

---

### Post by sudodus on 2014-05-22
It seems there is a version of Chrome that is ready for Ubuntu 14.04 LTS. Let us hope this link works for you. Otherwise you can browse the internet for [I][B]chrome for ubuntu 14.04
[/B][/I]
[URL="http://ubuntuportal.com/2014/04/how-to-install-google-chrome-web-browser-in-ubuntu-14-04-lts-trusty-tahr.html"]http://ubuntuportal.com/2014/04/how-to-install-google-chrome-web-browser-in-ubuntu-14-04-lts-trusty-tahr.html
[/URL]

---

