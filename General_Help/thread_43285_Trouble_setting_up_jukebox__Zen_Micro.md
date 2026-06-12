---
title: "Trouble setting up jukebox / Zen Micro"
date: 2005-06-21
forum: General Help
---

### Post by vtechstu on 2005-06-21
I'm trying to follow the directions from [http://gnomad2.sourceforge.net/?section=article](http://gnomad2.sourceforge.net/?section=article) to set up gnomad2.

When I get to this point:
```

chase@ubuntu:~$ sudo cat nomad.usermap >> /etc/hotplug/usb/usb.usermap ;cp nomadjukebox /etc/hotplug/usb/ ; chmod a+x /home/chase/libnjb-2.1.2/nomadjukebox
```


I get this error:
```

bash: /etc/hotplug/usb/usb.usermap: Permission denied
cp: cannot stat `nomadjukebox': No such file or directory
chmod: changing permissions of `/home/chase/libnjb-2.1.2/nomadjukebox': Operation not permitted
```

The webpage says it fixes the bugs in the last version, because i could never get my Zen Micro to work with the HowTo i found on the forum.  Any help would be greatly appreciated

Also,  says this
```

cat: nomad.usermap: No such file or directory
cat: /etc/hotplug/usb/usb.usermap: No such file or directory

```

---

### Post by vtechstu on 2005-06-21
Update:

I've narrowed down that code to this so far:  
```

chase@ubuntu:~/libnjb-2.1.2$ sudo cat nomad.usermap >>sudo /usr/share/doc/hotplug/examples/usb.usermap ;cp nomadjukebox /home/chase/libnjb-2.1.2 ; sudo chmod a+x /home/chase/libnjb-2.1.2/nomadjukebox  

```

the location of some of the files were in different places.  this command now gives me this error:
```

cp: `nomadjukebox' and `/home/chase/libnjb-2.1.2/nomadjukebox' are the same file

```

Thanks if you could help!!

---

