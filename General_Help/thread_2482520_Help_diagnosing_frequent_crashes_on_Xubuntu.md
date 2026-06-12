---
title: "Help diagnosing frequent crashes on Xubuntu"
date: 2023-01-02
forum: General Help
---

### Post by simongcox on 2023-01-02
I have recently switching from Windows to Xubuntu 22.04 (22.04.1 LTS) on a Dell Precision M4500 laptop. The computer is freezing several times per day - whilst I did have some problems with Windows crashing (who doesn't), this frequency is significantly worse, to the extent that the computer is borderline not usable (4 or 5 crashes so far today).

The freezing is a UI freeze. In some cases, the mouse continues to move across the screen, but the UI does not respond to clicks. In other cases, the mouse doesn't move at all or is not visible. When the freeze occurs, the music (streamed YouTube music video) stutters and loops before stopping.

My first guess was that it was the graphics driver, so I have installed the Nvidia 340 graphics driver (via apt-get) (replacing nouveau). This has not fixed the issue.

I have tried looking in the logs to see if there are any clues. The var/log/syslog file contains non-valid UTF-8 characters, and the section just before the time of the most recent crash just has a question mark symbol repeated as one long line in the file &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; etc etc (and then *Jan  2 20:58:41 Precision-M4500 systemd-modules-load[334]: Inserted module 'lp' *which I think is from the reboot). (I'm opening a copy of the log file in Mousepad).

I've tried pressing Alt + SysRq when the freeze happens, but this has had no effect.

I would be grateful for suggestions on next steps for diagnosing the issue.

---

### Post by #&amp;thj^% on 2023-01-02
I'm not sure if I can help you but this would be some good info to show us.
```
nvidia-smi
```
and 
```
inxi -C
```
paste that info back here it might get you more lookers

---

### Post by simongcox on 2023-01-03
Thanks

```
Command 'nvidia-smi' not found, but can be installed with:
sudo apt install nvidia-utils-390         # version 390.157-0ubuntu0.22.04.1, or
sudo apt install nvidia-utils-450-server  # version 450.216.04-0ubuntu0.22.04.1
sudo apt install nvidia-utils-470         # version 470.161.03-0ubuntu0.22.04.1
sudo apt install nvidia-utils-470-server  # version 470.161.03-0ubuntu0.22.04.1
```
etc, etc, etc

I have installed Nvidia 340

Here is the output from lspci | grep VGA:

```
01:00.0 VGA compatible controller: NVIDIA Corporation GT215GLM [Quadro FX 1800M] (rev a2)
```



```
CPU:
  Info: quad core model: Intel Core i7 X 920 bits: 64 type: MT MCP cache:
    L2: 1024 KiB
  Speed (MHz): avg: 1239 min/max: 1199/2000 cores: 1: 1223 2: 1208 3: 1204
    4: 1279 5: 1286 6: 1208 7: 1219 8: 1286

```

I've also had another freeze since, and this was from the last part of var/log/syslog before it switched to [COLOR=#000000]&#65533;:[/COLOR]

```
Jan  3 07:08:53 Precision-M4500 kernel: [36620.393598] nouveau 0000:01:00.0: gr: 00200000 [] ch 3 [003fa1a000 Xorg[1023]] subc 3 class 8597 mthd 1b0c data 1000f010
Jan  3 07:08:53 Precision-M4500 kernel: [36620.559524] nouveau 0000:01:00.0: gr: TRAP_MP_EXEC - TP 1 MP 0: 00000008 [TIMEOUT] at 07fa90 warp 31, opcode f6400001 0000c781
Jan  3 07:08:53 Precision-M4500 kernel: [36620.559535] nouveau 0000:01:00.0: gr: TRAP_MP_EXEC - TP 1 MP 1: 00000008 [TIMEOUT] at 07fa90 warp 31, opcode f6400001 0000c781
Jan  3 07:08:53 Precision-M4500 kernel: [36620.559542] nouveau 0000:01:00.0: gr: TRAP_MP_EXEC - TP 1 MP 2: 00000008 [TIMEOUT] at 07fa90 warp 31, opcode f6400001 0000c781
Jan  3 07:08:53 Precision-M4500 kernel: [36620.559550] nouveau 0000:01:00.0: gr: TRAP_MP_EXEC - TP 3 MP 0: 00000008 [TIMEOUT] at 07fa90 warp 31, opcode f6400001 0000c781
Jan  3 07:08:53 Precision-M4500 kernel: [36620.559557] nouveau 0000:01:00.0: gr: TRAP_MP_EXEC - TP 3 MP 1: 00000008 [TIMEOUT] at 07fa90 warp 31, opcode f6400001 0000c781
Jan  3 07:08:53 Precision-M4500 kernel: [36620.559564] nouveau 0000:01:00.0: gr: TRAP_MP_EXEC - TP 3 MP 2: 00000008 [TIMEOUT] at 07fa90 warp 31, opcode f6400001 0000c781
```


The other detail that I omitted from my first post is that I have a system resource monitor in the panel, and the system has not been under significant load at the point of freezing.

---

### Post by simongcox on 2023-01-03
inxi -Gxx

```
Graphics:
  Device-1: NVIDIA GT215GLM [Quadro FX 1800M] vendor: Dell driver: nouveau
    v: kernel pcie: speed: 5 GT/s lanes: 16 ports: active: VGA-1,eDP-1
    empty: DP-1,DP-2 bus-ID: 01:00.0 chip-ID: 10de:0cbc
  Device-2: Ricoh HD Webcam type: USB driver: uvcvideo bus-ID: 1-1.4:3
    chip-ID: 05ca:1814
  Display: x11 server: X.Org v: 1.21.1.3 compositor: xfwm v: 4.16.1 driver:
    X: loaded: modesetting unloaded: fbdev,vesa gpu: nouveau display-ID: :0.0
    screens: 1
  Screen-1: 0 s-res: 3840x1920 s-dpi: 96
  Monitor-1: VGA-1 pos: primary,left model: S2431W res: 1200x1920 dpi: 94
    diag: 616mm (24.2")
  Monitor-2: eDP-1 pos: primary,right model: LG res: 1920x1080 dpi: 142
    diag: 395mm (15.5")
  OpenGL: renderer: NVA3 v: 3.3 Mesa 22.0.5 direct render: Yes

```

It seems I was mistaken in thinking I had switched to the Nvidia driver

---

### Post by simongcox on 2023-01-03
I have now switched to the Nvidia legacy driver developed by kelebek333

Output of [COLOR=#000000][FONT=&quot]nvidia-smi[/FONT][/COLOR]


Tue Jan  3 08:05:43 2023       
+------------------------------------------------------+                       
| NVIDIA-SMI 340.108    Driver Version: 340.108        |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  Quadro FX 1800M     Off  | 0000:01:00.0     N/A |                  N/A |
| N/A   64C    P0    N/A /  N/A |    517MiB /  1023MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Compute processes:                                               GPU Memory |
|  GPU       PID  Process name                                     Usage      |
|=============================================================================|
|    0            Not Supported                                               |
+-----------------------------------------------------------------------------+


Let's see if this works...

---

### Post by Topsiho on 2023-01-03
If something like this happens to me in Ubuntu, i know it's the hardware, especially if it happens in another OS too.
The easiest thing to do, and  almost always with success, is checking the memory.

Happy computing everyone, in 2023:guitar:

Topsiho

---

