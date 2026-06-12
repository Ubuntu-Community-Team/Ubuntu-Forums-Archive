---
title: "Running an old DOS program in Virtualbox"
date: 2015-03-14
forum: General Help
---

### Post by KayeNg on 2015-03-14
Hi guys.  We have a really old DOS program that I want to try on Virtualbox.  I've already installed Virtualbox and added FreeDOS operating system to the virtual drive.  How do I run the old DOS program in my FreeDOS?

Just to give you a little info about the program, when I'm running Windows, all I have to do is copy an entire folder containing EVERYTHING relating to that program, into my (non-virtual) C: drive.  I then open command prompt and navigate to that folder and execute the .exe file to run the program.

How do I do that if the C: drive is virtual?

Thank you for your time.

---

### Post by andrew.46 on 2015-03-14
What is the name of the DOS program?

---

### Post by CaptainMark on 2015-03-14
^^ +1 
Name of the program would be good to know.

Generally Virtual Box doesn't see host files, you can override this but it's not recommended.
Sounds like you might be trying to flash a bios, that the only reason I can think off-hand why you would need to do this, if that's the case it can be done from a live CD more easily and a Freedos live cd can be made very easily with Unetbootin

---

### Post by KayeNg on 2015-03-14
Thanks for your responses guys.  Name of the program? I'm not sure what you mean by that, but in the command prompt of Windows, I just navigate to the directory and type something like "myprogram" because it's the one with the .exe extension.  It's a very old program that was written in Clipper back in the 80's.  

It's not a popular software by the way, if that's what your thinking.  It was made by the company's resident programmer.

---

### Post by Holger_Gehrke on 2015-03-14
Are you sure that going with Virtualbox is the right idea ? There is a specialized DOS Emulator named dosbox. You might have to play around with the settings a bit - especially with the speed of the emulated system - but you don't need any virtual drives or drive images with it; it maps directories on the host to drives.

---

### Post by SeijiSensei on 2015-03-14
+1 DOSbox

---

### Post by deadflowr on 2015-03-14
I agree with trying DosBox.
Virtualbox + freedos seems like overkill.

In DosBox, you can mount the path as a drive, if I remember.
So if the path is somewhere in your home folder you would mount that path as the D drive, or whatever drive you can set.

You can also set the mount point in the dosbox configuration folder.
(Which I cannot remember if it is inside .dosbox, or .config/dosbox)
the mount command is basically
```
mount <Choose-a-letter> /path/to/where/ever
```
In more practical terms
```
mount c ~/Downloads
```
will mount your Downloads directory as the c drive in DosBox.

You can add your mount points to a conf file in ~/.dosbox/dosbox-something.conf.
"something" would relate to whichever version of dosbox is installed.

I think the only thing about dosbox that I've read which may be a bit troubling is that  the sound settings can get funky.
But I have not seen this in my limited uses of it.

---

### Post by HermanAB on 2015-03-14
Dosbox or Wine would prolly be better.

---

### Post by kostkon on 2015-03-14
+1 for DOSBox. You can also create a launcher icon for it pretty easily.

---

### Post by deadflowr on 2015-03-15
> **kostkon said:**
> +1 for DOSBox. You can also create a launcher icon for it pretty easily.
I thought it already had one...

---

### Post by KayeNg on 2015-03-15
Hey Holger, you're right about using dosbox.  I'm able to run the program in dosbox but it's very slow, I tried to change the cycles like so: cycles=933000 but loading time is still slow, although a bit improved.  I'm not very good at tweaking cpu, any suggestions? Just to give you an idea, when I'm using the real dos in Windows, loading time takes about 3 seconds, but when I'm using Lubuntu and running the program via dosbox, it takes about 3 to 4 minutes.  
By the way, according to my Lubunto OS's System Profiler and Benchmark, there are four entries.  One is 1466.00 MHz, two are 933.00MHz, and another one is 2533.00 MHz.  If it helps.

Thank you

---

### Post by KayeNg on 2015-03-15
Thanks to other responders as well

---

### Post by Holger_Gehrke on 2015-03-15
dosbox emulates a complete PC (CPU, graphics and sound card) in software and by default tries to match the speed of an original PC-XT.
There should be a file named 'dosbox-<Version Number>.conf' in the directory '~/.dosbox'. Edit this to have the following settings in the section [cpu]:
```

core=dynamic
cycles=max

```
You might also try setting the emulated graphics board to something simple, by putting 'machine=vgaonly' or 'machine=hercules' in the section [dosbox] and to disable sound card emulation with 'mpu401=none' in section '[midi]', 'sbtype=none' in section [sblaster], 'gus=false' in section '[gus]'.

If all that doesn't speed it up to a point where it's usable, you could try dosemu instead of dosbox. dosemu doesn't emulate the CPU, it switches to virtual x86 mode and executes the DOS-program directly. In my experience - from several years ago - it's a bit flaky, only working with well-behaved programs. but with a program written in Clipper it *should* work.

If the source code of the program - you said it was developed in house - is still available, another alternative would be to look for a Clipper compatible compiler for Linux (a quick google shows several) and compile a native Linux version of the program.

---

### Post by KayeNg on 2015-03-15
Holger that's great! It works almost exactly as if I'm running it on Windows.  Then I tried dosemu as well.  The clipper program seems to have a faster startup in dosemu than dosbox, but other than that, they're almost identical.  I like the full screen mode of dosemu better, though.  Thanks a lot!

---

### Post by kostkon on 2015-03-15
> **deadflowr said:**
> I thought it already had one...
Probably I wasn't clear enough; I meant a launcher icon for the DOS application.

But, oh well, problem solved for KayeNg :KS

---

