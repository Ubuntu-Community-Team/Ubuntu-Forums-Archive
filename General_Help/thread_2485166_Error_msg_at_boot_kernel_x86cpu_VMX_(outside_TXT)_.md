---
title: "Error msg at boot: kernel: x86/cpu: VMX (outside TXT) disabled by BIOS"
date: 2023-03-21
forum: General Help
---

### Post by Shobuz99 on 2023-03-21
I have searched for this error msg already here to no avail.
I'm running an HP Elitebook 8640p 8GB memory 250GB storage

I get this error msg during boot, prior to ubuntu loading. 
```
 kernel: x86/cpu: VMX (outside TXT) disabled by BIOS 
```

This has happened every time I boot it.

I recently upgraded to Ubuntu 20.04.6 LTS earlier this month (March)

[ATTACH=CONFIG]291935[/ATTACH]
I searched through some posts and found the command  
```
 journalctl -p 3 -xb 
```

And got this response ```
 
Mar 21 09:01:44 rick-HP-EliteBook-8460p kernel: x86/cpu: VMX (outside TXT) disabled by BIOS
Mar 21 09:05:33 rick-HP-EliteBook-8460p gdm-password][1863]: gkr-pam: unable to locate daemon con>
Mar 21 09:05:59 rick-HP-EliteBook-8460p pulseaudio[1883]: GetManagedObjects() failed: org.freedes> 
```

My question is, what do I need to do fix this first 
```
 kernel: x86/cpu: VMX (outside TXT) disabled by BIOS 
```

and then fix the other two? ```
 
Mar 21 09:05:33 rick-HP-EliteBook-8460p gdm-password][1863]: gkr-pam: unable to locate daemon con>
Mar 21 09:05:59 rick-HP-EliteBook-8460p pulseaudio[1883]: GetManagedObjects() failed: org.freedes> 
```

I hope it's not something I did when I upgraded to 20.04.6 from 18.04 the 2nd time, and followed the instructions I was given.

Shobuz99

---

### Post by DuckHook on 2023-03-21
The VMX message indicates that your computer BIOS has not enabled _V_irtual _M_achine E_x_tensions. In other words, your computer either doesn't have this feature turned on, or is incapable of running VMs at all. To fix, go into your BIOS at boot and try to find settings like VMX or VT-x. If you don't run virtual machines, then it is not necessary to turn these on. Using the principle of least attack surface it is safer to have this feature off (which is also why BIOS is set to off by default), unless you intend to run VMs.

The other two messages are unrelated and can be addressed independently.

The PAM message could just be informational. Are you able to log in normally? If you get a challenge/response login that works, then I would just ignore this message.

The last message is about PulseAudio and could also be informational. If you get proper sound, then it is probably safe to also ignore this one.

---

### Post by MAFoElffen on 2023-03-21
> **Shobuz99 said:**
> 
```
 
Mar 21 09:01:44 rick-HP-EliteBook-8460p kernel: x86/cpu: VMX (outside TXT) disabled by BIOS
Mar 21 09:05:33 rick-HP-EliteBook-8460p gdm-password][1863]: gkr-pam: unable to locate daemon control file
Mar 21 09:05:59 rick-HP-EliteBook-8460p pulseaudio[1883]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply.

```

Message on 'gdm-password' is informational, meaning that when the system was booting it initially, is that the PAM process starts, but there is no credentials passed yet. At that time, it didn't find the credentials in a variable, so created it a variable placeholder for that, until it was needed. Systemd will set that variable on it's own once the session is up. The problem from a process perspective is that you are passing a password to PAM and all things hooked into that receive that password. Once it's verified you are you, the rest of the startup can continue, but that is already "after" PAM has started. and in this particular case  you have something "after" PAM  , the gnome-keyring that still needs your password. (Gained from the Graphical Login panel.)

Since informational and normal, nothign needs to be fixed with that.

Message on VMX, is telling you that virtual technologies in the BIOS is disabled. VMX stands for Virtual Machine Extensions and it is a virtualization technology. You can go into your BIOS setting and enable it and that message will go away.


If you don't have sound on "something". The pulse audio message is a problem and might need some tracking down to figure out what is wrong... It didn't say which device was throwing that problem so makes that a bit more challenging. If it were, per se, a bluetooth device, then it would be something like this:
RE: [https://askubuntu.com/questions/1024012/pulseaudio-bluez5-util-c-getmanagedobjects-failed-org-freedesktop-dbus-err](https://askubuntu.com/questions/1024012/pulseaudio-bluez5-util-c-getmanagedobjects-failed-org-freedesktop-dbus-err)

What might give you hints to that problem is doing this:
```

sudo nano /etc/pulse/client.conf

```
Add this line to the end of that file
```

extra-arguments = -vvvv --log-target=newfile:/tmp/pulse_verbose.log.txt --log-time=1

```
Save and reboot.

And posting that log as an attachment to a post.

Then you can do that again to either comment that line out or remove it.

---

### Post by Shobuz99 on 2023-03-21
> **DuckHook said:**
> The VMX message indicates that your computer BIOS has not enabled _V_irtual _M_achine E_x_tensions. In other words, your computer either doesn't have this feature turned on, or is incapable of running VMs at all. To fix, go into your BIOS at boot and try to find settings like VMX or VT-x. If you don't run virtual machines, then it is not necessary to turn these on. Using the principle of least attack surface it is safer to have this feature off (which is also why BIOS is set to off by default), unless you intend to run VMs.

The other two messages are unrelated and can be addressed independently.

The PAM message could just be informational. Are you able to log in normally? If you get a challenge/response login that works, then I would just ignore this message.

The last message is about PulseAudio and could also be informational. If you get proper sound, then it is probably safe to also ignore this one.

Thank you. I will check the BIOS at boot and see if the VMX or VM-x feature is there.
I don't intend to create, setup or use a Virtual Machine. So I'll leave well enough alone regardless.

Re: PAM - Yes I'm able to login normally with a password and it works. 
I'll leave that alone as well.

Re: PulseAudio - Yes the sound is working fine. 
I just keep it muted most of the time anyway. I prefer not to use the "beep bop bip boop" menu sounds to tell me what's happening...LOL!
If I want to hear audio on a video, I enable it. So far it's worked every time.:D

I think I'll be okay...

Thanks again. :)

Shobuz99

---

### Post by Shobuz99 on 2023-03-21
> **MAFoElffen said:**
> Message on 'gdm-password' is informational, meaning that when the system was booting it initially, is that the PAM process starts, but there is no credentials passed yet. At that time, it didn't find the credentials in a variable, so created it a variable placeholder for that, until it was needed. Systemd will set that variable on it's own once the session is up. The problem from a process perspective is that you are passing a password to PAM and all things hooked into that receive that password. Once it's verified you are you, the rest of the startup can continue, but that is already "after" PAM has started. and in this particular case  you have something "after" PAM  , the gnome-keyring that still needs your password. (Gained from the Graphical Login panel.)

Since informational and normal, nothign needs to be fixed with that.

Message on VMX, is telling you that virtual technologies in the BIOS is disabled. VMX stands for Virtual Machine Extensions and it is a virtualization technology. You can go into your BIOS setting and enable it and that message will go away.


If you don't have sound on "something". The pulse audio message is a problem and might need some tracking down to figure out what is wrong... It didn't say which device was throwing that problem so makes that a bit more challenging. If it were, per se, a bluetooth device, then it would be something like this:
RE: [https://askubuntu.com/questions/1024012/pulseaudio-bluez5-util-c-getmanagedobjects-failed-org-freedesktop-dbus-err](https://askubuntu.com/questions/1024012/pulseaudio-bluez5-util-c-getmanagedobjects-failed-org-freedesktop-dbus-err)

What might give you hints to that problem is doing this:
```

sudo nano /etc/pulse/client.conf

```
Add this line to the end of that file
```

extra-arguments = -vvvv --log-target=newfile:/tmp/pulse_verbose.log.txt --log-time=1

```
Save and reboot.

And posting that log as an attachment to a post.

Then you can do that again to either comment that line out or remove it.

Thank you MAFoElffen

I appreciate the additional information and reference.
I'm certain I'll want to use it at some point.:)


Shobuz99

---

### Post by Shobuz99 on 2023-03-22
DuckHook
Update:
I checked my BIOS (dated 2012) and yes, it shows TXT technology disabled.
I plan on leaving it that way because I don't have a reason to use a VM session.
However, now that I know I CAN enable it if I choose, that is an additional option that I didn't know I had previously.

Thank you for that.
I will mark this Solved

---

### Post by Shobuz99 on 2023-03-22
MAFoElffen

I added the code you suggested for the pulseaudio msg
The results:
```
 GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. 
Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, 
the reply timeout expired, or the network connection was broken.
```

I then opened a music video on YouTube and increased the volume. It worked as expected.

At this point I'm satisfied that whatever is happening, it's not affecting the sound when I un-mute it.

I think I'll just leave the extra-argument code as is.

Thank you for your help.

I will mark this solved.

---

