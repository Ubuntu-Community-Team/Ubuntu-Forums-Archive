---
title: "nvidia driver issue with feisty"
date: 2007-05-25
forum: General Help
---

### Post by emid on 2007-05-25
I had been having problems updating to the newest nvidia driver in the update manager.  I read somewhere to remove the current installed driver and then try to upgrade.  After removing the driver I couldn't install the new driver.  When I tried to reinstall the old one I got an error.  The result was a broken X.

My previous driver was the nvidia-glx and I was trying to install the nvidia-glx-new.

I have a 7600GT.

Here is what I get I try to install the nvidia-glx-new driver:

```

Unpacking nvidia-glx-new (from .../nvidia-glx-new_1.0.9755+2.6.20.5-16.28_amd64.deb) ...
dpkg-divert: `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new' clashes with `diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.28_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-new_1.0.9755+2.6.20.5-16.28_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If anyone could point me in the right direction I would really appreciate it.

---

### Post by Darkriser on 2007-05-25
What about trying the nVidia's proprietary driver? It works great for my card (6600 series).

Navigate [this thread]("http://ubuntuforums.org/showthread.php?t=263851") and follow STEP 2 -> Option 2.

Very easy and works for me!

Marcel

---

### Post by emid on 2007-05-25
I don't think that's going to do it, because I've already reinstalled the driver from nvidia's website.  My xorg.xonf says it is using the nvdia driver, but I still can't get beryl to work like it did before I tried to force the upgrade.

Any suggestions?

---

### Post by fraCPH on 2007-07-02
Hi emid, did you manage to solve your problem ?
I'm still working with "nv" drivers as I get the same error message you got while trying to install the nvidia-glx-new drivers and to remove the residual config of nvidia-glx.

---

### Post by Npl on 2007-07-02
NV drivers come in 2 parts, one is the nvidia-glx-new/nvidia-glx/nvidia-glx-legacy component, the other is something closely related to the kernel (AFAIR that component is provided by the linux-restricted package).

nvidia-glx-new aint working with the the component in the restricted package that ubuntu provides, you need to compile it yourself (and each time you install a new kernel revision it could potentially break - so you should recompile it anew each time you upgrade kernel).

I somehow got it finally working with [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"), but be aware that Envy alone just destroyed my previously working Nvidia driver and i had to run the X-Server with fallback drivers. I cant reproduce the steps I did until it finally worked, it was a great mess and I succeded by accident/luck and not because of knowledge.

---

### Post by fraCPH on 2007-07-02
Actually I believe that you need to re-compile the drivers upon installing the new kernel ONLY if you installed the drivers through ENVY or through the binary .run package supplied by the NVIDIA web site  (which is the same, I think).
If you install the nvidia-glx-* drivers with synaptic they should automatically update together with the new kernel, but here the problem is that I CANNOT install nor uninstall them, and the same happens if I try with envy, I always get the same "dpkg-divert" error.

---

### Post by Npl on 2007-07-02
> **fraCPH said:**
> Actually I believe that you need to re-compile the drivers upon installing the new kernel ONLY if you installed the drivers through ENVY or through the binary .run package supplied by the NVIDIA web site  (which is the same, I think).
If you install the nvidia-glx-* drivers with synaptic they should automatically update together with the new kernel, but here the problem is that I CANNOT install nor uninstall them, and the same happens if I try with envy, I always get the same "dpkg-divert" error.the nvidia-glx-* package aint the problem, the files installed with the linux-restricted package are (as they dont seem to fit together with nvidia-glx-new). At least they were for me, but I just realise now that I had no problem **installing** the package - just the X-Server wouldnt start and provide me a cryptic error-message instead.

Maybe the modules are still in use and cant be deinstalled cause of that? Did you try setting X to run with Vesa/nv, reboot and then uninstall the driver?

---

### Post by fraCPH on 2007-07-02
Well, actually my X already runs with nv drivers, however Synaptic is telling me that there is a residual config of nvidia-glx but does not allow me to remove it totally giving me the same error I get when trying to install it.

```
fra@fra-desktop:~$ sudo dpkg --purge nvidia-glx
Password:
(Lettura del database ... 161851 file e directory attualmente installati.)
Rimuovo nvidia-glx ...
Elimino i file di configurazione di nvidia-glx ...
rm: impossibile rimuovere `/usr/lib/libGL.so': Nessun file o directory
dpkg-divert: mancata corrispondenza nel pacchetto
  durante la rimozione di `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx'
  è stato trovato `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: errore processando nvidia-glx (--purge):
 il sottoprocesso post-removal script ha restituito un codice di errore 2
Sono occorsi degli errori processando:
 nvidia-glx

fra@fra-desktop:~$ sudo apt-get install nvidia-glx
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso       
Lettura delle informazioni di stato in corso... Fatto
I seguenti pacchetti NUOVI (NEW) saranno installati:
  nvidia-glx
0 aggiornati, 1 installati, 0 da rimuovere e 8 non aggiornati.
È necessario prendere 7995kB di archivi.
Dopo l'estrazione, verranno occupati 23,8MB di spazio su disco.
Get:1 http://security.ubuntu.com feisty-security/restricted nvidia-glx 1:1.0.9631+2.6.20.5-16.29 [7995kB]
Scaricato 7995kB in 41s (191kB/s)                                                                                                                           
Selezionato il pacchetto nvidia-glx, che non lo era.
(Lettura del database ... 161852 file e directory attualmente installati.)
Spacchetto nvidia-glx (da .../nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_amd64.deb) ...
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx' è in conflitto con `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-new'
dpkg: errore processando /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_amd64.deb (--unpack):
 il sottoprocesso pre-installation script ha restituito un codice di errore 2
Sono occorsi degli errori processando:
 /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Npl on 2007-07-02
try ```
sudo apt-get remove nvidia-glx*
```


you could also try disabling the glx-module (if loaded) - remove or put a # in front of the line```
Section "Module"
...
#  Load "glx"
```

other than that, i have no idea how to solve it.

---

### Post by DeleiMaciel on 2007-07-02
Hi all...
I'm with some troubles with my nvidia card. And looking for some solution on the brazilian Ubuntu Feisty forum, I met some other guys (from Brazil and Uruguay, and maybe some other places) who have the same problem with the same graphic card. 
My nvidia card is a "Nvidia GeForce FX 5200 - 128 MB - AGP 8X"   and I'm using the Ubuntu 7.04 with the newest update.

My problem is: when I start, the Ubuntu load perfectly, but when I'm wainting for the gdm screen, I hear the drums but the screen just don't appear! When I tried something like "Crtl + Alt + F1" and back to X with "ctrl + alt + F7" the gdm screen is there!! If I don't do this, but change the resolution with "crtl + alt + Nun + or -" the gdm appears too. If I login and try something who use the 3D acceleration, the pc just freeze!!! And I go to the "reset" button... :(

My first solution:
I've uninsttaled all nvidia drivers and install it again with 'aptitude'... So... my driver is nvidia-glx-new (that 1.0.9755) ... and I read a lot of Readme files and other documention in a lot of places... and find something saying to "disable the DRI module" 'cause this module "don't work in some graphic cards". Then I did it. With dpkg-reconfigure xserver-xorg, I disabled the DRI module. When I restart my computer, the gdm´s screen appears in the same time as i listen the drums the drums, and the 3D acceleration was working fine!! XD

And now:
A week ago I updated the sistem (and I'm sorry for that...) and I went back to the original problem... The 'nvidia-glx-new' package has been updated too, I guess...
I try uninstall and reinstall the drivers... but it just don't work anymore.

Friends, I'm a Biologist... I know more about frogs than about computers! :D
I'm just a single user!! I even know what is that DRI thing or if my AGP 8X works properly on my machine... :/

I've spent some nights on this... And a any help will be really really welcome... and it will help a lot of people...
If any other information would be necessary, please ask me.

Thanks for the chance!
And forgive me for my english...

---

### Post by fraCPH on 2007-07-02
I finaly managed to remove the residual config of nvidia-glx by typing 
```
dpkg-divert --list

```
and then one by one removing the diversions like this:
```
sudo dpkg-divert --remove /usr/lib32/libGL.so.1.2
```

However the problem remains when trying to re-install the drivers as it seems that nvidia-glx and nvidia-glx-new are both trying to rename their own libraries into a single file which causes a clash (sorry but I hardly understand it, cannot explain better than this).

---

