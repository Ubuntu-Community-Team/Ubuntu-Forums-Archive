---
title: "[SOLVED] No write access to /dev/dsp ?"
date: 2008-05-02
forum: General Help
---

### Post by WitchCraft on 2008-05-02
OK, i have the following problem:

I used espeak, and it worked well. Then I tried a few other text-to-speech programs. 

When I tried one of these programs (forgotten the name), the program crashed. 

Afterwards, when I opened espeak, it didn't work anymore, it outputs an error:
root@all:~# espeak something
PaHost_OpenStream: could not open /dev/dsp for O_WRONLY
PaHost_OpenStream: ERROR - result = -10000


Now, I thought this error would go away after restarting. But it doesn't...


Furthermore, when I open System->Preferences->Sound
and I switch Sound Events (Sound playback) to OSS instead of ALSA, and click on test, i get:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

Now, this used to work before, too...

And since no other application is open (not in the tray neither), it looks like the crash has somehow blocked/disallowed write access to /dev/dsp.


How can I re-establish write access to /dev/dsp?
I tried chmod +w, but that doesn't work...

```

root@all:~# ls -ls /dev/dsp
0 crwxrwxrwx 1 root audio 14, 3 2008-05-01 19:27 /dev/dsp

```

---

### Post by WitchCraft on 2008-05-02
```

root@all:~# strace -f /dev/dsp
execve("/dev/dsp", ["/dev/dsp"], [/* 34 vars */]) = -1 EACCES (Permission denied)
dup(2)                                  = 3
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(3, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 5), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fcf000
_llseek(3, 0, 0xbf9087c8, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: Permission denied\n", 32strace: exec: Permission denied
) = 32
close(3)                                = 0
munmap(0xb7fcf000, 4096)                = 0
exit_group(1)                           = ?
Process 9755 detached


```

---

### Post by chrisccoulson on 2008-05-02
Is your user a member of the audio group? What is the output of:
```
groups
```
If group 'audio' is not listed:
```
sudo usermod -a -G audio *<yourusername>*
```
...should add your user to the audio group. You will need to log out and back in again for changes to take effect

As a side note, you can't change permissions of anything under /dev permanently using chmod, as /dev is volatile (so you'll lose the changes at power down) and the permissions are determined by UDEV rules

---

### Post by WitchCraft on 2008-05-03
> **chrisccoulson said:**
> Is your user a member of the audio group? What is the output of:
```
groups
```
If group 'audio' is not listed:
```
sudo usermod -a -G audio *<yourusername>*
```
...should add your user to the audio group. You will need to log out and back in again for changes to take effect

As a side note, you can't change permissions of anything under /dev permanently using chmod, as /dev is volatile (so you'll lose the changes at power down) and the permissions are determined by UDEV rules


Wow, that helped. 
Strange however, that a crash can remove my user from the audio group...
Anyway, thank you so much!

---

