---
title: "Failed to open URL &quot;~/.wine/dosdevices/c:&quot;."
date: 2008-05-07
forum: General Help
---

### Post by xXChaoticNoiseXx on 2008-05-07
Specs:
Xubuntu Hardy Heron
Compiz Fusion + Emerald
Wine is the latest version

ok i have 2 problems regarding wine.

I cannot browse my c:/ Drive using the menu shortcut. I recieve the error:

Failed to open URL "~/.wine/dosdevices/c:".
The URL "~/.wine/dosdevices/c:" is not supported.

or

Failed to open URL "~/.wine/drive_c:".
The URL "~/.wine/drive_c:" is not supported.

if i input either one of these URLS into the terminal they execute and bring up the drive

my next problem is when ever i run the command:

$ wine guild wars -opengl

i get the error

wine: could not load L"C:\\windows\\system32\\guild.exe": Module not found


Would the module be openGl or is the problem in wine?

Im not a master but im fairly well versed in linux so i can do complex task if the solution calls for it. Please help me. I dont know what to do

---

### Post by Super R on 2008-05-08
Same exact problem here:(

---

### Post by xXChaoticNoiseXx on 2008-05-08
bump

---

### Post by Zorael on 2008-05-08
Please post the terminal output of the following commands.
```
$ ls -l ~/.wine
$ ls -l ~/.wine/dosdevices
```
(Omit the dollar-signs, that's code convention to show they're terminal commands.)

---

### Post by xXChaoticNoiseXx on 2008-05-08
Ok..... i figured out the problem with the menu object. I had to navigate to /usr/share/applications and open the menu object in text editor and change it from xdg-open to thunar and now it works like a charm.... but i still get the cannot find module error when i run wine guildwars.exe -opengl

Any Help?

Zorael - I am away from my Linux Box but when i get home this afternoon ill run those commands and post back..... thank you

---

### Post by xXChaoticNoiseXx on 2008-05-08
Ok..... i just figured out the last part..... it was right in front of my face..... simply inputting wine into the terminal automaticly directs it to the system32 folder, not the program files folder. The module not found error is referring to the .exe, if you first navigate to its location then run the .exe with the opengl switch it should open right up..... thanks to everyone for all your help

---

### Post by xXChaoticNoiseXx on 2008-05-08
now i have a new problem... when i run the Gw.exe with the opengl switch i recieve the following

[email]elijah@elijahs-room:~/.wine[/email]/drive_c/Program Files/Guild Wars$ ./Gw.exe -opengl
ALSA lib pcm_dmix.c:996:(snd_pcm_dmix_open) unable to open slave
fixme:mixer:ALSA_MixerInit No master control found on USB Device 0x46d:0x8d7, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f034,0x00000000), stub!
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x143148) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x29e05b0) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x29e0aa8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x26d1cb8) : stub
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:IWineD3DDeviceImpl_SetDialogBoxMode (0x143148) Dialogs cannot be disabled yet
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2cf0050) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x26d1848) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x26d1d40) : stub
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max temporary reg
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22
[email]elijah@elijahs-room:~/.wine[/email]/drive_c/Program Files/Guild Wars$ 

wine will open a window and the cursor will change then the window just closes

Any help?

---

### Post by stupidforum on 2008-05-08
run 
wine c:\\Program\ Files\\Guild\ Wars\\Gw.exe
Don't think the -opengl flag is necessary.  This has worked for me in every version of ubuntu since breazy (to some extent) but not in hardy.

---

### Post by JZhou on 2008-07-14
To workaround this problem, as I just guessed and tried, simply change the ~/.wine/drive_c in /usr/share/applications/wine-browsedrive.desktop to an absolute directory, which is prefixed by /home:)

---

