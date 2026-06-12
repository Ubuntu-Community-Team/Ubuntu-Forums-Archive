---
title: "Trying to figure out why &quot;pkill devilspie2&quot; doesn't work for my bash script"
date: 2022-10-03
forum: General Help
---

### Post by salamilimos on 2022-10-03
I installed devilspie2 and created debug.lua in ~/.config/devilspie2/ and added the following:


```
if (get_application_name()=="PulseEffects") then
	center();
end

```

I created a pulseeffects.desktop file in ~/.config/autostart/ with the following:


```
Exec=bash -c "devilspie2 & sleep 5; flatpak run com.github.wwmm.pulseeffects & sleep 10; wmctrl -r PulseEffects -t 3 & pkill devilspie2"
```

Through monitoring task manager, this command does the following, devilspie2 launches and PulseEffects launches to the center of the screen, PulseEffects moves to Workplace 4, then devilspie2 closes.


Then I created another pulseeffects.desktop in ~/.local/share/applications with the following:


```
Exec=bash -c "devilspie2 & sleep 5; flatpak run com.github.wwmm.pulseeffects & sleep 10; pkill devilspie2"
```

But in this command though, devilspie2 doesn't close after launching PulseEffects, it only closes when I close PulseEffects.


How can I fix this, so my second command closes devilspie2 after launching PulseEffects.


Thanks.

---

### Post by MAFoElffen on 2022-10-03
How about 
```

# Exec=bash -c 'devilspie2 &; pID=$!; sleep 5; flatpak run com.github.wwmm.pulseeffects &; sleep 10; kill $pID'

```
Does that work?

---

### Post by salamilimos on 2022-10-04
Doesn't work.

Here's the terminal output:

```
devilspie2 &; pID=$!; sleep 5; flatpak run com.github.wwmm.pulseeffects &; sleep 10; kill $pID
bash: syntax error near unexpected token `;'

```

---

### Post by MAFoElffen on 2022-10-04
Then maybe (running as root)
```

# Exec=bash -c 'devilspie2 & pID=$! ; sleep 5; flatpak run com.github.wwmm.pulseeffects & sleep 10; kill $pID'

```

---

### Post by #&amp;thj^% on 2022-10-04
> **salamilimos said:**
> 

```
Exec=bash -c "devilspie2 & sleep 5; flatpak run com.github.wwmm.pulseeffects & sleep 10; pkill devilspie2"
```

But in this command though, devilspie2 doesn't close after launching PulseEffects, it only closes when I close PulseEffects.


How can I fix this, so my second command closes devilspie2 after launching PulseEffects.


Thanks.

Mine's not a flatpak but it is running ATM.
```
Application: Xfce Terminal
Window: Terminal - 
Application: xed
Window: debug.lua (~/.config/devilspie2)
Application: Firefox
Window: Tutorial &#8211; Devilspie2 » Linux Magazine &#8212; Mozilla Firefox
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: xfdesktop
Window: Desktop
Application: xfce4-panel
Window: xfce4-panel
Application: xfce4-panel
Window: xfce4-panel

```
I'll use:
```
pgrep devilspie | xargs kill -9 

```
You'll just have to figure out the rest in your script.
```
ps -ef | grep -i '[d]evil'
me        8898 17717  0 13:29 pts/0    00:00:00 devilspie2 --debug



```
EDIT: After playing around this one works for me:
```
>> **_devilspie2 & sleep 5; flatpak run com.github.wwmm.pulseeffects & sleep 10; pgrep devilspie2 | xargs kill -9_**
[1]-  Killed                  devilspie2
[2]+  Done                    flatpak run com.github.wwmm.pulseeffects
[1] 26577
[2] 26778
Gtk-Message: 14:02:20.107: Failed to load module "canberra-gtk-module"

(pulseeffects:2): pulseeffects-WARNING **: 14:02:20.150: sie: rtkit: Failed to connect to system bus: Could not connect: No such file or directory

(pulseeffects:2): pulseeffects-WARNING **: 14:02:20.327: soe: rtkit: Failed to connect to system bus: Could not connect: No such file or directory

(pulseeffects:2): pulseeffects-WARNING **: 14:02:21.952: pulse_info: pulseaudio --dump-conf : execve failed: No such file or directory

(pulseeffects:2): pulseeffects-WARNING **: 14:02:21.954: pulse_info: pulseaudio --dump-resample-methods : execve failed: No such file or directory

(pulseeffects:2): pulseeffects-CRITICAL **: 14:02:23.381: pulse_manager: failed to move sink input: strawberry, idx = 92 to PE




```

---

### Post by salamilimos on 2022-10-04
> **1fallen said:**
> Mine's not a flatpak but it is running ATM.
```
Application: Xfce Terminal
Window: Terminal - 
Application: xed
Window: debug.lua (~/.config/devilspie2)
Application: Firefox
Window: Tutorial – Devilspie2 » Linux Magazine — Mozilla Firefox
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: system_conky
Window: system_conky
Application: xfdesktop
Window: Desktop
Application: xfce4-panel
Window: xfce4-panel
Application: xfce4-panel
Window: xfce4-panel

```
I'll use:
```
pgrep devilspie | xargs kill -9 

```
You'll just have to figure out the rest in your script.
```
ps -ef | grep -i '[d]evil'
me        8898 17717  0 13:29 pts/0    00:00:00 devilspie2 --debug



```
EDIT: After playing around this one works for me:
```
>> **_devilspie2 & sleep 5; flatpak run com.github.wwmm.pulseeffects & sleep 10; pgrep devilspie2 | xargs kill -9_**
[1]-  Killed                  devilspie2
[2]+  Done                    flatpak run com.github.wwmm.pulseeffects
[1] 26577
[2] 26778
Gtk-Message: 14:02:20.107: Failed to load module "canberra-gtk-module"

(pulseeffects:2): pulseeffects-WARNING **: 14:02:20.150: sie: rtkit: Failed to connect to system bus: Could not connect: No such file or directory

(pulseeffects:2): pulseeffects-WARNING **: 14:02:20.327: soe: rtkit: Failed to connect to system bus: Could not connect: No such file or directory

(pulseeffects:2): pulseeffects-WARNING **: 14:02:21.952: pulse_info: pulseaudio --dump-conf : execve failed: No such file or directory

(pulseeffects:2): pulseeffects-WARNING **: 14:02:21.954: pulse_info: pulseaudio --dump-resample-methods : execve failed: No such file or directory

(pulseeffects:2): pulseeffects-CRITICAL **: 14:02:23.381: pulse_manager: failed to move sink input: strawberry, idx = 92 to PE




```

Thank you so much, that worked, thank you.

I still want to understand why my autostart command worked and your command worked, but my second command didn't.

Thanks for the help fallen1, thank you.

---

