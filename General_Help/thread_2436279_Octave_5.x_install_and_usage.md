---
title: "Octave 5.x install and usage?"
date: 2020-02-03
forum: General Help
---

### Post by kwan-e on 2020-02-03
Hello all.  I am relatively new to Ubuntu (but not Linux) so please bear with me.

I am trying to run Octave 5.x under Ubuntu 18.04.4. The base repository only has the 4.2 version and I need 5.1 or later. I am in the process of migrating some Matlab scripts over to Octave and 5.x has Matlab compatibility improvements that simplify the task.

I was able to install using the Snap package. The install was fine, but I'm unable to actually install any Octave packages. To reproduce:
1. Install Octave via Snap and launch. Verify that 5.1 is running.
   ```
snap install octave --beta
   octave (beta) 5.1.0 from GNU Octave (octave-snap&#10003;) installed

```
2. Start Octave: snap run octave --gui

3. Install package:  pkg install -forge symbolic; pkg load symbolic; syms x

```
 >> pkg load symbolic >> syms x
Symbolic pkg v2.8.0: sh: 1: python: not found
error: Cannot run the Python executable "python"
    Try "sympref diagnose" for more information.
error: called from
    assert_have_python_and_sympy at line 61 column 7
    python_ipc_popen2 at line 79 column 5
    python_ipc_driver at line 59 column 15
    python_cmd at line 163 column 11
    valid_sym_assumptions at line 38 column 10
    assumptions at line 82 column 7
    syms at line 97 column 13
>>

```

I tried starting from a Python virtual environment, but the snap doesn't pick up the environment.  E.g.:
```
   source ~/bin/python_venv/p36/bin/activate
   snap run octave --gui
```


I also tried running from Flatpak but it doesn't even start:
```

(p36) [kwan@exeter Downloads]$ flatpak install org.octave.Octave.flatpakref
Installing in system:
org.freedesktop.Platform.openh264/x86_64/19.08 flathub 3e4c12dc2a37
org.octave.Octave/x86_64/stable                flathub 0aafd2e30314
  permissions: ipc, network, pulseaudio, wayland, x11, dri
  file access: host, xdg-config/kdeglobals:ro
  dbus access: com.canonical.AppMenu.Registrar, org.freedesktop.Flatpak
Is this ok [y/n]: y
Installing: org.freedesktop.Platform.openh264/x86_64/19.08 from flathub
[####################] Downloading files: 1/1 593.6 kB (593.6 kB/s)          
Warning: Failed to install org.freedesktop.Platform.openh264/x86_64/19.08: Error deploying: While trying to apply extra data: runtime/org.freedesktop.Platform/x86_64/19.08 not installed
Installing: org.octave.Octave/x86_64/stable from flathub
[####################] 594 metadata, 5917 content objects fetched; 127058 KiB transferred in 21 seconds
Now at 0aafd2e30314.


(p36) [kwan@exeter Downloads]$ flatpak run org.octave.Octave 
bwrap: Can't find source path /run/user/1000/doc/by-app/org.octave.Octave: No such file or directory



```


Any help would be greatly appreciated. I've burned a couple hours on this with no progress.  

TIA

---

### Post by kwan-e on 2020-02-03
I gave up on the Snap package approach. It has the right version but getting the environment configured was giving difficulties.  There were enough open issues regarding this approach that I figured it would be easier to wait for a newer version.

I did some troubleshooting on the Flatpak install and got tantalizingly close. Running the following got past the specific issues with the mount:
```

 systemctl restart --user xdg-document-portal


 systemctl stop --user flatpak-session-helper
 systemctl start --user flatpak-session-helper


```

Unfortunately, I couldn't get the PATH setup properly. I tried variations on the following:

```

 flatpak override --user --env=PYTHONHOME=/home/kwan/bin/python_venv/p36/ org.octave.Octave^C
 flatpak override --user --env=PATH=/app/bin:/usr/bin:/app/jre/bin:/home/kwan/bin/python_venv/p36/bin org.octave.Octave
 flatpak info --show-permissions org.octave.Octave

```

This was still giving errors about missing encodings. I set language  and other paths, but after another hour, punted.

Finally, I built octave directly from source. This required pulling in the qt5core-dev packages, and a ton of development tools, but it was successful (mostly).

```

GNU Octave, version 5.1.0
Copyright (C) 2019 John W. Eaton and others.
This is free software; see the source code for copying conditions.
There is ABSOLUTELY NO WARRANTY; not even for MERCHANTABILITY or
FITNESS FOR A PARTICULAR PURPOSE.  For details, type 'warranty'.


Octave was configured for "x86_64-pc-linux-gnu".


Additional information about Octave is available at https://www.octave.org.


Please contribute if you find this software useful.
For more information, visit https://www.octave.org/get-involved.html


Read https://www.octave.org/bugs.html to learn how to submitbug reports.
For information about changes from previous versions, type 'news'.


>> pkg load symbolic
>> syms x
Symbolic pkg v2.8.0: Python communication link active, SymPy v1.5.1.
>>

```

It's quite a bit slower than the pre-packaged versions. One of my tests takes about a minute to run, versus about 15s normally. During the build there were pages of warnings about packages.   I'm going to try some other gcc optimization flags and possibly link against the Intel optimized libraries.

---

### Post by Claus7 on 2020-02-05
Hello,

it's NOT a direct answer to your issues, yet I would like to inform you that the version 5.x can be found in ubuntu 20.04. It was one of the reasons of me upgrading, since I was facing some issues with saving plots on files with octave 4.x, so you could try this version of ubuntu, if you want octave installed by default without snap, flatpak or building from source.

20.04 is still under development, yet having it already in one of my systems, I should say that is pretty stable and octave is working fine.

Just a thought,
Regards!

---

