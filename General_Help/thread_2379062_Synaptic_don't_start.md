---
title: "Synaptic don't start"
date: 2017-11-30
forum: General Help
---

### Post by zohran on 2017-11-30
Hello, i have finished to switch with the new lastest linux kernel (4.15). I have rebooted successfully, all applications works correctly EXCEPT synaptics !

_**When i launch it with terminal, i have this error:**_
```
fulgurance@MSI-GS73VR-6RF:~$ sudo synaptic
[sudo] Mot de passe de fulgurance : 
No protocol specified
Unable to init server: Impossible de se connecter : Connexion refusée

(synaptic:2443): Gtk-WARNING **: cannot open display: :0
```
[U][B]
Without sudo (i have error message: "Starting 'synaptic package mananger' without administrative privileges. You will not be able to apply any changes, but you can still export the marked changes or create a download script for them):[/B][/U]
```
fulgurance@MSI-GS73VR-6RF:~$ synaptic
Gtk-Message: GtkDialog mapped without a transient parent. This is discouraged.
Erreur de segmentation (core dumped)
```

---

### Post by Bashing-om on 2017-11-30
zohran; Hey --- 

wayland has some growing pains . Authorizations are one of them for many GUI applications.

See if this work-a-round:
[https://ubuntuforums.org/showthread.php?t=2374812](https://ubuntuforums.org/showthread.php?t=2374812)

suffices for your use case .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by zohran on 2017-11-30
Oh thanks ! It's good !

---

### Post by Bashing-om on 2017-11-30
zohran' Great :)

If this matter is concluded -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

'buntu
[INDENT][INDENT]together we do
[/INDENT][/INDENT]

---

