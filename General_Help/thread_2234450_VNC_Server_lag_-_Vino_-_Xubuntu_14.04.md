---
title: "VNC Server lag - Vino - Xubuntu 14.04?"
date: 2014-07-14
forum: General Help
---

### Post by RallyDarkstrike on 2014-07-14
Hey all,

I've got an issue with Xubuntu 14.04 and Vino. I have a VNC server set up using Vino and can connect to it, no problem. However, it is VERY slow/laggy. In comparison, I have a server set up the EXACT SAME WAY on Linux Mint 17 Qiana, also with Vino with the same password, same settings, etc. on the same network connected to the same router (both are on wireless atm) and it is MUCH faster.

Is there any reason that Vino would cause much slower connections on Xubuntu 14.04 compared to Mint 17 with the exact same Vino setup? I would love to make it as snappy when remotely logged in as my Mint 17 machine....

Thanks for any ideas or help! :)

---

### Post by P_THE_AWESOME on 2014-07-14
I've had a lot of problems with vino in the past on multiple Ubuntu derivatives and versions. I eventually found x11vnc.

Quick setup guide 
[LIST=1]
[*]**Install**
```
sudo apt-get update && sudo apt-get install x11vnc
``` 
[*]**Build a command**
I would suggest you run x11vnc --help | less, but if you want a quick and dirty setup, just use mine:
```
x11vnc -bg -rfbport 5900 -find -rfbauth /home/<username>/.x11VNCpass -logappend [FONT=courier new]/home/<username>/.x11vnc.log[/FONT] -reopen -forever -ultrafilexfer -avahi
```
This  will run x11vnc in the background, will use port 5900, will find the most recent X desktop, will load the password from [FONT=courier new]/home/<username>/.x11VNCpass[/FONT], will append/create if it doesn't exist to the log at [FONT=courier new][FONT=courier new]/home/<username>/.x11vnc.log[/FONT], [/FONT]forever (won't exit after the first  connection ends), will fix file transfers for UltravNC *you can also use [FONT=courier new]--tightfilexfer[/FONT] for TightVNC)[FONT=courier new][/FONT], and will announce via zeroconfig/mdns/avahi/Bonjour. 
[*]**Create a Password**
You can use ```
[FONT=courier new]x11vnc --storepasswd <password> <file>[/FONT]
``` I used the location "[FONT=courier new]/home/<username>/.x11VNCpass[/FONT]". 
[*]**Add to startup**
The command arguments I have provided are set to use the current X  desktop session, and probably without admin rights (i.e. no /var/log/), _which means that it must be run after the user is logged in, not at boot._  However, there are options to work around this (either create a new  session or wait for the first active one). I've never looked into these  options in detail since I've only ever needed it after my computer's  auto-logon (it's HTPC, so this is perfect in this situation). Depending  on your Ubuntu flavor, a GUI somewhere will configure this.
 - Ubuntu: [FONT=courier new]gnome-session-properties[/FONT]
 - Lubuntu: [FONT=courier new]lxsession-edit[/FONT]
 - Xubuntu: I don't know the command, see [Add application to Xfce/Xubuntu session startup]("http://xubuntugeek.blogspot.com/2011/12/add-application-to-xfcexubuntu-session.html")
 - All Distros:[FONT=courier new] ~/.config/autostart[/FONT] (see [http://askubuntu.com/a/159011/199155](http://askubuntu.com/a/159011/199155)) 
[/LIST]

---

### Post by RallyDarkstrike on 2014-07-20
Hey man - thanks for the reply! I've used x11VNC in the past, I just assumed this was an issue with ALL VNC servers....apparently it's not as x11VNC works flawlessly! Marked as solved! :)

---

### Post by P_THE_AWESOME on 2014-07-20
Glad to help. Good luck and have fun.

---

### Post by RallyDarkstrike on 2014-07-27
Well....I spoke too soon - I installed X11VNC as mentioned above and it worked the first time, no problem....great! I connected to it then, no lag anymore, everything worked fine!

 So I shut the computer off and haven't used it for a week. Turned it on yesterday, tried remotely connecting via Remmina on my netbook running Mint 17 to the X11VNC server running on this desktop and....nothing. I enter my password, something flickers on my VNC client comp's screen for a split second on the client end and then immediately closes....?

[COLOR=#ff0000]EDIT - I can connect perfectly to it using my Windows machine running the UltraVNC client, but I get the 'flicker' described above and nothing else on my Mint 17 netbook running the Remmina client...?[/COLOR]

Any ideas?

---

### Post by P_THE_AWESOME on 2014-07-27
Try removing the -ultrafilexfer tag and restarting x11vnc and/or your computer.

If you really need to, you can try UltraVNC with WINE on the Mint computer. However, that should not be necessary.

---

### Post by RallyDarkstrike on 2014-07-27
Alright - figured out the problem. It WASN'T the -ultrafilexfer command, but actually the connection settings in Remmina - I had it set to '256 colors,' and 'Poor' and apparently something with the way the '256 colors' setting works (something about saving to jpeg files in the error logs?) isn't liked by Remmina, so I set it to 'High Color 16-bit' and all is now well! :)

---

### Post by permaquid on 2014-11-22
I was looking for a solution for what looks like the same problem. That is, I was using vino successfully for remote access from Ubuntu 10.10 running the Gnome desktop for quite a while, then got a new (remote) computer with 14.04 running Unity. With the exact same setup, no change in the VNC client, remote access is now unusably slow. I did try x11vnc; on connect, it crashed with a buffer overflow detected and quite a juicy stack trace. There seems to be a known bug somewhere in the VNC stack but I have the latest official vino and I am not interested in tracking down and applying some patch. This thread does not really provide a solution for the original question posed, which is: why is vino apparently so slow for remote access with 14.04 Unity, and what can be done about it. I have tried removing as many window decorations as possible; that's not the problem. What I see is a delay of up to five seconds responding to mouse clicks and keystrokes. Some keystrokes are missed. Just to emphasize, there has been no change at the client end; no change to the wireless network, the ISP, the computer and VM it is running on. The VM is Virtual Box with 14.04 Unity as well. All of which was quite usable (though not exciting) with 10.10 Gnome.

---

### Post by P_THE_AWESOME on 2014-11-22
Sir, I have always had problems with vino. That's why I switched to x11vnc. Vino is simply old and slow. Anywhere on AskUbuntu or these forums you will here people say that. It's annoying to work with and lacks customization. What you are describing is two bugs, not just one: its too slow and keystrokes are missed. It might be because the VM doesn't have enough memory or CPU, but it could also be that, once again, vino had not been maintained to fix bugs like this since a long time.

I should note that Virtualbox has it's own Remote Desktop feature that you might find useful. I've never played with it, but it is an option. Virtualbox's network interface system could be too slow and ruining your connection. **It's much harder to debug things like this from a VM because it could also be the VM that is causing the problem.**

Also, running full Ubuntu in a VM has always been laggy for me. Unity sucks up all of the available resources. I eventually switched to Lubuntu so that I could do more than browse he web and view my desktop

.[ATTACH=CONFIG]258133[/ATTACH]

---

### Post by permaquid on 2014-11-23
As I explained - the only difference in the setup was moving the server from 10.10 on one well-provisioned computer to a similar new computer running 14.04. Therefore, the client end is not relevant. If I were to guess, I would say that Vino does something bad with Unity.

---

