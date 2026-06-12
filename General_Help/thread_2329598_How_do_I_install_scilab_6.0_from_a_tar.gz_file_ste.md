---
title: "How do I install scilab 6.0 from a tar.gz file step by step?"
date: 2016-07-03
forum: General Help
---

### Post by afz12 on 2016-07-03
I want to install Scilab 6.0 on Ubuntu 16.04 and Ubuntu 16.10 using a tar file scilab-6.0.0-beta-2.bin.linux-x86_64.tar.gz. I have never made a successful tar file install and scilab is no exception. Which directory do I put the file in? I tried tar -xzvf scilab-6.0.0-beta-2.bin.linux-x86_64.tar.gz and it did something but ./configure didn't work. I put the tar file in Home and tried cd /home and then tar -xzvf scilab-6.0.0-beta-2.bin.linux-x86_64.tar.gz but the error message "file not found" occurred.

 I would appreciate if someone would post **_exact_** keystroke steps that will install Scilab 6.0 on (preferably) both notebooks (hp dv6 and hp Envy). Given that I have never had a successful tar file install, posting higher level instructions won't be helpful. I need very simple step by step terminal entries that will do the job.

Thanks for any replies in advance

---

### Post by ajgreeny on 2016-07-03
Why exactly do you need to install it using an archive?  It is in the repos, though not that version; 14.04 has 5.5.0-2; 16.04 has version 5.5.2-2.
Do you really need version 6.0.0 or will 5.5.2-2 do all you need?

It is not really possible to tell you how to install a package from an archive without knowing where the archive came from and what files are included in the archive, which could be source code files or could be an executable, or even a .deb package file.  I was going to have a look myself but when I saw the download was 325MB decided that I would rather not as I have no possible need for it.

So extract the archive scilab-6.0.0-beta-2.bin.linux-x86_64.tar.gz which will normally produce a folder called scilab-6.0.0-beta-2.bin.linux-x86_64 and see what is in that folder.  There should normally be an install or README file with instructions.  If it is source code you will probably need to install the **build-essentials** package in order to be able to configure, make and install the application.

See if that helps; if it is all gobbledegook to you come back again after seeing what the archive contains and we'll try to help more.

---

### Post by afz12 on 2016-07-03
Hi Ajgreeny

I clicked on the file and it produced a folder in Desktop/Simulation Software Examples/SciLab/Program Software/Linux/scilab-6.0.0-beta-2. I opened README and its contents are


'Unpack Scilab and call the execution script:
`./bin/scilab`

Advanced command line interpreter (GUI, help browser, Tcl/Tk...):
`./bin/scilab-adv-cli`

Command line interpreter:
`./bin/scilab-cli` "

How do I "unpack". Is this ./configure - this hasn't worked previously. Also the tar -xzvf scilab-6.0.0-beta-2.bin.linux-x86_64.tar.gz doesn't seem to work, even if I can find the directory using the terminal - were should this new file go? I would appreciate exact, clear instructions to complete this task, as I have had little success by guessing what higher level terminology means.

I prefer version 6.0 as Scilab, unlike many other applications, introduces major improvements with each new release. For example, version 5.2.2 limits its "stack" to 10,000 so I need to increase this to stacksize("max") for large matrix inversions. At the moment inv(A) crashes Scilab for anything larger than 16 * 16, even with setting maximum stacksize. My 2 notebooks have 6 GB and 8 GB RAM so this is a software issue. I have tried Windows version 6.0 using Wine and on XP as a virtual machine and this hassle is removed - although this only works for 32 bit versions and is therefore limiting. Also on another Mint Rosa partition I somehow got version 6.0 to work in some sort of way and large inversions are no problem there matrices up to 4096 * 4096 in size is OK. I have no idea how it did this - after lots of accidental trial and error.

Version 6.0 is recommended for Scilab. The sudo apt-get install only works with version 5. Another issue is that sometimes the internal help doesn't open in v5.0 - a bit annoying. Interesting the pseudo-matrix inversion command pinv(A), based on svd, has no problem with large matrices.

There are two reasons I have to understand installing tar files. Not only for Scilab (I found some deb files for version 5 but most end up with complaints "dependencies not satisfied") but for other tar files in future. I have read previous posts and Internet sites describing ./ make make install but these never seem to work - whether others have success doesn't help me much. Unfortunately the repositories are usually not up to date or they contain silly 32 versions of an application when the preferred versions should be 64 bit.

In summary, I would like to get on top of installing tar files for a change. Any education on how to do this, especially using simple step by step instructions, would be appreciated. Scilab (an excellent alternative to MATLAB and Octave) version 6.0 seems to be a very suitable target for this.

---

### Post by steeldriver on 2016-07-03
./configure is only something you would need when building software from source code

What you have downloaded appears to be a pre-compiled binary package - provided your system has all the necessary shared libraries, you should be able to run it directly

To do so, you would open a terminal (Ctrl-Alt-T), navigate to the unpacked directory using the 'cd' command - for example

```

cd ~/Desktop/"Simulation Software Examples"/SciLab/Program Software/Linux/scilab-6.0.0-beta-2

```
and then type

```

./bin/scilab

```

(or one of the other advanced options) exactly as described in the README file.

---

### Post by afz12 on 2016-07-03
Thanks steeldriver - I appreciate your clear instructions. I put is tar file in Desktop/test as the cd command didn't work. I then clicked the file and it extracted to 
scilab-6.0.0-beta-2 that I could cd to. Then your command ./bin/scilab worked - it opened Scilab 6.0 and this ran fine. 
However I then looked for it on the left panel in Ubuntu but only found version 5.5.2.2 - where is version 6.0? How do I now access it from
the left hand side panel like other programs? Do I need to remove version 5 somehow - is this a job for synaptic or is there a terminal
command in Linux to make the OS "see" version 6.0?

---

