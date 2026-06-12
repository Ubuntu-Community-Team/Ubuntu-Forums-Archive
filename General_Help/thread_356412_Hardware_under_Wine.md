---
title: "Hardware under Wine"
date: 2007-02-08
forum: General Help
---

### Post by ashmew2 on 2007-02-08
HI guys , I would like to know that is there anyway by which wine will detect my Graphic Card (GeForce MX 4000) , I mean for example  , If i want to say install the nvidia drivers under wine (/home/.wine/drive_c/ <== im talking about this environment) i need to first of all get wine to detect that graphic card. Is it possible ? 
Thanks

---

### Post by MoLE on 2007-02-16
Wine doesn't work that way.  If you need graphics acceleration, you need to install the nvidia-glx package on your ubuntu system.  Wine can then translate the DirectX instructions for your 3d application into native X-server instructions.  Just install the application under Wine, but check the application database at appdb.winehq.org.

---

### Post by ashmew2 on 2007-02-16
> **MoLE said:**
> Wine doesn't work that way.  If you need graphics acceleration, you need to install the nvidia-glx package on your ubuntu system.  Wine can then translate the DirectX instructions for your 3d application into native X-server instructions.  Just install the application under Wine, but check the application database at appdb.winehq.org.

Ive already installed the nVidia driver on my ubuntu system (using the great script , ENVY) , and the game i want to run "Wolverine's Revenge" has no info at the site u told me (it requires 3D ACCELERATION). Now what shud i do ?

---

### Post by MoLE on 2007-02-16
Well, the next step would be to run the game installer using wine.  Put the game disc in the drive and browse the contents.  You should find something like ```
setup.exe
```.
Then execute from the terminal:
```
wine /media/cdrom/setup.exe
```
And see if the game installs.

Given that the game isn't in the Wineapp database, you should consider entering it into the database and posting your  results of trying to get it running.  This helps others who may be in the same situation as you, as well as aiding the development of Wine.

---

### Post by ashmew2 on 2007-02-17
Hey Mole , thanks for replying to me 
Butive already tried installing it from the CD , it installs fine but when i go to play it ..
"The game requires 3D Acceleration to run , It will now CLose"

Hmmmz ? ANy ideez?

---

### Post by meng on 2007-02-17
wine is not a perfect answer to playing Windows games. cedega is better, but still a long way from perfect. If you need to play Windows games, particularly ones that are not very recent or extremely popular, you may have to keep some version of Windows.

---

### Post by ashmew2 on 2007-02-17
awwww..... :'(
I ve tried Cedega also for WOlverine's REvenge but no luck , guess i will have to live with CS (Counter Strike) until a decent 3d acceeration nvidia driver or sumtin is released  ,
THanks

---

### Post by MoLE on 2007-02-17
> **ashmew2 said:**
> 
 i will have to live with CS (Counter Strike) until a decent 3d acceeration nvidia driver or sumtin is released

Wine and it's derivatives have no need of a nvidia driver.  Wine is NOT an emulator - it's a translation layer.  In basic terms, it translates Win32 API system calls to their Unix equivalents. 

In this case, it seems that the game does a check for 3d-acceleration capability before loading.  To see what is happening 'under the hood', run wine with the debug options enabled, thus:

```
$ WINEDEBUG=all wine /path/to/wolverine's revenge/program_name
```

You can then check the output for references to 3d calls and work out what the missing functionality is.  The Wine folks offer some [great support options]("http://www.winehq.com/site/getting_help").  You should be able to find someone to help you interpret the output there.  Don't forget to post your findings in the [application database]("http://appdb.winehq.org/") to help the next person with the same problem.

---

### Post by ashmew2 on 2007-02-18
Man MoLe!! , Ur a life saver :) , I'll get back here as soon as i try it , Thanks!!

---

