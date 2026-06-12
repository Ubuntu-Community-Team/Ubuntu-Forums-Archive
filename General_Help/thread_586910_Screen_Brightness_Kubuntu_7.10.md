---
title: "Screen Brightness Kubuntu 7.10"
date: 2007-10-22
forum: General Help
---

### Post by jasonlfunk on 2007-10-22
I installed Kubuntu 7.10 yesterday on my Vostro 1400 and everything is working great except that I cannot adjust the screen brightness with my keyboard (Func + Up/Down). It works during the Kubuntu loading screen, but once I get into KDE it doesn't work anymore. Ideas?

---

### Post by landstalkerx on 2007-12-09
I'm having the same problem with an Inspiron 640m
I poked around through some of the logs and found the following occurs in the acpid log when I press the brightness down button:

[Sun Dec  9 14:59:33 2007] received event "video LCD 00000087 00000000"
[Sun Dec  9 14:59:33 2007] notifying client 5027[106:110]
[Sun Dec  9 14:59:33 2007] notifying client 5774[0:0]
[Sun Dec  9 14:59:33 2007] executing action "/etc/acpi/video_brightnessdown.sh"
[Sun Dec  9 14:59:33 2007] BEGIN HANDLER MESSAGES
[Sun Dec  9 14:59:33 2007] END HANDLER MESSAGES
[Sun Dec  9 14:59:33 2007] action exited with status 0
[Sun Dec  9 14:59:33 2007] completed event "video LCD 00000087 00000000"

From what I can tell that looks like it's executing properly. Any suggestions about where else I should look or what might be the problem?

One other thing to note, the buttons work fine if I boot with the 2.6.20-16-generic kernel

---

### Post by rojojoseph on 2007-12-24
I also have same problem 

I am using Thinkpad R60 , with Kubuntu.

but following statement helped me to control screen brightness.

dcop `dcop | grep power-manager` power-manager brightnessUp

dcop `dcop | grep power-manager` power-manager brightnessDown

rojo

---

