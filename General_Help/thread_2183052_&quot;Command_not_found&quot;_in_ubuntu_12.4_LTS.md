---
title: "&quot;Command not found&quot; in ubuntu 12.4 LTS"
date: 2013-10-23
forum: General Help
---

### Post by jeffhaddow on 2013-10-23
I have been using a cross compiler to develop machine code for a raspberry pi computer. The system works on Windows 7 but when I use the "make" command on the ubuntu system I get the following code
> 
jeff@lap-jeff:~/template$ make
arm-none-eabi-as -I source/ source/display.s -o build/display.o
make: arm-none-eabi-as: Command not found
make: *** [build/display.o] Error 127

I have added folder of the command to PATH$
> 
jeff@lap-jeff:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/jeff/arm-2008q3/bin

And the command utility is in the directory
> 
jeff@lap-jeff:~$ ls arm-2008q3/bin
arm-none-eabi-addr2line  arm-none-eabi-gcc-4.3.2  arm-none-eabi-objdump
arm-none-eabi-ar         arm-none-eabi-gcov       arm-none-eabi-ranlib
arm-none-eabi-as         arm-none-eabi-gdb        arm-none-eabi-readelf
arm-none-eabi-c++        arm-none-eabi-gdbtui     arm-none-eabi-run
arm-none-eabi-c++filt    arm-none-eabi-gprof      arm-none-eabi-size
arm-none-eabi-cpp        arm-none-eabi-ld         arm-none-eabi-sprite
arm-none-eabi-g++        arm-none-eabi-nm         arm-none-eabi-strings
arm-none-eabi-gcc        arm-none-eabi-objcopy    arm-none-eabi-strip

I think that the command originates from the makefile
 In the line below "# Rule to make the object files."

Text of Makefile:
```

###############################################################################
#       makefile
#        by Alex Chadwick
#
#       A makefile script for generation of raspberry pi kernel images.
###############################################################################

# The toolchain to use. arm-none-eabi works, but there does exist
# arm-bcm2708-linux-gnueabi.
ARMGNU ?= arm-none-eabi
#ARMGNU ?= arm-bcm2708-linux-gnueabi

# The intermediate directory for compiled object files.
BUILD = build/

# The directory in which source files are stored.
SOURCE = source/

# The name of the output file to generate.
TARGET = kernel.img

# The name of the assembler listing file to generate.
LIST = kernel.list

# The name of the map file to generate.
MAP = kernel.map

# The name of the linker script to use.
LINKER = kernel.ld

# The names of libraries to use.
LIBRARIES := csud

# The names of all object files that must be generated. Deduced from the
# assembly code files in source.
OBJECTS := $(patsubst $(SOURCE)%.s,$(BUILD)%.o,$(wildcard $(SOURCE)*.s))

# Rule to make everything.
all: $(TARGET) $(LIST)

# Rule to remake everything. Does not include clean.
rebuild: all

# Rule to make the listing file.
$(LIST) : $(BUILD)output.elf
        $(ARMGNU)-objdump -d $(BUILD)output.elf > $(LIST)

# Rule to make the image file.
$(TARGET) : $(BUILD)output.elf
        $(ARMGNU)-objcopy $(BUILD)output.elf -O binary $(TARGET)

# Rule to make the elf file.
$(BUILD)output.elf : $(OBJECTS) $(LINKER)
        $(ARMGNU)-ld --no-undefined $(OBJECTS) -L. $(patsubst %,-l %,$(LIBRARIES)) -Map $(MAP) -o $(BUILD)output.elf -T $(LINKER)

# Rule to make everything.
all: $(TARGET) $(LIST)

# Rule to remake everything. Does not include clean.
rebuild: all

# Rule to make the listing file.
$(LIST) : $(BUILD)output.elf
        $(ARMGNU)-objdump -d $(BUILD)output.elf > $(LIST)

# Rule to make the image file.
$(TARGET) : $(BUILD)output.elf
        $(ARMGNU)-objcopy $(BUILD)output.elf -O binary $(TARGET)

# Rule to make the elf file.
$(BUILD)output.elf : $(OBJECTS) $(LINKER)
        $(ARMGNU)-ld --no-undefined $(OBJECTS) -L. $(patsubst %,-l %,$(LIBRARIES)) -Map $(MAP) -o $(BUILD)output.elf -T $(LINKER)

# Rule to make the object files.
$(BUILD)%.o: $(SOURCE)%.s
        $(ARMGNU)-as -I $(SOURCE) $< -o $@

# Rule to clean files.
clean :
        -rm -f $(BUILD)*.o
        -rm -f $(BUILD)output.elf
        -rm -f $(TARGET)
        -rm -f $(LIST)
        -rm -f $(MAP)
```


I'm fairly new to this environment (Linux) and would apreciate any help.

All the best
Jeff

---

### Post by TheFu on 2013-10-23
arm-none-eabi-as is what?  A command or something else?

Adding a directory to a path is probably NOT what you want, especially if the command isn't inside it. Did you install the package which contains that command?

When posting makefiles, please wrap it in "code" tags ... see the "Adv Reply".  Please edit the 1st post and fix that.
Inside a makefile, tabs matter.  Spaces and tabs have different meanings, so be very careful which editor settings you have.

You can put the full path to the command inside the makefile. That is a best practice, BTW.

I suspect better help may occur from the rPi forums.

I did a quick google and there seems to be many issues around the toolchain for rpi. Lots of solutions on reputable websites.

---

### Post by jeffhaddow on 2013-10-23
@TheFu

Thanks for your reply. As far as I understand arm-none-eabi-as is a command as it is the same colour (green) as the commands in /bin.

I did not write the makefile.

I have posted this on the RasPi forums and not had a solution, and thought it may be one that is related to the operating system.

I'll have a look at googling my problem

All the best
Jeff

---

### Post by ajgreeny on 2013-10-23
I do not do any compiling and installing apps using source code etc etc, but I do know that for many of those activities it is necessary to install the **build-essential** package.
Could this be part of your problem?

---

### Post by jeffhaddow on 2013-10-23
@ajgreeny

Thanks - I installed build-essential the package, but it has made no difference -- Will I need to re-install the toolchain package?

All the best
Jeff

---

### Post by TheFu on 2013-10-23
> **jeffhaddow said:**
> @TheFu

Thanks for your reply. As far as I understand arm-none-eabi-as is a command as it is the same colour (green) as the commands in /bin.

I did not write the makefile.

I have posted this on the RasPi forums and not had a solution, and thought it may be one that is related to the operating system.

I'll have a look at googling my problem

Do you think it is a file permissions issue?  If so, run a **chmod a+x** on the file. The output of an **ls -al** in the directory would be helpful.  Learn about chmod - **man chmod** will explain.

Just suggesting that you edit the makefile/Makefile (case sensitvie) with the full path to the program it needs to run.  Just put /home/jeff/arm-2008q3/bin/ in front of it. There might be other changes needed to get the correct libraries linked too.

Your understanding is just a little too lite today. We've all been there and that will be handled with a little more time and practice.
 Keep plugging away.

---

### Post by steeldriver on 2013-10-23
"Command not found" can sometimes mean a dynamically linked *library *(or libraries) required by the command is not found, I think - try

```
ldd ~/arm-2008q3/bin/arm-none-eabi-as
```

---

### Post by jeffhaddow on 2013-10-23
@steeldriver

I tried this and get the result

code:
> jeff@lap-jeff:~$ ldd /home/jeff/arm-2008q3/bin/arm-none-eabi-as
    not a dynamic executable



All the best
Jeff

---

### Post by jeffhaddow on 2013-10-23
Hello TheFu

The executepermissions do not seem to be the problem:

Code
```
jeff@lap-jeff:~/arm-2008q3/bin$ ls -al
total 15124
drwxr-xr-x 2 jeff jeff    4096 Nov 13  2008 .
drwxrwxr-x 8 jeff jeff    4096 Oct 15 19:22 ..
-rwxr-xr-x 1 jeff jeff  480456 Nov 13  2008 arm-none-eabi-addr2line
-rwxr-xr-x 2 jeff jeff  502544 Nov 13  2008 arm-none-eabi-ar
-rwxr-xr-x 2 jeff jeff  862264 Nov 13  2008 arm-none-eabi-as
-rwxr-xr-x 2 jeff jeff  192648 Nov 13  2008 arm-none-eabi-c++
-rwxr-xr-x 1 jeff jeff  479448 Nov 13  2008 arm-none-eabi-c++filt
-rwxr-xr-x 1 jeff jeff  191208 Nov 13  2008 arm-none-eabi-cpp
-rwxr-xr-x 2 jeff jeff  192648 Nov 13  2008 arm-none-eabi-g++
-rwxr-xr-x 2 jeff jeff  189800 Nov 13  2008 arm-none-eabi-gcc
-rwxr-xr-x 2 jeff jeff  189800 Nov 13  2008 arm-none-eabi-gcc-4.3.2
-rwxr-xr-x 1 jeff jeff   23132 Nov 13  2008 arm-none-eabi-gcov
-rwxr-xr-x 1 jeff jeff 2806612 Nov 13  2008 arm-none-eabi-gdb
-rwxr-xr-x 1 jeff jeff 2806612 Nov 13  2008 arm-none-eabi-gdbtui
-rwxr-xr-x 1 jeff jeff  540508 Nov 13  2008 arm-none-eabi-gprof
-rwxr-xr-x 2 jeff jeff  744140 Nov 13  2008 arm-none-eabi-ld
-rwxr-xr-x 2 jeff jeff  490408 Nov 13  2008 arm-none-eabi-nm
-rwxr-xr-x 2 jeff jeff  627680 Nov 13  2008 arm-none-eabi-objcopy
-rwxr-xr-x 2 jeff jeff  753176 Nov 13  2008 arm-none-eabi-objdump
-rwxr-xr-x 2 jeff jeff  502544 Nov 13  2008 arm-none-eabi-ranlib
-rwxr-xr-x 1 jeff jeff  250408 Nov 13  2008 arm-none-eabi-readelf
-rwxr-xr-x 1 jeff jeff  705112 Nov 13  2008 arm-none-eabi-run
-rwxr-xr-x 1 jeff jeff  482268 Nov 13  2008 arm-none-eabi-size
-rwxr-xr-x 1 jeff jeff  302584 Nov 13  2008 arm-none-eabi-sprite
-rwxr-xr-x 1 jeff jeff  481736 Nov 13  2008 arm-none-eabi-strings
-rwxr-xr-x 2 jeff jeff  627680 Nov 13  2008 arm-none-eabi-strip


```

I edited the makefile to add the absolute address of the tokens and It now gives the same error but more verbose!!

```
jeff@lap-jeff:~/template$ make
/home/jeff/arm-2008q3/bin/arm-none-eabi-as -I /home/jeff/template/source/ /home/jeff/template/source/display.s -o /home/jeff/template/build/display.o
make: /home/jeff/arm-2008q3/bin/arm-none-eabi-as: Command not found
make: *** [/home/jeff/template/build/display.o] Error 127

```

> **TheFu said:**
> Do you think it is a file permissions issue?  If so, run a **chmod a+x** on the file. The output of an **ls -al** in the directory would be helpful.  Learn about chmod - **man chmod** will explain.

Just suggesting that you edit the makefile/Makefile (case sensitvie) with the full path to the program it needs to run.  Just put /home/jeff/arm-2008q3/bin/ in front of it. There might be other changes needed to get the correct libraries linked too.

Your understanding is just a little too lite today. We've all been there and that will be handled with a little more time and practice.
 Keep plugging away.

---

### Post by tgalati4 on 2013-10-23
I'm thinking that you have arm-executable files and that you have the wrong toolchain installed.  It seems that these files are used for compiling on the ARM (RaspberryPi) itself, not in a Linux environment.  The other possibility is that these are Windows executables and will only run in a Windows environment.

---

### Post by jeffhaddow on 2013-10-23
Hello tagalati4

The toolchain I used was the one that the Cambridge course says is for a Linux environment. It is not the toolchain for Windows is and It creates an kernal.img file which is put onto an SD card which is then used in the raspberrypi. The tool chain is not for use on the raspberrypi.  The instructions that I used to install the toolchain are here [http://www.cl.cam.ac.uk/projects/raspberrypi/tutorials/os/downloads.html#gnulinux](http://www.cl.cam.ac.uk/projects/raspberrypi/tutorials/os/downloads.html#gnulinux) (item 1.3 on the list)

All the best
Jeff

---

### Post by steeldriver on 2013-10-23
... so what does 

```
file /home/jeff/arm-2008q3/bin/arm-none-eabi-as
```

 say?

---

### Post by jeffhaddow on 2013-10-23
@ steeldriver

The file command gives the following

```

jeff@lap-jeff:~$ file /home/jeff/arm-2008q3/bin/arm-none-eabi-as
/home/jeff/arm-2008q3/bin/arm-none-eabi-as: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.2.5, stripped

```

All the best
Jeff

---

### Post by jeffhaddow on 2013-10-23
@streeldriver

I have a 64bit machine -- Could the fact that the file is 32bit be the problem?

all the best
Jeff

---

### Post by steeldriver on 2013-10-23
Yes it could mean you don't have the required 32-bit dynamic libs - which is why I suggested running 'ldd' on it - I was surprised you got "not a dynamic executable", and that doesn't seem to jive with what 'file' is telling you now i.e. "dynamically linked (uses shared libs)"

FWIW I downloaded the archive and I get

```

ldd arm/arm-2008q3/bin/arm-none-eabi-as
    linux-gate.so.1 =>  (0xb77aa000)
    libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xb75d9000)
    /lib/ld-linux.so.2 (0xb77ab000)

```

so I guess you'd need at least the 32-bit libc6 package

---

### Post by jeffhaddow on 2013-10-24
Many Thanks Steeldriver

The libc6 was unstalled however I installed libc6-dev-i386 and the make seems to have started working, although It is giving me screeds of output to work through with an "error 1" at the end. twosteps forward one step back !!!

Thanks again
Jeff

---

### Post by steeldriver on 2013-10-24
OK sounds like some progress at least

I'm a little confused about multiarch nowadays - it *used* to be the case that the recommended way was to install the ia32-libs metapackage, however I think that now that's frowned upon and you're supposed to enable the architecture using dpkg --add-architecture i386 and then add individual packages explicitly e.g. libc6-dev:i386 as needed

According to this link you may need a 32-bit libncurses (libncurses5-dev?) --> [https://launchpadlibrarian.net/151487295/readme.txt](https://launchpadlibrarian.net/151487295/readme.txt)

There appear to be newer versions of the toolchain here --> [https://launchpad.net/gcc-arm-embedded](https://launchpad.net/gcc-arm-embedded) but I couldn't see any mention of a native 64-bit pre-build

If you need further help then post back with the exact error messages

---

### Post by jeffhaddow on 2013-10-26
@steeldriver

I have been able to get the toolchain working.  I've sucessfullu got Input02 working. which draws random multicoloured lines, but the whole OS for my hexadecimal calculator only currently gives a multicolourd raster. I think that the toolchain that I'm using interprets some of the "compile" instructions from the one that I used on Windows 7. To get the input02 working I needed to change "align 16" to "align 4".

Thanks again
Jeff

---

### Post by binesh2 on 2014-07-03
Hi Jeff.. i had installed libc6-dev-i386 and still im gettin the same error message.Im using ubuntu 14.1.. I want to implement this tutorial on rpi :[http://wiki.osdev.org/ARM_RaspberryPi_Tutorial_C#Echo_kernel](http://wiki.osdev.org/ARM_RaspberryPi_Tutorial_C#Echo_kernel). I used the cambridge toolchain as well. can you help me out. thanks
-Binesh

---

