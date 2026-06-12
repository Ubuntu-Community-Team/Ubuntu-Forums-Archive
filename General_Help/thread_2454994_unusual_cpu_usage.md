---
title: "unusual cpu usage"
date: 2020-12-10
forum: General Help
---

### Post by lumaja2 on 2020-12-10
[SIZE=3]Ubuntu 20.04LTS[/SIZE]
 
 
  [SIZE=3]I am setting up a new installed 20.4 LTS to replace my working OS Ubuntu 16.04 LTS.[/SIZE]
  [SIZE=3]After install  “System Load Indicator” in Top Bar notice an unusual cpu usage.[/SIZE]
  [SIZE=3]Checking why the cpu showing high levels in comparison to Ubuntu 16.04 found that[/SIZE]
  [SIZE=3]after booting and leaving to idle for 10 minutes found the readings still high[/SIZE]
  [SIZE=3]cpu1= 8.2% to 37.9%    cpu2= 6.1% to 33.75% make an up and down pattern between[/SIZE]
  [SIZE=3]the two cpus.[/SIZE]
  [SIZE=3]Run top in terminal and found   gnome-shell using 37.9% cpu and 13.8% on memory.[/SIZE]
  [SIZE=3]I think this is to high and something not working properly.[/SIZE]
  [SIZE=3]Need help to clear up these condition.[/SIZE]
  [SIZE=3]Thank you[/SIZE]

---

### Post by ActionParsnip on 2020-12-10
How much RAM do you have? If you are unsure then please give the output of:
```

free -m

```

Thanks

---

### Post by Yellow Pasque on 2020-12-10
Also, make sure your graphics are working properly:
```
glxinfo -B
```

---

### Post by lumaja2 on 2020-12-10
```
uis@l-Ubuntu20:~$ free -m
               total        used        free      shared  buff/cache   available
 Mem:           3613         977        1328         384        1307        2018
 Swap:          2047           0        2047
 luis@l-Ubuntu20:~$ glxinfo -B
 
```
 
 Command 'glxinfo' not found, but can be installed with:
 
 
 ```
sudo apt install mesa-utils
 
 
 luis@l-Ubuntu20:~$ sudo apt install mesa-utils
 [sudo] password for luis:  
 Reading package lists... Done
 Building dependency tree        
 Reading state information... Done
 The following packages were automatically installed and are no longer required:
   libfprint-2-tod1 libllvm9 python3-click python3-colorama
 Use 'sudo apt autoremove' to remove them.
 The following NEW packages will be installed:
   mesa-utils
 0 upgraded, 1 newly installed, 0 to remove and 29 not upgraded.
 Need to get 34.2 kB of archives.
 After this operation, 150 kB of additional disk space will be used.
 Get:1 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) focal/universe amd64 mesa-utils amd64 8.4.0-1build1 [34.2 kB]
 Fetched 34.2 kB in 0s (74.7 kB/s)      
 Selecting previously unselected package mesa-utils.
 (Reading database ... 183582 files and directories currently installed.)
 Preparing to unpack .../mesa-utils_8.4.0-1build1_amd64.deb ...
 Unpacking mesa-utils (8.4.0-1build1) ...
 Setting up mesa-utils (8.4.0-1build1) ...
 Processing triggers for man-db (2.9.1-1) ...
 
```
 
 ```
luis@l-Ubuntu20:~$ glxinfo -B
 name of display: :0
 display: :0  screen: 0
 direct rendering: Yes
 Extended renderer info (GLX_MESA_query_renderer):
     Vendor: Intel Open Source Technology Center (0x8086)
     Device: Mesa DRI Intel(R) HD Graphics (HSW GT1) (0x402)
     Version: 20.0.8
     Accelerated: yes
     Video memory: 1536MB
     Unified memory: yes
     Preferred profile: core (0x1)
     Max core profile version: 4.5
     Max compat profile version: 3.0
     Max GLES1 profile version: 1.1
     Max GLES[23] profile version: 3.1
 OpenGL vendor string: Intel Open Source Technology Center
 OpenGL renderer string: Mesa DRI Intel(R) HD Graphics (HSW GT1)
 OpenGL core profile version string: 4.5 (Core Profile) Mesa 20.0.8
 OpenGL core profile shading language version string: 4.50
 OpenGL core profile context flags: (none)
 OpenGL core profile profile mask: core profile
 
 
 OpenGL version string: 3.0 Mesa 20.0.8
 OpenGL shading language version string: 1.30
 OpenGL context flags: (none)
 
 
 OpenGL ES profile version string: OpenGL ES 3.1 Mesa 20.0.8
 OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.10
 
 
  [SIZE=3]luis@l-Ubuntu20:~$ [/SIZE]
```

---

