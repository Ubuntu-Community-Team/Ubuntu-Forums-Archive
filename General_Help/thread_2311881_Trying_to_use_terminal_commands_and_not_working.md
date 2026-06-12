---
title: "Trying to use terminal commands and not working"
date: 2016-01-30
forum: General Help
---

### Post by NotWindows on 2016-01-30
Hello!

I bought a Lemaker Guitar single board computer for a project and need to update the OS which I am running Android 5. The problem is I am using the terminal and can't get this application called FWBurningTool to unzip and install in Ubuntu.

I posted what I am supposed to be able to do and it will download the file but that's it. There has to be something wrong here that I am unaware of. I am somewhat of a newbie to the terminal and command line.

**Linux**
I. Download the firmware burning tool such as **FWBurning Tool** from:

 
[LIST]
[*][http://mirror.lemaker.org/FW_Burning_Tool_For_Linux_V1.0_01.tar.gz](http://mirror.lemaker.org/FW_Burning_Tool_For_Linux_V1.0_01.tar.gz)
[*][http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z](http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z)
[/LIST]
 wget [http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z](http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z)
sudo apt-get install p7zip-full
7za x FW_Burning_Tool_for_Linux_PC_V1.1_01.7z

 II. In the command terminal, extract the archive file and install FWBurning Tool. 
 sudo tar -zxvf FWBurning_Tool_For_Linux_V1.0_01.tar.gz 
cd FWBurning_Tool_For_Linux_V1.0_01
sudo ./FWBurningTool-1.0.run

 III. Press and hold the software “ADFU” button, [Connect our PC to LeMaker Guitar via USB3.0/USB2.0 cable]("http://wiki.lemaker.org/File:%E7%A4%BA%E6%84%8F%E5%9B%BE.png"). [COLOR=red]When  LeMaker Guitar is powered on, it will take about 6 seconds to enter  ADFU mode. And then after it enters to the ADFU mode, we can release the  software “ADFU” button. [/COLOR]We can use the command “lsusb” to list  the USB devices. If can’t detects the USB device, please use the  hardware “ADFU” button on core board to enter ADFU mode. 
 sudo lsusb
…
Bus 001 Device 002: ID 10d6:10d6 Actions Semiconductor Co., Ltd
…

 IV. Write the .fw file into eMMC NAND Flash 
 sudo python ./ActionsFWU.py  --fw=[firmware_name].fw

Please Help!
Thanks,
Kevin

---

### Post by matt_symes on 2016-01-30
Hi

> **NotWindows said:**
> Hello!

I bought a Lemaker Guitar single board computer for a project and need to update the OS which I am running Android 5. The problem is I am using the terminal and can't get this application called FWBurningTool to unzip and install in Ubuntu.

I posted what I am supposed to be able to do and it will download the file but that's it. There has to be something wrong here that I am unaware of. I am somewhat of a newbie to the terminal and command line.

**Linux**
I. Download the firmware burning tool such as **FWBurning Tool** from:

 
[LIST]
[*][http://mirror.lemaker.org/FW_Burning_Tool_For_Linux_V1.0_01.tar.gz](http://mirror.lemaker.org/FW_Burning_Tool_For_Linux_V1.0_01.tar.gz)
[*][http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z](http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z)
[/LIST]
 wget [http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z](http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z)
sudo apt-get install p7zip-full
7za x FW_Burning_Tool_for_Linux_PC_V1.1_01.7z

 II. In the command terminal, extract the archive file and install FWBurning Tool. 
 sudo tar -zxvf FWBurning_Tool_For_Linux_V1.0_01.tar.gz 
cd FWBurning_Tool_For_Linux_V1.0_01
sudo ./FWBurningTool-1.0.run

 III. Press and hold the software “ADFU” button, [Connect our PC to LeMaker Guitar via USB3.0/USB2.0 cable]("http://wiki.lemaker.org/File:%E7%A4%BA%E6%84%8F%E5%9B%BE.png"). [COLOR=red]When  LeMaker Guitar is powered on, it will take about 6 seconds to enter  ADFU mode. And then after it enters to the ADFU mode, we can release the  software “ADFU” button. [/COLOR]We can use the command “lsusb” to list  the USB devices. If can’t detects the USB device, please use the  hardware “ADFU” button on core board to enter ADFU mode. 
 sudo lsusb
…
Bus 001 Device 002: ID 10d6:10d6 Actions Semiconductor Co., Ltd
…

 IV. Write the .fw file into eMMC NAND Flash 
 sudo python ./ActionsFWU.py  --fw=[firmware_name].fw

Please Help!
Thanks,
Kevin

Can you be a bit more clear about how it's failing ?

Which steps did you complete and at which step did it fail ?

BTW: Did you make FWBurningTool-1.1.run executable ?
```

matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % ./FWBurningTool-1.1.run
zsh: permission denied: ./FWBurningTool-1.1.run
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % ls -l                  
total 3640
-rw-rw-r-- 1 matthew matthew 3724620 Dec  8 01:50 FWBurningTool-1.1.run
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % **chmod 755 FWBurningTool-1.1.run **
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % ./FWBurningTool-1.1.run 
>>>FWBurningTool running on Ubuntu -x64
>>>FWBurningTool has been installed in /home/matthew/Bin/
>>>FWBurningTool installed completely
 
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % 
```

This creates the directory ~/Bin, containing these files.
```

matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % ls ~/Bin
ActionsFWU.py*  libFileSystem.so*  libProduction.so*  libScript.so*
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % 
```

I have not run it though.

Kind regards

---

### Post by grahammechanical on 2016-01-30
> sudo tar -zxvf FWBurning_Tool_For_Linux_V1.0_01.tar.gz

That should have created a folder called FWBurning_Tool_For_Linux_V10_01 and then extracted or decompressed the file into the folder. You should be able to see this folder & what is in it using the file manager.

> cd FWBurning_Tool_For_Linux_V1.0_01

That will cd = change directory into the folder. Then you can load or run the program with

> sudo ./FWBurningTool-1.0.run

At what point does it go wrong?

Regards.

---

### Post by NotWindows on 2016-01-30
I can get the file downloaded, the commands tell me I have p7zip-full is already the newest version. I did not make it excitable or run, that's why I was wondering if this step by step directions were correct. 

Then i put this in the command line:
7za x FW_Burning_Tool_for_Linux_PC_V1.1_01.7z

7-Zip (A) 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: FW_Burning_Tool_for_Linux_PC_V1.1_01.7z

file FW Burning Tool for Linux PC V1.1_01/FWBurningTool-1.1.run
already exists. Overwrite with 
FW Burning Tool for Linux PC V1.1_01/FWBurningTool-1.1.run?
(Y)es / (N)o / (A)lways / (S)kip all / A(u)to rename all / (Q)uit? y
Extracting  FW Burning Tool for Linux PC V1.1_01/FWBurningTool-1.1.run
Extracting  FW Burning Tool for Linux PC V1.1_01

Everything is Ok

Folders: 1
Files: 1
Size:       3724620
Compressed: 3724151

After that, I can't get any of this to work or at least the first line of commands!

In the command terminal, extract the archive file and install FWBurning Tool. 

 sudo tar -zxvf FWBurning_Tool_For_Linux_V1.0_01.tar.gz**(Can not open, no such file or directory)** 
cd FWBurning_Tool_For_Linux_V1.0_01
sudo ./FWBurningTool-1.0.run

---

### Post by steeldriver on 2016-01-30
It looks like you're following 2 different sets of instructions - **.7z** and **.tar.gz** are different archive formats, you probably only need to run the extract command for whichever file format you have actually downloaded (in this case, it appears you downloaded the .7z version - so you can skip the **tar** command)

---

### Post by matt_symes on 2016-01-30
Hi

> **steeldriver said:**
> It looks like you're following 2 different sets of instructions - **.7z** and **.tar.gz** are different archive formats, you probably only need to run the extract command for whichever file format you have actually downloaded (in this case, it appears you downloaded the .7z version - so you can skip the **tar** command)

Just been looking at the two archives and steeldriver above is bang on the money.

The only difference between the two archives is one library file as checking the hashes show.

```

matthew-xu-16-04:/home/matthew:2 % diff <(md5sum ~/Bin/* | cut -f1 -d' ') <(md5sum ~/Bin.PC/* | cut -f1 -d' ')
3c3
< 5ecf687b45a47fb36a73d43b295333fb
---
> 879a7588e9dcfdf72cf86daada641bb4
matthew-xu-16-04:/home/matthew:2 % 
```

The mismatching hash belongs to this file
```

matthew-xu-16-04:/home/matthew:2 % md5sum ~/Bin/* | grep 5ecf687b45a47fb36a73d43b295333fb
5ecf687b45a47fb36a73d43b295333fb  /home/matthew/Bin/libProduction.so
matthew-xu-16-04:/home/matthew:2 %
```

The 7z is a version bump from the tar.gz file.

Use the 7z version.

Kind regards

---

### Post by NotWindows on 2016-01-30
Ok I changed to .7z file type but now when put into the terminal I get this:
```

sudo -zxvf FW_Burning_Tool_for_Linux_PC_V1.1_01.7z
sudo: invalid option -- 'z'
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
```

---

### Post by matt_symes on 2016-01-30
Hi

You're mixing up your commands.

```
**7za x **FW_Burning_Tool_for_Linux_PC_V1.1_01.7z
```

There's also no need for *sudo* at this point.

That'll extract it. Make the .run file executable to run it.

Kind regards

---

### Post by NotWindows on 2016-01-30
Could you please type out a step by step for me? Sorry it's all getting a little confusing not knowing all of this and being a newbie to the terminal.

Thanks,
Kevin

---

### Post by matt_symes on 2016-01-31
Hi

> **NotWindows said:**
> Could you please type out a step by step for me? Sorry it's all getting a little confusing not knowing all of this and being a newbie to the terminal.

Thanks,
Kevin

No worries.

Open a terminal and copy and paste each of these commands into it.

```
cd ~ && mkdir temp && cd $_
```

```
wget http://mirror.lemaker.org/FW_Burning_Tool_for_Linux_PC_V1.1_01.7z
```

```
7za x FW_Burning_Tool_for_Linux_PC_V1.1_01.7z
```

```
cd FW\ Burning\ Tool\ for\ Linux\ PC\ V1.1_01/
```

```
chmod 755 FWBurningTool-1.1.run
```

```
./FWBurningTool-1.1.run
```

That last command should give output like this

```
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % ./FWBurningTool-1.1.run 
>>>FWBurningTool running on Ubuntu -x64
>>>FWBurningTool has been installed in **/home/matthew/Bin/**
>>>FWBurningTool installed completely
 
matthew-xu-16-04:/home/matthew/temp/FW Burning Tool for Linux PC V1.1_01:2 % 
```

Finally 

```
cd ~/Bin
```

You should now be in the directory where those extricated files reside.

```
matthew-xu-16-04:/home/matthew/Bin:2 % ls
ActionsFWU.py*  libFileSystem.so*  libProduction.so*  libScript.so*
matthew-xu-16-04:/home/matthew/Bin:2 %
```

As i stated in an earlier post, i have not run them.

I hope that helps.

Kind regards

---

### Post by NotWindows on 2016-02-01
/FWBurningTool-1.1.run

I am getting no such file or directory!

---

### Post by matt_symes on 2016-02-01
Hi

> **NotWindows said:**
> /FWBurningTool-1.1.run

I am getting no such file or directory!

It's 

```
**./**FWBurningTool-1.1.run
```

You missed the full stop or period (if you're American).

Kind regards

---

### Post by NotWindows on 2016-02-01
OK! Got it all figured out and it looks like it is now running it! I don't see the FWBurning Tool in my apps or programs.

---

### Post by matt_symes on 2016-02-01
Hi

> **NotWindows said:**
> OK! Got it all figured out and it looks like it is now running it! I don't see the FWBurning Tool in my apps or programs.

All the .run script did was extract the files from itself (the files were contained inside the script) to the ~/Bin directory it created for them.

If you want a menu item, you'll need to create a .desktop file and add ~/Bin to your PATH variable.

I'm off to bed though. I'm sure someone else will help you with that.

Kind regards

---

