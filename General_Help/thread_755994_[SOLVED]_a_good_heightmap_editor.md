---
title: "[SOLVED] a good heightmap editor?"
date: 2008-04-15
forum: General Help
---

### Post by crazyfuturamanoob on 2008-04-15
I need a good heightmap editor.
I have used gimp but I know there
are programs only for making heightmaps.
3D view would be a big +

Edit:
I need the heightmapeditor for making scorched3d maps.

Thanks

---

### Post by crazyfuturamanoob on 2008-04-15
Come on! Why nobody never replies my posts, or
if does, then he replies after half a year!?!?!?!?!?!?
I feel being segregated. :(:(:(:(:(:(

---

### Post by forrestcupp on 2008-04-15
> **crazyfuturamanoob said:**
> Come on! Why nobody never replies my posts, or
if does, then he replies after half a year!?!?!?!?!?!?
I feel being segregated. :(:(:(:(:(:(

We don't like you. :)

Check out [HME - Height Map Editor](http://hme.sourceforge.net/).  They have a linux version.

---

### Post by crazyfuturamanoob on 2008-04-16
> **forrestcupp said:**
> We don't like you. :)

Check out [HME - Height Map Editor](http://hme.sourceforge.net/).  They have a linux version.

You are serious? If so, why?
[size="1"](sorry I don't understand that kind of humour)[/size]


I already found that out myself but I have no clue how to
install it. I tried wine but it didn't open. Then I tried to compile
it with the commands but nothing happened. 

A little help please?

---

### Post by crazyfuturamanoob on 2008-04-16
See? All other topics have been answered, but not mine.:mad: :confused::(
What's the matter???? :confused::confused::confused:

Anyways I need help with running hme on my linux. 
Tell me the instructions how to do it, with all necessary details in.

---

### Post by forrestcupp on 2008-04-16
I was just joking about people not liking you.  That's why I put a :) after what I said.  Why would people not like you?  There are a lot of posts on these forums and everyone who helps is an amateur volunteering his time in his spare time.  No one can really help it if there isn't anyone available who has experience with your specific problem.

But about compiling HME, here is what it says in the linux.txt file that was included.
> I'll assume you do have SDL installed, on your system.

If not, go to: [www.libsdl.org](www.libsdl.org) , and get it.

To compile on Linux (and other Unix clones), you have to:

Edit the file global.h , and comment the  #define WINDOWS line.

Then, use this, in the source directory:

[b]gcc -o terrained -g *.c -lSDL -lpthread
[/b]


Please note that, in order for the program to work, you need the following files 

where the binary program is: font.bmp, icon.bmp, cursors.bmp and toolbar.bmp



I don't have a Linux machine, so I didn't test it on this OS, but some other people did,

and they reported me to work properly. In case you find a bug, please contact me.



Thanks to  Morpius <morpius@ntlworld.com> and  Bussman Alexander <zorax@linux.nu> 

for helping me with the porting stuff. 


So, basically, you start by unzipping the contents of the zip file to its own directory.  Then open the **global.h** file in a text editor and put a **#** in front of the **define WINDOWS** line.  But I opened mine and that was already commented out.  Then you open a terminal and change to the **src** directory in the folder you extracted this to.
```
cd */path/to/hme*/src
```
substituting the correct path to the folder you made.

Then you just type the command they gave you that I bolded.  Like they said, make sure that the binary file that you compile is in the same directory as the bmp files they listed.

You will not be able to compile anything unless you have build-essential installed
```
sudo apt-get install build-essential
```

---

### Post by crazyfuturamanoob on 2008-04-16
> **forrestcupp said:**
> 
[color=red]But I opened mine and that was already commented out.[/color]

Shouldn't it be // in front of the line? not #?

Most lines of that file begin with #, and all comments begin with //,
so should I put // instead of # in front of the windows line?
I don't see any comment in that file that begins with #.

The line wasn't commented with // when I dlled it and opened.

---

### Post by ibuclaw on 2008-04-16
Yes, it should be **//**

Not that I'd suggest that you will run into the same problem.
But I get a "segmentation fault" error after compiling.

[EDIT]
```

:~/hme/src$gdb terrained

(gdb) start
Breakpoint 1 at 0x8051699: file main.c, line 56.
Starting program: /home/iain/Desktop/hme/src/terrained 
[Thread debugging using libthread_db enabled]
[New Thread 0xb7bb68c0 (LWP 15396)]
[Switching to Thread 0xb7bb68c0 (LWP 15396)]
main () at main.c:56
56        Uint32 (*on_screen_pointer) (unsigned int) = on_screen;
(gdb) continue
Continuing.
[New Thread 0xb7c5eb90 (LWP 15489)]
[B]
Program received signal SIGSEGV, Segmentation fault.
0xb7e2d05d in fseek () from /lib/tls/i686/cmov/libc.so.6[/B]
(gdb) backtrace
#0  0xb7e2d05d in fseek () from /lib/tls/i686/cmov/libc.so.6
#1  0x0804cf5b in load_font () at font.c:28
#2  0x08051764 in main () at main.c:67
(gdb) up
#1  0x0804cf5b in load_font () at font.c:28
28	  fseek (f, 0, SEEK_END);
(gdb) print f
**$4 = (FILE *) 0x0**
(gdb) 

```
Looks like I've found a null pointer!!!
So the source needs a little work....

[EDIT2]
```

  FILE *f = NULL;
  f = fopen ("font.bmp", "rb");
  fseek (f, 0, SEEK_END);

```
Oops, the executable wasn't in the right folder.

To compile, use this instead:
```
 gcc -o ../terrained -g *.c -lSDL -lpthread 
```


Regards
Iain

---

### Post by crazyfuturamanoob on 2008-04-17
> FILE *f = NULL;
  f = fopen ("font.bmp", "rb");
  fseek (f, 0, SEEK_END);
Where I have to put this? :roll::?::shock::?:O:);-)

edit: I didn't put that code above into anywhere yet.
What I tried, is:
1. sudo apt-get install build-essential, this asked ubuntu cd
succelsfully installed, i think
2. commented the windows line
3. typed gdb terrained, but I didn't give ANY errors, then it asked for a command
4. I typed the code above, but it said "no such file or dir" 
after the first line, i didn't proceed

I want instructions in a form of the following:
1. do this
2. then do this
3. finally do this

---

### Post by forrestcupp on 2008-04-17
> **crazyfuturamanoob said:**
> Shouldn't it be // in front of the line? not #?



Yeah, that was dumb of me.  It's been a while since I've worked with C/C++ and my mind has been more in the configuration file mode where '#' is used for commenting.  I wasn't thinking about how in C/C++ the # is used for pre-processor commands.  Sorry.

> **crazyfuturamanoob said:**
> Where I have to put this? :roll::?::shock::?:O:);-)

edit: I didn't put that code above into anywhere yet.
What I tried, is:
1. sudo apt-get install build-essential, this asked ubuntu cd
succelsfully installed, i think
2. commented the windows line
3. typed gdb terrained, but I didn't give ANY errors, then it asked for a command
4. I typed the code above, but it said "no such file or dir" 
after the first line, i didn't proceed

I want instructions in a form of the following:
1. do this
2. then do this
3. finally do this
You don't need to put that code anywhere.  Your problem is that after you compile the binary, you need to move the binary file to the same directory as those bitmaps that it listed in the linux.txt file I quoted earlier.  If you don't put it in the same directory, then when you try to run it, it won't be able to find those bmp's that it needs.

---

### Post by crazyfuturamanoob on 2008-04-17
I am a bit confused about all those posts, I'm tired and
just 13, and I don't know english very well,
so could you please give step-by-step instructions?

---

### Post by forrestcupp on 2008-04-17
Ok.  I'll try to make it simple for you.  First, make sure you have the sdl dev files installed that you need:
```
sudo apt-get install libsdl1.2-dev libsdl-image1.2-dev
```

Now let's make a directory called 'hme' in your /home directory:
```
cd ~
mkdir hme
```
Now, unzip the contents of your zip file to that directory.  

**Edit:**
For future reference, I will add that I forgot to show how to comment out the correct line so it will compile for Linux instead of Windows.  Go to the program's **src** directory and open the **global.h** file in your text editor.  Now find the line that says **#define WINDOWS** and put a **//** at the beginning of the line to comment it out, then save the file and proceed.
```
// #define WINDOWS
```
**End of Edit**

Then open a terminal, go to the program's src directory, and compile it:
```
cd ~/hme/src
gcc -o terrained -g *.c -lSDL -lpthread
```
If all goes well, it should create a binary file in your src directory called **terrained**.  It may give you a few 'no newline at end of file' warnings, but those don't matter.  So now you have your binary file, but it won't work until you move it to the directory with the bitmap files.  So assuming you're still in your **src** directory, type
```
mv terrained ../
cd ../
```That will move the file up a level to your **hme** directory then change to that directory.  Then you can successfully run the program by either double clicking it in nautilus, or being in that directory in your terminal and typing
```
./terrained
```


Now don't say no one helps you anymore.

---

### Post by crazyfuturamanoob on 2008-04-18
[SIZE="5"]THANKS!!!! IT WORKS!!
WOHOOO I LOVE YOU!!!![/SIZE]
:guitar::guitar::guitar:

---

### Post by crazyfuturamanoob on 2008-04-19
oh wait... it still has a lot crash issues.
For example, it crashes:
-if I try to get it full screen
-if I try to make a new heightmap sized 256x256
-if I try to resize the window too big
...and so on. It crashes nearly every other time
I try to use it. This is *VERY* annoying.
Is there anything to do with the crashing problems?

And I noticed gimp is still better than that.
ROFL it can only generate random terrain 
that gimp can't. (actually I generate random 
terrain with it and then I edit it with gimp).

---

