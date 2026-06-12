---
title: "Running x-executables &amp; I cant download from the Ubuntu Software Centre"
date: 2015-10-08
forum: General Help
---

### Post by gareth-ward on 2015-10-08
Hi everyone,

I'm extremely new to all this so please go easy. Right, for a bit of background I have Ubuntu-Desktop running off my ChromeBook using crouton, I wanted to download an emulator for the NES. So I went the the Emuparadise website and downloaded the Rocknes emulator, which came zipped, inside was three files one being the "rocknes" file which is a x-executable. So my question is, how do I run this?

Also I cant seem to download anything from the Ubuntu software centre, the "buy" or "install" button is simply greyed out.

Thanks,
Gareth

---

### Post by v3.xx on 2015-10-08
> Also I cant seem to download anything from the Ubuntu software centre, the "buy" or "install" button is simply greyed out.


Try an update in terminal and post any errors.

```
sudo apt-get update
```

Also check the software center again, sometimes this will fix it.

---

### Post by gareth-ward on 2015-10-08
Updated without any issues but still not working :/

---

### Post by gareth-ward on 2015-10-08
[IMG]http://i.cubeupload.com/SJ5kuo.png[/IMG]
The install button usually located at the right (I know its now here at the minute) is simply grey and I can't click on it :/

---

### Post by v3.xx on 2015-10-08
Ok, no problem with a update.  Try a different package manager, see if it will work.

```
sudo apt-get install synaptic
```

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

Some other options

[http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html](http://www.datamation.com/open-source/the-death-of-ubuntus-software-center.html)

---

### Post by gareth-ward on 2015-10-08
Synaptic works like a charm, thank you very much! Now how do I run this x-executable file? thanks again for helping :)

---

### Post by v3.xx on 2015-10-08
Ok, halfway there :D

If you will post the download link to the package I can give it a try.

---

### Post by gareth-ward on 2015-10-09
Oh thanks man :) [http://www.emuparadise.me/Nintendo_Entertainment_System_Emulators/Linux/13](http://www.emuparadise.me/Nintendo_Entertainment_System_Emulators/Linux/13) Its just a NES emulator for Linux. Thanks again!

---

### Post by v3.xx on 2015-10-09
To me, this emulator looks old and unmaintained.  I cannot get the executable file to open.

Have you looked at other options?  There is Ubuntu supported emulation software.  Open your new package manager and do a search on "Nintendo".

also

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=game+emulators&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=game+emulators&sa=Search&cof=FORID:9)

---

