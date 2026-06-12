---
title: "&quot;No such file or directory&quot; When the file is there"
date: 2007-09-03
forum: General Help
---

### Post by cyberfunk on 2007-09-03
This has been a recurring problem for me on my attempts (i'm on my 4th now !!) to install Ubunutu on a brand new Dell machine.

I'm installing Feisty Fawn , 64 bit version.

What happens, at seemingly random times after I install the operating system is that files will stop executing.  The most recent time around, I thought i'd gotten rid of the problem for good by reinstalling the OS for the third time, but it began manifesting itself as firefox refusing to launch (see: [http://ubuntuforums.org/showthread.php?t=542247](http://ubuntuforums.org/showthread.php?t=542247)).

Unfortunately, this problem is not limited to Firefox, and other programs that i've installed with binary executables visible to me via the file manager and the terminal claim that, when I try to execute them, the files are unable to be found.  I can, of course view the binary contents of the files via less/cat/more/etc.  I am therefore convinced the files EXIST.  Futhermore I am certain that this is NOT a permissions error, as the execute bits are most definately set on these trouble files.  Which files are affected seems to be random.

A typical example is as follows:  

$ ./firefox-bin
bash: ./firefox-bin: No such file or directory
$ less firefox-bin
"firefox-bin" may be a binary file.  See it anyway?


 This is incredibly frustrating for obvious reasons, and has me both baffled and incensed, as the last time around I had just gotten my install perfectly setup with the ATI screen driver, right applications installed, etc, and then this disaster happened. Which made me feel like : ](*,).

At this point i'm very discouraged and scared to try again, lest I get it setup and/or usable and have it break on me like this at some undetermined point in the future.  Does anyone know what might cause this symptom and how to avoid it ?

Thanks very much in advance,

Cyberfunk

---

### Post by cyberfunk on 2007-09-03
One additonal piece of information: i'm not sure if this is linked or not, but the problem did ocurr just after removing the "redundant" ia32 libraries... but, again, i'm not sure if that's linked to the problem.

---

### Post by Foxray on 2007-09-03
do a chmod +x <binary file> and try to run it again.

have u tried just typing "firefox" without the "./"?
it should bring up firefox. If not you've got some underlying problem with your install. Also make sure that you check your installation cd integrity when you boot the live cd.

---

### Post by cyberfunk on 2007-09-03
I did the chmod +x already, but I tried it again for good measure, with no effect.

I've run a CD-check several times, and it checks out fine, and the MD5 hash matches that provided by Ubuntu on the ISO.

It's not just the firefox program.. it's others too, so i'm not sure what's going on.. should I perhaps try reinstalling the ia32 libs ? (I had them installed while I was messing around w/ the ATI 8.40.4 gfx card driver, they were required for the amdccle panel app)

---

### Post by firstone on 2007-09-06
I am a new Linux/Ubuntu user and I am having the same problem with Dynamips Cisco emulator. Although the install was fine and all files are there I get the "bash: /usr/local/bin/dynamips: No such file or directory" message.

Any help would be appreciated...Thanks

---

### Post by xaosist on 2007-09-10
I am also having this problem... is there any solution? any news or anything?

---

### Post by ghantoos on 2007-09-10
can you post the output of```
ls -ls
```of the directory containing the file your are trying to execute?

cheers,

ghantoos

---

### Post by cyberfunk on 2007-09-10
I seemed to have fixed the problem by installing the ia32-libs compatibility libraries for 32 bit binaries in Synaptic.. but I have no idea why this should fix the problem..

---

### Post by xaosist on 2007-09-13
I can confirm what this error is. When running binaries compiled on the 32 bit version of Ubuntu (probably other flavours of linux too) on the 64 bit Feisty Fawn Ubuntu without any compatibility libraries it just gives this error.

After installing the ia32-libs compatibility libraries for 32 bit binaries it gave me a more useful error message detailing what other libraries I was missing for the binary.

In the end I decided to just install the 32 bit Feisty Fawn Ubuntu as I was not using the 64 bit processor myself, and attempts to recompile the program were failing (my first time trying to compile from source)

It would have been nice if the initial error message had been a little more helpful, but it was my fault for not checking the binary was for a 64 bit system!

---

### Post by cyberfunk on 2007-09-15
I agree that this problem is very annoying.. unfortunately, I need to install the 64 bit Ubunutu, as I've got 4 GB Ram, and if I want to use it, I better go 64bit.  Sigh... Wish I could just use Mac OS X all the time..

---

