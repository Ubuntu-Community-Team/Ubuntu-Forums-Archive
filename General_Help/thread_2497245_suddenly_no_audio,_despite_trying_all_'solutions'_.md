---
title: "suddenly no audio, despite trying all 'solutions' found"
date: 2024-04-28
forum: General Help
---

### Post by crazybear on 2024-04-28
After years without any audio problem, my Dell XPS with Ubuntu 22.04 suddenly had all audio stop. I am not aware of any major program or other changes that would have caused it. There are two audio controllers - one embedded in the Processor and one in the Dell Dock - but none of that is new. After five days of NO audio and several hours per day looking up diagnoses ideas and solutions that worked for others, I'm at a loss. To post all the things I've tried would be a huge list. I'm posting a response I don't understand and the internet doesn't give any clues about the responses I could make sense of. Please help if you can. Thanks in advance. Trying to unmask pipewire-pulse.service and pulseaudio.service has not worked. Reinstalling has not worked.
```

systemctl --user status pipewire pipewire-pulse pulseaudio
&#9679; pipewire.service - PipeWire Multimedia Service
     Loaded: loaded (/usr/lib/systemd/user/pipewire.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2024-04-28 05:48:32 CEST; 1h 20min ago
TriggeredBy: &#9679; pipewire.socket
   Main PID: 5374 (pipewire)
      Tasks: 3 (limit: 76768)
     Memory: 5.0M
        CPU: 102ms
     CGroup: /user.slice/user-1000.slice/user@1000.service/session.slice/pipewire.service
             &#9492;&#9472;5374 /usr/bin/pipewire

Apr 28 05:48:32 standingwolf-XPS-2 systemd[5366]: Started PipeWire Multimedia Service.
Apr 28 05:48:32 standingwolf-XPS-2 pipewire[5374]: mod.jackdbus-detect: Failed to receive jackdbus reply: org.freedesktop.DBus.Error.ServiceUnknown: The name org.jackaudio.service was not provided by any .service files
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: ALSA lib parser.c:2108:(parse_master_file) unknown master file field Syntax
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: spa.alsa: '_ucm0001.hw:Dock,1': playback open failed: Device or resource busy
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: mod.adapter: 0x58e36034bb50: can't get format: Device or resource busy
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: ALSA lib parser.c:2108:(parse_master_file) unknown master file field Syntax
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: spa.alsa: '_ucm0002.hw:Dock': playback open failed: Device or resource busy

&#9675; pipewire-pulse.service
     Loaded: masked (Reason: Unit pipewire-pulse.service is masked.)
     Active: inactive (dead)

&#9675; pulseaudio.service
     Loaded: masked (Reason: Unit pulseaudio.service is masked.)
...skipping...
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: spa.alsa: '_ucm0001.hw:Dock,1': playback open failed: Device or resource busy
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: mod.adapter: 0x58e36034bb50: can't get format: Device or resource busy
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: ALSA lib parser.c:2108:(parse_master_file) unknown master file field Syntax
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: spa.alsa: '_ucm0002.hw:Dock': playback open failed: Device or resource busy

&#9675; pipewire-pulse.service
     Loaded: masked (Reason: Unit pipewire-pulse.service is masked.)
     Active: inactive (dead)

&#9675; pulseaudio.service
     Loaded: masked (Reason: Unit pulseaudio.service is masked.)
     Active: inactive (dead) since Sun 2024-04-28 06:51:42 CEST; 17min ago
   Main PID: 5377 (code=exited, status=0/SUCCESS)
        CPU: 49.558s

Apr 28 05:48:33 standingwolf-XPS-2 pulseaudio[5377]: Sink alsa_output.usb-Generic_USB_Audio_200901010001-00.HiFi__hw_Dock__sink does not exist.
Apr 28 05:48:33 standingwolf-XPS-2 systemd[5366]: Started Sound Service.
Apr 28 05:48:37 standingwolf-XPS-2 pulseaudio[5377]: Could not find org.bluez.BatteryProviderManager1.RegisterBatteryProvider(), is bluetoothd started with experimental features enabled (-E flag)?
Apr 28 05:48:37 standingwolf-XPS-2 pulseaudio[5377]: org.bluez.ProfileManager1.RegisterProfile() failed: org.bluez.Error.NotPermitted: UUID already registered
Apr 28 06:51:41 standingwolf-XPS-2 systemd[5366]: pulseaudio.service: Current command vanished from the unit file, execution of the command list won't be resumed.
Apr 28 06:51:41 standingwolf-XPS-2 systemd[5366]: Stopping pulseaudio.service...
Apr 28 06:51:41 standingwolf-XPS-2 systemd[5366]: pulseaudio.service: Got notification message from PID 5377, but reception is disabled.
Apr 28 06:51:42 standingwolf-XPS-2 pulseaudio[5377]: After module unload, module 'module-null-sink' was still loaded!
Apr 28 06:51:42 standingwolf-XPS-2 systemd[5366]: Stopped pulseaudio.service.
Apr 28 06:51:42 standingwolf-XPS-2 systemd[5366]: pulseaudio.service: Consumed 49.558s CPU time.
...skipping...
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: spa.alsa: '_ucm0001.hw:Dock,1': playback open failed: Device or resource busy
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: mod.adapter: 0x58e36034bb50: can't get format: Device or resource busy
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: ALSA lib parser.c:2108:(parse_master_file) unknown master file field Syntax
Apr 28 05:48:35 standingwolf-XPS-2 pipewire[5374]: spa.alsa: '_ucm0002.hw:Dock': playback open failed: Device or resource busy

```
```

standing-wolf2@standingwolf-XPS-2:~$ systemctl unmask pulseaudio
Unit pulseaudio.service does not exist, proceeding anyway.
standing-wolf2@standingwolf-XPS-2:~$ sudo systemctl --user unmask pulseaudio
[sudo] password for standing-wolf2: 
Failed to connect to bus: $DBUS_SESSION_BUS_ADDRESS and $XDG_RUNTIME_DIR not defined (consider using --machine=<user>@.host --user to connect to bus of other user)
standing-wolf2@standingwolf-XPS-2:~$ systemctl --user unmask pulseaudio
standing-wolf2@standingwolf-XPS-2:~$ systemctl --user mask pulseaudio.{service,socket} --now #unmask to revert
Created symlink /home/standing-wolf2/.config/systemd/user/pulseaudio.service &#8594; /dev/null.
Created symlink /home/standing-wolf2/.config/systemd/user/pulseaudio.socket &#8594; /dev/null.
standing-wolf2@standingwolf-XPS-2:~$ systemctl --user unmask pulseaudio.{service,socket} --now 
Removed /home/standing-wolf2/.config/systemd/user/pulseaudio.service.
Removed /home/standing-wolf2/.config/systemd/user/pulseaudio.socket.
standing-wolf2@standingwolf-XPS-2:~$ sudo systemctl --user unmask pulseaudio
Failed to connect to bus: $DBUS_SESSION_BUS_ADDRESS and $XDG_RUNTIME_DIR not defined (consider using --machine=<user>@.host --user to connect to bus of other user)
standing-wolf2@standingwolf-XPS-2:~$ systemctl --user unmask pulseaudio.{service,socket} --now 
standing-wolf2@standingwolf-XPS-2:~$ systemctl --user mask pulseaudio.{service,socket} --now #unmask to revert
Created symlink /home/standing-wolf2/.config/systemd/user/pulseaudio.service &#8594; /dev/null.
Created symlink /home/standing-wolf2/.config/systemd/user/pulseaudio.socket &#8594; /dev/null.
standing-wolf2@standingwolf-XPS-2:~$ inxi -A
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio
    driver: snd_hda_intel
  Device-2: Realtek USB Audio type: USB driver: snd-usb-audio
  Sound Server-1: ALSA v: k6.5.0-34-generic running: yes
  Sound Server-2: PipeWire v: 1.0.3 running: yes

```
```

standing-wolf2@standingwolf-XPS-2:~$ sudo pactl info
[sudo] password for standing-wolf2: 
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
standing-wolf2@standingwolf-XPS-2:~$ pulseaudio -k && pulseaudio -vvvv
E: [pulseaudio] main.c: Failed to kill daemon: No such process
standing-wolf2@standingwolf-XPS-2:~$ sudo fuser -v /dev/snd/*
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  standing-wolf2   5375 F.... pipewire-media-
/dev/snd/controlC1:  standing-wolf2   5374 F.... pipewire
                     standing-wolf2   5375 F.... pipewire-media-
/dev/snd/seq:        standing-wolf2   5374 F.... pipewire
standing-wolf2@standingwolf-XPS-2:~$ systemctl --user status pulseaudio
&#9675; pulseaudio.service
     Loaded: masked (Reason: Unit pulseaudio.service is masked.)
     Active: inactive (dead) since Sun 2024-04-28 06:51:42 CEST; 9h ago
   Main PID: 5377 (code=exited, status=0/SUCCESS)
        CPU: 49.558s

```

---

