---
title: "Recurrent issue across Ubuntu 13.10, Xubuntu 12.04"
date: 2014-03-23
forum: General Help
---

### Post by Catslothloaf on 2014-03-23
I'm posting this in the General Help section because my issue could fall under several different categories, although my hunch is that it all comes down to my hardware configuration. I've been having a problem that fresh installs, switching desktop environments, and switching Ubuntu versions couldn't fix. 

Machine: A refurbished Dell workstation. Optiplex 780- Tower Desktop Form Factor. Intel Core 2 Duo E7600, Nvidia GeForce GT430, 8GB RAM, 70GB (dev/sdb EXT4) and 1TB (dev/sda NTFS) HD's. 

Use history: Originally running only Win7 on the 1TB drive. Added a 70GB HD originally from a Toshiba laptop. Configured for dual-HD, dual-boot Windows 7 (on sda) and Ubuntu 13.04 (on sdb). When I was running 13.04 I never ran into the specific issues I'm having now, but I never attempted to perform an action that would cause the issue to appear, so it's probably safe to assume the underlying malfunctions were present during this time. Upgraded to 13.10 last week. 

Specific issue: 

1. Downloaded binary executable program "unetbootin" does not execute. 


Attempted fixes:

1. Deleted and re-downloaded executable file.
2. Ensured that specific command was being entered: 'sudo chmod +x ./Downloads/unetbootin-linux-585' and that 'run as executable' was checked under permissions tab. 
3. Ensured that Owner and Root have Read and Write privileges.
4. 'sudo bash ./Downloads/unetbootin-linux-585' returns 'cannot execute binary file'.\
5. Created Xubuntu 12.04 Live USB (with the Win7 version of unetbootin) and performed an 'Erase Ubuntu and Reinstall' installation. 
6. Attempted fixes 1-4 again. 

Any ideas what this might be? I also have graphical problems, i.e. certain custom icon themes display dark "for radiance-style" status indicator toolbar icons even when the desktop theme is dark "ambiance-style", light text appears in certain places on white "radiance-style" windows making text almost invisible, and (in Xubuntu) my X server monitor arrangement settings get reset every time I log out. I'm not necessarily looking for solutions to these graphical problems in this thread. I'm just including them in the hope that they might help diagnose my binary execution issue. 


Thanks.

---

### Post by slooksterpsv on 2014-03-24
Why don't you install it from the repositories? it will install everything you need to run it.

If you run ls -l ./unetbootin* it should show you the permissions. When I download unetbootin (not the deb) from sf.net it gives me an xrandr error, but the repos one works.

EDIT: I think its corrupt cause I can't get it to run, just use the DEB one or compile it yourself.

---

### Post by Impavidus on 2014-03-24
> **Catslothloaf said:**
> 
1. Deleted and re-downloaded executable file.
2. Ensured that specific command was being entered: 'sudo chmod +x ./Downloads/unetbootin-linux-585' and that 'run as executable' was checked under permissions tab. 
3. Ensured that Owner and Root have Read and Write privileges.
4. 'sudo bash ./Downloads/unetbootin-linux-585' returns 'cannot execute binary file'.\
5. Created Xubuntu 12.04 Live USB (with the Win7 version of unetbootin) and performed an 'Erase Ubuntu and Reinstall' installation. 
6. Attempted fixes 1-4 again. 

Point 4: bash doesn't run binary files. Bash only runs bash scripts. To run the binary file, omit the bash:```
$ bash hello
hello: hello: cannot execute binary file
$ ./hello
Hello world!
$
```

---

### Post by Catslothloaf on 2014-03-25
Bash won't execute a binary, huh? I didn't know. Someone on askubuntu suggested that I try it instead of just ```
 sudo ./Downloads/unetbootin-linux-585
``` 

But yeah, bash notwithstanding the problem still is that trying to execute through the terminal returns a prompt and nothing happens. 

As for just getting the program from the repo; it would work but that's not solving the issue. My system seems to be incapable of executing a downloaded binary. I'd like to find out why.

As a novice I know I don't have much hope of isolating and determining the cause of the issue without the advice of someone who does. But failing that, I'd at least like to know if this is a common issue, and seeing as how it has persisted through multiple fresh installations of different versions of Ubuntu, if it's likely that I'd ever run this OS on this machine and not have this issue?

---

### Post by slooksterpsv on 2014-03-25
The application is corrupt. I downloaded it and can't pull any information from the program as it being a valid app. I don't know how they compiled it, but something went haywire with it.

Download it from the repos using:

sudo apt-get install unetbootin

---

### Post by Impavidus on 2014-03-26
> **Catslothloaf said:**
> Bash won't execute a binary, huh? I didn't know.
Bash can ask the OS to execute a binary, but it can't execute the binary itself. It can only execute (interpret) bash scripts. For example, I have an executable binary called **hello.elf** and an executable bash script called **hello.bash**. Both produce the output *Hello world!*. Now the different commands give these outputs:

**./hello.elf** &#8594; *Hello world!* — Bash asks the OS to execute the binary. The binary is executed and produces the output.
**bash -c ./hello.elf** &#8594; *Hello world!* — Bash asks the OS to start another bash with the instruction to execute the _command_ ./hello.elf. The second bash executes this command like in the example above.
**bash ./hello.elf** &#8594; *./hello.elf: ./hello.elf: cannot execute binary file* — Bash asks the OS to start another bash with the instruction to execute the _file_ ./hello.elf. The second bash tries to interpret it, but sees that this is not a bash script and gives an error message.
**./hello.bash** &#8594; *Hello world!* — Bash asks the OS to execute the script. The OS starts another bash with the instruction to interpret the script, producing the desired output.
**bash -c ./hello.bash** &#8594; *Hello world!* — Bash asks the OS to start a second bash with the instruction to execute the command ./hello.bash. The second bash executes the command as in the example above, causing the OS to start a third bash, which interprets the script.
**bash hello.bash** &#8594; *Hello world!* —No ./ needed here. Bash asks the OS to start a second bash with the instruction to interpret the script. The second bash will interpret the script and produce the desired output.

So, **sudo bash ./binary-file** won't work, whereas **sudo ./binary-file** should work. If you don't get any output (no error), it usually means the executable was started. But if slooksterpsv says the application is corrupt, that's a different problem.

---

### Post by Catslothloaf on 2014-03-28
Thanks folks. I'm glad to hear that there was something wrong with the executable rather my computer, because not being able to run it when everything else could be installed and used normally made no sense. 

And thanks for the info about bash. Now I see why what I did wouldn't work.  

Super useful responses. Much appreciated.

---

