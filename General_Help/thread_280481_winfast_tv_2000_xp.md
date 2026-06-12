---
title: "winfast tv 2000 xp"
date: 2006-10-19
forum: General Help
---

### Post by feest on 2006-10-19
hi, i have a winfast tv 2000 xp tv tuner card but i cant get it to work under linux. i'ver tried several tv tuners but it just won't work.

my gamecube (connected through the composite port) does work (how strange) but it cannot find any channel on coax, can sombody help me with this?

---

### Post by mazirian on 2006-10-19
That card requires the bttv module. Have you loaded it?  I have the same card and it dsoes work, so unless your card is dead, it should work under linux perfectly well.  I can post further details later.

---

### Post by feest on 2006-11-16
bttv what? what is it, where can i download it?

---

### Post by mazirian on 2006-11-16
It's in your kernel already!  Just modprobe it  :)

You will need to pass it some arguments.  This is best done by creating the file /etc/modprobe.d/bttv with the following contents:

```

options bttv card=34 tuner=2 radio=1 gbuffers=4

```

---

### Post by feest on 2006-11-17
??????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????????

so what code do i need to enter and what's modprobing? can you give a step by step tutorial?

---

### Post by mazirian on 2006-11-17
The man page for modprobe is very detailed, please do read it to understand what and why you are you doing what I describe below.  That's the nice thing about linux, the documentation is built in. While you are at it, read these man pages too: modules,  modprobe.conf, modules.dep, modinfo, and lsmod.

Ok, now check to see if you already have the bttv module loaded (perhaps it is loaded but it did not properly autodetect your tvcard or perhpas it is loaded with incorrect options).  

```

lsmod | grep bttv

```

If you get nothing, the module is not loaded.  If the command instead returns bttv or tuner, you'll need to remove those modules before going further:

```

sudo rmmod bttv

```

Most debian systems have some magic in /etc/modules.conf that automatically removes the tuner module if you remove the bttv module.  Check to see if that worked:

```

lsmod | grep tuner

```

If the tuner module is still loaded, remove it with rmmod just as you did for bttv above.

The options needed to make this card work have changed recently due to changes in the kernel.  I am still using options that worked for me several kernel versions ago under gentoo in the 2.4 kernel tree, so I don't know that they are the best, but I do know that they currently work for me. Some of the options are related to compatibility with my video card.  You may need to research what options you need.  IN any event, to load the bttv modules with my options, enter the following command:

```

modprobe bttv card=34 tuner=2 radio=1 gbuffers=4

```

Now check to see that the modules loaded correctly:

```

dmesg

```

(By the way, now would be a good opportunity to look at dmesg's man page) You should see some stuff in there that reflects the bttv and tuner modules gettinbg loaded.  If you get error messages instead, let me know what they are.  If the tuner module did not get loaded automatically, load it now.

Assuming the bttv and tuner modules loaded properly, you want to test them now.  Try running tvtime or something.  If they are loaded but things are still not working, you may want to try loading the bttv module with different options.  Remove the tuner and bttv modules then reload with different options, all as described above.

Once you have it working, you'll want the bttv module to load correctly on each boot. Check /etc/modules and see if the bttv modules is listed there.  If not, add bttv on its own line.  Next, create the file in /etc/modprobe.d/ that I described in my previous post, using whatever modules options worked for you.

There is bttv faq somewhere that is helpful for playing with bttv options.  Good luck.

---

### Post by feest on 2006-11-17
```
sven@sven-desktop:~$ lsmod | grep bttv
bttv                  164304  1 bt878
video_buf              22148  1 bttv
i2c_algo_bit            9608  1 bttv
v4l2_common             6016  1 bttv
btcx_risc               5128  1 bttv
tveeprom               15248  1 bttv
videodev                9856  1 bttv
i2c_core               21904  7 i2c_acpi_ec,nvidia,tuner,bttv,i2c_algo_bit,tveeprom,i2c_nforce2
sven@sven-desktop:~$
```

this is what i get, so is it installed already or do i do something new?

---

### Post by mazirian on 2006-11-17
Well, you got to paragraph three of my post anyway....


Here, just make a file in /etc/modprobe.d/ called bttv with the contents specified in my first post and then reboot.  Your card should work.

---

### Post by Jongi on 2006-11-17
When you use the tv tuners, do you set them to the frequency range of your country?

---

### Post by mazirian on 2006-11-17
Ah good point, but that's the thing with this card. There are several variants of it.  Some are NTSC compliant only, some are PAL compliant only and some can do both formats; some can do tv stereo audio and some can not.
So, if feest is in europe, he wants to use PAL (probably), or if he is in the US, NTSC.  

The bigger problem with this card is that it is often not correctly autodetected, which is why you often have to set options in the kernel module for card, tuner, radio, etc.

feest, where are you located, that will determine what tuner setting to use.  For PAL  use tuner=5 and for NTSC use tuner=2.  I think...

---

### Post by feest on 2006-11-18
feest is in europe, i'm dutch but what contents should in that file now?

---

### Post by mazirian on 2006-11-18
I don't know.  The Netherlands use PAL (tuner=5, which is the default for the bttv module). The Netherlands Armed Forces Network (whatever that is) uses NTSC as we do here in the US (tuner=2).  Trial and error is a good thing.

---

### Post by feest on 2006-11-19
yeah but how do i activate that module

---

### Post by mazirian on 2006-11-19
It's getting loaded automatically on boot, just add the file I describe to /etc/modprobe.d/ and it will get loaded with options you put in the file.  After you reboot, run the dmesg command and see what messages were generated when the module loaded.  There should be something in there about the tuner modules .

---

### Post by feest on 2006-11-22
can you give me the file in one pease please beacuese i get a bit confused.

---

### Post by drphilngood on 2006-11-22
> **feest said:**
> can you give me the file in one pease please beacuese i get a bit confused.

Try installing TVtime; it has everything you mentioned you need and works well with your card.(I have the same card and use it)
```
sudo aptitude install TVtime
```

---

### Post by feest on 2006-11-22
well actually it doesn't recieve crap so maybe i have to try another cable

---

### Post by drphilngood on 2006-11-22
> **feest said:**
> well actually it doesn't recieve crap so maybe i have to try another cable

If you don´t get the ¨video source¨ and ¨Television standard¨ set correctly, it may seem like a bad cable.

---

### Post by mazirian on 2006-11-22
@drphilngood:  He has to have the bttv module set up correctly before he can get tvtime to work.  He may have already.  I don't know.  The bttv module is lame about correctly autodetecting this card.  It often needs to be fed module options to work correctly.

@feest:  On the other hand, the bttv module usually does autodetect correctly with people who need a PAL compatible tuner. I didn't realize you were ina PAL region initially. You might try starting tvtime, and using it's configuration interface to select PAL as opposed to NTSC or whatever.  If that works, great.  If not, the contents of the /etc/modprobe.d/bttv file are exactly as I put them to you in the several posts above.  That's it.  Just a single line  For PAL, you generally want to try tuner=5, and if that doesn't work, try tuner=2.  The other options ensure that the radio works and may be useful in getting a better picture quality.

---

### Post by feest on 2006-11-22
well i don't understand anythinng from that module so i didn't changed anything to that because i don't know what to change.

the settings adjust but it doesn't find any signal. no on M$ windows the quallity was also crap so maybe i have a lame cable. but if you can help me with that module please because i dont know what to do with it (or even what it does)

---

### Post by drphilngood on 2006-11-26
> **mazirian said:**
> @drphilngood:  He has to have the bttv module set up correctly before he can get tvtime to work.  He may have already.  I don't know.  The bttv module is lame about correctly autodetecting this card.  It often needs to be fed module options to work correctly.

My bad.  From this statement:

¨can you give me the file in one pease please beacuese i get a bit confused.¨

I thought he wanted someone to recommend a program and since I have the same tuner and TVtime auto-detected everything for me, I thought it  was a good choice.

Please excuse my ignorance, I´ll leave you two to it.

Good luck!

---

