---
title: "Broken Synaptic and dpkg"
date: 2007-09-19
forum: General Help
---

### Post by colonel_panic414 on 2007-09-19
I was looking for a web-controlled music server for my computer, and decided on mpd+a cellphone targeted web client. So, I went to install it through Synaptic, and then the installation froze like this:

```
Setting up mpd (0.12.2-2ubuntu2) ...
Stopping Music Player Daemon: not running or no pid_file set.
Starting Music Player Daemon: ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3968:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2145:(snd_pcm_open_noupdate) Unknown PCM default
```


So, I had to kill the process, because it just hung there for about 10 minutes. I tried to reinstall it, but when I open up synaptic or use apt, I get this error:

```
taylor@UbuntuBox:~$ sudo apt-get remove mpd
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
[1]+  Killed                  sudo dpkg --configure -a
```

But, when I run sudo dpkg --configure -a, it just gives me the same thing as what Synaptic spit out when I first tried installing MPD. 

So now, my Synaptic/apt is non-functional. I can't install updates, or any other packages. What should I do??

Thanks ahead of time, I appreciate any help or advice.

---

### Post by por100pre1 on 2007-09-19
Try this:

```
sudo /etc/init.d/mpd stop
```

```
pkill mpd
```

```
sudo apt-get install -f
```

---

### Post by colonel_panic414 on 2007-09-19
Well, the first two commands did their job, killing mpd.

The final code, sudo apt-get install -f did nothing but tell me to do sudo dpkg --configure -a again.

---

### Post by colonel_panic414 on 2007-09-19
Bump... Does anyone know what to do?

---

