---
title: "No sound"
date: 2013-01-27
forum: General Help
---

### Post by izvunzem4o on 2013-01-27
I've installed Kubuntu today and I have no sound. I've updated everything, checked the alsamixer, but when I try installing my sound card driver (HDA INTEL - Realtek ALC880), thats what it says ```
.....Decompress Driver source v1.0.24-5.16rc25
Compile Driver........
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/c3rb3ru5/Desktop/realtek-linux-audiopack-5.16/alsa-driver-1.0.24':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/c3rb3ru5/Desktop/realtek-linux-audiopack-5.16/alsa-driver-1.0.24'
gcc utils/mod-deps.c -o utils/mod-deps
make[1]: gcc: Command not found
make[1]: *** [utils/mod-deps] Error 127
make[1]: Leaving directory `/home/c3rb3ru5/Desktop/realtek-linux-audiopack-5.16/alsa-driver-1.0.24'
make: *** [dummy1] Error 2
if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/c3rb3ru5/Desktop/realtek-linux-audiopack-5.16/alsa-driver-1.0.24/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
rm: cannot remove `/dev/snd': Is a directory
rm: cannot remove `/dev/snd/by-path': Is a directory
rmdir: failed to remove `/dev/snd': Directory not empty
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
Remove Folder.....
./install: 47: ./install: alsaconf: not found

```Everything is unmuted. I'm using headphones.

---

### Post by jorok_tupur on 2013-01-27
According to the log, your install script cannot find the alsaconf.

According the [Debian's wiki]("http://wiki.debian.org/alsaconf"), [a bug report in Launchpad]("https://bugs.launchpad.net/alsa-utils/+bug/29597"), and [a thread in this forum]("http://ubuntuforums.org/showpost.php?p=12303069&postcount=2"), alsaconf has been removed from the alsa-utils package.

I suggest you search this forum using 'alsaconf' as the key word.

---

### Post by HiImTye on 2013-01-27
it says there's no compiler, make sure you have the *build-essential* package
```
sudo apt-get install build-essential
```

---

### Post by Yellow Pasque on 2013-01-27
It amazes me how many people try to install that Realtek driver (but I guess that's the Windows mentality, so I shouldn't be surprised). Rarely does downloading the Realtek version of the ALSA driver solve the issue (and it often makes things worse for inexperienced folks who don't install it properly). The only reason to use that driver would be if you had recent hardware that had undocumented processing coefficients and the changes hadn't made their way into mainstream ALSA yet.

Start by making sure you have the right device selected in Kubuntu's sound settings. Also info might be helpful: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

