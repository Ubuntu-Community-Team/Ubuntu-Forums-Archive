---
title: "burn an .uif image?"
date: 2007-07-30
forum: General Help
---

### Post by tubunu on 2007-07-30
This is the first time I've come across an .uif extension. I'd like to burn a CD with .uif image, how do I go about that? Does K3B support it?

---

### Post by sanone on 2007-07-30
It is an MagicISO format (which is a windows based burning program)...

There are currently no convertion tools availible but you can use MagicISO with Wine according to this post: [http://ubuntuforums.org/showthread.php?t=482963](http://ubuntuforums.org/showthread.php?t=482963)

Please do a little search on this youself the next time!

Cheers,
San

---

### Post by tubunu on 2007-07-30
Thanks!

---

### Post by lixy on 2007-08-10
> **sanone said:**
> 
Please do a little search on this youself the next time!


Cut the guy some slack. It was a fair question.

Anyway, for all you guys out there looking to burn a uif, MagicIso didn't wanna run on my system with either Wine or Crossover 6.0. It installs just fine, but running it pops up a fatal error window.

---

### Post by lixy on 2007-08-10
Ok. This uif business sucks. Magiciso isn't freeware anyway. I tried it under Windows, and it wouldn't let me burn files of over 300 megs (i.e: anything useful).  There are torrents of cracked copies out there, but they are filled with trojans and not worth bothering.

My advice: Next time you run across a uif, dump it in the trash.

---

### Post by tombott on 2007-10-09
UIF do suck.
However with MagicIso you can convert the UIF to an ISO and then burn using k3b, Gnome Baker, Nero etc.
I have just done this with a 2gb+ file no problems.

Tom

---

### Post by fmbugdadi on 2007-12-30
Well, looks, like I am going to have to do, what I did not want to do, and that is, resort to windows to burn an UIF file to an image that K3B can burn. I don't have any experience with WINE or CROSSOVER, and even if I did, I have heard multiple reports, that magic iso does not work with either APP. ..

---

### Post by siralphred on 2008-01-06
poweriso for linux can convert .uif images to iso

Example: Convert /home/sam/test.daa to standard iso file
Command: poweriso convert /home/sam/test.daa -o /home/sam/test.iso -ot iso

---

### Post by tanas on 2008-01-22
I just converted an uif to iso using MagicIso through Wine. Everything just ran perfect! Amazing.

So I just downloaded the .exe from Magiciso, double-clicked to open it with wine. 
Then you get usual Windows intallation routine (it gave the creeps, hadnt seen that for quite a while).
And then run it from the wine menu in the main menu.

---

### Post by koesti75 on 2008-02-09
I found the solution to convert the uif file into iso.

[http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#uif2iso](http://wiki.linuxquestions.org/wiki/CD_Image_Conversion#uif2iso)

Simply download the tool, extract and change into the folder. There you type to install:
$ sudo make install

And from now on you can use the commandline to convert .uif files as follows:
$ uif2iso input_file.uif output_file.iso

Done!
:-)

---

### Post by zami on 2008-02-20
I was having a hard time "making this go", so THANK YOU to you all for pointing out the program, and describing the various ways your compiled and converted.  Thank you thank you thank you!

-zami

---

### Post by rare HERO on 2008-02-23
not having any success with uif2iso

tried following instructions:
> Compile it using 'make', this will generate the uif2iso executable.
If you want to install it type 'make install' or just copy the
executable where you want since it's the only file you need.
The only requirement for compiling and using UIF2ISO is zlib (apt-get install zlib1g zlib1g-dev).
Using it then it's simple, just specify the input file and the ISO
file you want to create like the following example:
  uif2iso "my file.uif" output.iso


```
$ make
cc uif2iso.c -O2 -s -o uif2iso -lz

```

```
$ ./uif2iso  file.uif file.iso

UIF2ISO 0.1.2
by Luigi Auriemma
e-mail: aluigi@autistici.org
web:    aluigi.org

- open file.uif
- create file.iso

  file size    000000002042ce0b
  version      1
  image type   8
  padding      0
  sectors      285550
  sectors size 2048
  blhr offset  00000000204270a0
  blhr size    23915
  hash         269c6f68f845fc49a47cf174c30fe00a
- start unpacking:
  100%
- 0x0000000022db7000 bytes written

```

Make sure that you are in the folder w/ the file in question.

---

### Post by Paulo Wageck on 2008-02-23
uif2iso

BEST CHOICE!

just make shure u install zlib before compiling it..

---

### Post by Rat-Boy on 2008-02-29
HELP HELP HELP...
yea... i'm one of this annoying nooobs but i'm short before freacking out totally and run amok...
i'm using KUBUNTU an a laptop....
...i downloaded uif2iso and the source code went into the dir. and typed "make" -> this appeares (also if i use sudo if this makes any difference):

```
cc uif2iso.c -O2 -s -o uif2iso -lz
uif2iso.c:28:19: error: stdio.h: No such file or directory
uif2iso.c:29:20: error: stdlib.h: No such file or directory
uif2iso.c:30:20: error: string.h: No such file or directory
uif2iso.c:31:20: error: stdint.h: No such file or directory
uif2iso.c:32:18: error: zlib.h: No such file or directory
uif2iso.c:41: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u8
&#8217;
uif2iso.c:42: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u1
6&#8217;
uif2iso.c:43: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u3
2&#8217;
uif2iso.c:44: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;u6
4&#8217;
uif2iso.c:66: error: expected specifier-qualifier-list before &#8216;u32&#8217;
uif2iso.c:73: error: expected specifier-qualifier-list before &#8216;u64&#8217;
uif2iso.c:81: error: expected specifier-qualifier-list before &#8216;u32&#8217;
uif2iso.c:100: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*
&#8217; token
uif2iso.c:101: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:102: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:103: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:104: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:108: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:109: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:110: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c: In function &#8216;main&#8217;:
uif2iso.c:121: error: &#8216;z_stream&#8217; undeclared (first use in this function)
uif2iso.c:121: error: (Each undeclared identifier is reported only once
uif2iso.c:121: error: for each function it appears in.)
uif2iso.c:121: error: expected &#8216;;&#8217; before &#8216;z&#8217;
uif2iso.c:125: error: &#8216;FILE&#8217; undeclared (first use in this function)
uif2iso.c:125: error: &#8216;fdi&#8217; undeclared (first use in this function)
uif2iso.c:126: error: &#8216;fdo&#8217; undeclared (first use in this function)
uif2iso.c:127: error: &#8216;u64&#8217; undeclared (first use in this function)
uif2iso.c:127: error: expected &#8216;;&#8217; before &#8216;tot&#8217;
uif2iso.c:132: error: &#8216;u8&#8217; undeclared (first use in this function)
uif2iso.c:132: error: expected &#8216;;&#8217; before &#8216;ans&#8217;
uif2iso.c:138: error: &#8216;stdout&#8217; undeclared (first use in this function)
uif2iso.c:138: error: &#8216;NULL&#8217; undeclared (first use in this function)
uif2iso.c:160: warning: incompatible implicit declaration of built-in function &#8216;
printf&#8217;
uif2iso.c:166: error: &#8216;filei&#8217; undeclared (first use in this function)
uif2iso.c:167: error: &#8216;fileo&#8217; undeclared (first use in this function)
uif2iso.c:169: warning: incompatible implicit declaration of built-in function &#8216;
printf&#8217;
uif2iso.c:178: error: &#8216;ans&#8217; undeclared (first use in this function)
uif2iso.c:178: error: &#8216;stdin&#8217; undeclared (first use in this function)
uif2iso.c:184: error: &#8216;z&#8217; undeclared (first use in this function)
uif2iso.c:184: error: &#8216;alloc_func&#8217; undeclared (first use in this function)
uif2iso.c:184: error: expected &#8216;;&#8217; before numeric constant
uif2iso.c:185: error: &#8216;free_func&#8217; undeclared (first use in this function)
uif2iso.c:185: error: expected &#8216;;&#8217; before numeric constant
uif2iso.c:186: error: &#8216;voidpf&#8217; undeclared (first use in this function)
uif2iso.c:186: error: expected &#8216;;&#8217; before numeric constant
uif2iso.c:192: error: &#8216;SEEK_END&#8217; undeclared (first use in this function)
uif2iso.c:193: error: &#8216;file_size&#8217; undeclared (first use in this function)
uif2iso.c:194: error: &#8216;SEEK_SET&#8217; undeclared (first use in this function)
uif2iso.c:200: error: &#8216;bbis_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:201: error: &#8216;bbis_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:215: error: &#8216;u32&#8217; undeclared (first use in this function)
uif2iso.c:216: error: &#8216;bbis_t&#8217; has no member named &#8216;ver&#8217;
uif2iso.c:217: error: &#8216;bbis_t&#8217; has no member named &#8216;image_type&#8217;
uif2iso.c:218: error: &#8216;bbis_t&#8217; has no member named &#8216;padding&#8217;
uif2iso.c:219: error: &#8216;bbis_t&#8217; has no member named &#8216;sectors&#8217;
uif2iso.c:220: error: &#8216;bbis_t&#8217; has no member named &#8216;sectorsz&#8217;
uif2iso.c:221: error: &#8216;bbis_t&#8217; has no member named &#8216;blhr&#8217;
uif2iso.c:221: error: &#8216;bbis_t&#8217; has no member named &#8216;blhr&#8217;
uif2iso.c:222: error: &#8216;bbis_t&#8217; has no member named &#8216;blhrbbissz&#8217;
uif2iso.c:223: error: &#8216;bbis_t&#8217; has no member named &#8216;hash&#8217;
uif2iso.c:227: error: &#8216;bbis_t&#8217; has no member named &#8216;blhr&#8217;
uif2iso.c:230: error: &#8216;blhr_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:231: error: &#8216;blhr_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:234: error: &#8216;blhr_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:239: error: &#8216;in&#8217; undeclared (first use in this function)
uif2iso.c:239: error: &#8216;out&#8217; undeclared (first use in this function)
uif2iso.c:241: error: &#8216;tot&#8217; undeclared (first use in this function)
uif2iso.c:243: error: &#8216;blhr_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:246: warning: incompatible implicit declaration of built-in function &#8216;
malloc&#8217;
uif2iso.c:246: error: &#8216;blhr_t&#8217; has no member named &#8216;num&#8217;
uif2iso.c:249: error: &#8216;blhr_t&#8217; has no member named &#8216;num&#8217;
uif2iso.c:252: error: &#8216;blhr_t&#8217; has no member named &#8216;num&#8217;
uif2iso.c:255: error: &#8216;blhr_t&#8217; has no member named &#8216;num&#8217;
uif2iso.c:269: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:271: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:272: error: &#8216;blhr_data_t&#8217; has no member named &#8216;offset&#8217;
uif2iso.c:273: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:276: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:276: error: &#8216;bbis_t&#8217; has no member named &#8216;sectorsz&#8217;
uif2iso.c:277: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:279: error: &#8216;blhr_data_t&#8217; has no member named &#8216;type&#8217;
uif2iso.c:281: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:281: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:285: warning: incompatible implicit declaration of built-in function &#8216;
memcpy&#8217;
uif2iso.c:285: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:286: warning: incompatible implicit declaration of built-in function &#8216;
memset&#8217;
uif2iso.c:286: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:286: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:286: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:290: warning: incompatible implicit declaration of built-in function &#8216;
memset&#8217;
uif2iso.c:290: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:294: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:294: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:298: error: &#8216;blhr_data_t&#8217; has no member named &#8216;type&#8217;
uif2iso.c:303: error: &#8216;blhr_data_t&#8217; has no member named &#8216;sector&#8217;
uif2iso.c:303: error: &#8216;bbis_t&#8217; has no member named &#8216;sectorsz&#8217;
uif2iso.c:304: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:305: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c: At top level:
uif2iso.c:369: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*
&#8217; token
uif2iso.c:387: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:396: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:404: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:412: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c: In function &#8216;b2l_blhr&#8217;:
uif2iso.c:430: error: &#8216;blhr_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:431: error: &#8216;blhr_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:432: error: &#8216;blhr_t&#8217; has no member named &#8216;ver&#8217;
uif2iso.c:433: error: &#8216;blhr_t&#8217; has no member named &#8216;num&#8217;
uif2iso.c: In function &#8216;b2l_blhr_data&#8217;:
uif2iso.c:440: error: &#8216;blhr_data_t&#8217; has no member named &#8216;offset&#8217;
uif2iso.c:441: error: &#8216;blhr_data_t&#8217; has no member named &#8216;zsize&#8217;
uif2iso.c:442: error: &#8216;blhr_data_t&#8217; has no member named &#8216;sector&#8217;
uif2iso.c:443: error: &#8216;blhr_data_t&#8217; has no member named &#8216;size&#8217;
uif2iso.c:444: error: &#8216;blhr_data_t&#8217; has no member named &#8216;type&#8217;
uif2iso.c: In function &#8216;b2l_bbis&#8217;:
uif2iso.c:451: error: &#8216;bbis_t&#8217; has no member named &#8216;sign&#8217;
uif2iso.c:452: error: &#8216;bbis_t&#8217; has no member named &#8216;unknown1&#8217;
uif2iso.c:453: error: &#8216;bbis_t&#8217; has no member named &#8216;ver&#8217;
uif2iso.c:454: error: &#8216;bbis_t&#8217; has no member named &#8216;image_type&#8217;
uif2iso.c:455: error: &#8216;bbis_t&#8217; has no member named &#8216;padding&#8217;
uif2iso.c:456: error: &#8216;bbis_t&#8217; has no member named &#8216;sectors&#8217;
uif2iso.c:457: error: &#8216;bbis_t&#8217; has no member named &#8216;sectorsz&#8217;
uif2iso.c:458: error: &#8216;bbis_t&#8217; has no member named &#8216;unknown2&#8217;
uif2iso.c:459: error: &#8216;bbis_t&#8217; has no member named &#8216;blhr&#8217;
uif2iso.c:460: error: &#8216;bbis_t&#8217; has no member named &#8216;blhrbbissz&#8217;
uif2iso.c:461: error: &#8216;bbis_t&#8217; has no member named &#8216;unknown3&#8217;
uif2iso.c:462: error: &#8216;bbis_t&#8217; has no member named &#8216;unknown4&#8217;
uif2iso.c: At top level:
uif2iso.c:467: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:479: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c:493: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
uif2iso.c: In function &#8216;myexit&#8217;:
uif2iso.c:525: warning: incompatible implicit declaration of built-in function &#8216;                   exit&#8217;

```

jep... and now i'm pretty f'**'# cause also my sound doesn't work and my "apt-get install" doesn't work (E: Could not find package .....)and, and, and.

would be quite cool if somebody helps me soon cause on that image is windows and i want to be able to use my computer at least a bit.
AND i wont give up using linux but right now its well annoying me.
THX
:confused: :mad:

---

### Post by kioftes on 2008-03-01
I'm not an expert but it seems you're missing basic c libraries...try

sudo apt-get install gcc

as for the problem with apt-get please give us some more info....

---

### Post by Cerinthus on 2008-06-26
Well, I'm a few months out but might be able to help the next guy.  Your problem isn't that you need gcc, it's that you need libssl-dev.

sudo apt-get install libssl-dev

---

### Post by AngelX on 2008-07-21
For the guys that aren't masters in linux (like myself):

Before using th uif2iso you need the following packages:

 sudo apt-get install build-essential zlib1g-dev libssl-dev 

otherwise you will get the long list of compiler erros.

next do the

make

etc, etc, etc.

---

