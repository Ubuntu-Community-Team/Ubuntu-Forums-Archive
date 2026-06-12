---
title: "audio-recorder"
date: 2021-01-10
forum: General Help
---

### Post by Old Jimma on 2021-01-10
Hi Community:

I upgraded to 20.04.

How do I install audio-recorder? I can find it at > [https://launchpad.net/audio-recorder](https://launchpad.net/audio-recorder). However, I don't know how to find it with synaptic.

Thanks,
OJ

---

### Post by #&amp;thj^% on 2021-01-10
Like So:
```
sudo add-apt-repository ppa:audio-recorder/ppa
```
of course run:
```
sudo apt update && sudo apt install audio-recorder
```

---

### Post by #&amp;thj^% on 2021-01-11
Maybe not interested in a PPA addition, so go here: [https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa/+packages](https://launchpad.net/~audio-recorder/+archive/ubuntu/ppa/+packages)
Under " audio-recorder - 3.1.3~focal" click the dropdown.
Next download the "audio-recorder_3.1.3~focal_amd64.deb " and install it.
```
cd /to/donwloaded/.deb
```
Personally, I prefer gdebi over the software center for installing deb files. It is a lightweight application so the installation seems quicker
install "suggestion" dpkg command
```
 sudo dpkg -i path_to_deb_file
```

If you want to use the apt command for deb files, use it like this:
```
sudo apt install path_to_deb_file
```

If you get a dependency error while installing the deb packages, you can use the following command to fix it:
```

sudo apt install -f
```
Good Luck Old Jimma ;) I aslo included a screen shot to help if needed
If you followed this you won't receive automatic updates as you would with the PPA.

---

### Post by HermanAB on 2021-01-11
OK, I don't know what you want to do with the recorder, but note that *sox* offers two utilities called *play* and *rec*, which make recording and playback from the command line very easy indeed.

---

### Post by Old Jimma on 2021-01-13
Thanks to fallen1 and HermanAB for their replies!!

I had luck with fallen1's suggestion of downloading the deb file and using > sudo dpkg -i path_to_deb_file

Fallen1, will the amd version work with a computer with intel architecture? I have one of those that is being repaired now and will want to install audo-recorder on it.

Thanks!
Old Jimma

---

### Post by Holger_Gehrke on 2021-01-13
> **Old Jimma said:**
> Fallen1, will the amd version work with a computer with intel architecture? I have one of those that is being repaired now and will want to install audo-recorder on it.

Yes, it will. The 64 bit extension to the x86 architecture is called amd64 because both Intel and AMD had different ways of expanding x86. The Intel way of doing this (Itanium) failed in the market, so most x86 processors available today - even those made by Intel - use the extensions by AMD. I think you would know about it if you had a system based around an Itanium processor, those are very unusual and AFAIK only ever used in servers.

Holger

---

