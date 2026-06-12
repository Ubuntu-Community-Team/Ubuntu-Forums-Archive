---
title: "slow burning in edgy"
date: 2007-03-10
forum: General Help
---

### Post by pdrift on 2007-03-10
hi, this is my first post in these forms. and yes i'm a noob in linux.

i have been using edgy as my only os on this pc for about 3 weeks.
i'm forcing myself to learn to do things without windows. everything was working great at first but now for some reason whenever i try to burn a cd it takes like 20 min instead of 2 like before. and dvd's take an hour!
what happened? i don't know.

 i get an error that says opc failed. i use gnome baker but now it doesn't even let me burn, so i tried a different program and it burns slow. i been searching but theres tooo many threads. i tried enabling dma for this session but theres no change in speed. 

also, if i get this problem fixed does anyone know how to burn a dual layer disc for data? i'd like to burn some divx movies onto a dl disc. i managed to fit 10 movies in gnome baker but i got an error (and an expensive coaster) 

 one last thing, like i said i am a total noob. i installed from the live cd and used a combination of synaptic, autmaix2 and add/remove under applications to get where i am now. i've heard that automatix breaks system. i was actually thinking about re-installing the live cd again and installing all applications,codecs,libraries,dependencies, and updates manually using the terminal just so i can learn how it works!!!
i like this way better than windows and for the most part everything i need is here. my only need for windows is for my usb capture card and 
to convert video for my psp. other then that, its ubuntu all the way.

---

### Post by nero_86 on 2007-03-10
Type

```
hdparm /dev/hdX
```

where X in the letter of your burner and make sure there is the dma enabled.

---

### Post by pdrift on 2007-03-10
first off, i really appreciate the help. ok heres what is says

pdrift@Pdrift-linuxpc:~$ hdparm /dev/hda

/dev/hda:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device
pdrift@Pdrift-linuxpc:~$ 


just wondering, isn't hd for hard drive, i mean shouldn't my burner 
be called something like /dev/cda  ???

and i see it says dma off.
how do you enable it for good?

---

### Post by nero_86 on 2007-03-10
Enabling the dma on burner is possible whit

```
sudo hdparm -d1 /dev/hdX
```

it have to be similar to

```
/dev/hdd:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 **using_dma    =  1 (on)**
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

```

I don't know any devices named cda... I make a search about this  :-k

---

### Post by nero_86 on 2007-03-10
Sorry for my memory... The change is not permanent. For have dma enabled at every startup you have to modify the hdparm.conf file.

```
sudo cp /etc/hdparm.conf /etc/hdparm.conf_backup
gksudo gedit /etc/hdparm.conf

```
Add the following lines at the end of the file whit the right letter instead of X
```

/dev/hdX {
    dma = on
}
```
or if you prefer (it is the same thing)
```
/dev/cdrom {
    dma = on
}
```
where /dev/cdrom is the link to /dev/hdX. For the burner probably is /dev/cdrw the right link (for me is so).

---

### Post by pdrift on 2007-03-10
thank you i really appreciate your help.
i just burned a cd in less than 2 min.

i still need to modify the hdparm.conf file

---

