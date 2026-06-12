---
title: "Raw1394 Issue"
date: 2007-11-19
forum: General Help
---

### Post by siege911 on 2007-11-19
I'm having trouble Capturing video from Kino. I had downloaded and installed all of the UbuntuStudio packages and several other Video Production packages (such as ManDVD, Cinelerra, a few other dvd authoring programs, etc) and it was working great. After I sort of figured out which packages I wanted to use and which ones I didn't, I decided to reinstall Ubuntu. This time I only have installed the UbuntuStudio packages.

I can't capture Video at all. Under Kino -> Preferences -> IEEE 1394, I don't get any errors or anything, but my camera isn't listed.

I did have some issues with the /dev/raw1394 file so I ran:
```
sudo modprobe raw1394
(this got me the file)

sudo chown siege911 /dev/raw1394
sudo chmod 777 /dev/raw1394
(these got me better permissions)

sudo kino
(this was to see if it would work as root)
```


While I can access the raw1394 file and it appears I have proper access, I still can't seem to access the capture.

As I said, under Preferences, there is no error, but when I go to the Capture button to get my video, at the bottom it says:
```
Warning: raw1394 kernel module not loaded or failure to read/write /dev/raw1394!
```

I'm no linux expert but I'm fairly certain it's not a permissions thing.

What am I doing wrong?

---

### Post by siege911 on 2007-11-19
help...:(

---

### Post by ddennedy on 2007-11-20
try modprobe ohci1394

If it still does not work, maybe dmesg | grep 1394 will reveal something; this shows recent kernel messages related to IEEE 1394.

---

