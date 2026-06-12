---
title: "Switching between keyboard formats"
date: 2006-12-06
forum: General Help
---

### Post by jfbailey on 2006-12-06
Hello Everyone,

I like to switch between keyboard formats (maybe setups is the better designation?), specifically, between German and standard US-English. I can do this in ubuntu, but I have always had to reboot for the switch to take effect. Does anyone know how to make the switch without having to reboot?

Thanks!

Joe

---

### Post by annda on 2006-12-06
add keyboard layout switcher applet to the gnome panel - this will let you switch on the fly, and it is configurable, too, so you can decide if the switch should be general or specific to an application.

---

### Post by _Artem_ on 2006-12-14
> **annda said:**
> add keyboard layout switcher applet to the gnome panel - this will let you switch on the fly, and it is configurable, too, so you can decide if the switch should be general or specific to an application.
Hy! Quite same problem: Sometimes layout switching stops to work. Hot keys or mouse click on the keyboard aplet don't help. However, X restarting wins. Besides, after installing K3b on my Ubuntu switching absolutely fall. When I try to open 'Keyboard preferenses' in keyaboard applet pop-up window appears with info something like this: "Gnome settings manager doesn't answer. Probably KDE manager works". I have greped processes and there was no one with 'kde' string. But the same 'ps -ax | grep settings' has given me info about running gnome-settings-manager..
WTF?? And, again, CTRL+ALT+Backspace won.
Any ideas?

---

### Post by LeslieL on 2006-12-15
The keyboard applet doesn't work for me. I switch between Turkish and English quite often, and in Dapper clicking on the applet makes absolutely no difference. So I've made my own simple panel applets that will do it reliably.

What I did:
1. Right-click on panel. Choose "Add to panel".
2. Select "Custom Application Launcher"
3. In the popup: Name - Turkish
                        Comment - Switch keyboard to Turkish layout
                        Command - setxkbmap tr
                        Icon - /usr/share/xfce4/xkb/flags/tr.png 
  Close.
  This makes a Turkish flag icon on your panel.
4. Repeat 2 and 3 to make an English layout button. The command is "setxkbmap us", and I use the icon /usr/share/xfce4/xkb/flags/uk.png.

I sweated blood trying to find out how to make the keyboard applet work and didn't get anywhere. This works reliably as long as your xorg.conf file is set up to handle turkish and english layouts. 

ç&#305;&#351;&#287;üö:)

---

### Post by hadiriazi on 2006-12-15
Hey, I have almost the same problem with keyborad layout, except mine does'nt have to be restarted. This happened since I installed beryl. After that I could'nt get the ctrl + shift to change the layout. So now I have to go to the keyboard layout options and untick then re tick the option to make it work!!

any suggestions??

---

