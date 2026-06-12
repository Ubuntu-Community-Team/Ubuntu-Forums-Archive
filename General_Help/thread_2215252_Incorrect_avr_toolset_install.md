---
title: "Incorrect avr toolset install"
date: 2014-04-05
forum: General Help
---

### Post by imbatronics on 2014-04-05
Greetings all

I am trying to use the serial functionality of my Arduino Mega2560. I am  also very new to Linux. First time  poster ):P
(I put this post on the Beginner Secion as well but I think it might belong more in the General Support section, sorry for duplicate)

Recently installed ubuntu 12.04 alongside windows 7 to avoid additional hardware when coding in C on Arduino.

For what i was trying to do, I was told to install the following tools:  avr-gcc, avr-libc, avrdude. This was fine, I could handle even though I  was not used to the linux installation protocol. My problem arose when I  was trying to compile my main.c using **gcc main.c -o MateDealer** such that I could run the code from terminal/test it on the Arduino.

$ **make all**  //worked fine, no errors
$ **make program** //worked fine, no errors
[FONT=arial]hex file was generated and uploaded to  the Arduino (I assume, since Tx and Rx lights were going crazy, no  errors, avrdude seemed happy)

So, I tried to compile:[/FONT]
**gcc main.c -o MateDealer**

I get 
[B]main.c:16:20: fatal error: avr/io.h: No such file or directory
compilation terminated.[/B]

At this stage I had no idea what was going on, so I tried to copy/paste  the io.h file from where it was sitting to where it should be
First I needed to see where the includes needed to be so I ran
**avr-gcc -print-file-name=include**


which gave me
**/usr/lib/gcc/avr/4.5.3/include**


then I used
 **cp /usr/lib/avr/include/avr/io.h /usr/lib/gcc/avr/4.5.3/include**


which gave me
**cp: cannot create regular file `/usr/lib/gcc/avr/4.5.3/include/io.h': Permission denied**

[FONT=arial]So, I tried to work around this by changing the **#include <avr/io.h>** in main.c to **[FONT=arial]#include "io.h"[/FONT]** and copying (using terminal command cp) io.h to the folder in which main.c is sitting.[/FONT]
[FONT=arial]Then, when I ran **gcc main.c -o MateDealer **[FONT=arial]in terminal I got a _different_ err[/FONT][/FONT][FONT=arial]or compared to the above error[/FONT][FONT=arial][FONT=arial]
**main.c:16:20: fatal error: avr/io.h: No such file or directory**** .**
Instead, another "sub header file" _which is included in io.h_ is  also missing. I also need to include about 5 more header files e.g  avr/xxx.h and I assume each of them include their own "sub header  files".

My conclusion is that the compile found io.h, but I can't do this  manually for each missing header file as it will take ages. I believe I  have installed either avr-gcc, avr-libc, or avrdude (not sure which one)  in the wrong location! While trying to fix this I stumbled upon [http://www.nongnu.org/avr-libc/user-...l_avr_binutils]("http://www.nongnu.org/avr-libc/user-manual/install_tools.html#install_avr_binutils") which gave me the idea of incorrect install path. I also got errors after the [/FONT][/FONT]**$ make**[FONT=arial][FONT=arial] command (see link above) when trying to install binutils.[/FONT][/FONT]

[FONT=arial]How can I:

a) determine which of the 3 mentioned tools (if not all) I have installed in the incorrect place/directory/path?
b) reinstall the misplaced tool in the correct location?

Appologies for the long post, I just wanted to make sure I am being  clear as I often get lost trying to read other forum threads. Thank you  in advance for your help![/FONT]

---

### Post by steeldriver on 2014-04-05
Why areyou trying to compile your main.c file with **gcc**? shoudn't you be using **avr-gcc**?

---

### Post by imbatronics on 2014-04-05
tried **avr-gcc main.c -o MateDealerC**

**recieved this:**
In file included from main.c:16:0:
/usr/lib/gcc/avr/4.5.3/../../../avr/include/avr/io.h:428:6: warning: #warning "device type not defined"
In file included from main.c:20:0:
/usr/lib/gcc/avr/4.5.3/../../../avr/include/util/delay.h:95:3: warning: #warning "Compiler optimizations disabled; functions from <util/delay.h> won't work as designed"
/tmp/cc7l0rWH.o: In function `main':
main.c:(.text+0x1e): undefined reference to `setup_usart'
main.c:(.text+0x32): undefined reference to `setup_usart'
main.c:(.text+0x40): undefined reference to `send_str_p'
main.c:(.text+0x42): undefined reference to `mdb_cmd_handler'
main.c:(.text+0x44): undefined reference to `uplink_cmd_handler'
collect2: ld returned 1 exit status

---

### Post by steeldriver on 2014-04-05
The undefined references mean you need to specify the appropriate library or libraries to be linked to create your executable program - something like

```

avr-gcc main.c -o MateDealerC **-lsomelib -lotherlib -L/path/to/more/libs -lmorelibs**

```

I have no experience with avr so I can't really help you with that  except to suggest you look at the Makefile (for example for the **program **target that you were able to build successfully) and see what libraries and library paths it uses.

The warnings may mean that you are missing some flags or definitions - again, look in the successful Makefile for things like CFLAGS

---

### Post by imbatronics on 2014-04-05
looking in the makefile, this is what I find when searching for CFLAGS:

# Compiler flags.
#  -g*:          generate debugging information
#  -O*:          optimization level
#  -f...:        tuning, see GCC manual and avr-libc documentation
#  -Wall...:     warning level
#  -Wa,...:      tell GCC to pass this to the assembler.
#    -adhlns...: create assembler listing
CFLAGS = -g$(DEBUG)
CFLAGS += $(CDEFS) $(CINCS)
CFLAGS += -O$(OPT)
CFLAGS += -funsigned-char -funsigned-bitfields -fpack-struct -fshort-enums
CFLAGS += -Wall -Wstrict-prototypes
CFLAGS += -Wa,-adhlns=$(<:.c=.lst)
CFLAGS += $(patsubst %,-I%,$(EXTRAINCDIRS))
CFLAGS += $(CSTANDARD)
CFLAGS += -DF_OSC=$(F_OSC)

I am very new to Ubuntu so I cant really decode what you are meaning by "(for example for the **program **target that you were able to build successfully) and see what libraries and library paths it uses"

thanks for quick responses!

---

### Post by steeldriver on 2014-04-05
When you execute make like

```

make program

```

we'd call **program** the *target*. There should be a corresponding line in the Makefile telling make *how* to make that target - it may be obscured by the use of variables by the basic format will be something like

```

program: *list of things on which the target **program** depends*
      *instructions for how to make **program** from those things*
      *possible further instructions or things to do after*

```

If the target is an executable program (rather than an intermediate object file or library), those instructions should mention any libraries that are required at the link phase - either literally like

```

-lSDL -lm

```

or symbolically - like

```

$(LDFLAGS) $(LIBS)

```

in which case you will need to seek out the definitions of those variables (usually somewhere near the top of the Makefile) to find out what specific libraries they refer to.

---

### Post by imbatronics on 2014-04-05
[here]("https://github.com/Bouni/MateDealer/blob/master/arduino/makefile") (on github) is the makefile of the code I am trying to run on Arduino.
Go up a level to see it all. I'm still not quite sure what I am supposed to do :/
Again, appologies for incompetence, steep learning curve for me

---

### Post by steeldriver on 2014-04-05
OK... and what are you trying to do exactly? There is no need to run a complicated avr-gcc command if you already have a makefile that does everything for you

I had assumed that you were trying to build an application of your own and didn't have a makefile for it - but that does not seem to be the case? why do you need to do any more than you have already done (i.e. **make program**)?

---

### Post by imbatronics on 2014-04-05
if you look in line 35 of main.c found in repository from my last post, you will see:
send_str_p(0,PSTR("MateDealer is up and running\r\n"));
I would like to see "MateDealer is up and running" on the terminal.
The main point of the project I am working on is communicating with a vending machine coin mechanism using an Arduino. I need to send the arduino commands from Terminal etc

---

### Post by s-witzel on 2014-11-20
Isn't there any solution to this? I think this is actually a bug in Ubuntu. Because I have some files that compiled fine a long time ago and now they don't work any more. The problem seems to be that avr-libc is installed with its includes in

/usr/lib/avr/include

but the search path is

/usr/lib/gcc/avr/4.8.2/include

Of course one can manually change this, but I don't think one should have to (at least one didn't have to last time I tried to compile my code).
For some reason avr-related software seems to keep breaking in Ubuntu, I had a similar problem with avra at some point.

---

