---
title: "How to install cisco packet tracer"
date: 2018-02-10
forum: General Help
---

### Post by bryan309 on 2018-02-10
I found this conversation addressing the issue. I tried to follow it but with no luck.
[URL="https://askubuntu.com/questions/864226/installing-cisco-packet-tracer-7-on-ubuntu-16-10"]https://askubuntu.com/questions/864226/installing-cisco-packet-tracer-7-on-ubuntu-16-10

[/URL]

anyone can tell me how to install this?

The prompt went through the process described in the article, but when I try to start packettracer nothing happens. It says starting packet tracer and then nothing happens.

I'm new to linux and I don't like it very much so far. This is way too much trouble to get a simple program to work.

---

### Post by #&amp;thj^% on 2018-02-10
You do not mention which version you are trying to install.
We will need that to help. But I just installed "Cisco Packet Tracer 7.1 installed successfully"

---

### Post by #&amp;thj^% on 2018-02-11
Still waiting for this: You do not mention **which version you are trying to install.**

---

### Post by bryan309 on 2018-02-11
> **1fallen said:**
> Still waiting for this: You do not mention **which version you are trying to install.**

Hi Thanks for replying. 

I actually solved it. It's packet tracer 7. I find some vague instuctions [here]("https://askubuntu.com/questions/864226/installing-cisco-packet-tracer-7-on-ubuntu-16-10") I eventually managed to solve, but then packet tracer would not start.


I found this[ link]("https://askubuntu.com/questions/963457/cisco-packet-tracer-7-1-wont-start") that had this answer as to why packet tracer would not start after installation:

>  I was able to run Cisco Packet Tracer 7.1 on Ubuntu 16.04 by doing the following:

  1-Cisco Packet Tracer 7.1 requires an older version of a package not present on Ubuntu 16.04 so you need to get it by typing 

  wget [http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu52_52.1-3ubuntu0.7_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu52_52.1-3ubuntu0.7_amd64.deb)
  2- To install the package you just downloaded type

  sudo dpkg -i libicu52_52.1-3ubuntu0.7_amd64.deb
  3- Verify proper installation using this commands

  sudo updatedb; locate libicui18n
  Check for the following packages to be installed:

  
[LIST]
[*]/usr/lib/x86_64-linux-gnu/libicui18n.so.52 
[*]/usr/lib/x86_64-linux-gnu/libicui18n.so.52.1 
[/LIST]
  Those are the packages needed by Cisco Packet Tracer to work properly.

  Now you can type packettracer on terminal and the program should start.

     



That said, I find this really annoying having to search around the web for 1 hour or more for cryptic answers every time I want to install an app .

BTW it only allows me to start packet tracer from prompt. Is there no way to send a short cut to desktop or something other way to just click on an icon and run the app?

---

### Post by #&amp;thj^% on 2018-02-11
> **bryan309 said:**
> Hi Thanks for replying. 

I actually solved it. It's packet tracer 7. I find this[ link]("https://askubuntu.com/questions/963457/cisco-packet-tracer-7-1-wont-start") that had this answer:


Great Good job.
> **bryan309 said:**
> 
That said I find this really annoying that it's so much frustration searching around the web for 1 hour for cryptic answers every time I want to install an app .

It will over time become less "cryptic" as you become more familiar with Linux. ;)
Just ask questions here in in this forum...you will find some pretty talented helpful folks here.:D
> **bryan309 said:**
> 
BTW it only allows me to start packet tracer from prompt. Is there no way to send a short cut to desktop or something other way to just click on an icon and run the app? 
I will when time permits me see if I can show you how to make the shortcut..I have been consumed by Life lately.
Or maybe some other Kind user here might guide you through the steps as well.
May I offer you some advice>>>Linux is not Windows, a fun learning curve is in front of you.):P
EDIT: I will need the output of this to see what DE you are running: (For the shortcut)
```
echo $DESKTOP_SESSION
``` 
Paste that back here.

---

### Post by QIII on 2018-02-11
> That said, I find this really annoying having to search around the web for 1 hour or more for cryptic answers every time I want to install an app .

You are installing a third party package.  If the third party does not make the package easily installable on Linux, an installation method has to be cobbled together.  The vast majority of applications developed for or packaged for any particular family Linux distros install with little more than a single click.

Don't fool yourself.  Microsoft does not lift a finger to make third party software easy to install on Windows.  The developers of that software make sure installation is easy on Windows or they simply starve and go out of business.  Again:  installation packages are the responsibility of software developers, not Microsoft.  Windows does not make installation easy.  The software developer does.

Yours is not a complaint about Linux, but one about a third party software provider.

It is likely that you will get better help from Ubuntu users who understand that your gripes are unfounded if you leave them out.

---

