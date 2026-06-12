---
title: "Cant Open &quot;sh&quot; file! HELP PLEASE!"
date: 2008-05-09
forum: General Help
---

### Post by Luke08 on 2008-05-09
Im at University and they have a file you have to open if you want to access the internet so that it can find out if you have a virus scan fully functioning.  Im currently on Vista now to access the internet.  In Ubuntu 8.04 When i download it its called "CSA.sh" but it wont open?  On Vista its called "CSA.exe" so it does work here, and loads up...I have Wine, is it possible to open it as an EXE file in Ubuntu through wine. how do i get around this?

Any help would be greatly appreciated as i would like to use Ubuntu at uni rather than Vista.

Luke

---

### Post by Zack McCool on 2008-05-09
What have you done to open it?

First, it must be made executable...

```
 chmod u+x CSA.sh 
```

Then, if it is not in your PATH, you must specify the location...

```
 ./CSA.sh 
```

Also, are you running a virus scan?

---

### Post by Luke08 on 2008-05-09
in ubuntu im not running a virus scan no, cos theres no point is there...in Vista i have Avast running that it works.  I want to see if i can get the file working without having to run a virus scan, or should i temporarily download one to run then stop it after?

---

### Post by ryanhaigh on 2008-05-09
You will have to try running it in a terminal.
-Download the file to your desktop
-Open terminal from applications>accessories and enter the command
```

cd ~/Desktop

```
Followed by the commands Zack posted. If you still have trouble you could post the contents of the file for us to take a lookat. I think its pretty cool that your school acknowledges the existence of non windows computers (which is why your getting the .sh instead of .exe).

---

### Post by Luke08 on 2008-05-09
WOW...i dont know how it has happened but it has seemed to have worked.  I opened the file even though it said it had an error and loaded an internet page with an error also, but then reloaded a website and it worked.

Thanks guys for your help, im now running this through Ubuntu!

---

### Post by vdawg on 2008-05-09
Lol, I wonder what kind of a script could they run that would check for viruses on your linux machine without requiring priviliges :p, would you mind posting a link to that sh file?

Thanks!

---

### Post by ryanhaigh on 2008-05-09
Maybe something like a bunch of these

ps aux | grep clamav | grep -v grep
if [ $? == 0 ]; then
avinstalled = 1
fi

---

### Post by ehellmer on 2008-10-04
I have had the same problem with the same file and have not gotten it to work, the file is saved to my desktop, it's called CSA.sh, this is what I've tried:

erik@Automatron:~/Desktop$ cd ~/Desktop
erik@Automatron:~/Desktop$ chmod u+x CSA.sh
erik@Automatron:~/Desktop$ ./CSA.sh
mkdir: cannot create directory `.CSA.TEMP': File exists
./engine: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
./CSA.sh: 12: function: not found
./CSA.sh: 18: mozilla: not found
./CSA.sh: 18: mozilla: not found
./CSA.sh: 19: function: not found
./CSA.sh: 25: netscape: not found
./CSA.sh: 25: netscape: not found
./CSA.sh: 26: function: not found
./CSA.sh: 30: function: not found
./CSA.sh: 33: epiphany: not found
./CSA.sh: 34: function: not found
./CSA.sh: 37: konqueror: not found
./CSA.sh: 38: function: not found
./CSA.sh: 46: seamonkey: not found
./CSA.sh: 46: seamonkey: not found
./CSA.sh: 47: function: not found
./CSA.sh: 50: opera: not found
Error running CSA.sh.  Please call the helpdesk.
rm: cannot remove `tmp.csa': No such file or directory
erik@Automatron:~/Desktop$ 

it then opens up a firefox window telling me there is an error, also the file is removed from my desktop.

Any ideas?

---

### Post by ryanhaigh on 2008-10-06
> ./engine: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

That indiactes to me that you probably need [libstdc++5]("apt://libstdc++5") - The GNU Standard C++ Library v3 installed.

---

### Post by Fede_Fede on 2008-11-01
Sorry to necrobump, but I have the exact same problem, only it's an older version of Linux and it's on the PS3.

How would I go about getting that library on my windows vista pc and transferring it via USB? (mainly just looking for the site to download from, and instructions on what to do to it once the file is on the PS3).

Thx from a complete Linux nab :P

---

