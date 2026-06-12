---
title: "Wine sound help"
date: 2006-11-01
forum: General Help
---

### Post by BillGod on 2006-11-01
I know this has been posted before and I have tried everything that resolved other issues but I cannot seem to get this to work.  I cannot get sound in wine.  

When I run winecfg and click on audio it crashes and in the terminal window I get this error.

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack


I have checked the repositories I have added and the only jack i found was this one. libjack0.100.0-0  

I installed that package but still have no libjack.so

Per this thread [http://ubuntuforums.org/showthread.php?p=282154&mode=linear](http://ubuntuforums.org/showthread.php?p=282154&mode=linear)  I should be able to modify my wine config file.  My wine.inf file looks nothing like that one.

So I am stuck and dont really know how else to fix this issue.  Does anyone have any ideas?  The last thing on my list to convert to Linux was get diablo2 working.  The game is now playable but no sound... not a great loss.  how many times can you hear "not even death can escape you from me" anyway.  But I would like to get it working.

Thanks
Bill

---

### Post by LeslieL on 2006-11-01
I've had this problem with winecfg too. I have sound working in Crossover Office, but that's a commercial application. I do recommend it, though.

---

### Post by bolt212 on 2006-11-01
similer to my problem [http://ubuntuforums.org/showthread.php?t=290580](http://ubuntuforums.org/showthread.php?t=290580)

But it doesn't crash,  it freezes up on me and i get a  differn't

---

### Post by BillGod on 2006-11-01
HA I GOT IT!

if anyone else has this problem here is what you do.  Install libjack0.100.0-0 through synaptic.

sudo cp /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so

run winecfg and click on audio.  takes a second then will open.

---

### Post by bolt212 on 2006-11-01
When i try to run vent. after i connect to the server it will freeze up after a few seconds and i get this error

err:wave:wodOpen JACK_OpenWaveOutDevice(9) failed
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(0) failed
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(0) failed
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(1) failed
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(2) failed
err:wave:JACK_OpenWaveOutDevice jack server not running?
err:wave:wodOpen JACK_OpenWaveOutDevice(3) failed

It just keeps repeating over and over.

also,   right as vent starts up i get a bunch of errors 


err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:CoGetClassObject class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
err:ole:create_server class {a910187f-0c7a-45ac-92cc-59edafb77b53} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {a910187f-0c7a-45ac-92cc-59edafb77b53} could be created for context 0x17

---

### Post by noenter1 on 2007-01-30
Umm... cant do this cause permission is denied...

---

### Post by ssavelan on 2007-02-13
noenter1> you are probably not subscribed to this thread; but, did you try executing whatever command with sudo?

ie

sudo command -etc

---

### Post by noenter1 on 2007-03-01
At firt i didnt use sudo, then when i did i got:
```
$ sudo cp /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so
cp: cannot create regular file `/urs/lib/libjack.so': No such file or directory
```

Apperently I had created a libjack.so dir at one time and was interfering with creating a file with the same name. Dont ask why I created a directory for it as I can't remeber.

However even tho I fixed this. I still get:
```
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

---

### Post by josno on 2007-03-01
Should it not be /**usr**/lib/libjack.so?

---

### Post by noenter1 on 2007-03-01
Oh ya I typed that in wrong. Still get the same error when I goto the audio tab in winecfg. And yes i installed the one thru synaptic.

---

### Post by The Pinny Parlour on 2007-03-07
> **BillGod said:**
> HA I GOT IT!

if anyone else has this problem here is what you do.  Install libjack0.100.0-0 through synaptic.

sudo cp /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so

run winecfg and click on audio.  takes a second then will open.

Thanks mate.  That worked for me too

---

### Post by rybec on 2007-03-14
Don't copy /usr/lib/libjack-0.100.0.so.0 to /urs/lib/libjack.so, make a symbolic link.

sudo ln -s /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so

Links are easier to keep track of than extra copies of files.  Also, they use very little
disk space.

(In this case, libjack-0.100.0.so.0 is a just a symbolic link to another file, so it makes
little difference, but it is a good idea to be in the habit of using links when fixing issues with libraries like this.)

---

