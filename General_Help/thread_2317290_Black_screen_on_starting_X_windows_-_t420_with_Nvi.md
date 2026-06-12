---
title: "Black screen on starting X windows - t420 with Nvidia 4200M"
date: 2016-03-15
forum: General Help
---

### Post by entt on 2016-03-15
The card I have is a Nvidia GF119M (Quadro NVS 4200M).

I have installed the nvidia-352 package, and I have not installed any packages like Bumblebee.

However, when I start X Windows I am presented with a black screen.

See below for some log files which may help with troubleshooting:

[LIST]
[*]gpu-manager.log - [https://www.dropbox.com/s/ieaqeb088q88d3z/gpu-manager.log?dl=0](https://www.dropbox.com/s/ieaqeb088q88d3z/gpu-manager.log?dl=0)
[*]kern.log - [https://www.dropbox.com/s/lq4evy1ozhcrmbh/kern.log?dl=0](https://www.dropbox.com/s/lq4evy1ozhcrmbh/kern.log?dl=0)
[*]sys.log - [https://www.dropbox.com/s/aa1klmcphbxh57q/syslog?dl=0](https://www.dropbox.com/s/aa1klmcphbxh57q/syslog?dl=0)
[*]Xorg.0.log - [https://www.dropbox.com/s/db6o1ds0c1ofiz7/Xorg.0.log?dl=0](https://www.dropbox.com/s/db6o1ds0c1ofiz7/Xorg.0.log?dl=0)
[/LIST]

I can see the following error in syslog, but I am not sure if this is the root cause of the problem:
```

Mar 15 20:43:23 laurie-ThinkPad-T420s nvidia-persistenced: Started (721)
Mar 15 20:43:23 laurie-ThinkPad-T420s nvidia-persistenced: Failed to query NVIDIA devices. Please ensure that the NVIDIA device files (/dev/nvidia*) exist, and that user 136 has read and write permissions for those files.
Mar 15 20:43:23 laurie-ThinkPad-T420s nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced
Mar 15 20:43:23 laurie-ThinkPad-T420s nvidia-persistenced: Shutdown (721)

```

---

### Post by Bashing-om on 2016-03-15
entt; Hello;

I do not download off of dropbox - or any other - onto my system. How about using our pastebin site to relay the log files ?
If the log is too large to attach in the thread ..:
```

sudo apt install pastebinit
pastebinit /var/log/Xorg.0.log

``` as the relevant log we would want to see at this time.
Where the result of 'pastebinit' is a URL back in terminal, pass that link back here .

And also, let's see that the kernel sees the hardware, and the system sees the driver ( if any ):
```

lspci -k | grep -EA2 'VGA|3D'
sudo lshw -C display

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So,
[INDENT][INDENT]a tale is told
[/INDENT][/INDENT]

---

